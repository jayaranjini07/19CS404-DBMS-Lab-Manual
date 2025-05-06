# 🧪 Experiment 1: Entity-Relationship (ER) Diagram

## 🎯 Objective
To understand and apply the concepts of ER modeling by creating an ER diagram for a real-world application.

## 📚 Purpose
The purpose of this workshop is to gain hands-on experience in designing ER diagrams that visually represent the structure of a database including entities, relationships, attributes, and constraints.

---

## 🧪 Scenario Chosen: **Hospital Database**

---

## 🖼️ ER Diagram
*(Diagram created using draw.io and attached as part of this repository)*

---

## ✅ Entities and Attributes

### 1. **PATIENT**
- `PatientID` (Primary Key)  
- Name  
- Gender  
- DOB  
- Address  
- Phone  
- Insurance details  

### 2. **DOCTOR**
- `DoctorID` (Primary Key)  
- Name  
- Phone  
- Specialization  
- Email  
- Work schedule  

### 3. **DEPARTMENT**
- `DeptID` (Primary Key)  
- Dept name  
- Dept head *(References DoctorID)*  

### 4. **APPOINTMENT**
- `AppointmentID` (Primary Key)  
- PatientID *(Foreign Key)*  
- DoctorID *(Foreign Key)*  
- Reason to visit  
- Appointment date & time  
- Additional notes  

### 5. **MEDICAL RECORD**
- `MedicalRecordID` (Primary Key)  
- PatientID *(Foreign Key)*  
- DoctorID *(Foreign Key)*  
- Diagnoses  
- Treatments  
- Medications  
- Test results  

### 6. **BILLING**
- `BillID` (Primary Key)  
- PatientID *(Foreign Key)*  
- AppointmentID *(Foreign Key)*  
- Total amount  
- Payment status  
- Date of payment  

### 7. **PAYMENT**
- `PaymentID` (Primary Key)  
- BillID *(Foreign Key)*  
- Transaction date  
- Payment method  
- Amount paid  
- Exempt ID (optional)  

---

## 🔁 Relationships and Constraints

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

---

## 💡 Extension: Billing

The **Billing** entity is linked to both **Appointment** and **Patient**. Each appointment generates exactly one bill. The **Payment** entity supports **multiple payments per bill** (e.g., partial payments). This is modeled using a one-to-many relationship between **Billing** and **Payment**. Each payment records method, date, and amount—ensuring accurate tracking of all financial transactions.

---

## 🧠 Design Choices

- Chose **Patient**, **Doctor**, and **Appointment** as core entities reflecting fundamental hospital operations.  
- Added **Medical Record** as a distinct entity to separate treatment history from visit details.  
- Modeled **Billing** and **Payment** as independent entities to support flexible financial tracking.  
- Included **Department** as a structural unit and modeled department head relationships.  
- Used realistic cardinalities and participation to accurately reflect system requirements.

---

## ✅ Result

Successfully analyzed a real-world hospital scenario, identified key entities and relationships, and represented them using an ER diagram with clear cardinality and participation constraints. Modeled billing and payment in a detailed and scalable way, demonstrating strong understanding of ER modeling principles.
