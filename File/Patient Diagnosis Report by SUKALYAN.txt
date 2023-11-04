 -- creating a new database
CREATE DATABASE patient;
-- using database
USE patient;

-- creating table(•	Write a query to create a patients table with the fields such as date, 
-- patient id, patient name, age, weight, gender, location, phone number, disease, doctor name, 
-- and doctor id.)
CREATE TABLE patienttab(
date_ DATE, 
patient_id TEXT , 
patient_name TEXT, 
age INT, 
weight INT, 
gender TEXT, 
location TEXT, 
phone_number INT, 
disease TEXT, 
doctor_name TEXT, 
doctor_id INT);

-- Write a query to insert values into the patient’s table
INSERT INTO patienttab
VALUES('2019-06-15','AP2021','Sarath',67,76,'Male','chennai',5462829,'Cardiac','Mohan',21),
('2019-02-13','AP2022','John',62,80,'Male','banglore',1234731,'Cancer','Suraj',22),
('2018-01-08','AP2023','Henry',43,65,'Male','Kerala',9028320,'Liver','Mehta',23),
('2020-02-04','AP2024','Carl',56,72,'Female','Mumbai',9293829,'Asthma','Karthik',24),
('2017-09-15','AP2025','Shikar',55,71,'Male','Delhi',7821281,'Cardiac','Mohan',21),
('2018-07-22','AP2026','Piysuh',47,59,'Male','Haryana',8912819,'Cancer','Suraj',22),
('2017-03-25','AP2027','Stephen',69,55,'Male','Gujarat',8888211,'Liver','Mehta',23),
('2019-04-22','AP2028','Aaron',75,53,'Male','Banglore',9012192,'Asthma','Karthik',24);

-- Write a query to display the total number of patients in the table
SELECT COUNT(patient_id)
FROM patienttab;
-- total number of patient is 8

-- Write a query to display the patient id, 
-- patient name, gender, and disease of the patient whose age is maximum
SELECT patient_id,patient_name,gender,disease 
FROM patienttab
WHERE age = (SELECT MAX(age) FROM patienttab);

-- Write a query to display patient id and patient name with the current date
SELECT patient_id,patient_name, CURDATE() AS currentdate
FROM patienttab;

-- Write a query to display the old patient’s name and new patient's name in uppercase

SELECT UPPER(patient_name)
FROM patienttab;

-- Write a query to display the patient’s name along with the length of their name

SELECT patient_name,length(patient_name)
FROM patienttab;

-- Write a query to display the patient’s name, 
-- and the gender of the patient must be mentioned as M or F

SELECT patient_name, (CASE WHEN gender='MALE' THEN 'M' ELSE 'F' END)gender
FROM patienttab;

-- Write a query to combine the names of the patient and the doctor in a new column
SELECT patient_name,doctor_name, CONCAT(patient_name,' & ',doctor_name) AS Combined_Names
FROM Patienttab;

-- Write a query to display the patients’ age along with the logarithmic value (base 10) of their age.
SELECT age, LOG10(age) AS logarithmic_age
FROM patienttab;

-- Write a query to extract the year from the given date in a separate column.
SELECT date_, EXTRACT(year FROM date_)AS year_col
FROM patienttab;

-- Write a query to return NULL if the patient’s name 
-- and doctor’s name are similar else return the patient’s name.
SELECT CASE WHEN patient_name = doctor_name THEN NULL ELSE patient_name END AS result
FROM patienttab;

-- Write a query to return Yes if the patient’s age is greater than 40 else return No
SELECT patient_name, CASE WHEN age > 40 THEN 'yes' ELSE 'no' END AS result
FROM patienttab;
-- Write a query to display the doctor’s duplicate name from the table.
SELECT doctor_name, COUNT(doctor_name) AS count
FROM patienttab
GROUP BY doctor_name HAVING COUNT(doctor_name)>1;
