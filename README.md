# The Whistle of the Big Four: A Data-Driven Analysis of Referee Bias in Turkish Süper Lig

**Student:** Yusuf Ocakoglu
**Course:** DSA 210 - Introduction to Data Science

## 1. Motivation
I am Yusuf, and like many in Turkey, I am exposed to football discussions daily. However, I am frankly disturbed by how much the "referee decisions" and "favoritism" debates occupy our country's agenda. Instead of tactical analysis, hours of television and social media time are wasted on conspiracy theories about referees protecting big teams.

This project is born out of a desire to cut through this noise. Instead of subjective arguments, I want to use data science to objectively analyze whether there is a statistical bias protecting the "Big Four" (Galatasaray, Fenerbahçe, Beşiktaş, Trabzonspor) compared to Anadolu teams. My goal is to see if the "protective hand" is a myth or a mathematical reality.

## 2. Hypothesis (The Claim)
The core of this analysis focuses on the **"Tolerance Threshold"**: How many fouls can a team commit before receiving a yellow card?

* **Null Hypothesis ($H_0$):** There is no statistically significant difference in the disciplinary tolerance (Fouls per Yellow Card ratio) shown by referees to "Big Four" teams versus other teams in the Turkish Süper Lig.
* **Alternative Hypothesis ($H_1$):** The "Big Four" teams benefit from a significantly higher tolerance threshold (i.e., they are allowed to commit more fouls per card) compared to the rest of the league.

## 3. Data Source and Collection Plan
I am analyzing a comprehensive dataset covering the Turkish Süper Lig seasons from **2014-2015 to 2024-2025**.

* **Source:** Match data compiled from reliable sports data providers (integrated into `TURKISH_SUPER_LIG_FULL_DATASET.csv`).
* **Key Features:**
    * **Match Meta:** Date, Home Team, Away Team, Referee.
    * **Performance Metrics:** Fouls Committed (HF/AF), Yellow Cards (HY/AY), Goals (FTHG/FTAG).
    * **Derived Features:**
        * `Foul_Tolerance`: Calculated as $Total Fouls / Total Yellow Cards$ (handling division by zero).
        * `Is_Big4`: Categorical flag (1 for Big Four, 0 for Anadolu).

## 4. Questions to Address
1.  **The Tolerance Gap:** Is there a statistically significant difference in the "Fouls per Card" ratio between Big Four and Anadolu teams?
2.  **Referee Profiling:** Which individual referees show the highest variance in tolerance when officiating a Big Four match vs. a regular match?
3.  **Predictive Bias:** When we train a Machine Learning model to predict yellow cards, does the **"Team Name"** (Big 4 status) play a significant role, or is the decision based purely on the **"Foul Count"**?

## 5. Analysis & Machine Learning Plan

### Part A: Exploratory Data Analysis & Statistical Testing
* **Visualization:** I will use Box Plots and Violin Plots to visualize the distribution of "Foul Tolerance" scores, comparing the Big Four against the rest of the league.
* **Hypothesis Testing:** Since the data may not follow a normal distribution, I will use the **Mann-Whitney U Test** (Non-parametric T-test) to mathematically confirm if the difference between the two groups is significant ($p < 0.05$).

### Part B: Machine Learning (Predictive Modeling)
Instead of simple clustering, I will employ a **Supervised Learning** approach to quantify bias using Feature Importance analysis.

* **Algorithm:** **Random Forest Regressor**.
* **Target Variable:** Number of Yellow Cards ($Y$).
* **Features ($X$):** Foul Count, Venue (Home/Away), Referee ID, and **Is_Big4**.
* **Bias Detection Method:** I will analyze **Feature Importance**.
    * *Logic:* In a fair system, the number of fouls should be the dominant predictor of yellow cards. If the `Is_Big4` feature ranks high in importance (significantly affecting the model's prediction), it provides data-driven evidence of systemic bias.

## 6. Tools
* **Language:** Python
* **Libraries:**
    * `Pandas` & `NumPy`: For data manipulation and feature engineering.
    * `Seaborn` & `Matplotlib`: For comparative visualizations.
    * `SciPy`: For the Mann-Whitney U statistical test.
    * `Scikit-learn`: For the Random Forest Regressor and feature importance analysis.
