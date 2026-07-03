# Movie user rating analysis — Dataset Exploratory Data Analysis

Exploratory data analysis and cleaning of a ~9,800-movie TMDB dataset,
covering data quality handling, deduplication logic, and trend analysis.

## Tools
power query — with a Power BI dashboard layer.

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

## Stakeholder Questions

- Which genres deliver the best combination of audience volume *and* quality, rather than just popularity?
- Is Drama's dominance in total votes a durable trend, or inflated by decades of accumulated back-catalog volume?
- What's driving the falloff in vote volume after ~2020 — a real engagement decline, or recent titles simply not having had time to accumulate votes yet?

## Findings
<img width="1302" height="383" alt="image" src="https://github.com/user-attachments/assets/13fc7057-8cfa-448b-83a4-bdfd2f5ce545" />
<img width="1388" height="128" alt="image" src="https://github.com/user-attachments/assets/4da02c17-a3ff-423d-a6fa-d8f7bf9920fc" />

- Adventure delivers the strongest combination of audience volume and quality. The genre has 4.3M total votes — among the highest of any genre — paired with a [53.3] average rating, [outperforming/matching] genres with comparable volume. Its top titles (Inception, Interstellar, The Avengers, Deadpool, Avatar) are all recognizable blockbusters, reinforcing that Adventure isn't just heavily watched — it's consistently well-received at scale.

<img width="1953" height="1106" alt="image" src="https://github.com/user-attachments/assets/5b72544d-0842-4242-a085-f3be62409f7a" />

<img width="1957" height="1108" alt="image" src="https://github.com/user-attachments/assets/af471329-a2f2-4c37-af2b-d5e33fb1c917" />

-To test whether Drama's dominance is durable, we compared genre popularity across two non-overlapping periods. In 1970–1999, Drama averaged a 22 popularity rating across 752 movies. In 2000–2021, that rose to 28 across 2,000 movies — but Action also grew significantly in this period, reaching [4M entries / 5M entries]. [Drama still leads Action by X points, suggesting its dominance does not hold in the modern era. / Action has closed the gap, suggesting Drama's historical lead is narrowing rather than durable.]

-Votes have not been recorded for this time range.
