# NBA Playoff Performance and Impact Dashboard

A Tableau-based interactive visualization suite designed to analyze NBA playoff performance, player efficiency, and impact metrics. This dashboard complements the machine learning research on playoff Box Plus/Minus (BPM) estimation, translating complex statistical modeling and multidimensional player tracking data into intuitive visual analytics.

---

## Overview

Quantifying player performance in the NBA playoffs presents unique challenges due to heightened defensive intensity, shortened rotations, and strategic game planning. Traditional box-score metrics often fail to capture true court impact and efficiency trade-offs.

This interactive Tableau dashboard bridges statistical research and visual analytics. It enables users to explore:
- Player workload vs. scoring efficiency (Usage Rate vs. True Shooting Percentage vs. Box Plus/Minus).
- Historical playoff impact distributions and longitudinal player trajectories (e.g., LeBron James, Derrick Rose).
- Feature relationships identified through machine learning models (XGBoost, Random Forest) for playoff BPM estimation.

---

## Research Context

This dashboard visualizes data and findings associated with the following study:

> Xiaoyang Su, Yanming Li, Yiheng Chen, and Xiangyu Huang. *From Player Tracking Data to Impact Quantification: An XGBoost Framework for Playoff BPM Estimation.* In **ICCDE 2026: 2026 12th International Conference on Computing and Data Engineering**, 2026. [DOI: 10.1145/3801839.3801860](https://doi.org/10.1145/3801839.3801860)

The accompanying Python modeling repository can be found at [NBA-playoff-data-analysis](https://github.com/yourusername/NBA-playoff-data-analysis).

---

## Live Dashboard

<!-- - **Tableau Public URL**: [View Interactive Dashboard](https://public.tableau.com/) *(Add your published workbook link here)*
- **Tableau Desktop File**: Located in `tableau/nba_playoff_dashboard.twbx` -->

---

## Dashboard Views and Features

### 1. Player Playoff Profile and Core Metrics
- Comprehensive player card displaying traditional and advanced metrics: Points, Rebounds, Assists, Minutes per Game, and Box Plus/Minus (`BPM`).
- Position-adjusted percentiles across offensive and defensive rating metrics.
- Multi-season filtering (1980–present) with criteria matching the research sample (minimum 3 minutes per game and 2 games played).

### 2. Efficiency and Workload Landscape (USG% vs. TS% vs. BPM)
- Scatter and contour plots exploring the relationship between Usage Rate (`USG%`) and True Shooting Percentage (`TS%`).
- Dynamic color encoding by overall BPM and Defensive BPM (`DBPM`), showing how high-volume offensive anchors balance scoring efficiency.
- Interactive threshold lines highlighting league-average true shooting and replacement-level thresholds.

### 3. Longitudinal Trajectories and Case Studies
- Multi-year playoff performance tracking for marquee players (e.g., LeBron James' 15+ playoff runs).
- Visualizing peak vs. twilight playoff runs, workload spikes, and clutch efficiency variances.
- Head-to-head comparison tool allowing side-by-side metric normalization across eras and positions.

### 4. Machine Learning Insights and Metric Importance
- Visual presentation of regression findings from the companion XGBoost study (test R² = 0.9000).
- Variable importance ranking across key features: `pos`, `usg_pct`, `ts_pct`, `ast_pct`, `tov_pct`, `orb_pct`, `drb_pct`, `blk_pct`, `stl_pct`, `pf_per_g`.
- Comparison of single-variable baseline predictions against full multi-feature models.

---

## Data and Preprocessing

The underlying dataset is derived from historical NBA playoff records spanning 1950 to 2022:
- **Raw Source**: `playoffStats.csv` (10,648 player-season records, 51 statistical attributes).
- **Study Filter**: Post-1980 modern era (introduction of the 3-point line), filtered to players with `mp_per_g > 3` and `g > 2`.
- **Target Variable**: Box Plus/Minus (`bpm`), a box-score-based metric estimating a basketball player's on-court contribution per 100 possessions relative to a league-average player.
- **Data Pipeline**: Cleaned, transformed, and aggregated using Python (`pandas`, `numpy`) before import into Tableau Data Extracts (`.hyper`).

---

## Repository Layout

```text
NBA-player-performance-dashboard/
├── data/
│   ├── raw/                 # Original playoff statistics extracts
│   └── processed/           # Aggregated CSVs optimized for Tableau connection
├── tableau/
│   └── nba_playoff_dashboard.twbx   # Packaged Tableau Workbook
├── assets/
│   ├── overview.png         # Main dashboard screenshot
│   ├── usg_ts_scatter.png   # Workload vs efficiency view screenshot
│   └── comparison.png       # Head-to-head comparison view screenshot
├── .gitignore
└── README.md
```

---

## How to Access and Run

### Online (Recommended)
1. Open the [Tableau Public](https://public.tableau.com/) project page in any modern desktop or tablet browser.
2. Use interactive filters (Season slider, Team dropdown, Position selectors) directly on the canvas.

### Local (Tableau Desktop)
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/NBA-player-performance-dashboard.git
   ```
2. Open `tableau/nba_playoff_dashboard.twbx` using Tableau Desktop (v2022.1 or newer).
3. Connect or refresh the data source extract if updating with recent playoff data.

---

## Citation and References

If you use this dashboard, the associated data processing scripts, or the underlying research findings, please cite:

```bibtex
@inproceedings{su2026player,
  author    = {Su, Xiaoyang and Li, Yanming and Chen, Yiheng and Huang, Xiangyu},
  title     = {From Player Tracking Data to Impact Quantification: An XGBoost Framework for Playoff BPM Estimation},
  booktitle = {Proceedings of the 2026 12th International Conference on Computing and Data Engineering (ICCDE 2026)},
  year      = {2026},
  doi       = {10.1145/3801839.3801860}
}
```

---

<!-- ## Author and Contact

- **Author**: Xiaoyang Su
- **GitHub**: [github.com/yourusername](https://github.com/yourusername)
- **Tableau Public**: [public.tableau.com/app/profile/yourusername](https://public.tableau.com/)
- **Email**: your.email@example.com -->
