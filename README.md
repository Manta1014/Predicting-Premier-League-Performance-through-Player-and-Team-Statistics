# ⚽ Premier League SQL Analytics Project

This repository presents a SQL-based data analytics project that explores team and player performance in the 2023–2024 English Premier League (EPL).  
We use normalized relational databases and advanced SQL techniques to examine the connection between individual statistics and overall team success, aiming to identify key predictors of league performance.

👉 **[Research Paper (PDF)](https://github.com/Manta1014/Predicting-Premier-League-Performance-through-Player-and-Team-Statistics/blob/main/Research%20Paper_Jinuk%20Seo_Wonjune%20Lee.pdf)**  

---

## 💡 Project Goals
- Investigate whether teams with top scorers and high-rated players achieve higher league rankings.
- Measure player goal efficiency beyond expected goals (xG).
- Analyze possession and xG to predict potential top teams for the next season.
- Explore how missed big chances relate to team success.

---

## 🗄 Database Design
Our database is designed based on a normalized Entity-Relationship (ER) model with the following key entities:
- `pl_table_2023_24`: Central table storing team performance (points, goal difference, etc.)
- `player_top_scorers`
- `player_player_ratings`
- `player_big_chances_missed`
- `player_expected_goals`
- `possession_percentage_team`

Each of the player-related tables has a **1:N relationship** with `pl_table_2023_24`, linked via the `Team` field.  
This structure ensures minimal redundancy and supports complex queries through JOINs and CTEs.

---

## 🔍 SQL Research & Queries

### 🔹 Top Scorers vs Team Rank
Finds each team’s top scorer and compares their goal tally with team points and goal difference.  
📂 [Query](https://github.com/Manta1014/Predicting-Premier-League-Performance-through-Player-and-Team-Statistics/blob/main/Do_teams_with_the_top_scorers_perform_better_in_the_league_query.txt)

💡 **Insight:** Teams with high-performing strikers generally ranked higher (e.g., Manchester City’s Erling Haaland scored 27 goals contributing to 91 points).

---

### 🔹 Player Goal Efficiency (Actual Goals vs xG)
Identifies players who outperformed their expected goals.  
📂 [Query](https://github.com/Manta1014/Predicting-Premier-League-Performance-through-Player-and-Team-Statistics/blob/main/Which_players_scored_most_efficient_at_scoring_goals_beyond_expected_goals_query.txt)

💡 **Insight:** Cole Palmer (+3.8 goals above xG) showed exceptional finishing, while others like Darwin Núñez underperformed.

---

### 🔹 Average Player Rating vs League Points
Calculates average team rating and compares it to league points.  
📂 [Query](https://github.com/Manta1014/Predicting-Premier-League-Performance-through-Player-and-Team-Statistics/blob/main/Do_teams_with_the_high_player_rating_tend_to_rank_higher_in_the_league_query.txt)

💡 **Insight:** Higher-rated teams (e.g., Man City, avg. 7.24 rating) achieved better league results.

---

### 🔹 Big Chances Missed
Ranks teams by the number of big chances missed.  
📂 [Query](https://github.com/Manta1014/Predicting-Premier-League-Performance-through-Player-and-Team-Statistics/blob/main/Which_team_missed_big_chances_most_query.txt)

💡 **Insight:** Highlighted inefficiencies in teams with high missed chance counts.

---

### 🔹 Predict Next Season’s Top Teams (xG + Possession)
Combines xG and possession to rank teams most likely to succeed.  
📂 [Query](https://github.com/Manta1014/Predicting-Premier-League-Performance-through-Player-and-Team-Statistics/blob/main/Which_team_would_likely_to_win_next_season(based_on_xg_and_possession)_query.txt)

💡 **Insight:** High xG + high possession teams are strong candidates for next season’s title.

---

## ✨ Technical Highlights
- SQLite-based database with strict normalization
- Use of:
  - **JOINs** and **CTEs (WITH clause)** for complex analytics
  - **Aggregation**, **HAVING**, **nested subqueries**
  - Foreign key relationships for relational integrity
- ACID principles maintained in query operations

---

## 📊 Results Summary
- **Top scorers and player ratings** align strongly with league success.
- **Balanced attacking depth** (top 5 scorer averages) linked to stronger teams.
- **High possession + high xG** teams (e.g., Man City) are top performers.
- Missed big chances expose key weaknesses in some teams.

---

## 📎 Citation
> Jinuk Seo & Wonjune Lee (2025). *Predicting Premier League Performance through Player and Team Statistics*. George Mason University.

---

## 📂 File Structure

```
SQL-PremierLeague-Analysis/
├── queries/
├── results/
├── paper/
├── README.md
```

---

## Notes
- Data Source: [Kaggle Premier League 23/24 Dataset](https://www.kaggle.com/datasets/whisperingkahuna/premier-league-2324-team-and-player-insights)
- The analysis focuses on 2023–2024 season data.
