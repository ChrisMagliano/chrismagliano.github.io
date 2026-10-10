---
title: "Exploratory Data Analysis of the Most Streamed Spotify Songs"
excerpt: "Exploring streaming popularity, release patterns, and cross-platform engagement through data visualization."
collection: portfolio
category: "Data Science"
tags:
  - Python
  - EDA
  - Data Visualization
header:
  teaser: "/images/spotify_logo.png"
---

![Spotify logo](/images/spotify_logo.png){:.align-right width="200px"}

# Table of Contents
- [Project Overview](#project-overview)
- [Data Sources & Tools](#data-sources--tools)
- [Data Cleaning & Preparation](#data-cleaning--preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations and Insights](#recommendations-and-insights)
- [Limitations](#limitations)
- [References](#references)

## Project Overview

This project explores the characteristics of highly streamed songs on [Spotify](https://www.spotify.com/) using a dataset compiled up to 2024. The analysis investigates release patterns, artist popularity, cross-platform performance, explicit-content classifications, and relationships between engagement metrics and *Track Score*.

The dataset is a selected sample of popular tracks, **not a representative record of every song released on Spotify**. All findings should be interpreted within that scope.

## Data Sources & Tools

The [Kaggle dataset](https://www.kaggle.com/datasets/pragyantiwari/spotify-refined-explicity-classified-1) contains approximately **4,600 tracks and 30 original features**, including release dates, artists, Spotify streams, cross-platform engagement, and Track Score. The analysis uses Python for cleaning, visualization, and exploratory statistics.

Full preprocessing and analysis code: [GitHub repository](https://github.com/ChrisMagliano/EDA_spotify_songs/tree/main).

## Data Cleaning & Preparation

After removing duplicates and nonessential columns, the working dataset contained **4,598 tracks and 22 features**. Missing numerical values were imputed using the median, which is less sensitive to outliers than the mean. This introduces uncertainty, particularly for features with substantial missingness.

## Exploratory Data Analysis

The analysis addresses five questions:

1. How do release years and months vary among the sampled tracks?
2. Which songs and artists lead the Spotify, YouTube, and TikTok metrics?
3. How do artist output and average Track Score relate?
4. Do explicit and non-explicit tracks differ in Track Score or release patterns?
5. Which engagement metrics are associated with Track Score?

## Results and Findings

### 1. Release patterns

<div style="text-align: center; max-width: 800px; margin: 1.5rem auto;">
  <img src="/images/portfolio_spotify/num_tracks_year.png" alt="Number of sampled tracks by release year" style="width: 100%;">
  <p><em>Figure 1. Number of sampled tracks by release year, through 2023.</em></p>
</div>

**Figure 1** shows a marked increase in the number of sampled songs released in recent years, particularly after 2015. Recent years approach 400 tracks per year in the sample, compared with much smaller counts in earlier periods. Because the dataset selects popular tracks, this pattern **cannot by itself establish growth in total industry releases**.

<div style="text-align: center; max-width: 800px; margin: 1.5rem auto;">
  <img src="/images/portfolio_spotify/months.png" alt="Sampled tracks by release month" style="width: 100%;">
  <p><em>Figure 2. Distribution of sampled tracks by release month, through 2023.</em></p>
</div>

**Figure 2** identifies **January (431 tracks; 9.3%)** and **October (384; 8.3%)** as the most common release months in this sample, compared with **April (257; 5.5%)** and **February (267; 5.8%)**. These differences may reflect release schedules, sampling effects, or seasonal dynamics; they do not establish an optimal release month.

### 2. Most popular tracks and artists across platforms

<div style="text-align: center; max-width: 800px; margin: 1.5rem auto;">
  <img src="/images/portfolio_spotify/most_streamed_tracks.png" alt="Leading tracks across Spotify, YouTube and TikTok" style="width: 100%;">
  <p><em>Figure 3. Leading tracks by the dataset's Spotify, YouTube, and TikTok engagement metrics.</em></p>
</div>

In the dataset, **“Blinding Lights” (The Weeknd)** leads Spotify streams, followed by **“Shape of You” (Ed Sheeran)**. On YouTube, **“Baby Shark”** leads views, followed by **“Despacito”**. TikTok is dominated by viral sounds such as **“Monkeys Spinning Monkeys” (Kevin MacLeod)** and **“Love You So” (The King Khan & BBQ Show)**.

**Important:** TikTok sound uses/views, YouTube video views, and Spotify audio streams measure different behaviors. Their absolute totals should not be interpreted as a like-for-like ranking of platform listening.

<div style="text-align: center; max-width: 800px; margin: 1.5rem auto;">
  <img src="/images/portfolio_spotify/most_streamed_artists.png" alt="Leading artists across platforms" style="width: 100%;">
  <p><em>Figure 4. Leading artists by the dataset's Spotify, YouTube, and TikTok metrics.</em></p>
</div>

**Bad Bunny, The Weeknd, and Drake** rank prominently on Spotify; **Ed Sheeran, Bad Bunny, and Taylor Swift** on YouTube. TikTok's leading artists differ because highly reusable audio clips can accumulate exceptionally large engagement counts.

### 3. Artist productivity and Track Score

<div style="text-align: center;">
  <div style="display: inline-block; width: 49%; vertical-align: top; text-align: center;">
    <img src="/images/portfolio_spotify/artists_tracks.png" alt="Top five artists by sampled track count" style="width: 100%;">
    <p><em>Figure 5. Top five artists by number of sampled tracks.</em></p>
  </div>
  <div style="display: inline-block; width: 49%; vertical-align: top; text-align: center;">
    <img src="/images/portfolio_spotify/artists_score_tracks.png" alt="Average Track Score of the five artists" style="width: 100%;">
    <p><em>Figure 6. Mean Track Score for the artists in Figure 5.</em></p>
  </div>
</div>

**Taylor Swift and Drake** each appear with **63 tracks** in the sample, but have lower average Track Scores than some less-represented artists in this comparison. The source analysis reports that using the median does not change the ranking. This is a descriptive association, not evidence that releasing more tracks reduces popularity.

### 4. Explicit versus non-explicit tracks

<div style="text-align: center;">
  <div style="display: inline-block; width: 49%; vertical-align: top; text-align: center;">
    <img src="/images/portfolio_spotify/class_pie.png" alt="Explicit and friendly classification" style="width: 100%;">
    <p><em>Figure 7. Explicit versus friendly classification in the sample.</em></p>
  </div>
  <div style="display: inline-block; width: 49%; vertical-align: top; text-align: center;">
    <img src="/images/portfolio_spotify/track_score_class.png" alt="Track Score by explicit classification" style="width: 100%;">
    <p><em>Figure 8. Track Score by explicit classification.</em></p>
  </div>
</div>

Approximately **76%** of sampled tracks are classified as *friendly* and **24%** as *explicit*. Mean Track Scores are **41.46** and **42.8**, respectively. The original analysis reports no statistically significant difference; the underlying test specification and p-value should be checked in the notebook before making a formal inferential claim.

<div style="text-align: center; max-width: 800px; margin: 1.5rem auto;">
  <img src="/images/portfolio_spotify/expl_friend_years.png" alt="Explicit and friendly tracks by release year" style="width: 100%;">
  <p><em>Figure 9. Sampled explicit and friendly tracks by release year, through 2023.</em></p>
</div>

**Figure 9** shows different historical patterns for the two classes, including a decline in explicit tracks within the sample around **2002–2006**. The dataset alone cannot establish whether this reflects changes in censorship, genre popularity, distribution, or the sampling of highly streamed songs.

### 5. Correlation analysis

<div style="text-align: center; max-width: 800px; margin: 1.5rem auto;">
  <img src="/images/portfolio_spotify/df_corr.png" alt="Spearman correlation matrix for track metrics" style="width: 100%;">
  <p><em>Figure 10. Spearman rank-correlation matrix of selected dataset features.</em></p>
</div>

The [Spearman rank correlation coefficient](https://en.wikipedia.org/wiki/Spearman%27s_rank_correlation_coefficient) summarizes monotonic associations, ranging from **−1 to +1**. It is suitable for ranked relationships and does not require normally distributed variables.

The matrix suggests that **Track Score** has no single strongly dominant correlate among the selected features, although **Spotify Playlist Reach** and **Spotify Popularity** show positive associations. Stronger clusters appear among metrics within each platform:

- **Spotify:** Streams, Playlist Count, Playlist Reach, and Popularity.
- **YouTube:** Views and Likes.
- **TikTok:** Posts, Likes, and Views.

Spotify Streams are also positively associated with Shazam counts. These patterns describe **correlation, not causal mechanisms**: they cannot establish that Shazam searches cause subsequent Spotify plays, or that platform algorithms directly produce the observed associations.

## Recommendations and Insights

- **Release timing:** January and October are relatively common in this sample, but there is insufficient evidence to identify an optimal release month.
- **Platform differences:** Viral TikTok audio, YouTube video views, and Spotify streams capture distinct forms of engagement; cross-platform comparisons require metric normalization.
- **Artist output:** More sampled tracks do not necessarily imply a higher average Track Score.
- **Explicit content:** The two classifications have similar mean Track Scores in the reported analysis.
- **Track popularity:** No single observed feature fully explains Track Score; playlist reach and platform popularity warrant further investigation.

## Limitations

- **Selection bias:** The dataset contains popular tracks rather than the complete Spotify catalog. It cannot support claims about overall release volume or industry-wide behavior.
- **Missing data:** Median imputation can affect distributions and correlations. Results should be checked against complete-case or alternative-imputation analyses.
- **Metric comparability:** Spotify streams, YouTube views, and TikTok engagement are not directly equivalent.
- **Observational design:** Correlations and temporal patterns do not establish causation.
- **Data validation:** The original text describes **1,071** as a minimum Spotify-stream threshold, but later calls it a maximum; this should be verified against the raw CSV. Statistical-significance claims should also be checked against the underlying code.

## References

- [Spotify](https://www.spotify.com/)
- [Kaggle: Spotify dataset](https://www.kaggle.com/datasets/pragyantiwari/spotify-refined-explicity-classified-1)
- [Spearman's rank correlation coefficient](https://en.wikipedia.org/wiki/Spearman%27s_rank_correlation_coefficient)
- [Super Bowl XXXVIII halftime show controversy](https://en.wikipedia.org/wiki/Super_Bowl_XXXVIII_halftime_show_controversy#:~:text=The%20Super%20Bowl%20XXXVIII%20halftime,Timberlake%20to%20the%20viewing%20public.) — historical context discussed in the original version, not established as a causal explanation by this dataset.
- [Full analysis and preprocessing code on GitHub](https://github.com/ChrisMagliano/EDA_spotify_songs/tree/main)

For questions or feedback: chrismagliano.cm@gmail.com · christian.magliano@unina.it
