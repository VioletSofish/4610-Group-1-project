# 4610-Group-1-project
## Team Name
Sp26_61608_Group 1

## Team Members
1. Violet Sofish
2. Lauren Harville
3. Andrew Heighton
4. Asanti Kumera
5. Aidan Pfeiffer
6. Doc Rush
   
## Problem Decsription
We are a telehealth patient & provider portal focused on managing virtual clinic throughput and insurance reimbursement. We are responsible for making and facilitating appointments, patient-physician communications, and prescriptions. Physicians can have multiple specialties, appointments have a status, and encounter status and insurance claim payments are linked.

## Data Model
Our model is a fictional telehealth platform that maps out the relationships between patients, providers, insurance, payments, and medical records. At the center, patients are the driving force of our database. Patients have unique IDs, names, identification information and contanct information.

Each appointment between a patient and a provider is recorded as a medical encounter. These are stored with the meeting date and status, whether the appointment is currently scheduled, completed but unpaid for, or paid for. The providers can have many different titles, each having their own names and identification/contact information. Outside of appointments, any emails, on-platform messages, or calls between patient and provider are stored with a timestamp and transcript as communications.

Providers can write prescriptions, which are recorded as a many-to-many relationship with the prescribed patient. Each patient also has a one-to-one relationship displaying their medical history and current information, which is reviewed by the provider prior to meetings.

After each encounter, a single invoice is generated. This invoice can be payed off in multiple installments and by either the patient, insurance, or a combination of the two - depending on the policy. After the invoice is fully covered, the status of the MedicalEncounter is changed to 'paid'.

There are a few different InsuranceProvider companies, each offering a handful of unique plans. Each unique pairing of one of these InsurancePlans and a patient is recorded as CustomerInsurance, a many-to-many relationship.
<img width="867" height="620" alt="data model screenshot" src="https://github.com/user-attachments/assets/0b21972a-bdda-4865-9a55-af7d4dc9c162" />

## Data Dictionary
<img width="620" height="132" alt="communications" src="https://github.com/user-attachments/assets/bbe24754-74b5-4dbd-a49a-1f6a7b6390be" />
<img width="620" height="173" alt="Customerinsurance" src="https://github.com/user-attachments/assets/6f2a579f-7710-458f-8c1b-8e425521b197" />
<img width="620" height="112" alt="insuranceplan" src="https://github.com/user-attachments/assets/f2cef23d-185c-4c17-bdee-2f00e9cee7c4" />
<img width="620" height="112" alt="insuranceprovider" src="https://github.com/user-attachments/assets/8111f1a0-b350-4310-82b5-16e2b3162b1a" />
<img width="620" height="112" alt="invoice" src="https://github.com/user-attachments/assets/4eb8f9f2-7d38-48bc-b3d2-6a3bddaab494" />
<img width="620" height="135" alt="medicalencounters" src="https://github.com/user-attachments/assets/7ea30e66-ce23-4a0f-a5f2-5c4d2c0b9e2c" />
<img width="620" height="100" alt="medicalrecords" src="https://github.com/user-attachments/assets/3a9cc8e1-f0b7-42ec-bb44-b3bccac136b7" />
<img width="620" height="130" alt="patients" src="https://github.com/user-attachments/assets/937c5af7-618d-43df-a9e7-06b58d96b693" />
<img width="620" height="130" alt="payments" src="https://github.com/user-attachments/assets/0506223d-5079-4d7a-bae8-4bfd37add8bd" />
<img width="620" height="95" alt="prescriptions" src="https://github.com/user-attachments/assets/aed568b0-187d-49e5-8c0d-4b2a645da412" />
<img width="620" height="173" alt="provider" src="https://github.com/user-attachments/assets/48ed5875-185e-44ed-ae0f-989ddf25a96e" />

## Queries

## Database Information
Name of the database: ns_Sp26_61608_Group1
Additional Information: each marked query can be called using. _________
