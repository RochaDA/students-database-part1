# 🧠 Students Database Project (Part 1)

This project is part of the **FreeCodeCamp Relational Database Certification**.  
It uses **Bash** and **PostgreSQL** to automatically import and manage data from CSV files into a database.

---

## 🗂️ Project Overview

The goal of this project is to populate a PostgreSQL database with data from two CSV files:

- `courses.csv` — contains course and major information  
- `students.csv` — contains student details such as name, major, and GPA  

The Bash script (`insert_data.sh`) reads data from both CSV files and:
- Inserts new **majors** and **courses** if they don’t already exist  
- Links majors and courses together in a join table  
- Inserts **students** with their associated major and GPA  

This project demonstrates:
- Automating SQL queries with Bash  
- Using conditionals and loops in shell scripts  
- Managing table relationships with SQL foreign keys  

---

## ⚙️ How It Works

### 1. Processing Courses and Majors

The first loop in the script reads data from `courses_test.csv`:

1. Checks if a **major** already exists in the `majors` table  
   - If not found, inserts it  
2. Checks if a **course** already exists in the `courses` table  
   - If not found, inserts it  
3. Links the **major** and **course** in the `majors_courses` table  

### 2. Processing Students

The second loop reads data from `students_test.csv`:

1. Retrieves the `major_id` for each student’s major  
2. If not found, sets the value to `NULL`  
3. Inserts the student into the `students` table with:
   - `first_name`
   - `last_name`
   - `major_id`
   - `gpa`

---

## 🧾 Database Schema

| Table | Description |
|--------|--------------|
| **majors** | Stores all available majors (`major_id`, `major`) |
| **courses** | Stores all available courses (`course_id`, `course`) |
| **majors_courses** | Join table linking majors and courses (`major_id`, `course_id`) |
| **students** | Contains student records (`student_id`, `first_name`, `last_name`, `major_id`, `gpa`) |

### 🔗 Relationships

majors (1) <─── majors_courses ───> (1) courses

└──< students


---

## 🖥️ How to Run the Script

Make sure you have PostgreSQL running and the `students` database created.

Then execute the script in your terminal:

```bash
./insert_data.sh

```

This will:

Truncate existing tables (clear old data)

Import new data from the CSV files

Display messages for each successful insertion

## 🧰 Requirements

- Bash shell
- PostgreSQL

The following files in the same directory:
- insert_data.sh
- courses_test.csv
- students_test.csv

## 🏁 Learning Objectives

This project helped me to practice:

- Automating PostgreSQL operations using Bash scripts

- Handling conditional logic and loops in shell programming

- Managing relationships between multiple database tables

- Writing reusable, idempotent data import scripts
