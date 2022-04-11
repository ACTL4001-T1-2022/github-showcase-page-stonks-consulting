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

To calculate the Individual Metric for each player, we first filtered players that played in league “A”,”B”,”C” or “RFL”, played more than three league games (to remove players whos statistics are misleading), and whose age aligns with the [average peak performance age within the next 5 or 10 years](https://www.frontiersin.org/articles/10.3389/fpsyg.2019.00076/full#:~:text=In%20a%20recent%20study%2C%20Dendir,the%2025%E2%80%9327%20age%20range.). We then calculated Individual Metrics for each position (FW, MF, DF) using the scaled “League Data” variables that reflected a player’s quality independent of the team they play for. Individual Metrics were then projected for each player over the next 5/10 years, aggregated and then scaled (for computing reasons).

The Team Metric for a team is defined as the aggregate Individual Metrics of all players in the team. Because the performance of a team is not completely determined by the quality of individual players, we modelled the affect on team performance when familiar neighbouring players are selected. This “Chemistry Bonus” is a 2% increase in Individual Metrics for pairs of neighbouring players that play in the same nation of league squad. 

An Answer Set Programming ([Cringo](https://potassco.org/clingo/run/)) approach was used to select players for a “Starting Team” that maximize the Team Metric for the three most common formations seen in the [English Premier League during 2019/2020](https://www.premierleague.com/news/2165778#:~:text=The%20ever%2Dpopular%204%2D2,%2D4%2D2%2D1.):

![Formation and metric score](https://user-images.githubusercontent.com/103341948/162705945-f7b983b2-0a4f-4e58-acbc-abc302c06599.jpg)

As shown above, the best team is formed under a 4-3-3 formation and the players selected are:

|**Player**|**Position**|**Individual Metric**|**Chemistry Adjusted Metric**|**Salary + Loan Fee**|
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

To calculate the sensitivity of the “Starting Team”, each player in the team was removed sequentially, and the next best team was calculated. The difference in Team Metric score, total salary cost (including 10% loaning fee) and selected players between the “Starting Team” and next best team was calculated. The sensitivity of the “Starting Team” is immaterial (14 different players were selected in total. Salaries differed by ∂456,000 on average. Team Metric differed by 850 on average.) which suggest the likelihood of achieving Commissioner Bayes objectives is not highly variable on any of the individual players selected.

In relation to implementation, we deconstructed Commissioner Bayes objectives into four separate problems, and designed each solution around our team selection tool:

|            **Problem**               | **Designed Solution**              |
| :----------------------------------- | :--------------------------------- |
| Which players should be loaned?      | Players that:<ul><li>increase/are expected to increase the “Team Metric”</li><li>play in leagues “A”,”B”,”C” or RFL</li><li>have played more than 3 league games</li><li>are within the required age range for a particular team</li></ul> | 
| When should players be loaned?       | Whenever financially and logistically possible |
| Which players should be loaned out?  | Players that:<ul><li>are underperforming compared to their projected Individual Metric</li><li>are older than 29 years old</li><li>can be replaced by another player that increases the Team Metric</li></ul>|
| When should players be loaned out?   | Whenever logistically possible |


Our tool will be utilized as often as possible by Rarita to maximise the likelihood of achieving Commissioner Bayes objectives. 

## Implementation Plan
@ Prav and Yatty
Year | Matchday | Sponsor | Broadcast | Staff | Other | UIUD Profit | **Expected Profit**
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 1 | 25.00 | 78.00 | 72.00 | -98.25 | -50.44 | 26.31 | **27.23**
| 2 | 26.00 | 83.46 | 79.20 | -104.15 | -55.48 | 29.03 | **31.03**
| 3 | 27.04 | 89.30 | 87.12 | -110.40 | -61.03 | 32.03 | **35.26**
| 4 | 28.12 | 95.55 | 95.83 | -117.02 | -67.14 | 35.35 | **40.00**
| 5 | 29.53 | 102.24 | 105.42 | -124.04 | -73.85 | 39.30 | **45.69**
| 6 | 31.00 | 109.40 | 115.96 | -133.34 | -81.23 | 41.78 | **49.91**
| 7 | 32.55 | 118.15 | 127.55 | -143.34 | -89.36 | 45.56 | **55.91**
| 8 | 34.19 | 127.60 | 140.31 | -154.09 | -98.29 | 49.71 | **62.67**
| 9 | 35.89 | 137.81 | 154.34 | -165.65 | -108.12 | 54.27 | **70.31**
| 10 | 37.69 | 148.84 | 169.78 | -178.07 | -118.93 | 59.29 | **78.94**


## Economic Impact
@ Karina
## Risk Considerations
Forming a competative football team is a difficult undertaking and is subject to a broad range of risks. A risk analysis was completed to identify key risks faced by the team, the potential impact, and measures to mitigate the risk. 
#### Player Misconduct. 
Anti-social behaviour (both on and off-field) represented a considerable financial (quantitative) and reputation (qualitative) risk to Rarita. Experience from other sporting codes suggested the likelihood of severe misconduct by a player within the team is likely within the next 5 years. An incident could impact:
* Sponsor share prices. 
* Broadcasting revenue.
* Ticket sales. 
* Rarita's international tourism. 

Transfering or removing this risk was not possible. However, establishing a strict Player Code of Conduct (with enforceable penalties) to govern on and off-field behaviour was advised as a means to mitigate the risk. This would aid in reducing the frequency and severity of incidents. 

#### Poor Public Opinion
Though difficult to quantify, a lack of public support for Rarita’s national team and the investment would have considerable economic and political consequences for Rarita, and was identifed as another key risk. 
Potential impacts could be:
* Social and Politcal Unrest.
* Wasted public spending, and the foregone benefits of other investment such as in education or healthcare.
* Low broadcasting & ticket sale revenue. 

To mitigate this risk, it was advised to conduct focus groups, and liaise with key stakeholders in the community, to ensure the investment and national team’s introduction aligns with their broader interests.





# Delete below this before submission. Keep for now as a template for formatting. 

### Congrats on completing the [2022 SOA Research Challenge](https://www.soa.org/research/opportunities/2022-student-research-case-study-challenge/)!

>Now it's time to build your own website to showcase your work.  
>To create a website on GitHub Pages to showcase your work is very easy.

This is written in markdown language. 
>
* Click [4001 link](https://classroom.github.com/a/ggiq0YzO) to accept your group assignment.
* Click [5100 link](https://classroom.github.com/a/uVytCqDv) to accept your group assignment 

#### Follow the [guide doc](Doc1.pdf) to submit your work. 
---
>Be creative! Feel free to link to embed your [data](player_data_salaries_2020.csv), [code](sample-data-clean.ipynb), [image](ACC.png) here

More information on GitHub Pages can be found [here](https://pages.github.com/)
![](Actuarial.gif)
