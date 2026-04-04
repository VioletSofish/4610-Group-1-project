# 4610-Group-1-project
## Team Name
Sp26_61608_Group 1

## Team Members
1. Violet Sofish: https://github.com/VioletSofish/4610-Group-1-project/tree/main#4610-group-1-project 
2. Lauren Harville: https://github.com/4610LaurenGit/Sp26_61608_Group-1.git 
3. Andrew Heighton: 
4. Asanti Kumera: https://github.com/asanti00/MIST4610GroupProject1.git
5. Aidan Pfeiffer: https://github.com/abp80036/MIST4610Group1.git
6. Doc Rush: 
   
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

<img width="653" height="415" alt="Screenshot 2026-04-03 at 9 43 42 PM" src="https://github.com/user-attachments/assets/16944f85-d3a1-43dc-9ed8-503a471103dc" />


1. Retrieve a list of all patients whose email ends in “.com”. Include their first name, last name, phone number, and email.
<img width="1470" height="956" alt="query 1 (updated)" src="https://github.com/user-attachments/assets/c1542fbb-475f-44e0-8e4a-da17a9bd0eb8" />
Query 1 shows patients whose email addresses end in ".com". It uses a regular expression (REGEXP) to filter emails that match this pattern. The results return the patient’s information for anyone whose email ends with ".com".

2. Find all medical encounters that are currently marked as “Scheduled.” Include the encounter ID, patient ID, provider ID, and appointment date.
<img width="1470" height="956" alt="query 2" src="https://github.com/user-attachments/assets/ccce2e53-9313-4414-87b3-87fd660493ba" />
Query 2 finds all medical encounters that currently have a status of "Scheduled." The subquery first identifies the encounter IDs that meet this condition, and then the main query pulls the encounter ID, patient ID, provider ID, and appointment date for those records.

3. List the patient name and invoice amount for payments that are greater than $3000 that are associated with completed appointments that have been paid for. Additionally, order the results by invoice amount in ascending order. The finance team can use this to identify higher balances and prioritize follow-up actions.
<img width="1470" height="956" alt="query 3 (updated)" src="https://github.com/user-attachments/assets/3545517d-d129-49e4-841f-9c1fc5487899" />
Query 3 finds patients who have invoice amounts greater than $3000 from appointments that have been marked as paid. It joins the Patients, MedicalEncounters, and Invoice tables to connect patient information with their billing records. The WHERE clause filters the results based on the invoice amount and appointment status, and the ORDER BY sorts the results from lowest to highest invoice amount.

4. Lists all patients who haven't sent at least one message
<img width="1470" height="956" alt="query 4" src="https://github.com/user-attachments/assets/6ea7bb89-abe8-45b0-9dc1-1b887739c33a" />
Query 4 finds patients who have not sent any messages. It checks the Communications table to see if there are any records linked to each patient, and if none exist, that patient is included in the results. The NOT EXISTS condition makes sure only patients with no messages are returned.

5. For each patient, calculate the total amount billed (from invoices) and the total amount paid (from payments). Display the patient’s name along with both totals, even if a patient has no payments recorded.
<img width="1470" height="956" alt="query 5" src="https://github.com/user-attachments/assets/bb18f18f-ad10-42f4-913b-55e93b08bbd1" />
This query calculates how much each patient has been billed and how much they have paid so far. It uses subqueries to add up the total invoice amounts and the total payments for each patient. The query still shows all patients even if they do not have any payments recorded, which means some totals may show as NULL. This helps compare what each patient owes versus what they have already paid.

6. Identify the provider who has handled the highest number of medical encounters. Display the provider’s name and the total number of encounters they have managed.
<img width="1470" height="956" alt="query 6" src="https://github.com/user-attachments/assets/176eb1b1-2ebd-46c4-93d0-4c480b08fab5" />
Query 6 finds the provider who has handled the most medical encounters. The subquery counts how many encounters each provider has and orders them from highest to lowest, then selects the provider with the highest total. The main query then returns the name of that provider.

7. List patients whose total payments exceed the average payment amount across all patients. This identifies patients with high payments that contribute to the overall revenue made, which can impact future business strategies. 
<img width="1470" height="956" alt="query 7 (updated)" src="https://github.com/user-attachments/assets/9f12b9cb-fd9f-422c-89db-73947776c507" />
Query 7 finds patients whose total payments are higher than the average total payment across all patients. It first groups payments by patient to calculate how much each person has paid, then compares those totals to the overall average using a subquery. The HAVING clause filters the results to only show patients whose total payments are above that average.

8. List all patients who have invoices with no payments at all. The finance team can use this to identify unpaid balances and focus on follow-up actions. 
<img width="1470" height="956" alt="query 8" src="https://github.com/user-attachments/assets/56be12e0-a96f-4a1c-9d23-9a5204f2a5f2" />
Query 8 finds patients who have invoices that do not have any payments recorded. It joins the Patients, MedicalEncounters, and Invoice tables to connect patients to their invoices, and then uses a NOT EXISTS subquery to check if any payments exist for those invoices. If no payment is found, the invoice is included in the results.

9. This lists every patient along with any prescription information, even if the patient has never received a prescription. Include the patient’s ID, first name, last name, prescription ID, and medication name. Make sure patients with no prescriptions still appear in the results.
<img width="1470" height="956" alt="query 9" src="https://github.com/user-attachments/assets/8d15488d-ee67-4799-8761-a567e4ef492f" />
Query 9 lists all patients and any prescriptions they may have. A LEFT JOIN is used so that patients without prescriptions are still included in the results. If a patient does not have a prescription, the prescription fields will show as NULL. The results are ordered by patient name and prescription ID to keep the output organized.

10. Calculates the total payments made by each patient and identifies those in the top 50% of total spending
<img width="1470" height="956" alt="query 10" src="https://github.com/user-attachments/assets/aa98aaed-a28e-4716-a9a8-2a669d5732ab" />
Query 10 highlights the highest-paying patients, enabling managers to focus resources on making sure these people are getting the health they need. This helps increase loyalty to the programs and also strengthens relationships with important patients.


## Database Information
Name of the database: ns_Sp26_61608_Group1
Additional Information: each marked query can be called using CALL GP_Q1();
