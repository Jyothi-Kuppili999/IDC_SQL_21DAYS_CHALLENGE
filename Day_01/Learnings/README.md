
### 🗓️ Day 1 – Intro to SQL & the SELECT Command
📘 What I Learned Today

Basics of SQL and how relational databases store data

Using the SELECT command to pull data from tables

Viewing all rows & columns using SELECT *

Fetching only needed fields instead of everything

Using AS to rename columns for better readability

Good habits: limit results while exploring & comment code

### 💻 Sample Queries I Practiced
-- Show all columns from patients table
SELECT * FROM patients;

-- Retrieve only required fields
SELECT patient_id, name, age 
FROM patients;

-- Take a quick look at the services table
SELECT * 
FROM services_weekly 
LIMIT 10;

#### 🎯 Task of the Day

Question: List all unique hospital services available in the hospital.

#### 💡 How I Approached It

I first figured out which table stores service details → services_weekly

Looked for the column that contains service names → service

Since repeating service names exist, I need unique values only

SQL provides DISTINCT to filter out duplicates

So I selected only that column with DISTINCT

## ✅ Final Query:

SELECT DISTINCT service 
FROM services_weekly;

#### 📝 Key Takeaway

Use DISTINCT when you want unique values, especially while exploring categorical fields like departments, services, user roles, etc.
