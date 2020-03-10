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
Data was collected using three different methodologies:
1. [Player Statistics](https://github.com/bgp09002/NBA/blob/master/1.%20Data%20Gathering/Get%20Player%20Stats.ipynb)
    - The library `basketball_reference_web_scraper` was used. This library scrapes data from the website [basketball-reference.com](https://www.basketball-reference.com/), which houses NBA statistics dating back to the 1940s.
2. [Player Salaries](https://github.com/bgp09002/NBA/blob/master/1.%20Data%20Gathering/Get%20Player%20Salaries.ipynb)
    - The library `selenium` was used to scrape player name and salary data by year from [hoopshype.com](https://hoopshype.com/salaries/players/).
3. [Team Statistics](https://github.com/bgp09002/NBA/blob/master/1.%20Data%20Gathering/Get%20All%20Teams%20Stats.ipynb)
    - The library `nba_api` was used. This library scrapes data from the [NBA's official website](https://stats.nba.com/)
    