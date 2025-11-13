🗓️ Day 10 – CASE Statements (Conditional Logic)
📘 Topics I Learned Today

Using CASE to add conditional logic in SQL queries

Difference between Simple CASE (matches specific values) and Searched CASE (evaluates logical conditions)

Creating derived columns dynamically

Performing conditional aggregation using CASE

Applying CASE inside SELECT, ORDER BY, and even within aggregate functions

Importance of ordering conditions — first match is applied

💻 Practice Queries
-- Categorize satisfaction levels
SELECT 
    name,
    satisfaction,
    CASE 
        WHEN satisfaction >= 90 THEN 'Excellent'
        WHEN satisfaction >= 75 THEN 'Good'
        WHEN satisfaction >= 60 THEN 'Fair'
        ELSE 'Needs Improvement'
    END AS satisfaction_category
FROM patients;

-- Create age-based groups
SELECT 
    name,
    age,
    CASE 
        WHEN age < 18 THEN 'Pediatric'
        WHEN age BETWEEN 18 AND 65 THEN 'Adult'
        ELSE 'Senior'
    END AS age_group
FROM patients;

-- Conditional aggregation per service
SELECT 
    service,
    COUNT(*) AS total_patients,
    SUM(CASE WHEN satisfaction >= 80 THEN 1 ELSE 0 END) AS high_satisfaction_count,
    SUM(CASE WHEN satisfaction < 60 THEN 1 ELSE 0 END) AS low_satisfaction_count
FROM patients
GROUP BY service;

🧪 Practice Tasks I Completed

✔ Classified patients into High / Medium / Low satisfaction groups
✔ Labeled staff as Medical or Support based on roles
✔ Segmented patients by age group (0–18, 19–40, 41–65, 65+)

🧠 Thought Process for Today’s Challenge

Challenge: Build a service performance summary showing service name, total admitted patients, and a performance category:
‘Excellent’ (avg satisfaction ≥ 85), ‘Good’ (≥ 75), ‘Fair’ (≥ 65), otherwise ‘Needs Improvement’.
Results should be ordered by average satisfaction in descending order.

How I approached it:

I began by identifying the required metrics:

SUM(patients_admitted) → total admitted

AVG(satisfaction) → average satisfaction per service

Then, I grouped by service since we need service-wise summaries

Used a CASE expression to categorize each service’s performance

Ordered results by average satisfaction for ranking

✅ Final Query:

SELECT 
    service,
    SUM(patients_admitted) AS total_admitted,
    ROUND(AVG(satisfaction), 2) AS avg_satisfaction,
    CASE 
        WHEN AVG(satisfaction) >= 85 THEN 'Excellent'
        WHEN AVG(satisfaction) >= 75 THEN 'Good'
        WHEN AVG(satisfaction) >= 65 THEN 'Fair'
        ELSE 'Needs Improvement'
    END AS performance_category
FROM services_weekly
GROUP BY service
ORDER BY avg_satisfaction DESC;

📝 Key Notes

CASE is an expression, not a control structure — it returns a value, not flow control

Use Simple CASE for value matching and Searched CASE for conditional logic

Always include an ELSE to handle unmatched conditions

You can use CASE in SELECT, ORDER BY, or even within SUM() or AVG()

Execution is top-to-bottom — once a match is found, others are ignored

CASE improves report readability and flexibility by embedding logic into SQL

⭐ Takeaway

CASE brings decision-making into SQL — turning static data into smart, dynamic insights. It’s a must-know for dashboards, conditional KPIs, and performance reporting.
