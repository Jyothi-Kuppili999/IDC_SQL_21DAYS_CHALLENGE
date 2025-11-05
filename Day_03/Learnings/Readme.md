### 🗓️ Day 3 – Sorting Data using ORDER BY
📘 Concepts I Learned Today

Using ORDER BY to sort results

Sorting in ascending (ASC) & descending (DESC) order

Sorting by more than one column

Sorting by column names or column positions (not recommended but possible)

Behavior of NULL values in sorting

Importance of sorting in analysis and performance impact

### 💻 Practice Queries
-- Highest age first
SELECT * 
FROM patients
ORDER BY age DESC;

-- Sort by age (descending) & within same age, sort names alphabetically
SELECT * 
FROM patients
ORDER BY age DESC, name ASC;

-- Sort by column index (2nd column) - not best practice but works
SELECT name, age 
FROM patients
ORDER BY 2 DESC;

-- Retrieve top satisfied patients
SELECT *
FROM patients
ORDER BY satisfaction_score DESC
LIMIT 10;

### 🧪 Practice Tasks I Completed

✔ Sort patients by age (desc)
✔ Sort weekly service data by week ascending & patient requests descending
✔ Sort staff alphabetically by name

### 🧠 Thought Process for Today’s Challenge

Challenge: Show the top 5 weeks with the highest patient refusals.
Return week, service, patients_refused, patients_request — sorted by refusals descending.

How I approached it:

Identify table containing weekly service data

Need to select week, service, refusal count, request count

Focus on sorting by refusals in descending order

Limit results to 5 highest refusal weeks

Use ORDER BY + LIMIT combo

### ✅ Final Query:

SELECT week, service, patients_refused, patients_request
FROM services_weekly
ORDER BY patients_refused DESC
LIMIT 5;

### 📝 Key Notes

ORDER BY always executes after filtering (WHERE)

ASC is default, so writing ASC is optional

Multi-column sort helps when values tie in the first column

Sorting can be slow on huge tables → indexes help

LIMIT pairs extremely well with ORDER BY for “Top-N” results

### ⭐ Personal Takeaway

Sorting is one of the simplest yet most powerful SQL tools — especially for reports (Top 5, Top 10, highest, lowest, trends, rankings, etc.).
