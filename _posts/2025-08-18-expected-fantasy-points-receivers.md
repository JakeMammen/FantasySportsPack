---
title: "Expected Fantasy Points Receivers"
show_date: true
categories:
  - Blog
tags:
  - Fantasy Football
  - Xfp
layout: single
classes: wide
---

# 2024 NFL Wide Receiver PPR Fantasy Football Analysis

The following analysis evaluates the 2024 NFL regular season performance of wide receivers (WRs) in terms of PPR (Points Per Reception) fantasy football points, comparing actual performance to expected performance. The R script processes player stats, aggregates them, and creates a formatted table using the `gt` package to display both actual and expected metrics for the top 130 WRs who played at least 8 games. A key modification consolidates stats for players like Davante Adams, who played for multiple teams (e.g., NYJ and LV), into a single entry to avoid duplicates.

## Data Used

### Player Stats (`pbp`)
- **Source**: `nflreadr::load_player_stats(seasons = 2024, stat_type = "offense")`
- **Description**: Weekly offensive stats for the 2024 regular season (weeks 1–18).
- **Key Columns**: `player_id`, `player_name`, `recent_team`, `position`, `receptions`, `targets`, `receiving_yards`, `receiving_tds`, `receiving_fumbles_lost`, `receiving_2pt_conversions`, `rushing_yards`, `rushing_tds`, `rushing_fumbles_lost`, `rushing_2pt_conversions`.
- **Processing**: Filtered for WRs, standardized names (e.g., "D.Adams" for Davante Adams), and calculated PPR points with fumble penalties.

### Roster Data (`roster`)
- **Source**: `nflreadr::load_rosters(2024)`
- **Description**: 2024 NFL roster data to confirm player positions and IDs.
- **Key Columns**: `gsis_id`, `position`, `full_name`.

### Expected Fantasy Points (`ff_opportunity`)
- **Source**: `load_ff_opportunity(seasons = 2024, stat_type = "weekly", model_version = "latest")`
- **Description**: Expected fantasy points for WRs based on predictive models.
- **Key Columns**: `player_id`, `full_name`, `week`, `receptions_exp`, `rec_yards_gained_exp`, `rush_yards_gained_exp`, `rec_touchdown_exp`, `rush_touchdown_exp`, `pass_fantasy_points_exp`, `rush_fantasy_points_exp`, `rec_fantasy_points_exp`, `posteam`.
- **Processing**: Aggregated into `receiver_totals` for expected receptions, yards, touchdowns, and total expected PPR points across weeks 1–18.

## Analysis Process

### Data Processing
- **Receiving Stats (`pass_df`)**: Aggregated weekly receiving stats for WRs, calculating PPR points (1 point per reception, 0.1 points per yard, 6 points per TD, 2 points per 2-point conversion, -2 points per fumble lost).
- **Rushing Stats (`rush_df`)**: Aggregated rushing stats for WRs with non-zero rushing yards or TDs, calculating PPR points similarly.
- **Expected Stats (`receiver_totals`)**: Summed expected receptions, yards (receiving + rushing), touchdowns, and fantasy points across the season.
- **Consolidation**: Grouped stats by `player_id` and `player_name` to combine stats for players like Davante Adams who played for multiple teams, assigning a single team (e.g., NYJ for Adams).

### Data Integration
- Combined `pass_df`, `rush_df`, and `receiver_totals` into `avg_fp_df` using `player_id` for accurate joins.
- Filtered for WRs with at least 8 games played to focus on significant contributors.
- Selected columns: `team`, `player_name`, `games`, `targets`, `catches`, `yards`, `td`, `fumbles`, `PPR_pts`, `rec_exp`, `yds_exp`, `tds_exp`, `total_expected_points`.

### Output
- Created a `gt` table (`fp_WR2024`) displaying the top 130 WRs, ranked by actual PPR points.
- **Columns**: Rank, team logo, player name, games played (GP), targets, receptions (Rec), yards (Yds), touchdowns (TD), fumbles (Fum), actual PPR points (FP), expected receptions (Rec (Exp)), expected yards (Yds (Exp)), expected touchdowns (TD (Exp)), and expected PPR points (FP (Exp)).
- **Formatting**: Numeric columns formatted with commas or one decimal place, color gradients for actual (purple) and expected (gold) PPR points, and team logos displayed.

## Results

- **Output Table**: The final table shows the top 130 WRs for the 2024 season, with actual and expected PPR performance metrics. For example, Davante Adams appears as a single entry (under NYJ) with his total stats aggregated across all teams he played for, avoiding duplicates.
- **Key Metrics**:
  - **Actual Metrics**: Receptions, yards (receiving + rushing), touchdowns, fumbles, and total PPR points reflect actual performance.
  - **Expected Metrics**: Expected receptions, yards, touchdowns, and PPR points provide a benchmark for what was predicted based on opportunity and role.
  - **Comparison**: Players exceeding expected points (e.g., high `PPR_pts` vs. `total_expected_points`) likely outperformed their role, while those underperforming may have missed opportunities or faced challenges (e.g., injuries, poor quarterback play).
- **Player Consolidation**: The script ensures players like Davante Adams, who switched teams, have their stats combined into one entry, with the team set to NYJ as per the script’s logic.

## How to Use for Fantasy Football

The analysis and resulting table are valuable for fantasy football players, particularly in PPR leagues, in the following ways:

### Player Evaluation
- **Performance vs. Expectation**: Compare actual PPR points (FP) to expected points (FP (Exp)) to identify overperformers (e.g., players with high efficiency or breakout seasons) and underperformers (e.g., players who didn’t capitalize on opportunities). For example, a WR with 200 actual PPR points but 150 expected points likely had a standout season.
- **Consistency**: Look at games played (GP) to assess reliability. Players with 16–18 games are more dependable than those with 8–10 games due to injuries.
- **Volume and Efficiency**: High targets and receptions indicate a player’s involvement in the offense, while comparing actual yards and TDs to expected values shows efficiency.

### Draft and Trade Decisions
- **Draft Strategy**: For 2025 drafts, prioritize WRs who outperformed expectations in 2024 (high `PPR_pts` vs. `total_expected_points`), as they may continue to exceed their role. Conversely, be cautious with players who underperformed unless their situation (e.g., team, quarterback) improves.
- **Trade Targets**: Identify undervalued players (high expected points but lower actual points) who may rebound in 2025 due to changes in team dynamics or health. For example, Davante Adams’ consolidated stats provide a clear picture of his total production, making him a high-value trade target if his expected points suggest untapped potential.

### Start/Sit Decisions
- While the table is season-long, the comparison of actual vs. expected metrics can inform weekly start/sit decisions in 2025. Players consistently meeting or exceeding expected points are safer starts, while those with lower actual points may be riskier unless their situation improves.

### Team Context
- The team logo and assigned team (e.g., NYJ for Davante Adams) help contextualize performance. For players who changed teams, like Adams, check their 2024 team context (e.g., quarterback quality, offensive scheme) to project 2025 performance.
- Use the table’s team assignments to assess whether a player’s 2024 performance was boosted or hindered by their team’s offensive system.

### Long-Term Planning
- **Dynasty Leagues**: For keeper or dynasty leagues, focus on younger WRs with high expected points, as they may have growing roles. The table helps identify such players by showing their opportunity share (e.g., high `rec_exp` or `yds_exp`).
- **Regression Candidates**: Players with actual PPR points far above expected points may regress in 2025, while those below expected points could improve if their situation stabilizes.

## Practical Tips for Fantasy Football Use
- **Filter the Table**: Export the `fp_WR2024` table to a CSV or use it interactively in R to filter for specific players, teams, or thresholds (e.g., `PPR_pts > 150`) to focus on your roster or league needs.
- **Cross-Reference with 2025 Projections**: Combine this data with 2025 preseason projections (available via `nflreadr` or other fantasy platforms) to see if players’ roles are expected to grow or shrink.
- **Monitor Team Changes**: For players like Davante Adams, verify their 2025 team status (e.g., still with NYJ?) to ensure the table’s team assignments remain relevant.
- **Use Visual Cues**: The table’s color gradients (purple for actual PPR, gold for expected PPR) quickly highlight top performers and potential sleepers. Focus on players with strong colors in both columns for balanced value.

## Notes
- **Data Source**: The analysis relies on `nflreadr` for actual stats and `ff_opportunity` for expected stats, ensuring reliable and up-to-date data as of August 18, 2025.
- **Limitations**: The table is season-long and doesn’t account for weekly variability or 2025 roster changes. Supplement with current news (e.g., via web searches or X posts) for the latest team and player updates.
- **Customization**: If specific tweaks are needed (e.g., adding per-game averages, filtering for specific teams, or including other positions like RBs), the script can be modified further.
- **Davante Adams**: The consolidation ensures his stats are accurately represented as a single entry, making it easier to evaluate his 2024 performance (e.g., total PPR points across NYJ and LV) for fantasy decisions.

This analysis provides a comprehensive tool for fantasy football managers to assess WR performance, identify value, and make informed decisions for drafts, trades, and roster management in PPR leagues.

![Expected Fantasy Points 2024 Receivers]({{ site.baseurl }}/assets/images/exp_fp_WR2024.png "Expected Fantasy Points 2024 Receivers")
