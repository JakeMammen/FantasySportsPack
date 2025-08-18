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

The following analysis evaluates the 2024 NFL regular season performance of wide receivers (WRs) in terms of PPR (Points Per Reception) fantasy football points, comparing actual performance to expected performance. Using [nflfastr](https://www.nflfastr.com/index.html) and [nflreadr](https://nflreadr.nflverse.com/index.html) data to summarize player stats, aggregates them, and create a formatted table to display both actual and expected metrics for the top 130 WRs who played at least 8 games during the 2024 regular season. A couple of modifications were made to consolidates stats for players, who played for multiple teams, into a single entry to avoid duplication. Additionally, fumbles lost, passing plays where the receiver passed the ball, and rushing plays were included in total Actual Fantasy Points. 

[nflreadr](https://nflreadr.nflverse.com/index.html) offers a function to calculate expected fantasy points called 'ffopportuniity'. I used this function to summarize the expected metrics including: Excpected Receptions, Expected Yards, and Expected Touchdowns for the 2024 fantasy football season. The [ffopportunity](https://ffopportunity.ffverse.com/) function calculates Expected Fantasy Points by preprocessing and applying an xgboost model to nflverse play-by-play data. Expected Fantasy Points are a measure of player opportunities in fantasy football - essentially aiming to quantify how many points the average player would score given a specific situation and opportunity. It uses xgboost and another model trained on public nflverse data from 2006-2020 to do this. [Sydlowski J, Ho T (2024).](https://ffopportunity.ffverse.com/)

## Results and How to Use for Fantasy Football

**Comparison**: Players exceeding expected points (e.g., high `Expected FP` vs. `Actual FP`) likely outperformed their role, while those underperforming may have missed opportunities or faced challenges (e.g., injuries, poor quarterback play).

The analysis and resulting table are valuable for fantasy football players, particularly in PPR leagues, in the following ways:

### Player Evaluation
- **Performance vs. Expectation**: Compare actual PPR points (FP) to expected points (FP) to identify overperformers (e.g., players with high efficiency or breakout seasons) and underperformers (e.g., players who didn’t capitalize on opportunities). For example, a WR with 200 actual PPR points but 150 expected points likely had a standout season.
- **Consistency**: Look at games played (GP) to assess reliability. Players with 16–18 games are more dependable than those with 8–10 games due to injuries.
- **Volume and Efficiency**: High targets and receptions indicate a player’s involvement in the offense, while comparing actual yards and TDs to expected values shows efficiency.

### Draft and Trade Decisions
- **Draft Strategy**: For 2025 drafts, prioritize WRs who outperformed expectations in 2024 (high `Actual FP` vs. `Expected FP`), as they may continue to exceed their role. Conversely, be cautious with players who underperformed unless their situation (e.g., team, quarterback) improves.
- **Trade Targets**: Identify undervalued players (high expected fantasy points but lower actual fantasy points) who may rebound in 2025 due to changes in team dynamics or health.

### Long-Term Planning
- **Dynasty Leagues**: For keeper or dynasty leagues, focus on younger WRs with high expected points, as they may have growing roles. The table helps identify such players by showing their opportunity share (e.g., high `Expected Rec` or `Expected Yds`).
- **Regression Candidates**: Players with actual PPR  fantasy points far above expected points may regress in 2025, while those below expected points could improve if their situation stabilizes.

## Practical Tips for Fantasy Football Use
- **Filter the Table**: Download the 2024 WR PPR stats: [wr_2024_ppr_stats.csv](https://raw.githubusercontent.com/JakeMammen/FantasySportsPack/refs/heads/master/assets/data_tables/wr_2024_ppr_stats.csv) table to a CSV to filter for specific players, teams, or thresholds (e.g., `PPR_pts > 150`) to focus on your roster or league needs.
- **Cross-Reference with 2025 Projections**: Combine this data with 2025 preseason projections to see if players’ roles are expected to grow or shrink.
- **Monitor Team Changes**: For players like Davante Adams, verify their 2025 team status (e.g., still with NYJ?) to ensure the table’s team assignments remain relevant.
- **Use Visual Cues**: The table’s color gradients (purples for actual PPR and expected PPR) quickly highlight top performers and potential sleepers. Focus on players with strong colors in both columns for balanced value. Additionally we can utilize the FORP column to analyze over or underperforming players based soley on opportunity. FORP is calculated by subtracting a player's (opportunity-adjusted) expected fantasy points from their actual fantasy point total. A positive FORP value indicates a player performing better than expected based on their opportunities, while a negative value suggests underperformance. Obviously this does not take into account highly skilled players (e.g. J.Chase, J.Jefferson, or M.Nabers, etc.). These players would need to be judged based off other factors that could contribute to actual fantasy points over the course of a season. 

## Notes
- **Data Source**: The analysis relies on `nflreadr` for actual stats and `ff_opportunity` for expected stats, ensuring reliable and up-to-date data as of August 18, 2025.
- **Limitations**: The table is season-long and doesn’t account for weekly variability or 2025 roster changes. Supplement with current news (e.g., via web searches or X posts) for the latest team and player updates.

This analysis provides a comprehensive tool for fantasy football managers to assess WR performance, identify value, and make informed decisions for drafts, trades, and roster management in PPR leagues.

![Expected Fantasy Points 2024 Receivers]({{ site.baseurl }}/assets/images/exp_fp_WR2024.png "Expected Fantasy Points 2024 Receivers")
