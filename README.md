# EMR-Database
This EMR database is designed to cater elderly patients. The subscriber is the care giver of the elderly patient who buys the subscription to a team of doctors who can visit the elderly patient to gather vitals and any other required data to start a treatment plan. Designed to keep a track of  internal operations and data collection of the patient.


Human Health Database Schema

📑 About the project

This repository provides a MySQL DDL script that builds the Human_health relational database—an opinionated data model for managing comprehensive clinical, administrative, and lifestyle information about patients.

The schema is designed for clinics, research teams, or health–tech start‑ups that need an extensible and referentially‑intact data store covering everything from demographics and vitals to surgical history and daily‑living metrics.

🗂️ Schema at a glance

| Table                                   | Category        | Brief description                                                   |
|-----------------------------------------|-----------------|---------------------------------------------------------------------|
| Patients                                | Core            | Master patient demographics and contact details                     |
| Teams                                   | Core            | Multidisciplinary care teams assigned to patients                   |
| FMD                                     | Core            | Family Medicine Doctors linked to teams                             |
| HCC                                     | Core            | Health-care Coordinators linked to teams                            |
| Visits                                  | Core            | Encounter scheduling and logistics                                  |
| Subscriber                              | Administration  | Non-patient contact who receives updates and provides consent       |
| Subscription                            | Administration  | Links subscribers to patients and captures enrollment metadata      |
| Vitals                                  | Clinical        | Temperature, BP, BMI, glucose, and other vital signs                |
| Focused_Examination                     | Clinical        | Targeted physical findings for specific systems                     |
| Physical_exam                           | Clinical        | Comprehensive physical assessment outcomes                          |
| Medications                             | Clinical        | Prescribed medicines, dosages, and timing                           |
| Labs                                    | Clinical        | Laboratory orders or observation metadata                           |
| ROS                                     | Clinical        | Review-of-systems responses                                         |
| Allergy                                 | Clinical        | Allergy catalogue (type, name)                                      |
| Allergy_has_Patients                    | Clinical        | Junction linking allergies to patients                              |
| Family_history                          | History         | Familial conditions and hereditary risks                            |
| Past_medical_history                    | History         | Catalogue of historical diseases                                    |
| Patients_has_Past_medical_history       | History         | Junction linking patients to past medical conditions                |
| Past_surgical_history                   | History         | Archive of surgical procedures                                      |
| Past_surgical_history_has_Patients      | History         | Junction linking patients to past surgeries                         |
| ADLS                                    | Lifestyle       | Basic activities-of-daily-living assessment                         |
| IADLS                                   | Lifestyle       | Instrumental ADL evaluation (phone use, shopping, housekeeping)     |
| Geriatric                               | Lifestyle       | Common geriatric screening items                                    |
| Addiction                               | Lifestyle       | Substance-use profile                                               |
| Dental_record                           | Lifestyle       | Dental health tracking                                              |
| ODPARA                                  | Lifestyle       | Pain onset, duration, progression, associated factors               |


Tip: All foreign‑key relationships use ON UPDATE NO ACTION / ON DELETE NO ACTION to enforce integrity without cascading deletes.

🛠️ Prerequisites

MySQL 8.0+ (or compatible MariaDB version)

MySQL Workbench or command‑line access

🚀 Installation

# 1. Clone the repo
$ git clone https://github.com/<your‑org>/human_health_db.git
$ cd human_health_db

# 2. Log in to MySQL and run the script
mysql ‑u <user> ‑p < human_health_schema.sql

# or import via MySQL Workbench > File » Run SQL Script…

The script will:

Create the Human_health schema.

Build all tables and indexes.

Establish primary‑ & foreign‑key constraints.

Note: The circular relationship between Teams, FMD, and HCC is resolved automatically by MySQL’s deferred FK parsing during the same session.

🏃‍♀️ Quick start usage

-- List all active patients
SELECT MRN, First_Name, Last_Name, DOB
FROM Human_health.Patients;

-- Fetch latest vitals for a patient
SELECT *
FROM Human_health.Vitals
WHERE Patients_MRN = 1234
ORDER BY Vital_date DESC
LIMIT 1;

Feel free to extend the schema with views, stored procedures, or ORMs as suits your stack.

🤝 Contributing

Pull requests are welcome! For major changes, please open an issue first to discuss what you would like to change.


👤 Authors & Acknowledgments

Tabina Navaid – primary architect

⭐ If you find this useful

Give the repository a star—it helps others discover the project!
