# Wallet vs. Passion: A Data-Driven Analysis of the "Escapism" Effect in Turkish Football

I am **Yusuf Ocakoglu**. Living in Turkey, I witness the economic challenges, high inflation, and the rising cost of living firsthand every day. Normally, when the economy gets tough and money becomes tight, the first thing people cut from their budget is entertainment and luxury expenses.

However, as a football fan, I have noticed something surprising: **Even though the economy is struggling and ticket prices are skyrocketing, football stadiums in Turkey are fuller than ever.** This observation goes against basic logic—why do people keep spending money on football when they are trying to save? This led me to the idea of **"Escapism"**—maybe people are flocking to stadiums not in spite of the crisis, but *because* of it, using football as a psychological escape.

For my DSA 210 project, I want to test this observation with data: **Is football a luxury that people give up during crises, or is it a sanctuary that they cling to even more?**

### Hypothesis (My Claim)

* **Null Hypothesis ($H_0$):** There is a negative correlation between economic distress (High Inflation, High Unemployment) and stadium attendance. (i.e., As the economy gets worse, people stop going to matches to save money).
* **Alternative Hypothesis ($H_1$):** Stadium attendance remains stable or even increases during economic downturns, supporting the "Escapism" theory. This suggests that for Turkish people, football is a psychological necessity rather than just entertainment.

### Data Source and Collection Plan

To test this, I will combine football data with economic indicators covering the last **10 football seasons (2014-2024)**.

* **Source:** I will use **Transfermarkt** for football stats, **TÜİK (Turkish Statistical Institute)** for economic data, and internet archives for historical ticket prices.
* **Collection Method:** I will use Python (BeautifulSoup) to scrape football data and download official economic datasets directly.

**1. Primary Data (Target Variable): Süper Lig Attendance**
* **What:** Average number of fans per game and stadium fill rates (%).
* **Source:** Transfermarkt (Web Scraping).

**2. Enrichment Data 1 (Economic Stressors): The Economy**
* **What:** Monthly Inflation Rate (CPI), USD/TRY Exchange Rate, and Unemployment Rate.
* **Source:** TÜİK (TurkStat) and EVDS (Central Bank of Turkey).

**3. Enrichment Data 2 (Cost of Entry): Ticket Prices**
* **What:** Historical Passolig card fees and minimum season ticket prices for major teams.
* **Source:** Internet Archives (Wayback Machine) and News Search (Manual Entry).

**Data Preparation:** I will merge the weekly/yearly match data with the monthly economic data to see how they interact over time.

### Questions I Plan to Address

* **Is Football "Crisis-Proof"?** Does high inflation actually stop fans from going to the stadium?
* **Is there a Delay?** If the Dollar/TL exchange rate spikes today, does the stadium attendance drop immediately, or does it take a few months to show?
* **Big Teams vs. Others:** Is this "Escapism" effect valid only for big clubs (Galatasaray, Fenerbahçe, Beşiktaş) or does it apply to all teams?
* **Purchasing Power:** How much harder has it become to buy a ticket compared to the minimum wage over the last 10 years?

### Analysis Focus

* I will start with **Exploratory Data Analysis (EDA)** to plot the "Economic Crisis" and "Stadium Fullness" on the same graph to see if they move together or in opposite directions.
* I will use **Time-Series Visualizations** to spot specific moments (like the 2018 or 2021 currency shocks) and see how the fans reacted.

### ML Modeling Plan

* **Objective:** To build a model that tries to predict the "Average Attendance" based on the economic situation of the country.
* **Model:** I plan to use **Linear Regression** to see which economic factor (Inflation? Dollar? Unemployment?) has the biggest impact on whether people go to the match or not.

### Limitations and Future Work

**Limitations:**
It is hard to separate the "Economic Effect" from the "Team Success Effect." A team playing for the championship will always have a full stadium, regardless of the economy. My model might struggle to distinguish between a "rich fan" and a "passionate fan."

**Future Work:**
In the future, I could add a "Team Performance" score to the data to filter out the success factor. Also, analyzing social media (Twitter) sentiment during matches could help confirm if people are using football to vent their frustration.
