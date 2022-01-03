# Answers

## Answers for break

1. `SELECT country, COUNT(event) FROM summer GROUP BY country HAVING COUNT(event) > 100 ORDER BY COUNT(event) DESC`

   - ...33 results

2. `SELECT DISTINCT Athlete FROM summer WHERE Country = "CAN" GROUP BY Athlete HAVING COUNT(DISTINCT medal) = 3`

   - OTTENBRITE, Anne
   - TEWKSBURY, Mark
   - THOMPSON, Lesley Allison
   - VAN KOEVERDEN, Adam

3. `WITH all_athletes AS (SELECT * FROM summer UNION SELECT * FROM winter) SELECT athlete, country, count(medal) as cnt_medal, group_concat(distinct event) FROM all_athletes GROUP BY athlete, country ORDER BY cnt_medal DESC LIMIT 10`

   - ...10 results

4. `SELECT GROUP_CONCAT(distinct sport), GROUP_CONCAT(event), COUNT(medal) as medals, athlete, GROUP_CONCAT(distinct country) FROM summer WHERE year = 2012 GROUP BY athlete ORDER BY medals DESC`

   - ...1,777 results

5. `WITH olympics AS (SELECT * FROM summer UNION SELECT * FROM winter) SELECT DISTINCT o.country, d.population FROM olympics o JOIN dictionary d ON (o.country = d.code) WHERE o.medal = "Gold" AND ((o.sport = "Boxing" AND o.year = 2008) OR (o.sport = "skiing" AND o.year = 2006))`

   - ...21 results

## Answers for homework

1. `SELECT duration FROM movies WHERE title = "Outback"`

   - 86

2. `SELECT title FROM movies where year = "2017" AND director = "Peter Sullivan"`

   - The Sandman

3. `SELECT reviews_from_users , reviews_from_critics FROM movies WHERE imdb_title_id = "tt7336182"`

   - reviews_from_users - 47
   - reviews_from_critics - 12

4. `SELECT m.title , COUNT(r.votes_1) FROM movies m JOIN ratings r ON (m.title = "Joker")`

   - 448

5. `SELECT COUNT(production_company) FROM movies`

   - 3146

6. `SELECT AVG(duration) FROM movies WHERE year <> 2018 AND (actors LIKE "%Dharmajan Bolgatty%" OR actors LIKE "%Sugith Varughes%")`

   - 136.0769

7. `SELECT title, genre, (worlwide_gross_income_in_USD - budget) AS profit FROM movies WHERE production_company = "DreamWorks" ORDER BY profit DESC`

   - 1917 Drama; War 289857224
   - Qua la zampa 2 - Un amico \_\_ per sempre Adventure; Comedy; Drama 59790499
   - The Turning - La casa del male Drama; Horror; Mystery 4596113

8. `SELECT m.title, m.year, r.age_18_to_30_avg_vote FROM movies m JOIN ratings r ON (r.imdb_title_id = m.imdb_title_id) WHERE m.actors LIKE '%Lin Shaye%' ORDER BY age_18_to_30_avg_vote ASC`

   - Max Reload and the Nether Blasters 2020 4.1

9. `WITH avg0_18 AS (SELECT AVG(age_0_to_18_avg_vote) as avg, "0_18" as class FROM ratings), avg18_30 AS (SELECT AVG(age_18_to_30_avg_vote) as avg, "18_30" as class FROM ratings), avg30_45 AS (SELECT AVG(age_30_to_45_avg_vote) as avg, "30_45" as class FROM ratings), avg45plus AS (SELECT AVG(age_45_plus_avg_vote) as avg, "45plus" as class FROM ratings), avgs AS (SELECT * FROM avg0_18 UNION SELECT * FROM avg18_30 UNION SELECT * FROM avg30_45 UNION SELECT * FROM avg45plus ) SELECT MIN(class) FROM avgs`

   - 0_18

10. `SELECT genre, avg(duration) FROM movies GROUP BY genre ORDER BY avg(duration) DESC LIMIT 3`

    - 219.0000 Action; Fantasy; Horror
    - 197.0000 Comedy; Drama; War
    - 185.0000 History; War

11. `WITH years AS (SELECT m.year , r.average_vote FROM movies m JOIN ratings r ON (m.imdb_title_id=r.imdb_title_id) WHERE language="English"), average AS (SELECT year, avg(average_vote) as average_votes FROM years GROUP BY year ORDER BY avg(average_vote) DESC) SELECT * FROM average`

    - 2019 5.9125000000000005
    - 2018 5.588333333333333
    - 2017 5.504
    - 2020 5.033333333333333

12. `SELECT m.title ,r.males_vote_count,r.females_vote_count , IF( r.males_avg_vote>r.females_avg_vote, r.males_avg_vote-r.females_avg_vote, r.females_avg_vote-r.males_avg_vote) as gap from movies m JOIN ratings r ON (m.imdb_title_id=r.imdb_title_id) ORDER BY gap DESC LIMIT 10`

    - Semma Botha Aagatha 148 1 5
    - New Heaven and New Earth 9 26 4.4
    - Removed 92 38 3.4
    - Escape and Evasion 77 9 3
    - No Doubt 146 142 2.9000000000000004
    - Mehbooba 142 7 2.6999999999999993
    - The Theta Girl 94 33 2.5
    - Abdel et la comtesse 64 12 2.4000000000000004
    - Armenian Haunting 66 14 2.4000000000000004
    - D--rt k--seli ----gen 74 17 2.3999999999999995

13. `WITH director AS (SELECT director, AVG(duration) as director_avg_movie_duration FROM movies GROUP BY director), production AS (SELECT production_company , MIN(year) as company_firstmovie_year FROM movies GROUP BY production_company), basicWithDir AS (SELECT m.title, m.year,m.production_company,d.director,d.director_avg_movie_duration FROM movies m JOIN director d ON (m.director=d.director)), totalResult AS (SELECT b.title,b.year,b.director,b.director_avg_movie_duration , p.production_company,p.company_firstmovie_year FROM basicWithDir b JOIN production p ON (b.production_company=p.production_company)) SELECT * FROM totalResult`

    - ...3,147 results
