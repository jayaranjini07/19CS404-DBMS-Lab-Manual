## 📚 Purpose:
 The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.
 
 ---
 
 ## 🧪 Choose One Scenario:
 
 ### 🔹 Scenario 1: University Database
 Design a database to manage students, instructors, programs, courses, and student enrollments. Include prerequisites for courses.
 
 **User Requirements:**
 - Academic programs grouped under departments.
 - Students have admission number, name, DOB, contact info.
 - Instructors with staff number, contact info, etc.
 - Courses have number, name, credits.
 - Track course enrollments by students and enrollment date.
 - Add support for prerequisites (some courses require others).
 
 ---
 
 ### 🔹 Scenario 2: Hospital Database
 Design a database for patient management, appointments, medical records, and billing.
 
 **User Requirements:**
 - Patient details including contact and insurance.
 - Doctors and their departments, contact info, specialization.
 - Appointments with reason, time, patient-doctor link.
 - Medical records with treatments, diagnosis, test results.
 - Billing and payment details for each appointment.
 
 ---
 
 ## 📝 Tasks:
 1. Identify entities, relationships, and attributes.
 2. Draw the ER diagram using any tool (draw.io, dbdiagram.io, hand-drawn and scanned).
 3. Include:
    - Cardinality & participation constraints
    - Prerequisites for University OR Billing for Hospital
 4. Explain:
    - Why you chose the entities and relationships.
    - How you modeled prerequisites or billing.
 
 # ER Diagram Submission - Student Name
 
 ## Scenario Chosen:
 University / Hospital (choose one)
 Hospital 
 
 ## ER Diagram:
 ![ER Diagram](er_diagram.png)
 ![image](https://github.com/user-attachments/assets/e37329bf-0b46-4fc6-917f-01839cb80a21)
 
 ## Entities and Attributes:
 - Entity1: Attributes
 - Entity2: Attributes
 - PATIENT: PatientID, Name, Gender, DOB, Adress, Phone, Insurance details,
 - DOCTOR: DoctorID, Name, Phone, Specialization, Email, Work schedule
 - DEPARTMENT: DeptID, Dept name, Dept head
 - APPOINTMENT: AppointementID, PatientID, DoctorID, Reason to visit, Appointment date & time
 - MEDICAL RECORD: Medical record ID, PatientID, DoctorID, Test result, Treatments, Medications, Diagnoses
 - BILLING: BillID, PatientID, AppointmentID
 ...
 
 ## Relationships and Constraints:
| Relationship                         | Cardinality     | Participation         |
|--------------------------------------|------------------|------------------------|
| Patient – Appointment                | One-to-Many      | Partial – Total        |
| Doctor – Appointment                 | One-to-Many      | Partial – Total        |
| Patient – Medical Record             | One-to-Many      | Partial – Total        |
| Doctor – Medical Record              | One-to-Many      | Partial – Partial      |
| Appointment – Billing                | One-to-One       | Total – Total          |
| Billing – Payment                    | One-to-Many      | Partial – Total        |
| Doctor – Department                  | Many-to-One      | Total – Partial        |
| Department – Doctor (Dept Head)      | One-to-One       | Partial – Partial      |

 ...
 
 ## Extension (Prerequisite / Billing):
 The **Billing** entity is linked to both **Appointment** and **Patient**. Each appointment generates exactly one bill. The **Payment** entity supports **multiple payments per bill** (e.g., partial payments). This is modeled using a one-to-many relationship between **Billing** and **Payment**. Each payment records method, date, and amount—ensuring accurate tracking of all financial transactions.
 
 ## Design Choices:
 - Chose **Patient**, **Doctor**, and **Appointment** as core entities reflecting fundamental hospital operations.  
- Added **Medical Record** as a distinct entity to separate treatment history from visit details.  
- Modeled **Billing** and **Payment** as independent entities to support flexible financial tracking.  
- Included **Department** as a structural unit and modeled department head relationships.  
- Used realistic cardinalities and participation to accurately reflect system requirements.
 
 ## RESULT
Successfully analyzed a real-world hospital scenario, identified key entities and relationships, and represented them using an ER diagram with clear cardinality and participation constraints. Modeled billing and payment in a detailed and scalable way, demonstrating strong understanding of ER modeling principles.
