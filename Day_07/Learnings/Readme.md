🗓️ Day 7 – HAVING Clause
📘 Topics I Explored Today

Using HAVING to filter grouped/aggregated results

Understanding difference between WHERE (row-level filtering) vs HAVING (group-level filtering)

Applying conditions on aggregate functions (COUNT, SUM, AVG, etc.)

Combining both WHERE and HAVING in the same query

Filtering multiple groups using logical operators (AND/OR)

Referencing aggregate aliases in certain SQL engines

💻 Practice Queries
-- Show services with more than 100 patients
SELECT service, COUNT(*) AS patient_count
FROM patients
GROUP BY service
HAVING COUNT(*) > 100;

-- Filtering rows first, then filtering grouped results
SELECT service, COUNT(*) AS elderly_count
FROM patients
WHERE age >= 65
GROUP BY service
HAVING COUNT(*) > 20;

-- Multiple aggregate filters together
SELECT 
    service,
    AVG(satisfaction) AS avg_satisfaction,
    COUNT(*) AS total_patients
FROM patients
GROUP BY service
HAVING AVG(satisfaction) > 80
   AND COUNT(*) > 50;

🧪 Practice Tasks I Completed

✔ Identified services with > 500 admitted patients
✔ Found services with avg satisfaction < 75
✔ Listed weeks with staff presence < 50

🧠 Thought Process for Today’s Challenge

Challenge: Find services that refused more than 100 patients in total AND have an average satisfaction below 80.
Return: service name, total refused, average satisfaction.

How I approached it:

I recognized that the question needs grouped results → group by service

We need two metrics:

Total refused → SUM(patients_refused)

Average satisfaction → AVG(satisfaction)

Both conditions involve aggregated values → must use HAVING

Combine both conditions with AND

Return only the required columns

✅ Final Query:

SELECT 
    service,
    SUM(patients_refused) AS total_refused,
    AVG(satisfaction) AS avg_satisfaction
FROM services_weekly
GROUP BY service
HAVING SUM(patients_refused) > 100
   AND AVG(satisfaction) < 80;

📝 Key Notes

WHERE filters rows first, HAVING filters groups later

HAVING is used only after GROUP BY

Aggregates (COUNT, SUM, AVG, etc.) cannot be used in WHERE

Use HAVING to apply conditions on aggregates

Combining WHERE + HAVING makes queries efficient

Query order: FROM → WHERE → GROUP BY → HAVING → ORDER BY

⭐ Takeaway

HAVING is powerful when you want to filter summary-level insights — perfect for dashboards, KPIs, and comparative analysis across categories.
