# Architecture & Implementation Plan 

## Instructions : 
* Create a high-level architecture diagram showing how the components fit together.
* Describe how each cloud service will be used, and connect back to prior coursework.
* Plan must include:
  1. Service mapping
  2. Data flow narrative
  3. Security, Identity, and Governance Basics (1–2 paragraphs)
     * How would you manage credentials (e.g., environment variables)?
     * What kinds of access controls / RBAC would be needed?
     * From a high level, how do you avoid putting real PHI into public environments?
  4. Cost and Operational Consideration (1–2 paragraphs)
     * Which components might cost the most (compute vs. storage vs. AI).
     * Where you might use serverless / scheduled jobs instead of always-on VMs.
     * Any decisions you’d make to keep this in a “student budget” or free tier.

## Architecture Diagram 
![diagram](architecture_diagram.jpg)

## 1. Service Mapping 
| Layer | Cloud Service | Role in Solution | Related Coursework |
|:-------:|:-------:|:-------:|:-------:|
| Frontend | Flask App | Upload data & display results | Assignment 2 |
| Storage | GCP Cloud Storage | Store CSV uploads | Module 6 |
| Compute | Cloud Run | Runbackend API & ETL | Assignment 3 & Module 5 |
| Database | Cloud SQL | Store cleanned thyroid data | Assignment 4 & Module 7 |
| Analytics | BigQuery | Trend analysis on TSH/T4/T3 | Module 7 |

## 2. Data Flow Narrative 
Step 1: The user uploads the thyroid lab and symptom CSV files via Flask.

Step 2: Files are stored in GCP Cloud Storage. *Files are organized by data type and upload date.*

Step 3: After upload, the Flask application sends an API request to trigger an ETL process running in a Cloud Run container.

Step 4: Cloud Run ETL service reads the CSV files from Cloud Storage and performs data validation and cleaning. *Includes checking required fields, normalizing column names, validating data ranges, and handling missing or invalid values.*

Step 5: Cleaned records are inserted into the Cloud SQL database.

Step 6: Selected datasets are loaded into BigQuery, where analytics compute trends in thyroid hormone levels and flag abnormal patterns.

Step 7: Flask app displays tables and charts for monitoring.

## 3. Security, Identity, and Governance Basics
Cloud credential handling and secret management are used to handle security. GCP Secret Manager is used to securely store application credentials, such as database connection information and service access keys, which are then accessed at runtime by the Flask application and Cloud Run services through environment variables. Using unique permissions given to patients and providers, role-based access control (RBAC) guarantees that only authorized individuals can access sensitive data. Only synthetic (de-identified) data is used; no actual patient identifiers are kept, and all cloud resources are set up with minimal permissions that comply with the principle of least privilege in order to reduce governance and privacy problems.

## 4. Cost and Operational Considerations
By utilizing serverless processing via Cloud Run, automatic scaling eliminates the need for constantly operating virtual machines. This would help reduce operational costs, which is a plus in the long run. Since CSV files and log data are kept in cloud storage is relatively small, storage costs are still reasonable. BigQuery prevents unnecessary compute utilization by executing analytics workloads only when needed. Free tiers and student cloud credits are used whenever possible to maintain the system's overall cost-effectiveness while maintaining all necessary functionality.
