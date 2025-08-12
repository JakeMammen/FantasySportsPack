---
title: "Expected Fantasy Points Receivers"
date: 2025-08-11
categories:
  - Blog
tags:
  - Fantasy Football
  - Xfp
layout: single
classes: wide
---

# 2024 NFL Fantasy Football Expected Stats Analysis

The following analyzes NFL play-by-play data from the 2024 regular season (Weeks 1–18) to calculate **actual and expected fantasy football statistics** for wide receivers (WRs) in a Points Per Reception (PPR) scoring system. Using `nflfastR` data, it focuses on players with at least 8 games played, providing insights into their performance and opportunities.

- **Actual Stats**:
  - Games played
  - Targets (passes thrown to the player)
  - Receptions (catches)
  - Passing and rushing yards
  - Passing and rushing touchdowns
  - Fumbles lost
  - Actual PPR points (1 point per reception, 0.1 points per yard, 6 points per touchdown, 2 points per two-point conversion, -2 points per fumble lost)

- **Expected Stats**:
  - **Expected receptions** (`exp_catches`): Based on completion probability (`cp`) for each pass.
  - **Expected yards** (`exp_yards`): Based on air yards and expected yards after catch for non-missing data plays.
  - **Expected touchdowns** (`exp_td`): Based on plays where the pass could reach the end zone.
  - **Expected PPR points** (`exp_PPR_pts`): Combines expected receptions, yards, and touchdowns using the PPR scoring formula.

![Expected Fantasy Points 2024 Receivers](/assets/images/exp_fp_WR2024.png "Expected Fantasy Points 2024 Receivers")
