🗓️ Day 9 – Working With Date Functions
📘 Topics I Explored Today

Using date functions to manipulate and extract date-related values

Performing date arithmetic (adding/subtracting days)

Converting date values into components (year, month, day, week)

Calculating duration between two dates

Filtering records based on date ranges

Understanding database-specific differences in date functions

💻 Practice Queries
-- Calculate number of days a patient stayed
SELECT 
    patient_id,
    name,
    arrival_date,
    departure_date,
    CAST(JULIANDAY(departure_date) - JULIANDAY(arrival_date) AS INTEGER) AS stay_days
FROM patients;

-- Extract year and month separately
SELECT 
    patient_id,
    strftime('%Y', arrival_date) AS arrival_year,
    strftime('%m', arrival_date) AS arrival_month
FROM patients;

-- Filter by full-year range
SELECT *
FROM patients
WHERE arrival_date BETWEEN '2024-01-01' AND '2024-12-31';

-- Patients admitted in June
SELECT *
FROM patients
WHERE strftime('%m', arrival_date) = '06';

🧪 Practice Tasks I Completed

✔ Extracted year from arrival dates
✔ Calculated number of days stayed by each patient
✔ Filtered admissions based on specific months

🧠 Thought Process for Today’s Challenge

Challenge: Find the average length of stay (in days) for each service, but only include services where the average stay exceeds 7 days. Show average stay, patient count, and order results by average stay descending.

How I approached it:

Length of stay = departure date – arrival date

In SQLite, use: JULIANDAY(departure_date) - JULIANDAY(arrival_date)

This value needs to be aggregated per service → use GROUP BY service

Compute average stay length using AVG()

Only show services where the average stay > 7 → apply HAVING AVG(...) > 7

Include patient count using COUNT(*)

Order by average stay in descending order for meaningful ranking

✅ Final Query:

SELECT 
    service,
    ROUND(AVG(JULIANDAY(departure_date) - JULIANDAY(arrival_date)), 2) AS avg_stay_days,
    COUNT(*) AS patient_count
FROM patients
GROUP BY service
HAVING AVG(JULIANDAY(departure_date) - JULIANDAY(arrival_date)) > 7
ORDER BY avg_stay_days DESC;

📝 Key Notes

Use ISO date format YYYY-MM-DD for reliable comparisons

Date arithmetic varies by SQL engine (SQLite, MySQL, PostgreSQL)

strftime() is powerful for extracting date parts

Casting results helps maintain consistent numeric output

Avoid heavy date functions in WHERE to preserve performance

Date operations are essential for time-based reporting (trends, durations, monthly summaries)

⭐ Takeaway

Date functions make time-based analysis possible — critical for calculating lengths of stay, tracking trends, filtering by time periods, and building meaningful dashboards.
