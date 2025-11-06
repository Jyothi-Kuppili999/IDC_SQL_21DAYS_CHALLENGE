### 🗓️ Day 4 – Working with LIMIT and OFFSET
📘 Topics I Explored

Limiting query results with LIMIT

Skipping rows using OFFSET

Applying pagination in SQL

Combining LIMIT + OFFSET + ORDER BY

Understanding how databases handle row ordering

Database-specific variations of limit syntax

### 💻 Practice Queries
-- Fetch first 5 patients
SELECT * 
FROM patients 
LIMIT 5;

-- Skip first 10 and get next 10 (Page 2)
SELECT * 
FROM patients 
LIMIT 10 OFFSET 10;

-- Get Page 3: Rows 21–30
SELECT * 
FROM patients 
LIMIT 10 OFFSET 20;

-- View the 10 latest patient admissions
SELECT *
FROM patients
ORDER BY arrival_date DESC
LIMIT 10;

### 🧪 Practice Tasks I Solved

✔ Displayed first 5 patients from the list
✔ Fetched patients 11 – 20 using OFFSET
✔ Found 10 most recent patient admissions

### 🧠 Thought Process for Today’s Challenge

Challenge: Retrieve the 3rd to 7th highest satisfaction scores, showing patient_id, name, service, and satisfaction.

How I broke it down:

Identify the column to rank → satisfaction

We need sorted data first → use ORDER BY satisfaction DESC

To skip the top 2 highest scores → use OFFSET 2

To get the next 5 rows only → use LIMIT 5

Combine both with a proper order

### ✅ Final Query:

SELECT patient_id, name, service, satisfaction
FROM patients
ORDER BY satisfaction DESC
LIMIT 5 OFFSET 2;

### 📝 Key Notes

LIMIT defines how many rows to fetch, OFFSET defines how many to skip

Always pair LIMIT with ORDER BY for predictable results

Pagination formula: OFFSET = (page_number - 1) × page_size

Query execution order: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT

Syntax differs slightly between SQL dialects (MySQL, SQL Server, Oracle, etc.)

### ⭐ Takeaway

LIMIT and OFFSET are super useful for data previews, dashboards, and reports — helping you fetch just the slice of data you need efficiently.
