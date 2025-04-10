# SQL for Data Analysis

**🧾 Objective: Use SQL queries to extract and analyze data from a sample database**

### 📌 Query 1: Top 5 Longest Movies
```sql
-- SQL Query
SELECT title, length 
FROM film 
ORDER BY length DESC 
LIMIT 5;
```

**Result:**

| title            | length |
|------------------|--------|
| GANGS PRIDE      | 185    |
| HOME PITY        | 185    |
| CHICAGO NORTH    | 185    |
| CONTROL ANTHEM   | 185    |
| DARN FORRESTER   | 185    |

---

### 📌 Query 2: Number of Films per Rating
```sql
SELECT rating, COUNT(*) AS total_films
FROM film
GROUP BY rating
ORDER BY total_films DESC;
```

**Result:**

| rating | count |
|--------|-------|
| G      | 178   |
| NC-17  | 210   |
| PG     | 194   |
| PG-13  | 223   |
| R      | 195   |


---

### 📌 Query 3: Join Example – Customer & Payment Info
```sql
SELECT c.first_name, c.last_name, SUM(p.amount) AS total_spent
FROM customer c
JOIN payment p ON c.customer_id = p.customer_id
GROUP BY c.customer_id
ORDER BY total_spent DESC
LIMIT 5;
```

**Result:**

| first_name | last_name | total_amount |
|------------|-----------|--------------|
| KARL       | SEAL      | 221.55       |
| ELEANOR    | HUNT      | 216.54       |
| CLARA      | SHAW      | 195.58       |
| MARION     | SNYDER    | 194.61       |
| RHONDA     | KENNEDY   | 194.61       |


---

### 📌 Query 4: Subquery – Films Longer Than Average
```sql
SELECT title, length
FROM film
WHERE length > (SELECT AVG(length) FROM film)
ORDER BY length DESC;
```

**Result:**

| Title                        | Value |
|-----------------------------|-------|
| CHICAGO NORTH               | 185   |
| CONTROL ANTHEM              | 185   |
| DARN FORRESTER              | 185   |
| GANGS PRIDE                 | 185   |
| HOME PITY                   | 185   |
| MUSCLE BRIGHT               | 185   |
| POND SEATTLE                | 185   |
| SOLDIERS EVOLUTION          | 185   |
| SWEET BROTHERHOOD           | 185   |
| WORST BANGER                | 185   |
| CONSPIRACY SPIRIT           | 184   |
| CRYSTAL BREAKING            | 184   |
| KING EVOLUTION              | 184   |
| MOONWALKER FOOL             | 184   |
| SMOOCHY CONTROL             | 184   |
| SONS INTERVIEW              | 184   |
| SORORITY QUEEN              | 184   |
| THEORY MERMAID              | 184   |
| CATCH AMISTAD               | 183   |
| FRONTIER CABIN              | 183   |
| SCALAWAG DUCK               | 183   |
| WIFE TURN                   | 183   |
| YOUNG LANGUAGE              | 183   |
| BAKED CLEOPATRA             | 182   |
| MONSOON CAUSE               | 182   |
| RECORDS ZORRO               | 182   |
| REDS POCUS                  | 182   |
| SATURN NAME                 | 182   |
| SEARCHERS WAIT              | 182   |
| ANALYZE HOOSIERS            | 181   |
| HAUNTING PIANIST            | 181   |
| HOTEL HAPPINESS             | 181   |
| INTRIGUE WORST              | 181   |
| JACKET FRISCO               | 181   |
| LAWLESS VISION              | 181   |
| LOVE SUICIDES               | 181   |
| RUNAWAY TENENBAUMS          | 181   |
| STAR OPERATION              | 181   |
| WILD APOLLO                 | 181   |
| ALLEY EVOLUTION             | 180   |
| CONFIDENTIAL INTERVIEW      | 180   |
| IMPACT ALADDIN              | 180   |
| MIXED DOORS                 | 180   |
| MUSSOLINI SPOILERS          | 180   |
| NASH CHOCOLAT               | 180   |
| SOMETHING DUCK              | 180   |
| ANONYMOUS HUMAN             | 179   |
| BORN SPINAL                 | 179   |
| CASUALTIES ENCINO           | 179   |
| CAUSE DATE                  | 179   |
| FLIGHT LIES                 | 179   |
| KICK SAVANNAH               | 179   |
| POTLUCK MIXED               | 179   |
| REDEMPTION COMFORTS         | 179   |
| SLACKER LIAISONS            | 179   |
| TEXAS WATCH                 | 179   |
| TORQUE BOUND                | 179   |
| VIRGIN DAISY                | 179   |
| YOUTH KICK                  | 179   |
| DROP WATERFRONT             | 178   |
| EXPRESS LONELY              | 178   |
| FURY MURDER                 | 178   |
| IMAGE PRINCESS              | 178   |
| INNOCENT USUAL              | 178   |
| MADNESS ATTACKS             | 178   |
| NAME DETECTIVE              | 178   |
| ROCKETEER MOTHER            | 178   |
| WARDROBE PHANTOM            | 178   |
| WRONG BEHAVIOR              | 178   |
| DOUBLE WRATH                | 177   |
| DOZEN LION                  | 177   |
| EMPIRE MALKOVICH            | 177   |
| MANCHURIAN CURTAIN          | 177   |
| QUEST MUSSOLINI             | 177   |
| RIDER CADDYSHACK            | 177   |
| BRAVEHEART HUMAN            | 176   |
| CAPER MOTIONS              | 176   |
| CYCLONE FAMILY              | 176   |
| DRACULA CRYSTAL             | 176   |
| ENTRAPMENT SATISFACTION     | 176   |
| GATHERING CALENDAR          | 176   |
| GREEK EVERYONE              | 176   |
| HOOSIERS BIRDCAGE           | 176   |
| SWEDEN SHINING              | 176   |
| WRATH MILE                  | 176   |

---

### 📌 View Creation Example
```sql
CREATE VIEW top_customers AS
SELECT c.first_name, c.last_name, SUM(p.amount) AS total_spent
FROM customer c
JOIN payment p ON c.customer_id = p.customer_id
GROUP BY c.customer_id
HAVING total_spent > 100;
```

---

### 📌 Index Optimization Example
```sql
CREATE INDEX idx_film_length ON film(length);
```

---

