### 🗓️ Day 2 – Filtering Data with the WHERE Clause
📘 Topics Covered Today

Using WHERE to filter records

Comparison operators (>, <, =, !=)

Combining conditions with AND, OR, NOT

Pattern filtering with LIKE

Checking ranges using BETWEEN

Using IN for cleaner multiple-value filters

Handling NULL values with IS NULL / IS NOT NULL

### 💻 Queries I Practiced
-- Patients older than 60
SELECT *
FROM patients
WHERE age > 60;

-- Patients older than 60 AND in a specific department
SELECT *
FROM patients
WHERE age > 60
  AND service = 'Cardiology';

-- Specific services using OR
SELECT *
FROM patients
WHERE service = 'Emergency' OR service = 'Cardiology';

-- Using IN (cleaner alternative to multiple ORs)
SELECT *
FROM patients
WHERE service IN ('Emergency', 'Cardiology', 'Neurology');

-- Between range example
SELECT *
FROM patients
WHERE age BETWEEN 18 AND 65;

-- Check NULL values
SELECT *
FROM patients
WHERE discharge_date IS NULL;

### 🎯 Practice Tasks I Solved

Patients above age 60

Staff in Emergency department

Weeks with > 100 admissions

### 🧠 Thought Process for Today’s Challenge

Question: Show all patients admitted to the ‘Surgery’ department with satisfaction score below 70. Display patient_id, name, age, and satisfaction score.

How I approached it:

Identify the table containing patient details

We need rows only where service = 'Surgery'

Filter further for satisfaction_score < 70

Only fetch required columns (avoid SELECT *)

Combine both conditions using AND

### ✅ Final Query:

SELECT patient_id, name, age, satisfaction_score
FROM patients
WHERE service = 'Surgery'
  AND satisfaction_score < 70;

### 📝 Key Learnings

WHERE filters rows — it's the base of data extraction

Use IN instead of repeating OR conditions

Numbers don’t need quotes; strings must use single quotes ' '

BETWEEN includes both start and end values

Use IS NULL and IS NOT NULL, not = NULL
