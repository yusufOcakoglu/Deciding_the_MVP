# Deciding the MVP: A Data-Driven Analysis of NBA Player Value
I have decided to choose a claim to investigate for my DSA 210 project: "What factors actually determine the NBA's Most Valuable Player?"
This project plan is submitted to fulfill the Project Proposal requirement due on 31 October.

# Hypothesis (My Claim)
•	Null Hypothesis (): There is no statistically significant difference in predictive power between traditional statistics (like Points Per Game) and advanced metrics (like Win Shares) when identifying the MVP. Team success (win percentage) is also not a primary determining factor.

•	Alternative Hypothesis (): Advanced metrics (e.g., Win Shares, PER) combined with team success (win percentage) are significantly stronger and more important predictors for the MVP award than traditional, high-volume stats (e.g., PPG) alone.

________________________________________
# Data Source and Collection Plan
To test my hypothesis, I will need to collect and combine several public datasets. As per the project guidelines, I will enrich a primary public dataset with other data.

•	Source: All data will be sourced from Basketball-Reference.com.

•	Collection Method: I will perform web scraping using Python libraries. My plan is to write a script that iterates through approximately 30 NBA seasons (e.g., 1995-2025) and gathers the following three distinct data tables:
## 1.	Primary Data (Player Stats): The "Advanced" and "Per Game" statistics tables for all players for each season.
## 2.	Enrichment Data 1 (Team Success): The "Team Standings" table for each season to get team win-loss records.
## 3.	Enrichment Data 2 (Target Variable): The "Awards" voting results table for each season.
•	Data Preparation Plan: I will then "enrich" the primary player data by merging it with the team success data and using the awards data to create my target variable: a new column named is_mvp (1 for the winner, 0 for everyone else).

________________________________________
# Questions I Plan to Address
•	Does the data support the common narrative that team success is a "prerequisite" for winning MVP?
•	Has there been a shift over the decades? Are advanced metrics (like Win Shares) more correlated with winning MVP in the modern era than in the 1990s?
•	Which specific metric (e.g., PER, Win Shares, PPG) holds the most statistical importance in predicting the winner?
•	Can a model be trained on a pre-filtered list of "candidates" (e.g., All-Stars) to effectively predict the winner from that small group?
________________________________________
# Analysis Focus
•	My initial analysis will involve Exploratory Data Analysis (EDA) and Hypothesis Testing. I will use t-tests to compare the statistical profiles of MVP winners versus non-winners.
•	I will visualize the correlations between team wins, individual stats, and winning the award.
________________________________________
# ML Modeling Plan
•	Objective: To build a binary classification model that predicts the probability of a player winning the MVP award based on their regular season performance statistics.
•	Model: As required for the 02 January deadline, I plan to implement a Logistic Regression or Random Forest model using Python's scikit-learn library.

