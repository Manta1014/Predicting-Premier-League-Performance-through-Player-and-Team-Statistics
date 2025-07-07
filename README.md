# ⚽ Premier League SQL Analytics Project

This repository contains an SQL-based analysis of the 2023–2024 English Premier League (EPL) season.  
The project explores how player-level and team-level statistics relate to league outcomes, using SQL queries to identify patterns and potential predictors of success.

👉 **[Research Paper (PDF)](./paper/Research_Paper_Jinuk_Seo_Wonjune_Lee.pdf)**

---

## 💡 Project Goals
- Investigate whether teams with high-rated players or top scorers perform better.
- Identify players with the best goal efficiency (actual goals vs. expected goals).
- Analyze team possession and xG to predict next season’s top teams.
- Explore which teams miss the most big chances and how that relates to performance.

---

## 🗄 Data
- **Premier League team table:** `pl_table_2023_24`
- **Player ratings:** `player_player_ratings`
- **Top scorers:** `player_top_scorers`
- **Expected goals (xG):** `player_expected_goals`
- **Big chances missed:** `player_big_chances_missed`
- **Possession percentage:** `possession_percentage_team`

---

## 🛠 Methods
- **SQL database:** SQLite, designed with a normalized schema.
- **Techniques:** JOINs, CTEs (WITH clauses), aggregation, nested queries, filtering, ordering.

---

## 🔍 Key Queries

### 🔹 Team Ratings vs League Rank
```sql
WITH team_ratings AS (
    SELECT r.Team, ROUND(AVG(r."FotMob Rating"), 2) AS avg_rating
    FROM player_player_ratings r
    GROUP BY r.Team
)
SELECT t.name AS Team, t.pts, team_ratings.avg_rating
FROM pl_table_2023_24 t
JOIN team_ratings ON t.name = team_ratings.Team
ORDER BY t.pts DESC;
