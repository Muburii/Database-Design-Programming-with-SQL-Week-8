ClinicDB Database Documentation
Overview
ClinicDB is a comprehensive database system designed for managing a medical clinic's operations, including patient records, doctor schedules, appointments, prescriptions, and billing.

Database Schema
Tables Structure
1. Patients
Stores patient demographic and medical information
2. Doctors
Contains doctor information and credentials
3. Departments
Organizes doctors into medical departments
4. Appointments
Manages patient-doctor scheduling
5. MedicalRecords
Stores patient medical history
6. Prescriptions
Tracks prescribed medications
7. Medications
Catalog of available medications
8. Prescription_Medications
Junction table for prescriptions and medications
9. Bills
Manages financial transactions

Views
DoctorSchedules
Provides an overview of doctor appointments
CREATE VIEW DoctorSchedules AS
SELECT 
    d.doctor_id,
    d.full_name AS doctor_name,
    a.appointment_date,
    a.end_time,
    p.full_name AS patient_name,
    a.status
FROM Doctors d
JOIN Appointments a ON d.doctor_id = a.doctor_id
JOIN Patients p ON a.patient_id = p.patient_id
ORDER BY d.doctor_id, a.appointment_date;

Triggers
chk_future_appointment
Ensures appointments are scheduled for future dates

ERD Diagram for the system.

Installation
Create the database:

CREATE DATABASE ClinicDB;
USE ClinicDB;
Execute all the CREATE TABLE statements in order

Add the trigger and view definitions.
