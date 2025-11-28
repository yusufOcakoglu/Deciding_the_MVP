# Wallet vs. Identity: A Data-Driven Analysis of the Rise of Far Right in Europe
*I am Yusuf Ocakoglu. I have a keen interest in European politics and I've been watching European politics videos frequently(e.g.49W Youtube Channel). Recently, Europe has been experiencing a significant political shift with the rise of far-right and populist parties (e.g., AfD in Germany, RN in France). While political commentators often debate whether this shift is driven by cultural anxiety (migration) or economic hardship (cost of living), there is rarely a data-backed consensus on which factor is the primary driver.*

*Therefore, I have decided to chose a claim to investigate for my DSA 210 project: "Do specific economic pain points, like housing and food costs, predict the rise of far right parties better than migration numbers?"*



# Hypothesis (My Claim)
•	**Null Hypothesis:** *There is no statistically significant difference in predictive power between general macro-economic indicators (like GDP) or demographic factors (migration numbers) and specific cost-of-living metrics (Housing/Food prices) when predicting the rise of populist party votes.*

•	**Alternative Hypothesis:** *Specific "kitchen table" economic metrics—specifically Housing Cost Indices and Food Inflation—are significantly stronger predictors of populist party polling numbers than general migration statistics or broad GDP growth.*

________________________________________
# Data Source and Collection Plan
*To test my hypothesis, I will need to collect and combine several public datasets. As per the project guidelines, I will enrich a primary public dataset with other data sources.*

•	**Source:** *Data will be sourced from Politico.eu, Eurostat, and UNHCR/Eurostat Migration Databases. I will be dealing with three distinct datasets to create a unified time-series analysis.*

•	**Collection Method:**  *I will perform a hybrid of API usage and web scraping using Python libraries (eurostat). My plan is to aggregate data for key European countries (Germany, France, Italy) over the last 5-10 years.*

 **1.	Primary Data (Target Variable):** *The "Poll of Polls" data for specific European countries. This tracks the daily/weekly voting intention for political parties.*
 Source: Politico Europe (Scraping/JSON extraction).
 
 **2. Enrichment Data 1 (Economic Stressors):** *Harmonised Index of Consumer Prices (HICP) with a focus on specific sub-indices: Food and Housing/Utilities.*
 Source: Eurostat API.
 
**3.	Enrichment Data 2 (Demographics):** *Asylum applicant numbers and migration statistics.*
 Source: Eurostat/UNHCR.

•	**Data Preparation Plan:** *I will enrich the political polling data by merging it with the monthly economic and migration indices based on date and country codes. This will create a master dataframe suitable for time-series regression.*

________________________________________
# Questions I Plan to Address
•	*Is the "Cost of Living" the real driver? Do spikes in the Housing Price Index correlate more strongly with populist polling surges than spikes in migration numbers?*

•	*s there a time lag? How long does it take for a jump in food inflation to reflect in political polling numbers? (e.g., does the reaction happen instantly or 3 months later?)*

•	*Does the "Economy" matter more than "Culture"? When comparing the feature importance of economic variables vs. demographic variables, which one holds more statistical weight in predicting the target variable?*

________________________________________
# Analysis Focus

•	*My initial analysis will involve Exploratory Data Analysis (EDA) to visualize the trends of inflation, migration, and political polling on the same timeline.*

•	*I plan to use correlation matrices and time-series visualization to identify potential "breaking points" where economic stress triggered political shifts.*
________________________________________
# ML Modeling Plan

•	**Objective:**
*To build a Multiple Regression Model (or a Time-Series Regressor) that predicts the polling percentage of a populist party based on the independent economic and social variables.*

•	**Model:**
*This step will be evaluated after some progress through the project.*

# Limitations and Future Work:
  ## Limitations:
   *An expected limitation is the inability to quantify media narratives and political charisma. A sudden scandal involving a politician or a viral news story can shift votes regardless of the economic situation, which is difficult to capture in a purely numerical dataset.*
  ## Future Work:
   *To address the missing "narrative" aspect, future work could involve scraping news headlines from major European outlets to perform Sentiment Analysis. This would allow the model to account for the "public mood" driven by media, not just raw economic numbers. For now, this exceeds the scope of the current project timeline.*

