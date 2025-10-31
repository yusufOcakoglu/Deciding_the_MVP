# Deciding the MVP: A Data-Driven Analysis of NBA Normal Season MVP Winners
*I am Yusuf Ocakoglu. I have been interested in NBA Basketball and I've been watching NBA match and player analysis videos(e.g. "Thinking Basketball" YouTube channel) for a long time. In NBA,every year, there has been a subject that all basketball experts cannot have a consensus on: To whom will The NBA Normal Season MVP Award be given? NBA and various websites proivde wide range of data concerning player,team and award data. These publicly available data had me thinking about working on it as my project subject.*

*Therefore, I have decided to choose a claim to investigate for my DSA 210 project: "What factors actually determine the NBA's Most Valuable Player?"*



# Hypothesis (My Claim)
•	**Null Hypothesis:** *There is no statistically significant difference in predictive power between traditional statistics (like Points Per Game) and advanced metrics (like Win Shares) when identifying the MVP. Team success (win percentage) is also not a primary determining factor.*

•	**Alternative Hypothesis:** *Advanced metrics (e.g., Win Shares, PER) combined with team success (win percentage) are significantly stronger and more important predictors for the MVP award than traditional, high-volume stats (e.g., PPG) alone.*

________________________________________
# Data Source and Collection Plan
*To test my hypothesis, I will need to collect and combine several public datasets. As per the project guidelines, I will enrich a primary public dataset with other data.*

•	**Source:** *All data will be sourced from Basketball-Reference.com. Although all data will be sourced from same website, I will be dealing with three distinct dataset.*

•	**Collection Method:**  *I will perform web scraping using Python libraries. My plan is to write a script that iterates through approximately 30 NBA seasons (e.g., 1995-2025) and gathers the following three distinct data tables:*

 **1.	Primary Data (Player Stats):** *The "Advanced" and "Per Game" statistics tables for all players for each season.*
 https://www.basketball-reference.com/players/
 
 **2. Data Collection 1 (Team Success):** *The "Team Standings" table for each season to get team win-loss records.*
 https://www.basketball-reference.com/teams/
 
**3.	Data Collection 2 (Target Variable):** *The "Awards" voting results table for each season.*
https://www.basketball-reference.com/awards/mvp.html

•	**Data Preparation Plan:** *I will then "enrich" the primary player data by merging it with the team success data and using the awards data to create my*

________________________________________
# Questions I Plan to Address
•	*Does the data support the common narrative that team success is a "prerequisite" for winning MVP?*

•	*Has there been a shift over the decades? Are advanced metrics (like Win Shares) more correlated with winning MVP in the modern era than in the 1990s?*

•	*Which specific metric (e.g., PER, Win Shares, PPG) holds the most statistical importance in predicting the winner?*

•	*Can a model be trained on a pre-filtered list of "candidates" (e.g., All-Stars) to effectively predict the winner from that small group?*
________________________________________
# Analysis Focus

•	*My initial analysis will involve **Exploratory Data Analysis (EDA) and Hypothesis Testing**. Type of test to be conducted will be discussed.*

•	*I am planning to visualize the correlations between team wins, individual stats, and winning the award. Further analysis on the shift over the decades about metrics may be conducted.*
________________________________________
# ML Modeling Plan

•	**Objective:**
*To build a binary classification model that predicts the probability of a player winning the MVP award based on their regular season performance statistic.*

•	**Model:**
*This step will be evaluated after some progress through the project.*

# Limitations and Future Work:
  ## Limitations:
   *An expected limitation is to overlook the effect of narratives: Tweets about a player, comeback histories, public popularity of a player in a season has the potential to shift the votes one candidate to another among the MVP candidates.*


