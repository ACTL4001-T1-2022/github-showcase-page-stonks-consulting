# SOA Case Study 2022: Rarita's National Football Team ⚽
![](giphy.gif)

---
## Project Outline

The goal of this assignment was to formulate a comprehensive plan for Rarita (a fictional country) to construct an internationally competitive football team. Criteria for a "competitive" team was defined within the [SOA Student Case Study 2022](https://www.soa.org/globalassets/assets/files/static-pages/research/opportunities/2022-student-research-case-study.pdf) as:
>1. Rank within the top 10 members of the FSA for the season within the next 5 years.
>2. Have a high probability of achieving an FSA championship within the next 10 years.

The potential economic impacts of the team were also assessed, and given the uncertainty involved in such a venture, a thorough risk analysis was conducted, highlighting the key risks, impacts, and potential risk mitigation measures. 

## Team Selection
Our team selection methodology aims to achieve Commissioner Bayes objectives by developing a tool that identifies the best team and can be implemented continuously throughout the next ten years. Our tool calculates the projected individual quality of players (called the “Individual Metric”) and then selects players to form the best team (by maximising the “Team Metric”). 

**Individual Metrics**

To calculate the Individual Metric for each player, we first filtered players that played in league “A”,”B”,”C” or “RFL”, played more than three league games (to remove players whos statistics are misleading), and whose age aligns with the [average peak performance age within the next 5 or 10 years](https://www.frontiersin.org/articles/10.3389/fpsyg.2019.00076/full#:~:text=In%20a%20recent%20study%2C%20Dendir,the%2025%E2%80%9327%20age%20range.). We then calculated Individual Metrics for each position (FW, MF, DF) using the scaled “League Data” variables that reflected a player’s quality independent of the team they play for. Individual Metrics were then projected for each player over the next 5/10 years, aggregated and then scaled (for computing reasons).

**Team Metrics**

The Team Metric for a team is defined as the aggregate Individual Metrics of all players in the team. Because the performance of a team is not completely determined by the quality of individual players, we modelled the affect on team performance when familiar neighbouring players are selected. This “Chemistry Bonus” is a 2% increase in Individual Metrics for pairs of neighbouring players that play in the same nation of league squad. 

**Squad Selection**

An Answer Set Programming ([Cringo](https://potassco.org/clingo/run/)) approach was used to select players for a “Starting Team” that maximize the Team Metric for the three most common formations seen in the [English Premier League during 2019/2020](https://www.premierleague.com/news/2165778#:~:text=The%20ever%2Dpopular%204%2D2,%2D4%2D2%2D1.):

![Formation and metric score](https://user-images.githubusercontent.com/103341948/162705945-f7b983b2-0a4f-4e58-acbc-abc302c06599.jpg)

As shown above, the best team is formed under a 4-3-3 formation and the players selected are:

|**Player**|**Position**|**Individual Metric**|**Chemistry Adjusted Metric**|**Salary + Loan Fee (∂)**|
|:---|:---|:---|:---|:---|
|F. Akumu|GK|857|892|5,600,000|
|C. Kakayi|DF|523|544|7,308,400|
|C. Baluka|DF|792|840|7,760,000|
|S. Rizzo|DF|739|769|6,461,400|
|X. Takagi|DF|1000|1020|4,810,000|
|R. Jimenez|MF|718|809|16,340,000|
|V. Persson|MF|64|64|11,749,100|
|L. Leibowitz|MF|1000|1082|8,600,000|
|P. Villa|FW|647|714|35,290,000|
|P. Rabiu|FW|688|760|36,060,000|
|Z. Zziwa|FW|1000|1104|9,120,000|

We then selected a “Reserve Team” of eleven young players that are expected to peak in performance in the next 5-10 years. Our belief is that developing these young players within Rarita will be cheaper and more effective then loaning international players. The total cost of this team is ∂76,543,900.

**Sensitivity Analysis**

To calculate the sensitivity of the “Starting Team”, each player in the team was removed sequentially, and the next best team was calculated. The difference in Team Metric score, total salary cost (including 10% loaning fee) and selected players between the “Starting Team” and next best team was calculated. The sensitivity of the “Starting Team” is immaterial (14 different players were selected in total. Salaries differed by ∂456,000 on average. Team Metric differed by 850 on average.) which suggest the likelihood of achieving Commissioner Bayes objectives is not highly variable on any of the individual players selected.

**Probability Ranges of Success**

For each national team in the tournament data we calculated an "Attack Score" (total goals/maximum recorded number of games) and "Defense Score" (total times dribbled past*total errors/maximum recorded games). We then simulated 1000 knockout tournament games where the winner of each game was the nation with the highest difference between their Attack Score and the oppositions Defense Score. We added a randomly generated 0%-10% bonus to each nationals Attack/Defense score to simulate uncertainty. Out of 1000 simulations, our selected team won the tournament 402 times, and placed within the top 10 FSA nations 673 times.

## Implementation Plan

### Team Selection 
**Team Selection Implementation Strategy**

Our implementation plan is structured using the three stages of the Actuarial Control Cycle. We deconstructed Commissioner Bayes objectives into four separate problems, and designed each solution around our team selection tool:

|            **Problem**               | **Designed Solution**              |
| :----------------------------------- | :--------------------------------- |
| Which players should be loaned?      | Players that: increase/are expected to increase the “Team Metric”, play in leagues “A”,”B”,”C” or "RFL", have played more than 3 league games, are within the required age range for a particular team | 
| When should players be loaned?       | Whenever financially and logistically possible |
| Which players should be loaned out?  | Players that: are underperforming compared to their projected Individual Metric, are older than 29 years old, can be replaced by another player that increases the Team Metric|
| When should players be loaned out?   | Whenever logistically possible |

Our tool will be utilized as often as possible by Rarita to maximise the Team Metric, which improves the likelihood of achieving Commissioner Bayes objectives. In addition, regularly utilizing our tool will allow Rarita to update assumptions or metrics and address any discrepancies between the projected and observed performance of players.

### Revenues & Expenses
**Matchday**

We hope to make revenue from selling memberships and season ticket passes to supporters. From the outset, the aim is to sell memberships cheaper to appeal to the masses (Central/West Rarita). As the team becomes more competitive and more popular, the memberships should increase and as such we can adequately monitor and optimise the price to maximise revenue using economic modelling. The figures below were determined by assessing the average growth in match day revenue and correlating to positions finished in the respective national tournaments.
 - Current revenue is 24.63 Doubloons per capita
 - An expected increase of 4% per capita each year
 - Upon the completion of stadium building, we expect a one-year abnormal increase in match-day sales


**Sponsorships**

Finding sponsorships allows private investment into the team and provides the team with capital to spend on improving resources. The aim is to make early investments into hiring a sponsorship committee who will be devoted to creating sponsorship packages and then researching potential sponsors to partner with. As the club becomes more competitive and popular, we expect the sponsorship deals to increase in size and provide more revenue, goods and services for the club. The figures we have calculated reflect that sponsorship revenue was closely correlated to nations with high GDP.
 - Current revenue is 75.06 Doubloons per capita
 - We expect to receive close to 7% per capita increase in revenue each year
 - By Year 10, we expect to receive 150 Doubloons per capita from sponsorships and advertising


**Broadcasting**

The aim is to sell rights of broadcasting Rarita games to television companies on small-term contracts. Then, as the popularity and competitive nature of the team increases, we expect to sign longer-term contracts for higher deals. This is the biggest revenue stream we expect.
 - Current revenue is 63.44 Doubloons per capita
 - At Year 1, expected revenue of 72 Doubloons per capita
 - At Year 4, we expect to increase rights to 100 Doubloons per capita
 - At Year 6, we expect to be competing for FSA titles and securing a long-term deal at approximately 140 Doubloons per capita


**Social Media**

While our largest sources of revenue will be broadcasting rights and sponsorships, we expect social media to play a large role in popularizing Rarita’s team. This is evident in the correlation between a team’s past success and its social media following. Initiatives such as player interviews, behind the scene insights and matchday reviews led by a dedicated social media team will enhance fan following and encourage matchday attendance, whilst maintaining key sponsors. Additional revenue from a strong social media may be reinvested in supporting associated industries such as tourism and hospitality. 

**Staff Expenses**

Currently, staff expenses for competitive teams are larger in dollar terms (greater proportion of GDP), however we do not see correlation in terms of annual staff expense growth which is 6% across all nations.
 - Current expenses at 98.25 Doubloon per capita
 - Initial expenses to grow at 6% per capita each year
 - At Year 6, we expect an increase of growth rate to around 7.5% per capita

**Other Expenses** 

- We expect rent and facility management to grow by 10% each year
- With the stadium expected to be completed at the end of Year 3, we expect a one-off larger increase in expenses for that year

Estimated revenues and expenses on a yearly timeline are outlined below (all values expressed as Rarita Doubloons per capita)

| Year | Matchday | Sponsor | Broadcast | Staff | Other | UIUD Profit | **Expected Profit** |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 1 | 25.00 | 78.00 | 72.00 | -98.25 | -50.44 | 26.31 | **27.23** |
| 2 | 26.00 | 83.46 | 79.20 | -104.15 | -55.48 | 29.03 | **31.03** |
| 3 | 27.04 | 89.30 | 87.12 | -110.40 | -61.03 | 32.03 | **35.26** |
| 4 | 28.12 | 95.55 | 95.83 | -117.02 | -67.14 | 35.35 | **40.00** |
| 5 | 29.53 | 102.24 | 105.42 | -124.04 | -73.85 | 39.30 | **45.69** |
| 6 | 31.00 | 109.40 | 115.96 | -133.34 | -81.23 | 41.78 | **49.91** |
| 7 | 32.55 | 118.15 | 127.55 | -143.34 | -89.36 | 45.56 | **55.91** |
| 8 | 34.19 | 127.60 | 140.31 | -154.09 | -98.29 | 49.71 | **62.67** |
| 9 | 35.89 | 137.81 | 154.34 | -165.65 | -108.12 | 54.27 | **70.31** |
| 10 | 37.69 | 148.84 | 169.78 | -178.07 | -118.93 | 59.29 | **78.94** |

### Key Monitoring Metrics

To measure the long-term financial sustainability of Rarita’s club, we monitor indicators on a yearly basis: 
 - Operating profit: gross margin of key commercial activities, borrowings ratio, staff costs as a percentage of total turnover
 - Team’s youth development KPIs: conversion rate to a professional contract, number of international caps won by home players whilst playing for club
 - Player trading performance: sell-on value of player registrations divided by the purchase value, indicating scouting talent ability

<img width="1313" alt="Screen Shot 2022-04-11 at 7 33 09 pm" src="https://user-images.githubusercontent.com/103308390/162711704-5aa6c8ba-4b61-4a76-acdb-dedfdaa7b086.png">

<img width="1303" alt="Screen Shot 2022-04-11 at 7 33 30 pm" src="https://user-images.githubusercontent.com/103308390/162711380-82be3527-1ff5-4f56-93d1-3ebb584c6550.png">

## Economic Impact

**GDP per Capita**
- Projected using Monte-Carlo simulations 
- $23.7bn expected growth by the end of 10 years 
- Expected to reach $35,300 by 2030

<img width="510" alt="Screen Shot 2022-04-11 at 6 52 18 pm" src="https://user-images.githubusercontent.com/103412094/162703270-07b8e7f9-2a13-4417-915c-ae579d87e62a.png">


**GNI per Capita**
- Projected using Monte-Carlo simulations
- Expected to grow to $39,900 by 2030
<img width="552" alt="Screen Shot 2022-04-11 at 6 53 00 pm" src="https://user-images.githubusercontent.com/103412094/162703282-256f6d9a-570f-411b-b456-b8c369c7d3d2.png">


**Household Savings and Health Expenditure** 
- Expected to remain mostly flat through the next 10 years
- As Rarita's economy matures, it will shift to from producing goods to services, thus expanding its financial sector. Due to Rarita's maturing financial sector, the household savings rate will grow slightly approaching 9% by 2030.
- Impacts resulting from the implementation plan will be immaterial

**Inflation**
- Expected to increase in 2021 in the aftermath of the pandemic 
- Using an ARMA model, it gradually subsides to the long term average: 3%

<img width="432" alt="Screen Shot 2022-04-11 at 7 10 28 pm" src="https://user-images.githubusercontent.com/103412094/162704200-b4056f38-f615-49f9-8288-96239efee40d.png">


**Unemployment Rate** 
- Historically was estimated to be approx. 6.5%
- Projections are stable with unemployment gradually declining to 5% 


**Related industries**

Benchmarked against data from global industry markets, we calculated the added impact on CAGR, from Rarita’s football team. The industries positively impacted include:
- Sports betting (4.92% CAGR)
- Manufacturing (2.4% CAGR)
- Hospitality (7.29% CAGR)
- Tourism (5.05% CAGR)
- Transport (1.93% CAGR)

## Methodology, Modelling and Assumptions

#### **Economic Metrics**

**Population Growth**
- We have used an ARIMA(0, 2, 2) model based on Holt's linear trend (double exponential smoothing) method to forecast population growth to 2030. 

<img width="245" alt="newplot (20)" src="https://user-images.githubusercontent.com/103188193/162736934-03ba23cd-894e-452b-bacd-4b6c1cf27868.png">

- As the population of Rarita is clearly an upward trending function, the Holt's linear trend helps in dealing with this trending data. The ACF spike at lag 0 further supports the case for a ARIMA(0, 2, 2) model.

<img width="912" alt="newplot (15)" src="https://user-images.githubusercontent.com/103188193/162723591-d3cb2c2f-f526-4e74-b1ef-4b3be200fef2.png">

- Projections show stable population growth at 0.4% per annum to 13.1 million by 2030.  

![newplot (14)](https://user-images.githubusercontent.com/103188193/162723499-aca53f25-ce12-4e5e-b774-35f6210ecf97.png)

- Overall, football is likely to have a negligible impact on population growth. 

**GDP per Capita**
- The Monte Carlo method assumes that year-on-year GDP per Capita growth is a normally distributed random variable ~ N(0.02745, 0.00115).

**GNI per Capita**
- The Monte Carlo method assumes that year-on-year GDP per Capita growth is a normally distributed random variable ~ N(0.02273, 0.00121).

**Inflation Rate**
- We have selected an ARMA(1, 1) model based on the Akaike Information Criterion (AIC). The heatmap below shows the p and q values (x and y-axes respectively) for which the AIC is minimised. 

![newplot (13)](https://user-images.githubusercontent.com/103188193/162727183-7e438ea1-83ca-4463-96c0-400617d24daa.png)

- While the AIC is minimised under a MA(2) model, the ARMA(1, 1) model offers similar model fitting allowing for better smoothing. Additionally, it reflects our projection that the pandemic will put increase inflation in the short-run followed by a gradual decline to the long-run average of 3%.

 ![newplot](https://user-images.githubusercontent.com/103188193/162727554-70c39490-ddef-49e0-acfa-2fe95744cc9a.png)

**Unemployment Rate**
- This metric was not provided in the Rarita data. However we believe it is an important metric to monitor in relation to Rarita’s football plans as it plays a major role in developing Rarita's industries, education sector as well as sociodemographics. 
- To proxy Rarita's unemployment rate, we utilised external World Bank data on selected regions and income groups. We have selected regions and income groups rather than individual countries as we believe the larger sample size incorporated into the data allows for more reliable models to be developed. 
- A linear regression is conducted on the various regions and income groups using explanatory variable GDP per Capita growth, Inflation, Healthcare Expenditure and Household Savings.
- Individual models were then fitted on Rarita's economic data to arrive as a proxy unemployment rate. As such the assumption is that the coefficients of the fitted models reflect those of Rarita and that the dynamics driving the economy (and by extension unemployment) in the two are similar. 
- Linear regression models fitted on World and OECD members groups demonstrated the best ability to predict unseen data (here post-2016 was used as test data)

|![Picture4](https://user-images.githubusercontent.com/103188193/162737943-29cf35a1-57aa-4acb-92e6-11b2edd1c962.png)|![Picture5](https://user-images.githubusercontent.com/103188193/162738002-79a6582f-cc16-4914-9cbd-8f2b44cb1b6b.png)|

- Rarita's economic metrics align more closely World group and the OECD member group's R-squared highlights a superior fit. 

|<img width="466" alt="Picture9" src="https://user-images.githubusercontent.com/103188193/162738101-a0a1c2de-d59a-4691-bce7-d18368df2fa4.png">|<img width="405" alt="Picture10" src="https://user-images.githubusercontent.com/103188193/162738177-54f248f4-97de-4f4c-8cd1-baeb2744fe13.png">|

- As such a simple average between World and OECD member proxies is selected to arrive at Rarita's historic unemployment rate. The historical average of 6.5% is reasonable and justifiable given Rarita's economic metrics. 
- However, the model is unable to predict the effects of the pandemic in 2020. A loading of 20% has been applied based on the average changes in unemployment seen across the world. 

<img width="289" alt="Picture12" src="https://user-images.githubusercontent.com/103188193/162738421-2baac30d-874e-4778-95b2-a89543334be7.png">

- As the unemployment rate is only a proxied measure, we have used pandemic and football impact loadings and 3-year running averages to project unemployment. Assuming a conservative 4:1 relationship between GPD per capita growth and unemployment by Okun's Law, we have applied pandemic reversal loading in 2021 and 2022 as we expect strong GDP growth and rising inflation (Phillip's curve) to drive declining unemployment rates. Using revenue/expense analysis and the impact of the implementation plan on Rarita's GDP, we have similarly included a loading which reduces the unemployment rate as Rarita's industries grow and jobs are created by infrastructure such as the new stadium. 

![Picture3](https://user-images.githubusercontent.com/103188193/162738510-5c5de382-f072-4bcd-a3a1-49a48ebe6c7a.png)

**Healthcare Expenditure and Household savings**
- Initially, a Vector Autoregression (VAR) model was considered such that the variables GDP per Capita growth, Inflation, Unemployment Rate, Healthcare Expenditure and Household Savings could be used in a multivariate setting to predict one another. The model, however, is overly complicated and while performing well on the training data shows overfitting when applied to the test dataset. It is therefore unreliable in projecting the variables listed above. 
- As such, we have only projected healthcare expenditure and household savings using the VAR models that were selected in Excel.
- Models fitted on World Bank data are tested on the unseen Rarita data which acts as a test set. Overall the World, upper-middle income and OECD members groups' models are able to accurately predict Rarita's historic healthcare expenditure and household savings. 
- A simple average between the model above is taken to fit to Rarita historicals and project future rates. Projections show stability indicating minimal overfitting.

|![Picture1](https://user-images.githubusercontent.com/103188193/162738608-c0c3d35b-c782-4081-bd46-f9c114010335.png)|![Picture2](https://user-images.githubusercontent.com/103188193/162738638-bcd0b01f-3770-4325-87f1-24bafb9688d9.png)|

## Risk Considerations
Forming a competative football team is a difficult undertaking and is subject to a broad range of risks. A risk analysis was completed to identify key risks faced by the team, the potential impact, and measures to mitigate the risk. 

**Player Misconduct**

Anti-social behaviour (both on and off-field) represented a considerable financial (quantitative) and reputation (qualitative) risk to Rarita. Experience from other sporting codes suggested the likelihood of severe misconduct by a player within the team is likely within the next 5 years. An incident could impact:
* Sponsor share prices. 
* Broadcasting revenue.
* Ticket sales. 
* Rarita's international tourism. 

Transfering or removing this risk was not possible. However, establishing a strict Player Code of Conduct (with enforceable penalties) to govern on and off-field behaviour was advised as a means to mitigate the risk. This would aid in reducing the frequency and severity of incidents. 

**Poor Public Opinion**

Though difficult to quantify, a lack of public support for Rarita’s national team and the investment would have considerable economic and political consequences for Rarita, and was identifed as another key risk. 
Potential impacts could be:
* Social and Politcal Unrest.
* Wasted public spending, and the foregone benefits of other investment such as in education or healthcare.
* Low broadcasting & ticket sale revenue. 

To mitigate this risk, it was advised to conduct focus groups, and liaise with key stakeholders in the community, to ensure the investment and national team’s introduction aligns with their broader interests.
