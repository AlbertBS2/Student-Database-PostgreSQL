# Building a Student Database
### Overview
This document provides an overview and instructions for working with the students database. The database is designed to store information about students, their majors, courses, and the relationships between majors and courses.
### Database Schema
The universe database consists of the following tables:
1. courses
2. majors
3. majors_courses
4. students
### Table Descriptions and Relationships
#### courses
Stores information about the courses available.
- Columns: course_id (integer, primary key), course (character varying(100), not null)
- Sequences: courses_course_id_seq: Sequence for generating unique course IDs.
- Primary Key: courses_pkey (course_id)
#### majors
Stores information about the majors offered.
- Columns: major_id (integer, primary key), major (character varying(50), not null)
- Sequences: majors_major_id_seq: Sequence for generating unique major IDs.
- Primary Key: majors_pkey (major_id)
#### majors_courses
Stores the relationships between majors and courses, indicating which courses are required for each major.
- Columns: major_id (integer, not null), course_id (integer, not null)
- Primary Key: majors_courses_pkey (major_id, course_id)
- Foreign Keys: majors_courses_major_id_fkey (major_id) references majors(major_id), majors_courses_course_id_fkey (course_id) references courses(course_id)
#### students
Stores information about the students enrolled.
- Columns: student_id (integer, primary key), first_name (character varying(50), not null), last_name (character varying(50), not null), major_id (integer), gpa (numeric(2,1))
- Sequences: students_student_id_seq: Sequence for generating unique student IDs.
- Primary Key: students_pkey (student_id)
- Foreign Key: students_major_id_fkey (major_id) references majors(major_id)
### Setup Instructions
1. Connect to your PostgreSQL server.
2. Create a new database named students.
3. Execute the SQL script provided (students.sql) using psql or any SQL client.
### Conclusion
This database schema and initial data setup provide a robust foundation for managing student records, courses, and majors. For any additional modifications or enhancements, ensure the referential integrity is maintained by appropriately updating primary and foreign keys. For any inquiries or improvements, feel free to contact me.
