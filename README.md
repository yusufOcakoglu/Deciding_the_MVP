# The Whistle of the Big Four: A Data-Driven Analysis of Referee Bias in Turkish Süper Lig

**Student:** Yusuf Ocakoglu 
**Course:** DSA 210 - Introduction to Data Science

---

## 1. Motivation
As someone living in Turkey, I am exposed to football discussions daily. However, I am deeply disturbed by how much the "referee decisions" and "favoritism" debates occupy our country's agenda. Instead of tactical analysis, hours of television and social media time are wasted on conspiracy theories about referees protecting big teams.

This project is born out of a desire to cut through this noise. Instead of subjective arguments, I want to use data science to objectively analyze whether there is a statistical bias protecting the **"Big Four"** (Galatasaray, Fenerbahçe, Beşiktaş, Trabzonspor) compared to Anadolu teams. My goal is to see if the "protective hand" is a myth or a mathematical reality.

## 2. Hypotheses
The core of this analysis focuses on the **"Tolerance Threshold"**: How many fouls can a team commit before receiving a yellow card?

* **Null Hypothesis ($H_0$):** There is no statistically significant difference in the disciplinary tolerance (Fouls per Yellow Card ratio) shown by referees to "Big Four" teams versus other teams.
* **Alternative Hypothesis ($H_1$):** The "Big Four" teams benefit from a significantly higher tolerance threshold compared to the rest of the league.
* **Pressure Hypothesis ($H_{pressure}$):** Teams in high-stress situations (relegation battle or playing against title contenders) experience significantly lower tolerance thresholds.
* **Stadium Effect Hypothesis:** Referees exhibit a subconscious bias towards the Home team due to crowd pressure, regardless of the team's reputation.
* **Technological Correction Hypothesis:** The introduction of VAR (Video Assistant Referee) has reduced or eliminated the statistical bias observed in previous seasons.

## 3. Data Source and Preparation
I am analyzing a comprehensive dataset covering **8 seasons** of the Turkish Süper Lig (2017-2018 to 2024-2025).

* **Sources:**
    * **FBRef:** Referee assignments and metadata scraped using Python (`BeautifulSoup`).
    * **Football-data.co.uk:** Detailed match statistics (Fouls, Cards, Shots, Corners).
* **Data Cleaning & Handling Anomalies:**
    * **Pandemic Era (2019-2021):** Matches played without fans were treated as a separate category to isolate the "Home Advantage" variable.
    * **Earthquake Impact (2023):** Matches involving Hatayspor and Gaziantep FK after the Feb 2023 earthquake were removed to prevent data skewing from forfeits.
* **Engineered Features:**
    * **`Foul_Tolerance`:** $\frac{\text{Total Fouls}}{\text{Total Yellow Cards}}$ (The primary metric of leniency).
    * **`Pressure`:** $\text{Shots on Target} + \text{Corners}$ (A proxy for offensive intensity).
    * **`Dynamic_Rank`:** Simulated historical league tables calculated for *every match day* to determine the exact standing of each team before the whistle.
    * **`Referee_Profile`:** Clusters generated via Machine Learning (Strict, Balanced, Red Zone).
    * **`Chaos`:** Binary target for matches with >6 yellow cards.

## 4. Key Questions Addressed
1.  **The Tolerance Gap:** Is there a statistically significant difference in "Fouls per Card" between the Big Four and Anadolu teams?
2.  **The VAR Effect:** Did the introduction of technology in 2018 kill the "Invisible Hand"?
3.  **The "Despair" Effect:** Do teams fighting against relegation (Rank 16+) receive harsher treatment compared to mid-table teams?
4.  **The "Victim" Effect:** Does playing against a title contender lower a team's tolerance threshold?
5.  **Reputation vs. Reality:** In a predictive model, which factor is a stronger predictor of cards: the team's "Brand Name" (Is_Big4) or their "Actual Standing" (Rank)?

## 5. Methodology & Analysis

### Part A: Exploratory Data Analysis (EDA) & Visualization
Following Gestalt principles and focusing on the Data-Ink ratio, I utilized advanced visualizations to understand distributions.
* **Violin Plots:** Used to visualize the density of Foul Tolerance across different groups, revealing that averages are often misleading due to outliers.
* **Referee Landscape:** A multi-dimensional scatter plot mapping referees based on their "Strictness" and "Bias Score," identifying distinct behavioral clusters.

### Part B: Statistical Inference (Hypothesis Testing)
Since the foul tolerance data is non-normally distributed, I employed both Parametric and Non-Parametric tests.

1.  **General Bias:** The overall difference between Big 4 and Anadolu teams was **not significant** ($p \approx 0.08$).
2.  **The VAR Correction:**
    * **Pre-VAR:** Significant Bias ($p = 0.014$).
    * **Post-VAR:** No Significant Bias ($p = 0.347$). Technology acted as an equalizer.
3.  **Home vs. Away:** Highly significant difference ($p < 0.00001$). Referees are statistically more lenient towards the Home team.
4.  **Title Contender Effect:** Referees are significantly stricter against opponents of Title Contenders ($p < 0.001$).
5.  **ANCOVA Analysis:** Even after controlling for **Match Pressure** (Covariate), the rank-based bias remained significant.

### Part C: Machine Learning & Advanced Analytics
I moved beyond description to prediction using Scikit-Learn.

1.  **Unsupervised Learning (K-Means Clustering):**
    * Identified 3 distinct referee profiles: *Strict (Disciplinarian)*, *Balanced*, and *Red Zone (High Bias)*.
2.  **Supervised Learning (Random Forest Regressor):**
    * **Result:** The model revealed that a team's **Rank (23.7% importance)** is a significantly stronger predictor of cards than their **Big 4 Status (2.9% importance)**.
    * **Conclusion:** Referees react to **Power**, not just Reputation.
3.  **Chaos Prediction (Classification):**
    * Built a model to predict high-tension matches (>6 Cards).
    * Using Class Weight Balancing, achieved a **Recall of ~74%**, successfully flagging the majority of chaotic games before kickoff.
4.  **Simulation Engine:**
    * Performed "What-If" scenarios (e.g., *Derby with a Strict Referee vs. Biased Referee*), showing that the referee assignment alone can shift the expected card count by ~25%.

## 6. Limitations
* **Missing Event Data:** The dataset does not include direct Red Cards or Penalty Kick decisions, which are often the most controversial aspects.
* **Foul Subjectivity:** All fouls are treated as equal in the count. The data does not distinguish between a "tactical foul" and a "minor foul."
* **Attendance Proxy:** Due to a lack of exact match-by-match attendance logs, "Home Advantage" is analyzed broadly rather than by specific decibel levels.

## 7. Future Work
* **NLP Analysis:** Scraping social media sentiment to measure "External Pressure" on referees before matches.
* **Player Profiling:** Analyzing if specific aggressive players carry a "Reputation Tax" independent of their team.
* **Real-Time Dashboard:** Deploying the Chaos Prediction model as a live tool for sports analysts.

## 8. Tools & Libraries
* **Python:** Core language.
* **Pandas & NumPy:** Data manipulation and Dynamic Ranking algorithm.
* **BeautifulSoup:** Web scraping (FBRef).
* **Seaborn & Matplotlib:** Visualization (Violin, Scatter, Heatmaps).
* **SciPy & Statsmodels:** Statistical testing (Mann-Whitney U, T-Test, OLS, ANCOVA).
* **Scikit-learn:** Machine Learning (K-Means, Random Forest, Poisson Regression).

---
