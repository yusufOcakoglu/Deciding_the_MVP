# The Whistle of the Big Four: A Data-Driven Analysis of Referee Bias in Turkish Süper Lig

**Student:** Yusuf Ocakoglu  
**Course:** DSA 210 - Introduction to Data Science

## 1. Motivation
As someone living in Turkey, I am exposed to football discussions daily. However, I am deeply disturbed by how much the "referee decisions" and "favoritism" debates occupy our country's agenda. Instead of tactical analysis, hours of television and social media time are wasted on conspiracy theories about referees protecting big teams.

This project is born out of a desire to cut through this noise. Instead of subjective arguments, I want to use data science to objectively analyze whether there is a statistical bias protecting the "Big Four" (Galatasaray, Fenerbahçe, Beşiktaş, Trabzonspor) compared to Anadolu teams. My goal is to see if the "protective hand" is a myth or a mathematical reality.

## 2. Hypotheses
The core of this analysis focuses on the **"Tolerance Threshold"**: How many fouls can a team commit before receiving a yellow card?

* **Null Hypothesis ($H_0$):** There is no statistically significant difference in the disciplinary tolerance (Fouls per Yellow Card ratio) shown by referees to "Big Four" teams versus other teams in the Turkish Süper Lig.
* **Alternative Hypothesis ($H_1$):** The "Big Four" teams benefit from a significantly higher tolerance threshold compared to the rest of the league.
* **Pressure Hypothesis ($H_{pressure}$):** Teams in high-stress situations (relegation battle or playing against title contenders) experience significantly lower tolerance thresholds.

## 3. Data Source and Preparation
I am analyzing a comprehensive dataset covering the Turkish Süper Lig seasons from **2017-2018 to 2024-2025**.

* **Source:** Match data compiled from reliable sports data providers (integrated into `TURKISH_SUPER_LIG_FULL_DATASET.csv`).
* **Key Features:** Match Meta (Date, Teams, Referee), Performance Metrics (Fouls, Cards, Goals), Half-time Scores.
* **Engineered Features:**
    * `Rank` & `Points`: Simulated historical league tables calculated for every match day to determine the exact standing of each team *before* the whistle.
    * `Foul_Tolerance`: $Total Fouls / Total Yellow Cards$.
    * `Is_Title_Contender`: Flag for teams in the Top 3 during the second half of the season.
    * `Is_Relegation_Zone`: Flag for teams in the bottom 4 positions.

## 4. Key Questions Addressed
1.  **The Tolerance Gap:** Is there a statistically significant difference in "Fouls per Card" between the Big Four and Anadolu teams?
2.  **The "Despair" Effect:** Do teams fighting against relegation (Rank 16+) receive harsher treatment compared to mid-table teams?
3.  **The "Victim" Effect:** Does playing against a title contender lower a team's tolerance threshold (do referees protect the favorite by punishing the opponent)?
4.  **Reputation vs. Reality:** In a predictive model, which factor is a stronger predictor of cards: the team's "Brand Name" (Is_Big4) or their "Actual Standing" (Rank)?

## 5. Methodology & Analysis

### Part A: Statistical Testing (W3, W4, W6)
Since the foul tolerance data is non-normally distributed and contains outliers, I employed **Non-Parametric Testing**.
* **Test:** Mann-Whitney U Test.
* **Key Finding:** We found a highly significant difference ($p < 0.001$) in the treatment of teams playing against title contenders. Referees are much stricter against the opponents of teams in the championship race.



### Part B: Exploratory Data Analysis & Visualization (W2a)
Following Gestalt principles and focusing on the Data-Ink ratio, I used **Violin Plots** to visualize distributions. This allowed for an "X-ray" view of the data density rather than just looking at misleading averages.
* **Referee Landscape:** A multi-dimensional scatter plot was created to map referees based on their "Strictness" (Avg Cards) and "Bias Score" (Big 4 vs. Others).

### Part C: Machine Learning & Feature Importance (W8, W9)
I utilized a **Random Forest Regressor** to quantify the impact of different factors on yellow card counts.
* **Result:** The model revealed that a team's **Rank** (24% importance) is a significantly stronger predictor of cards than their **Big 4 Status** (3% importance). This suggests that referees are more influenced by the competitive "power" and immediate standing of a team rather than just their historical name.



## 6. Limitations
While the analysis is robust, it acknowledges several constraints:

1.  **Missing Event Data:** The dataset does not include direct Red Cards or Penalty Kick decisions, which are often the most controversial aspects of referee bias.
2.  **Foul Subjectivity:** All fouls are treated as equal in the count. The data does not distinguish between a "tactical foul" and a "minor foul."
3.  **Simulation Accuracy:** League rankings were simulated based on match results. While highly accurate, they may not perfectly reflect mid-season administrative point deductions by the TFF.
4.  **Attendance Proxy:** Due to lack of exact match-by-match attendance logs, "Crowd Pressure" was estimated using stadium capacity and match importance as proxies.

## 7. Tools & Libraries
* **Python:** Core language for analysis.
* **Pandas & NumPy:** Data cleaning and ranking simulation.
* **Seaborn & Matplotlib:** Advanced visualizations (Violin Plots, Landscape Scatter).
* **SciPy:** Statistical testing (Mann-Whitney U, Shapiro-Wilk).
* **Scikit-learn:** Random Forest modeling and Feature Importance analysis.
