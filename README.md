
# Team 8 Mist 4610 Group Project 1

### Team Name:

61608 Group 8

## Team Members:

[Will Solomon](https://github.com/Willtsolomon)

[Libby Lausier](https://github.com/libbylausier)

[Jack Smith](https://github.com/jacklsmith14)

[Grace Yao](https://github.com/graceyao2)

[Jack Clark](https://github.com/JackClark12)

[Zoey Cho](https://github.com/hc29584)

## Problem Description:

The problem at hand is to model a relational database for the day-to-today workings of an Emergency Healthcare Clinic. The central entity of this model is the Patients entity. The clinic also wants to keep track of things such as the staff members, prescriptions, invoices, medical equipment, ect.  Our group is interested in accurately modeling these entities and relationships, by generating sample data, and integrating each entity with the sample data. Finally, we would like to test our model and sample data by formulating applicable queries that provide relevant and valuable information regarding the Emergency Clinics Operations.

## Data Model:

Data Model Explanation: Our data model is designed to efficiently manage the operations of our emergency healthcare clinic, ensuring that we deliver timely and comprehensive medical care to patients with urgent health needs. Our clinic operates around the clock, offering a wide range of medical services from minor injuries to critical conditions, all with a focus on patient-centric care.

At the core of our database is the Patients entity. This entity represents individuals seeking medical assistance at our clinic. Each patient is assigned a unique Patient ID, serving as a primary key for identification purposes. The Patients entity captures essential information about each patient, including their Name, Date of Birth, Gender, City, State, Phone Number, Email, and Emergency Contact Information. These details enable us to effectively communicate with patients and their families, ensuring seamless coordination of care.

Our clinic organizes its operations into various departments, each responsible for specific aspects of patient care and administrative functions. These departments may include Emergency Medicine, Pediatrics, Internal Medicine, Radiology, and Administration, among others. Each department is represented as an entity within our data model, facilitating efficient management of resources and personnel allocation.

Within each department, there are many healthcare professionals, including physicians, nurses, technicians, and administrative staff. The one-to-many relationship between the Departments and Employees entities allows us to track staffing levels, roles, and responsibilities across the clinic. This ensures that the right personnel are available to provide care to patients at all times.

Our clinic offers a diverse range of medical services to meet the needs of our patients. These services may include diagnostic imaging, laboratory testing, minor surgical procedures, and specialized treatments for acute conditions. Each service is represented as an entity within our data model, with attributes such as Service ID, Service Name, Description, and Associated Costs.

In addition to medical services, our clinic may also offer supplementary facilities and resources, such as pharmacies, rehabilitation centers, and counseling services. These facilities are integrated into our data model as separate entities, allowing for comprehensive management of patient care and support services.

Furthermore, we recognized the importance of tracking patient interactions and medical histories to ensure continuity of care. Therefore, our data model includes entities such as Medical Records, Visit Logs, and Treatment Plans, which capture detailed information about patient encounters, diagnoses, treatments, and follow-up care.

Overall, our data model provides a comprehensive framework for managing the complex operations of our emergency healthcare clinic, enabling us to deliver efficient, high-quality care to patients in need, around the clock.

![1111111](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/5e62ccd1-2461-4f35-a5bd-40304ead66e3)

## Data Dictionary:

![Image 3-26-24 at 4 35 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/cb23d2ab-c0c7-4a41-ba51-a2d0f64493d1)
![Image 3-26-24 at 4 37 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/8155233f-5a8b-4bbc-be90-d0e62073cd8f)
![Image 3-26-24 at 4 39 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/47ff8745-6cd3-4cdf-8864-78e68381f8e9)
![Image 3-26-24 at 4 40 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/3c248003-ac54-4289-8226-0e8d193692a6)
![Image 3-26-24 at 4 40 PM (1)](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/b8ab9cfd-55f6-4a90-868b-72fb237c3718)
![Image 3-26-24 at 4 40 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/20a9d336-762f-47e0-a4e6-c187248427e4)
![Image 3-26-24 at 4 41 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/75ca1beb-67ec-41f5-ad08-5c2cfb046297)


## Queries:

<img width="660" alt="Screenshot 2024-03-27 at 7 11 35 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/cdf684a5-26de-464b-9b62-afb702a1de4b">

1. This query allows us to find the patients whose insurances expire in the next 2 months.

SELECT name, email, expirationDate
FROM Patients 
JOIN PatientInsurances USING (patientID)
WHERE expirationDate REGEXP '2024-05' OR expirationDate REGEXP '2024-04';

<img width="538" alt="Screenshot 2024-03-27 at 7 27 32 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/d105c4d0-5877-42b2-812e-f88dc4806159">

Q1 Description- Insurance Expiration Tracking: This query identifies patients whose insurance policies are set to expire in the next two months by checking for expiration dates in May or April 2024. This is crucial for clinics as it helps in proactive patient communication, ensuring that patients are aware of their insurance status and can take necessary actions to renew their policies or arrange alternative payment methods. It supports the clinic's financial stability by minimizing the risk of unpaid services due to expired insurance.

---------------------------------------------------------------------------------------
2. Find the percentage of all patients that are from Alabama.

SELECT CONCAT(ROUND(COUNT(state) /(SELECT COUNT(state) FROM Patients)*100, 2), "%") as statePreportion
FROM Patients
WHERE state = "Alabama";

<img width="642" alt="Screenshot 2024-03-27 at 7 28 31 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/77ee9165-9777-4e8f-9225-e0fb027097f1">

Q2 Description- Patient Demographics Analysis: By calculating the percentage of patients from Alabama, this query aids in understanding the demographic spread of the clinic's patient base. This insight is important for tailoring healthcare services, outreach, and educational programs specific to the predominant patient population. It can also guide resource allocation, such as staffing needs and the types of medical services offered, to better serve the community's health needs.

---------------------------------------------------------------------------------------
3. Find the names and ID of the patients that have NOT paid.
   
SELECT name, Patients.patientID, CONCAT("$", Payments.amount)
From Patients 
JOIN Visits USING (patientID) 
JOIN Invoices USING (visitID) 
JOIN Payments USING (invoiceID)
WHERE paymentStatus = "Unpaid"; 

<img width="536" alt="Screenshot 2024-03-27 at 7 28 46 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/6735d1e3-de9a-45e7-aa60-f17248398e1e">

Q3 Description- Unpaid Invoices Monitoring: This query lists patients who have outstanding payments by identifying unpaid invoices. It's vital for the clinic's revenue cycle management, helping the billing department to follow up on unpaid bills and maintain a healthy cash flow. Prompt identification and resolution of unpaid accounts can significantly impact the clinic's operational efficiency and financial health.

---------------------------------------------------------------------------------------

4. Find Equipment name, associated cost, and date treated of equipment used within the year of 2024 so far.

SELECT Equipments.name, CONCAT("$",cost) as cost, dateTreated
FROM Equipments
JOIN PatientTreatments USING (equipmentID)
WHERE dateTreated REGEXP "2024";

<img width="637" alt="Screenshot 2024-03-27 at 7 29 01 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/724f8b0a-4151-4a62-8ad9-c272bf6c75be">

Q4 Description-Equipment Utilization and Cost Management: By listing the equipment used within the year, along with associated costs and treatment dates, this query provides insights into equipment utilization and expenditure. It helps the clinic in budgeting and financial planning, ensuring that equipment costs are accounted for and optimized for patient care. It also aids in inventory management and the planning of future investments in medical equipment.

---------------------------------------------------------------------------------------

5. Find the total amount of money paid by each patient.
   
SELECT totalAmount, Patients.name
FROM Patients
JOIN Visits ON Patients.patientID = Visits.patientID
JOIN Invoices ON Visits.patientID = Invoices.patientID
WHERE totalAmount > 50
Group By Patients.name, totalAmount;

<img width="567" alt="Screenshot 2024-03-27 at 7 29 14 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/2c0e6c50-411a-419f-86f5-51af624b4fc5">

Q5 Description- Financial Analysis of Patient Payments: The query identifies the total amount of money paid by each patient, focusing on those who have spent over $50. This is relevant for analyzing patient spending patterns, assessing the financial health of the clinic, and identifying key revenue-generating services. It enables the clinic to make informed decisions about service pricing, discounts, and insurance negotiations to enhance profitability and patient satisfaction.

---------------------------------------------------------------------------------------

6. List the names of each patient, the staff member name and ID they were seen by, and the Date the Patient was seen.
   
SELECT MedicalStaffs.staffID, staffName, Patients.name, appointmentDate
FROM MedicalStaffs
JOIN Appointments on MedicalStaffs.staffID = Appointments.staffID
JOIN Patients on Appointments.patientID = Patients.patientID;

<img width="642" alt="Screenshot 2024-03-27 at 7 29 28 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/6d5eaeb9-e985-4085-abdc-ea76f66f5889">

Q6 Description- Staff and Patient Interaction Tracking: Listing the names of patients, the staff members who saw them, and the dates of these interactions, this query supports staff scheduling and patient care coordination. It provides a clear record of patient-staff interactions, aiding in personnel management, ensuring adequate staff-patient ratios, and enhancing patient care by maintaining continuity and personalization of services.

---------------------------------------------------------------------------------------

7.This query lists the names of the medical staff that specialize in Orthopedics as well as the number of patients they have had appointments with.

SELECT staffName, specialization, COUNT(Distinct Visits.visitID) AS numTreated
FROM MedicalStaffs
JOIN PatientTreatments ON MedicalStaffs.staffID = PatientTreatments.staffID
JOIN Visits ON PatientTreatments.visitID = Visits.visitID
WHERE specialization REGEXP "Orthopedics" 
GROUP BY MedicalStaffs.staffID; 

<img width="638" alt="Screenshot 2024-03-27 at 7 29 49 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/6983aa53-4650-4b61-970b-7050b557dc18">

Q7 Description- Specialization and Patient Load Analysis: By identifying medical staff specializing in Orthopedics and the number of patients they have treated, this query helps in resource allocation and highlights areas of high demand. It informs the clinic's staffing decisions, professional development opportunities, and the need for expanding services in high-demand specializations to meet patient needs effectively.

-------------------------------------------------------------------------------------------

8. List Medical Staff Who Completed Appointments and the Number of Unique Patients Seen who the status had resolved.

SELECT  MedicalStaffs.staffName, MedicalStaffs.specialization, COUNT(DISTINCT Patients.patientID) AS’ PatientsSeen’
FROM MedicalStaffs
JOIN Appointments ON MedicalStaffs.staffID = Appointments.staffID
JOIN Patients ON Appointments.patientID = Patients.patientID
WHERE Appointments.status = 'Resolved'
GROUP BY MedicalStaffs.staffID;

<img width="640" alt="Screenshot 2024-03-27 at 7 30 03 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/c902c553-3534-4322-b014-47ac75b9e5fb">

Q8 Description- Performance Metrics for Medical Staff: This query lists medical staff who have completed appointments with a status of 'Resolved', along with the number of unique patients seen. It serves as a performance indicator, rewarding efficiency and effectiveness in patient care. It aids in recognizing and promoting high-performing staff, motivating improvements in patient service quality, and identifying areas for operational enhancements.

---------------------------------------------------------------------------------------

9. This query finds the insurance providers that support the clinic that cover 5 or more patients at the clinic. 

SELECT InsuranceProviders.name as Provider,contactInfo, COUNT(patientID) AS NumberOfPatients
FROM InsuranceProviders 
JOIN PatientInsurances USING (providerID)
GROUP BY providerID
HAVING COUNT(patientID) >= 5;

<img width="633" alt="Screenshot 2024-03-27 at 7 30 20 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/e5490819-684b-4345-8f0b-101fe71edc4f">

Q9 Description- Insurance Provider Collaboration: Finding insurance providers that cover five or more patients at the clinic, this query identifies key insurance partnerships. It's essential for negotiating insurance contracts, understanding patient insurance preferences, and ensuring a broad coverage network. This collaboration between clinics and insurance providers is vital for patient access to affordable care and clinic revenue management.

---------------------------------------------------------------------------------------
10. This query finds the staffName, position, and specialization of staff members that used the ECG machine. 

SELECT staffName,position,specialization
FROM MedicalStaffs 
WHERE EXISTS (
    SELECT*
    FROM PatientTreatments 
    JOIN Equipments USING (equipmentID)
    WHERE MedicalStaffs.staffID = PatientTreatments.staffID AND Equipments.name REGEXP 'ECG'
    
<img width="623" alt="Screenshot 2024-03-27 at 7 30 38 PM" src="https://github.com/Willtsolomon/MIST-4610-Project-one/assets/165089413/18e5248a-8d81-4526-8a0d-1e608b7c1a5a">

Q10 Description- Staff Utilization of Medical Equipment: By identifying staff members who have used the ECG machine, this query highlights the integration of technology in patient care and the expertise of staff in utilizing specific equipment. It's relevant for assessing training needs, ensuring competent use of medical technology, and planning for equipment maintenance or upgrades to enhance patient care quality.

## Database Information

Database Name: ns_Sp24_61608_Group8

