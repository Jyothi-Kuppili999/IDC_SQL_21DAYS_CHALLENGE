### 🗓️ Day 6 – GROUP BY Clause
📘 Topics I Focused On

Using GROUP BY to summarize data by categories

Applying aggregate functions per group (COUNT, SUM, AVG, etc.)

Understanding grouping logic — one result per group

Grouping by multiple columns for deeper insights

Differentiating WHERE (row filter) vs HAVING (group filter)

Combining GROUP BY with ORDER BY to rank groups

### 💻 Practice Queries
-- Count patients per service
SELECT service, COUNT(*) AS total_patients
FROM patients
GROUP BY service;

-- Aggregating multiple metrics per service
SELECT 
    service,
    COUNT(*) AS total_patients,
    AVG(age) AS avg_age,
    AVG(satisfaction) AS avg_satisfaction
FROM patients
GROUP BY service
ORDER BY total_patients DESC;

-- Group by multiple columns (service + age group)
SELECT
    service,
    CASE WHEN age >= 65 THEN 'Senior' ELSE 'Adult' END AS age_group,
    COUNT(*) AS count
FROM patients
GROUP BY service, age_group;

### 🧪 Practice Tasks I Completed

✔ Counted patients grouped by service
✔ Calculated average age of patients per service
✔ Found total staff count per role

### 🧠 Thought Process for Today’s Challenge

Challenge: For each hospital service, find total admitted, total refused, and admission rate (% of requests admitted).
Order results by admission rate (highest first).

How I approached it:

Identified relevant columns: patients_admitted, patients_refused, and patients_request from services_weekly

Need grouped results per service → use GROUP BY service

Calculate totals using SUM() for admitted and refused

Compute admission rate using the formula:
(SUM(patients_admitted) / SUM(patients_request)) * 100

Round the rate for readability and order results in descending order

### ✅ Final Query:

SELECT 
    service,
    SUM(patients_admitted) AS total_admitted,
    SUM(patients_refused) AS total_refused,
    ROUND((SUM(patients_admitted) * 100.0 / SUM(patients_request)), 2) AS admission_rate
FROM services_weekly
GROUP BY service
ORDER BY admission_rate DESC;

### 📝 Key Notes

GROUP BY groups rows before aggregates are calculated

All non-aggregated columns in SELECT must appear in GROUP BY

Use WHERE to filter rows before grouping

Use HAVING to filter after aggregation

You can sort results by aggregate values (ORDER BY COUNT(*) DESC)

Combining GROUP BY + ORDER BY makes summary reports meaningful

#### ⭐ Takeaway

GROUP BY is the foundation of data summarization — it transforms raw data into insightful metrics like counts, averages, or totals per category.
