# Movie user rating analysis — Dataset Exploratory Data Analysis

## Table of Contents
- [Tools](#tools)
- [What's here](#whats-here)
- [Key decisions](#key-decisions)
- [Stakeholder Questions](#stakeholder-questions)
- [Findings](#findings)
- [Recommendations](#recommendations)

Exploratory data analysis and cleaning of a ~9,800-movie TMDB dataset,
covering data quality handling, deduplication logic, and trend analysis.

## Tools
power query — with a Power BI dashboard layer.

## What's here
- `PowerBI file` — cleaning via power query, and live dashboard
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
- Are non-English films underrepresented relative to their quality — is there an untapped audience being missed by an English-heavy content slate?

## Findings
<img width="1302" height="383" alt="image" src="https://github.com/user-attachments/assets/13fc7057-8cfa-448b-83a4-bdfd2f5ce545" />

<img width="1388" height="128" alt="image" src="https://github.com/user-attachments/assets/4da02c17-a3ff-423d-a6fa-d8f7bf9920fc" />

- Adventure delivers the strongest combination of audience volume and quality. The genre has 4.3M total votes — among the highest of any genre — paired with a [53.3] average rating, [outperforming/matching] genres with comparable volume. Its top titles (Inception, Interstellar, The Avengers, Deadpool, Avatar) are all recognizable blockbusters, reinforcing that Adventure isn't just heavily watched — it's consistently well-received at scale.

<img width="1953" height="1106" alt="image" src="https://github.com/user-attachments/assets/5b72544d-0842-4242-a085-f3be62409f7a" />

<img width="1957" height="1108" alt="image" src="https://github.com/user-attachments/assets/af471329-a2f2-4c37-af2b-d5e33fb1c917" />

-To test whether Drama's dominance is durable, we compared genre popularity across two non-overlapping periods. In 1970–1999, Drama averaged a 22 popularity rating across 752 movies. In 2000–2021, that rose to 28 across 2,000 movies — but Action also grew significantly in this period, reaching [4M entries / 5M entries]. [ [Action has closed the gap, suggesting Drama's historical lead is narrowing rather than durable.]

<img width="1939" height="1091" alt="image" src="https://github.com/user-attachments/assets/32373ef4-7ce3-433f-8a4d-2e02ead3d172" />

<img width="1954" height="1142" alt="image" src="https://github.com/user-attachments/assets/da6f78c0-1e9e-493d-a9c3-f5a70a3a725a" />

- Japan is the second-largest market by film volume in this dataset, behind English-language releases. Over the last two decades (2004–2024), animation performs comparably well across both markets — Japan (45.13 popularity, 1.17M votes) and English-language releases (45.09 popularity, 1.05M votes) are nearly identical on quality, with Japan holding a modest edge in raw volume. This is notable because English-language animation is dominated by a handful of major studios (e.g., Disney), yet Japan's more fragmented studio landscape matches that performance despite being the smaller of the two markets.

## Recommendations 

- **Genre investment:** If a studio had to greenlight one genre for a high-budget slate, Adventure is the safer bet — it delivers both scale and audience satisfaction, not just one or the other.
- **Long-term genre strategy:** If Action's growth trajectory continues to close the gap on Drama, a studio betting long-term on Drama as the "safe genre" should watch Action closely — the historically dominant genre may not stay dominant, and a content strategy built on yesterday's numbers could miss the shift.
- **Reading recent trends correctly:** Before treating the post-2020 dip as a sign of declining engagement, a team needs to separate "the audience is disengaging" from "the data hasn't caught up yet" — acting on trailing metrics too early can trigger the wrong response to a problem that doesn't actually exist.





