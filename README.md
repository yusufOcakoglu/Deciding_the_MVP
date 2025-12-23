# The Whistle of the Big Four: A Data-Driven Analysis of Referee Bias in Turkish Süper Lig

**Student:** Yusuf Ocakoglu  
**Course:** DSA 210 - Introduction to Data Science

## 1. Motivation
I am Yusuf, and like many in Turkey, I am exposed to football discussions daily. However, I am frankly disturbed by how much the "referee decisions" and "favoritism" debates occupy our country's agenda. Instead of tactical analysis, hours of television and social media time are wasted on conspiracy theories about referees protecting big teams.

This project is born out of a desire to cut through this noise. Instead of subjective arguments, I want to use data science to objectively analyze whether there is a statistical bias protecting the "Big Four" (Galatasaray, Fenerbahçe, Beşiktaş, Trabzonspor) compared to Anadolu teams. My goal is to see if the "protective hand" is a myth or a mathematical reality.

## 2. Hypothesis (The Claim)

* **Null Hypothesis ($H_0$):** There is no statistically significant difference in the disciplinary actions (cards per foul, penalty decisions) taken by referees against the "Big Four" teams versus other teams in the Turkish Süper Lig.
* **Alternative Hypothesis ($H_1$):** The "Big Four" teams receive significantly more favorable treatment (e.g., lower card-to-foul ratios, higher penalty frequency) from referees compared to the rest of the league.

## 3. Data Source and Collection Plan
To insure a robust sample size for Machine Learning, I will analyze data from the **last 10 seasons (2014-2015 to 2023-2024)**.

* **Primary Data (Match Stats):** I will use **football-data.co.uk** and **fbref.com** to obtain match-by-match statistics.
    * *Features:* Date, Home Team, Away Team, Full Time Result, Fouls Committed (Home/Away), Yellow Cards (Home/Away), Red Cards (Home/Away).
* **Enrichment Data (Referee & Team Categories):** 
    * I will enrich the match data by scraping/adding a "Referee" column for each match (sourced from **TFF.org** or **Mackolik**).
    * I will add a categorical feature identifying teams as "Big4" or "Anadolu".
    * I will create a derived dataset of "Referee Profiles" to track individual referee behaviors over time.

## 4. Questions to Address
1.  **The "Immunity" Factor:** Do Big Four teams commit more fouls per yellow card than Anadolu teams? (i.e., is their "tolerance limit" higher?)
2.  **Referee Clustering:** Can we cluster referees into groups (e.g., "Strict", "Lenient", "Big-Team Friendly") based on their decision patterns?
3.  **Home Advantage vs. Big Team Advantage:** Does playing at home affect the referee's decisions more if the home team is one of the Big Four?

## 5. Analysis & Machine Learning Plan

### Exploratory Data Analysis (EDA)
* **Visualization:** I will use box plots and violin plots to compare the distribution of "Fouls per Card" ratios between Big 4 and other teams.
* **Correlation:** Analyzing the correlation between "Team Market Value" (proxy for Big 4 status) and "Penalties Awarded".

### Machine Learning Model
I plan to use **Unsupervised Learning** to uncover hidden patterns in referee behaviors.

* **Algorithm:** K-Means Clustering.
* **Goal:** To group referees based on their statistical tendencies (e.g., avg. cards shown, avg. fouls called, home bias ratio).
* **Interpretation:** If a specific cluster is dominated by referees who statistically favor the Big Four, this will support the Alternative Hypothesis.

## 6. Tools
* **Language:** Python
* **Libraries:**
    * `Pandas` for data manipulation and enrichment.
    * `Matplotlib` / `Seaborn` for visualization.
    * `Scikit-learn` for K-Means Clustering.
    * `SciPy` for statistical hypothesis testing (T-tests).
