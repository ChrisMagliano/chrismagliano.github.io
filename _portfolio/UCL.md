---
title: "Exploratory Data Analysis of UEFA Champions League 1955-2023"
excerpt: "Data Analysis of the UEFA Champions League statistics from 1955 to 2023."
collection: portfolio
category: "Data Science"
tags:
  - Python
  - EDA
  - Data Visualization
header:
  teaser: "/images/portfolio_ucl/Logo_UEFA_Champions_League.png"
---
![Illustration of combining vision and language modalities](/images/portfolio_ucl/Logo_UEFA_Champions_League.png){:.align-right width="200px"}

# Table of Contents
- [Project Overview](#project-overview)
- [Data Sources & tools](#data-sources-and-tools)
- [Data Cleaning & Preparation](#data-cleaning-and-preparation)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Results and Findings](#results-and-findings)
- [Recommendations and Insights](#recommendations-and-insights)
- [Limitations](#limitations)
- [References](#references)

## Project Overview

How has European club football evolved since the first European Cup in 1955? This project explores the history of the [UEFA Champions League](https://www.uefa.com/uefachampionsleague/)—known as the *European Cup* until its 1992 rebranding—from the 1955–56 through the 2022–23 season.

Using historical club-performance and final-match datasets, I investigate **which teams and countries dominate**, how performance relates to experience, and how finals have changed in terms of goals, home-country advantage, and attendance.

## Data Sources and tools

Two datasets, sourced from [Kaggle](https://www.kaggle.com/datasets/fardifaalam170041060/champions-league-dataset-1955-2023), underpin the analysis:

- **`UCL_AllTime_Performance_Table.csv`** — club-level totals: matches (`M.`), wins (`W`), draws (`D`), losses (`L`), goals for/against (`Goals`), goal difference (`Dif`) and points (`Pt`).
- **`UCL_Finals_1955-2023.csv`** — season-level final results: season, winners and runners-up (with their countries), score, venue, attendance and match notes (including extra time, penalties and replays).

The original dataset description is credited to [Fardifa Fathmiul Alam](https://www.kaggle.com/datasets/fardifaalam170041060/champions-league-dataset-1955-2023). Analysis uses Python for data preparation, visualization and statistical comparisons.

## Data Cleaning & Preparation

Data cleaning and feature preparation—including team-performance ratios and final-match attributes—are documented in the [GitHub repository](https://github.com/ChrisMagliano/EDA_UEFA_Champions_League). The underlying code is the authoritative reference for implementation details.

## Exploratory Data Analysis

The analysis addresses four questions:

1. Which clubs have the most appearances, victories and final appearances?
2. How are titles distributed across countries and across time?
3. How do scorelines and home-country participation relate to final outcomes?
4. How has final attendance evolved, and how does it differ across host countries?

## Results and Findings

### Team performances

**Appearances and victories.** Real Madrid leads the historical ranking by matches played and wins; Bayern Munich and Barcelona follow among the most frequently appearing clubs.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/top10_matches.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 1: Distribution of the top 10 teams for number of played matches in UCL.</em></p>
</div>


**Win/loss ratio.** A different ranking emerges when comparing wins with losses rather than counting wins alone. Bayern Munich and Barcelona have slightly higher ratios than Real Madrid in this dataset. To reduce instability from small samples, this comparison includes only clubs with **at least 50 matches**. Historical context for [Manchester City](https://www.uefa.com/uefachampionsleague/history/clubs/52919--man-city/) and [Paris Saint-Germain](https://www.uefa.com/uefachampionsleague/history/clubs/52747--paris-sg/) is supplemented with UEFA club histories.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/top10_wlratio.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 2: Distribution of the top 10 teams for win/loss ratio in UCL.</em></p>
</div>


**Finals won and lost.** Real Madrid leads with **14 titles** in the period analyzed, followed by AC Milan and Bayern Munich with **7 each**. Juventus has the most final defeats (**7**), ahead of Bayern Munich and Benfica (**5 each**).


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/top_bot_finalist.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 3: On left panel, distribution of the top five teams per UCL titles. On right panel, distribution of the top five teams per number of lost UCL finals.</em></p>
</div>


**Matches versus wins.** Clubs with more matches generally record more wins. Real Madrid, for example, has **291 wins in 486 matches** (approximately **59.9%**). The chart compares observed totals with reference win-rate lines and fits linear and quadratic models. The quadratic model achieves a lower reported MSE (**19 versus 49**) and higher R² (**0.98 versus 0.95**). This is a descriptive fit, however: it does **not** establish that additional matches cause better performance. Stronger teams may both qualify more frequently and win more often, and the tournament format changed over time. For definitions of [R²](https://en.wikipedia.org/wiki/Coefficient_of_determination), [MSE](https://en.wikipedia.org/wiki/Mean_squared_error) and the [law of large numbers](https://en.wikipedia.org/wiki/Law_of_large_numbers), see the linked references.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/matches_wins.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 4: Left panel, distribution of the number of wins against the number of matches alongside linear relationship with coefficient equal to 1/3, 1/2 and 2/3. Right panel, linear and quadratic fit of the data.</em></p>
</div>


**Correlation structure.** The club-level correlation matrix summarizes relationships among participation and performance metrics. Interpret these correlations in light of the competition's changing format, especially the transition from knockout-only competition to formats featuring a group stage ([background](https://en.wikipedia.org/wiki/UEFA_Champions_League)).


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/all_time_corr.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 5: Correlation matrix of the `all_time` dataset.</em></p>
</div>


**Geographical concentration.** Titles are concentrated in Western Europe. In the original geographical aggregation, Spain leads with **19**, England has **15**, and Italy has **12**; Germany is reported with **9** when historical West German titles are grouped with Germany. Historical borders and country classifications matter when comparing this map with the year-by-year chart.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/geo_pandas.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 6: Geospatial distribution of UCL trophies in Europe. </em></p>
</div>


**Titles through time.** The year-by-country heatmap reveals changing periods of dominance: Real Madrid's early five-title run, the Dutch clubs' four consecutive wins from 1970 to 1973, and Spain's renewed prominence during the 2010s. It also makes visible the broader variety of winning countries in intervening decades. The display retains historical labels such as West Germany and Yugoslavia where present in the original dataset.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/win_country_years.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 7: UCL titles by winning country and year.</em></p>
</div>


### Finals analysis

#### Scores and goals

**Most common scorelines.** A **1–0** result is the most frequent final score in the source analysis (**19 occurrences**), followed by **2–1** (**10**) and **2–0** (**8**). These figures suggest that narrow margins are common, but score frequencies alone cannot identify teams' tactical intentions.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/top5_scores.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 8: Top five scores in a UCL final.</em></p>
</div>


**Goals by decade.** Average total goals fluctuate substantially across decades. The 1960 final, [Real Madrid 7–3 Eintracht Frankfurt](https://www.uefa.com/uefachampionsleague/match/61542--real-madrid-vs-eintracht-frankfurt/), is a notable high-scoring example. The 1980s and the three 2020–2023 finals in the dataset have relatively low averages (**1.40** and **1.00**, respectively). Comparisons with the 2020s should be treated cautiously because the decade is incomplete.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/goals_per_decade.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 9: Mean total goals in a UCL final per decade.</em></p>
</div>


**How finals were decided.** According to the source classification, **51** finals ended in regulation time, **11** were decided on penalties, **5** in extra time, and **2** required a replay (see the [1974 European Cup final](https://en.wikipedia.org/wiki/1974_European_Cup_final)).


<div style="float: right; width: 600px; text-align: center;">
    <img src="/images/portfolio_ucl/notes_pie.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 10: UCL Finals by how the matches were decided.</em></p>
</div>


**Home-country advantage.** Among the subset of finals with a club competing in its home country, the home-country side won **58.3%** and lost **41.7%**. This is a descriptive association; the sample is small and does not establish a causal home advantage.


<div style="float: right; width: 600px; text-align: center;">
    <img src="/images/portfolio_ucl/pie_home.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 11: Outcomes for finalists playing in their home country.</em></p>
</div>


**Goals by home-country status.** The analyzed subset reports an average of **1.67** goals for the home-country team versus **1.00** for the opponent. The distributions are non-normal under the reported [Shapiro–Wilk test](https://en.wikipedia.org/wiki/Shapiro%E2%80%93Wilk_test) (p < 0.05). A [Mann–Whitney U test](https://en.wikipedia.org/wiki/Mann%E2%80%93Whitney_U_test) gives **p = 0.09**, so the difference is **not statistically significant at the 5% level**. Both samples contain 12 observations.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/goals_home_visitor.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 12: Goal distributions for home-country finalists and their opponents, with KDE.</em></p>
</div>


#### Attendance

**Attendance over time.** Final attendance varies widely with stadium capacity and historical circumstances. The source highlights **124,000** spectators at the 1957 final and **127,621** at Hampden Park in 1960. The **2020 final had no spectators** because of COVID-19 restrictions, with capacity restrictions continuing into 2021.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/attendance_years.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 13: Attendance during UCL final across the years.</em></p>
</div>


**Attendance and home-country participation.** Finals featuring a club from the host country show higher attendance in the source sample. The reported Mann–Whitney U test gives **p < 0.05**, indicating a difference between the distributions. This does not by itself isolate the effect of local participation from stadium size, era or other factors.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/attendance_home.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 14: Final attendance with versus without a home-country finalist.</em></p>
</div>


**Attendance by host country.** Average attendance is sensitive to the number of finals hosted: countries with very few observations can rank highly because of a single large event. The second panel therefore restricts the comparison to countries hosting **at least four finals**, producing a more stable descriptive comparison.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/top_venues.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 15: Host-country average final attendance: overall (left) and countries hosting at least four finals (right).</em></p>
</div>


**Finals correlation matrix.** The final chart summarizes relationships among numeric final-match variables. No strong additional association is identified beyond the modest positive relationship between attendance and the home-country indicator discussed above.


<div style="float: right; width: 800px; text-align: center;">
    <img src="/images/portfolio_ucl/finals_corr.png" alt="Illustration of combining vision and language modalities" style="width: 100%;">
    <p><em>Figure 16: Correlation matrix of the `finals` dataset.</em></p>
</div>


## Recommendations and Insights

### Insights

- **Dominance depends on the metric.** Real Madrid leads by total titles and wins; efficiency ratios can rank other clubs higher.
- **Success is geographically concentrated.** Western European clubs account for most titles, though historical country boundaries affect totals.
- **Participation and wins move together.** The quadratic fit describes the observed pattern better than the linear fit, without proving an experience-driven causal effect.
- **Finals are frequently close.** The 1–0 scoreline is the most common; scoring patterns vary by decade.
- **Home-country effects need caution.** Home-country finalists win more often descriptively, but the goals comparison is not significant at the 5% level.
- **Attendance reflects context.** Venue capacity, host-country participation and pandemic restrictions all matter.

### Recommendations

- Compare teams using **both totals and normalized rates**, with minimum-sample thresholds.
- Treat historical format changes and country classifications explicitly in longitudinal comparisons.
- Investigate the matches–wins relationship using season-level data and controls before interpreting it as learning.
- When evaluating home-country effects, account for opponent strength, venue capacity and time period.
- Report host-country attendance averages alongside the **number of finals hosted**.

## Limitations

- The finals dataset does not include potentially relevant match-level variables such as weather, cards or possession.
- Aggregate club statistics do not track team strength or participation season by season.
- Small samples limit the precision of home-country comparisons and recent-decade averages.
- Historical country definitions and competition-format changes complicate comparisons over time.
- Observational relationships and model fit should not be interpreted as causal evidence.

## References

1. [Manchester City UCL History](https://www.uefa.com/uefachampionsleague/history/clubs/52919--man-city/)
2. [Paris Saint-Germain UCL History](https://www.uefa.com/uefachampionsleague/history/clubs/52747--paris-sg/)
3. [UEFA Champions League](https://en.wikipedia.org/wiki/UEFA_Champions_League)

The complete Python analysis is available on [GitHub](https://github.com/ChrisMagliano/EDA_UEFA_Champions_League). For questions, contact chrismagliano.cm@gmail.com or christian.magliano@unina.it.
