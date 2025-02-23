# Vital-Patient-Data-Insights-with-SQL
-- Create Patients table
CREATE TABLE Patients (
    patient_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    gender VARCHAR(10)
);

-- Create Doctors table
CREATE TABLE Doctors (
    doctor_id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    specialty VARCHAR(50)
);

-- Create Appointments table
CREATE TABLE Appointments (
    appointment_id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    appointment_date DATETIME,
    status VARCHAR(20),
    FOREIGN KEY (patient_id) REFERENCES Patients(patient_id),
    FOREIGN KEY (doctor_id) REFERENCES Doctors(doctor_id)
);

-- Insert sample data into Patients
INSERT INTO Patients (first_name, last_name, gender) VALUES
('John', 'Doe', 'Male'),
('Jane', 'Smith', 'Female'),
('Mark', 'Johnson', 'Male'),
('Emily', 'Davis', 'Female'),
('Michael', 'Brown', 'Male'),
('Sarah', 'Wilson', 'Female'),
('David', 'Lee', 'Male'),
('Laura', 'Garcia', 'Female'),
('James', 'Martinez', 'Male'),
('Linda', 'Anderson', 'Female'),
('Robert', 'Thomas', 'Male'),
('Patricia', 'Jackson', 'Female'),
('Charles', 'Harris', 'Male'),
('Barbara', 'Clark', 'Female'),
('Joseph', 'Lewis', 'Male'),
('Susan', 'Walker', 'Female'),
('Daniel', 'Hall', 'Male'),
('Jessica', 'Allen', 'Female'),
('Paul', 'Young', 'Male'),
('Karen', 'King', 'Female'),
('Kevin', 'Wright', 'Male'),
('Nancy', 'Lopez', 'Female'),
('Brian', 'Hill', 'Male'),
('Lisa', 'Scott', 'Female'),
('George', 'Adams', 'Male'),
('Betty', 'Baker', 'Female'),
('Edward', 'Gonzalez', 'Male'),
('Helen', 'Nelson', 'Female'),
('Ronald', 'Carter', 'Male'),
('Sandra', 'Mitchell', 'Female'),
('Anthony', 'Perez', 'Male'),
('Ashley', 'Roberts', 'Female'),
('Steven', 'Phillips', 'Male'),
('Kimberly', 'Campbell', 'Female'),
('William', 'Evans', 'Male'),
('Dorothy', 'Edwards', 'Female'),
('Jason', 'Collins', 'Male'),
('Michelle', 'Stewart', 'Female'),
('Matthew', 'Sanchez', 'Male'),
('Melissa', 'Morris', 'Female'),
('Andrew', 'Rogers', 'Male'),
('Stephanie', 'Reed', 'Female'),
('Joshua', 'Cook', 'Male'),
('Amanda', 'Morgan', 'Female'),
('Nicholas', 'Bell', 'Male'),
('Angela', 'Murphy', 'Female');

-- Insert sample data into Doctors
INSERT INTO Doctors (first_name, last_name, specialty) VALUES
('Alice', 'Brown', 'Cardiology'),
('Bob', 'White', 'Pulmonology'),
('Charlie', 'Green', 'General Medicine'),
('Diana', 'Clark', 'Neurology'),
('Evan', 'Scott', 'Orthopedics');

-- Insert sample data into Appointments
INSERT INTO Appointments (patient_id, doctor_id, appointment_date, status) VALUES
(1, 1, '2024-09-25 10:00:00', 'Scheduled'),
(2, 2, '2024-09-26 14:00:00', 'Completed'),
(3, 3, '2024-09-27 09:00:00', 'Cancelled'),
(4, 4, '2024-09-28 11:00:00', 'Scheduled'),
(5, 5, '2024-09-29 15:00:00', 'Completed'),
(6, 1, '2024-09-30 08:30:00', 'Scheduled'),
(7, 3, '2024-10-01 13:00:00', 'Scheduled'),
(8, 2, '2024-10-02 16:00:00', 'Completed'),
(9, 4, '2024-10-03 10:00:00', 'Scheduled'),
(10, 5, '2024-10-04 12:00:00', 'Completed'),
(11, 1, '2024-10-05 09:30:00', 'Scheduled'),
(12, 3, '2024-10-06 14:00:00', 'Scheduled'),
(13, 2, '2024-10-07 11:00:00', 'Completed'),
(14, 4, '2024-10-08 15:00:00', 'Cancelled'),
(15, 5, '2024-10-09 08:00:00', 'Scheduled');

-- Example Queries using the concepts you've learned

-- 1. Get all scheduled appointments
SELECT * FROM Appointments WHERE status = 'Scheduled';

-- 2. Count patients by gender
SELECT gender, COUNT(*) AS patient_count FROM Patients GROUP BY gender;

-- 3. Get distinct specialties of doctors
SELECT DISTINCT specialty FROM Doctors;

-- 4. Join Patients and Appointments to see who has an appointment
SELECT P.first_name, P.last_name, A.appointment_date, A.status
FROM Patients P
LEFT JOIN Appointments A ON P.patient_id = A.patient_id;

-- 5. Order doctors by their specialty
SELECT * FROM Doctors ORDER BY specialty;

-- 6. Limit the results to only 10 patients
SELECT * FROM Patients LIMIT 10;

-- 7. Group appointments by status and show how many for each
SELECT status, COUNT(*) AS total FROM Appointments GROUP BY status HAVING COUNT(*) > 0;

