# Netflix Movie Analytics — Dataset Exploratory Data Analysis

Exploratory data analysis and cleaning of a ~9,800-movie TMDB dataset,
covering data quality handling, deduplication logic, and trend analysis.

## Tools
Python (pandas), Jupyter — with a Power BI dashboard layer [in progress].

## What's here
- `movie_eda.ipynb` — cleaning + exploratory analysis
- `mymoviedb.csv` — source data (public TMDB export)

## Key decisions
- **Load integrity:** the raw file had inconsistent line terminators that broke
  a standard read. Pinned the line terminator to retain all 9,827 rows rather
  than dropping malformed lines — zero data loss.
- **Duplicates:** 314 titles repeat, but 0 rows share both title and release
  date (and 0 are fully identical), confirming these are sequels/remakes, not
  duplicate records — all retained.
- **Types:** converted Release_Date from text to datetime to enable time-based analysis.

## Findings
WIP
