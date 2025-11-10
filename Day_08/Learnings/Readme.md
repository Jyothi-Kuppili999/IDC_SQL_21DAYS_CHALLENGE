### 🗓️ Day 8 – String Functions in SQL
📘 Topics I Explored Today

Changing text case with UPPER() and LOWER()

Measuring string length using LENGTH()

Combining text fields using CONCAT()

Extracting parts of text with SUBSTRING()

Cleaning spaces using TRIM(), LTRIM(), RTRIM()

Replacing text patterns with REPLACE()

Using string functions inside SELECT, WHERE, and CASE

### 💻 Practice Queries
-- Convert names to uppercase
SELECT UPPER(name) AS name_upper
FROM patients;

-- Combine name and service
SELECT CONCAT(name, ' - ', service) AS patient_info
FROM patients;

-- Show only names longer than 15 characters
SELECT name, LENGTH(name) AS name_length
FROM patients
WHERE LENGTH(name) > 15;

-- Extract first 3 letters of the name
SELECT SUBSTRING(name, 1, 3) AS name_prefix
FROM patients;

-- Replace text inside a string
SELECT REPLACE(service, 'Emergency', 'ER') AS service_short
FROM patients;

### 🧪 Practice Tasks I Completed

✔ Converted all patient names to uppercase
✔ Calculated name length for all staff members
✔ Created staff ID–Name combined strings using hyphens

### 🧠 Thought Process for Today’s Challenge

Challenge: Build a patient summary with:
patient_id, full name in UPPERCASE, service in lowercase, age category (Senior/Adult/Minor), and name length.
Only include names longer than 10 characters.

How I approached it:

Identify the required output columns and related transformations:

Name → UPPER(name)

Service → LOWER(service)

Age grouping → CASE expression

Name length → LENGTH(name)

Apply a CASE block to derive categories:

Age ≥ 65 → Senior

Age ≥ 18 → Adult

Else → Minor

Use WHERE LENGTH(name) > 10 to filter only long names

Select all transformed fields together

### ✅ Final Query:

SELECT 
    patient_id,
    UPPER(name) AS name_upper,
    LOWER(service) AS service_lower,
    CASE
        WHEN age >= 65 THEN 'Senior'
        WHEN age >= 18 THEN 'Adult'
        ELSE 'Minor'
    END AS age_category,
    LENGTH(name) AS name_length
FROM patients
WHERE LENGTH(name) > 10;

### 📝 Key Notes

String functions are lightweight in SELECT but expensive in WHERE

Use CONCAT or || based on SQL engine

Always be mindful of case sensitivity when comparing text

Use TRIM to clean user-entered data before filtering or joining

SUBSTRING is useful for abbreviation, formatting, and label building

### ⭐ Takeaway

String functions help transform raw text into readable, formatted, and categorized information — essential for creating dashboards, reports, and clean datasets.
