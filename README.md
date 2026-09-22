FlywayPractice
A Spring Boot project demonstrating database version control using Flyway migrations with MySQL.

📚 What is Flyway?
Flyway is a database migration and version-control tool. It helps manage database schema changes in a proper, trackable sequence instead of applying changes manually.

Example flow:

V1 → Create table
V2 → Add column
V3 → Add another column
V4 → Insert data
🎯 Why Flyway?
Database version control
Managing database changes safely
Maintaining migration history
Applying changes automatically on startup
Keeping dev / test / production databases consistent
🛠️ Tech Stack
Spring Boot
Java 17
Maven
MySQL
Flyway
Spring JDBC

Note: This project does not use JPA/Hibernate.

🗄️ Database Setup
Create the database before running the app:
sql
CREATE DATABASE flyway_demo;
📁 Migration Folder Structure
Flyway automatically looks for migration files in:
src/main/resources/db/migration
Project layout:
src
└── main
    └── resources
        └── db
            └── migration
                ├── V1__create_student_table.sql
                ├── V2__add_phone_to_student.sql
                ├── V3__add_city_to_student.sql
                └── V4__insert_student_data.sql
🔢 Migrations
V1 — Create student table
sql
CREATE TABLE student (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100)
);
V2 — Add phone column
sql
ALTER TABLE student
ADD COLUMN phone VARCHAR(15);
V3 — Add city column
sql
ALTER TABLE student
ADD COLUMN city VARCHAR(50);
V4 — Insert initial data
sql
INSERT INTO student (name, email, phone, city)
VALUES
('Rutuja', 'rutuja@gmail.com', '9876543210', 'Pune'),
('Priya', 'priya@gmail.com', '9876543211', 'Mumbai'),
('Sneha', 'sneha@gmail.com', '9876543212', 'Nashik');

Final student table columns:
student
├── id
├── name
├── email
├── phone
└── city

flyway_schema_history
Flyway automatically creates a flyway_schema_history table that records which migrations have already been executed.
Version	Description
1	create student table
2	add phone to student
3	add city to student
4	insert student data

Learn a Golden Rule
Never modify an already executed migration.
If V3__add_city_to_student.sql has already run, don't edit it — create a new file instead, e.g. V4__some_new_change.sql. Every new database change gets a new migration version.

GitHub
Repository: RutujaBorse26/learning-flyway.md
Pushed to the backend branch using the standard Git flow:
git init
git add .
git commit
git remote add origin
git branch -M backend
git push origin backend
