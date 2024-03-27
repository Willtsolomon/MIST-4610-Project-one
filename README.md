
# Team 8 Mist 4610 Group Project 1

### Team Name:

Group 8

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

![Image%203-26-24%20at%204 32%E2%80%AFPM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/f7d780a0-b0e5-48e5-9ad2-4d4458c672a1)

## Data Dictionary:

![Image 3-26-24 at 4 35 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/cb23d2ab-c0c7-4a41-ba51-a2d0f64493d1)
![Image 3-26-24 at 4 37 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/8155233f-5a8b-4bbc-be90-d0e62073cd8f)
![Image 3-26-24 at 4 39 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/47ff8745-6cd3-4cdf-8864-78e68381f8e9)
![Image 3-26-24 at 4 40 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/3c248003-ac54-4289-8226-0e8d193692a6)
![Image 3-26-24 at 4 40 PM (1)](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/b8ab9cfd-55f6-4a90-868b-72fb237c3718)
![Image 3-26-24 at 4 40 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/20a9d336-762f-47e0-a4e6-c187248427e4)
![Image 3-26-24 at 4 41 PM](https://github.com/Willtsolomon/MIST-4610-Project-one/assets/150104481/75ca1beb-67ec-41f5-ad08-5c2cfb046297)


## Queries:


## Database Information

Database Name: ns_Sp24_61608_Group8

