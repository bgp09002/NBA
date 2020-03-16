# Rise of the 3 Point Shot in the NBA

## Problem Statement

The popularity and usage of the 3 point shot has risen substantially in the NBA in the last 10+ years. This is due in large part to a higher usage and trust of analytics throughout the league. Some teams have taken larger strides than others into implementing more 3 point shots per game, but the league as a whole 3 point shots per game are trending upwards. The goal of my project is to try and see if this trend is actually accurate. Are 3 point shots more representative for success than 2 point shots? Are teams that attempt more 3 point shots than others more successful?

## Executive Summary

### Objectives
- Collect NBA data
    - 3 point field goals and 2 point field goals for both players and teams
        - Attempts, makes, and percentages
    - Team wins and playoff berths from 1983 onwards for measures of team success
        - 1983 was the first year 16 teams were selected to the playoffs
    - Player salary from 1990 onwards for measures of individual player value
        - 1990 was earliest data available
- Visualize trends of the data to show how the NBA has been changing over these timeframes
- Construct both regression and classification models in order to target which type of shot is more important to success
    - Regression model utilized to show how many wins in the 82 game season a given team will have
    - Classification model utilized to show whether or not a given team will make the playoffs, appear in the NBA Finals, or win the NBA Championship

### Data Gathering
Data was collected using three different methodologies, shown as links to their codebooks:
1. [Player Statistics](https://github.com/bgp09002/NBA/blob/master/1.%20Data%20Gathering/Get%20Player%20Stats.ipynb)
    - The library `basketball_reference_web_scraper` was used. This library scrapes data from the website [basketball-reference.com](https://www.basketball-reference.com/), which houses NBA statistics dating back to the 1940s.
2. [Player Salaries](https://github.com/bgp09002/NBA/blob/master/1.%20Data%20Gathering/Get%20Player%20Salaries.ipynb)
    - The library `selenium` was used to scrape player name and salary data by year from [hoopshype.com](https://hoopshype.com/salaries/players/).
3. [Team Statistics](https://github.com/bgp09002/NBA/blob/master/1.%20Data%20Gathering/Get%20All%20Teams%20Stats.ipynb)
    - The library `nba_api` was used. This library scrapes data from the [NBA's official website](https://stats.nba.com/).

### Feature Engineering
All of the data gathered from the three methodologies above was vast and full, but there was still some feature engineering necessary. 
- **2 point field goals** 
    - 3 point field goal makes and attempts are always specified, but 2 point field goal makes and attempts are not. There is a general field goal makes and attempt statline, so in order to create the specific 2 point field goal makes and attempts, I needed to subtract 3 point field goal makes and attempts from the general field goal totals.
- **Per game basis**
    - All of the scoring stats that I had accumulated were season totals. I needed to get everything on a per game played basis. Some players played in less games due to things like injuries or resting. As for team totals, two seasons in my dataset were shortened due to labor disputes causing lockouts. The 1998 season had 50 regular season games and the 2011 season had 66 regular season games.
- **3 pointer attempted per 2 pointer attempted**
    - Since the true goal of this project deals with the relation between and change over time of 3 pointers compared to 2 pointers, I needed to create a feature that distinctly shows this change.
- **Normalized Player Salary**
    - To account for inflation and a change in league salary cap over time, I had to normalize each players salary by making it a percentage of the league's total salary for that year. This makes each players normalized salary comparative year over year. 
    
### Modeling
While my goal is to determine whether 3 point shots or 2 point shots are more important in, modeling was used a source to target feature importance. Both linear regression and logistic regression modeling was used. Linear regression was used in order to predict regular season wins by team. Logistic regression was used to predict whether teams made the playoffs, made the NBA finals, or won the NBA championship.

**Linear Regression for Wins**:
1. My first attempt was trying to see if only using offensive shooting statistics would work in order to keep everything in context. I modeled using: `FG2_PCT`,`FG3_PCT`,`FT_PCT`,`FG2A_PER_GP`,`FG3A_PER_GP`,`FG3A/FG2A`.
    - Train R<sup>2</sup>: 0.4028
    - Test R<sup>2</sup>: 0.2947
        - These values did not seem high enough and the model seems to be relatively overfit to the training data, so I didn't want to make any conclusions from it until I tried 

### Limitations
A large limitation to this project is the inability to get totals of specific locations on the court of shot selection. While the most important differentiator is whether or not a given shot was a 3 pointer or a 2 pointer, it would be helpful to see distributions of shots from specific spots on the court or specific distances away from the basket. One major outcome of the move towards analytics in the NBA has been the near elimination of mid-range shots (2 pointers that are farther away from the basket) to make way for higher percentage shots closer to the basket or 3 pointers which are slightly lower percentage shots but give the team 1 extra point.

## Conclusions and Future Work
Here's where I'll talk about my conclusions!!!