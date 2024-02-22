# EPL STATS ANALYSIS FOR 21/22 SEASON

## TABLE OF CONTENTS

- [INTRODUCTION](#introduction)
- [PROJECT BACKGROUND](#project-background)
- [Problem](#problem)
- [Data source](#data-source)
- [Tools](#tools)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [DATA ANALYSIS](#data-analysis)
- [RESULTS AND FINDINGS](#results-and-findings)
- [RECOMMENDATION AND CONCLUSION](#recommendation-and-conclusion)
- [REFERENCE](#reference)

# INTRODUCTION

## PROJECT BACKGROUND

The English Premier League is one of the most esteemed football competitions globally, featuring 380 matches hosted at various venues nationwide. The officiating of each match holds significant sway over match outcomes and ultimately impacts the league standings. The insights derived from this report hold relevance for analysts, league viewers, the English Football Association, and all associated stakeholders.

### Problem

This analysis and report's primary objective is to examine individual referees' officiating patterns across all matches of the EPL 2021/2022 season. Utilizing available data on key incidents in each game, the aim is to provide insights into referees' unique contributions in shaping matches' outcomes.

### Data source

The primary dataset used for this analysis is the CSV file obtained from data.world

### Tools

* Excel - used for data cleaning and visualization [download here](https://microsoft.com)
* SQL management server studio - Data analysis [download here](https://learn.microsoft.com)
* MS Word - used for report writing/storytelling [download here](https://microsoft.com).

### Exploratory Data Analysis

EDA involved the following:

* How many games were officiated by individual referees?
* What was the average number of goals distribution per game for individual referees?
* What was the average number of fouls distribution per game for individual referees?
* What was the average number of yellow cards per game for individual referees?
* What was the average number of red cards per game for individual referees?
* What were the average home shots on goal per game for individual referees?
* What were the average away shots on goal per game for individual referees?
* What was the average home ball possession per game for individual referees?
* What was the average away ball possession per game for individual referees?
* What was the average home/away team win percentage per game for individual referees?

## DATA ANALYSIS

```sql
SELECT referee, COUNT (*) AS Games_Officated
FROM EPLsoccer21-22
GROUP BY referee
ORDER BY Games_Officated DESC;
```
SQL code queried on SSMS to determine the number of game officiated by individual referees throughout the season.

![image](https://github.com/Tobicity/TOBI-A.-C.-PORTFOLIO-1-SQL-EXCEL-/assets/151846661/2af3e5b2-3c02-4dbb-8427-fd1d423bd76c)


```sql
SELECT referee,
      ROUND(AVG(FTHG + FTAG), 0) AS avg_goals_per_game,
      ROUND(AVG(HF + AF). 0) AS avg_fouls_per_game,
      ROUND(AVG(HY + AY), 0) AS avg_yellow_cards_per_game,
      ROUND(AVG(HR + AR), 0) AS avg_red_card_per_game
FROM EPLsoccer21-22
GROUP BY referee;
```
SQL code queried on SSMS to determine the average number of goals, fouls, yellow/red cards in each game for individual referees.

![image](https://github.com/Tobicity/TOBI-A.-C.-PORTFOLIO-1-SQL-EXCEL-/assets/151846661/b3fadeb3-c37d-4959-85e6-1b94e3251644)

![image](https://github.com/Tobicity/TOBI-A.-C.-PORTFOLIO-1-SQL-EXCEL-/assets/151846661/20a8eed3-050d-4876-94cd-86811d678414)

![image](https://github.com/Tobicity/TOBI-A.-C.-PORTFOLIO-1-SQL-EXCEL-/assets/151846661/62167337-36c0-4d8f-afeb-ce5ae44f6ed3)

![image](https://github.com/Tobicity/TOBI-A.-C.-PORTFOLIO-1-SQL-EXCEL-/assets/151846661/de14a2d2-8a5c-4441-9a7e-fd36264b342d)

```sql
SELECT referee,
    ROUND(AVG(HST), 0) AS avg_home_shots_on_goal
    ROUND(AVG(AST), 0) AS avg_away_shots_on_goal,
    ROUND(AVG(HST / (HST + AST) * 100), 0) AS avg_possession_home,
    ROUND(AVG(AST / (HST + AST) * 100), 0) AS avg_possession_away
FROM EPLsoccer21-22
GROUP BY referee;
```
SQL code queried on SSMS to determine the average number of home/away shots on goal, and average ball possession for both the home/away teams in each game officiated by individual referees.

![image](https://github.com/Tobicity/TOBI-A.-C.-PORTFOLIO-1-SQL-EXCEL-/assets/151846661/fa90d5f0-384d-40d9-bdcc-d336b8899c9a)

![image](https://github.com/Tobicity/TOBI-A.-C.-PORTFOLIO-1-SQL-EXCEL-/assets/151846661/766c48b1-7105-4fd8-b5e6-a1ffd36910d8)

![image](https://github.com/Tobicity/TOBI-A.-C.-PORTFOLIO-1-SQL-EXCEL-/assets/151846661/12b98dd8-3293-46ea-b220-c9f052f33ec3)

![image](https://github.com/Tobicity/TOBI-A.-C.-PORTFOLIO-1-SQL-EXCEL-/assets/151846661/9d45e06e-a25a-4e25-b9b5-76e8d2e8d041)

```sql
SELECT referee,
    ROUND(SUM(CASE WHEN FTHG > FTAG THEN 1 ELSE 0 END) * 100 / COUNT(*), 2) AS         home_win_percentage,
    ROUND(SUM(CASE WHEN FTAG > FTHG THEN 1 ELSE 0 END) * 100 / COUNT(*), 2) AS              away_win_percentage
FROM EPLsoccer21-22
GROUP BY referee;
```
SQL code queried on SSMS to determine the rate of home/away wins in percentage for each game officiated by individual referees.

## RESULTS AND FINDINGS

* The number of games officiated by individual referees was determined showing the level of trust and general acceptance of individual performances.
* Various charts and graphs were created to show the average goals, fouls, cards, shots, ball possession and winning rates per match officiated for each referee throughout the season.
* Individual insights were generated by analyzing each referee's performance to show patterns, consistencies and/or intent.

## RECOMMENDATION AND CONCLUSION

Anomalies in referee general performance spotting by this analysis should be escalated to avoid and reduce officiating biases.
This information is relevant for football associations, fans, punters, analysts and all other stakeholders.

## REFERENCE

Badreddine, S., & Spranger, M. (2021). Extending Real Logic with Aggregate Functions. In NeSy (pp. 115-125).

[Data source](https://data.world)

😄
