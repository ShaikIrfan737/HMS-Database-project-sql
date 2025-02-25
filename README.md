# Hospital Management System (HMS)

Overview

The Hospital Management System (HMS) is a database-driven project designed to efficiently manage essential hospital data, including information about patients, doctors, and medical procedures. The system is built using MySQL to ensure organized, fast, and secure data management.

Purpose

The main objective of this project is to demonstrate how a MySQL database can efficiently store, retrieve, and manage hospital-related data, thereby improving hospital operations and ensuring seamless data handling.

Features

Organized Data: Structured database schema for effective data management.

Fast Data Retrieval: Optimized SQL queries for quick access to critical information.

Clear Relationships: The ER diagram provides a clear representation of data relationships.

Scalability: The database design allows for future enhancements and additional functionalities.

Strong Data Integrity: The use of primary and foreign keys ensures data accuracy and consistency.

Database Structure

Entities and Tables

The database consists of multiple tables to store relevant hospital data, including:

Patients: Stores patient information such as name, admission date, and discharge date.

Doctors (Physicians): Contains physician details and their department affiliations.

Nurses: Maintains nurse information, including their registration status.

Appointments: Tracks appointments between patients and doctors.

Medical Procedures: Stores details about medical treatments and costs.

Departments: Manages hospital departments and their respective heads.

Rooms & Blocks: Contains information about hospital rooms and their locations.

Key SQL Queries

Here are some SQL queries used in the project:

Find all registered nurses:

SELECT * FROM Nurse WHERE registered = 't';

Total appointments per physician:

SELECT Physician, COUNT(*) AS total_appointments FROM appointment GROUP BY Physician;

Patients who have been discharged:

SELECT name FROM HospitalPatient WHERE discharge_date IS NOT NULL;

List of department heads:

SELECT name FROM Physician WHERE employeeid IN (SELECT head FROM department);

Number of physicians in each department:

SELECT d.name AS Department, COUNT(p.employeeid) AS PhysicianCount
FROM department d
JOIN affiliated_with aw ON d.department_id = aw.department
JOIN Physician p ON aw.physician = p.employeeid
GROUP BY d.name;

Patients treated by a specific physician (e.g., John Dorian):

SELECT * FROM appointment a JOIN Physician p ON a.physician = p.employeeid WHERE p.name = 'John Dorian';

View for physician-department association:

CREATE VIEW PhysicianDepartment AS
SELECT p.name AS Physician, d.name AS Department
FROM Physician p
JOIN affiliated_with aw ON p.employeeid = aw.physician
JOIN department d ON aw.department = d.department_id;

Key Findings

This project demonstrates how MySQL can be leveraged to manage hospital data effectively. By structuring information about patients, doctors, and procedures in a relational database, hospital operations can be streamlined and optimized.

Conclusion

Through this project, we have learned how to design, implement, and query a relational database for hospital management. This knowledge is crucial for developing robust data-driven applications in the healthcare industry.

Author

Developed as part of a project on Hospital Management System using MySQL.
