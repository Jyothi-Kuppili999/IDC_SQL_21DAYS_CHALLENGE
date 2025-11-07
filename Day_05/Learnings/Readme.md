🗓️ Day 5 – Aggregate Functions (COUNT, SUM, AVG, MIN, MAX)
📘 Topics I Learned Today

Aggregate functions summarize multiple rows into one result

Using COUNT, SUM, AVG, MIN, and MAX for analysis

Handling NULLs in aggregation

Combining multiple aggregates in a single query

Applying filters with WHERE while using aggregates

Using ROUND() for formatting numerical output

Counting unique records with DISTINCT

💻 Practice Queries
-- Total number of patients
SELECT COUNT(*) AS total_patients
FROM patients;

-- Multiple aggregates in one query
SELECT 
    COUNT(*) AS total,
    AVG(age) AS avg_age,
    MIN(age) AS youngest,
    MAX(age) AS oldest,
    SUM(satisfaction) AS total_satisfaction
FROM patients;

-- Filtered average (only for Cardiology)
SELECT AVG(satisfaction) AS avg_cardiology_satisfaction
FROM patients
WHERE service = 'Cardiology';

-- Rounded average value
SELECT ROUND(AVG(age), 2) AS avg_age_rounded
FROM patients;

-- Counting unique service types
SELECT COUNT(DISTINCT service) AS unique_services
FROM patients;

🧪 Practice Tasks I Completed

✔ Counted total patients in hospital
✔ Calculated average satisfaction score
✔ Found minimum and maximum patient ages

🧠 Thought Process for Today’s Challenge

Challenge: Calculate total patients admitted, total patients refused, and the average satisfaction (rounded to 2 decimals) across all services and weeks.

How I approached it:

Identify the correct dataset → weekly services table (services_weekly)

Columns to use: patients_admitted, patients_refused, and satisfaction

Apply aggregates:

SUM() → total admitted and refused

AVG() → average satisfaction

Use ROUND() for clean decimal output

Combine all in a single SELECT statement

✅ Final Query:

SELECT 
    SUM(patients_admitted) AS total_admitted,
    SUM(patients_refused) AS total_refused,
    ROUND(AVG(satisfaction), 2) AS avg_satisfaction
FROM services_weekly;

📝 Key Notes

Aggregates work across rows, not individual records

NULL values are ignored in SUM, AVG, MIN, and MAX

Always alias your aggregates for clarity

You can mix aggregates in the same query

Use WHERE to aggregate subsets of data

COUNT(DISTINCT column) helps find unique entries

⭐ Takeaway

Aggregate functions are essential for data summaries and insights — perfect for dashboards, KPIs, and analytical reports.
