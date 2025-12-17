# Use Case Description 
## Instructions : 
Define a healthcare scenario 
A description consisting of:
1. Problem Statement: What problem are you solving? Who are the users?
2. Data Sources: What data would you store, and where does it come from?
3. Basic Workflow: A step-by-step description of how data flows through the system

## Problem Statement : 
Hyperthyroidism is an endocrine disorder characterized by excessive thyroid hormone production, leading to symptoms such as tachycardia, 
weight loss, anxiety, heat intolerance, and tremors. Effective management requires frequent laboratory monitoring (TSH, free T4, T3) and 
ongoing symptom tracking to prevent complications such as atrial fibrillation, osteoporosis, and thyroid storm (Wiersinga et al., 2023).

The main problem faced by healthcare providers is that thyroid-related data often varies across multiple systems, including EHR, 
lab reports, patient-reported symptoms, and medication records. This inconsistency leads to manual data review, limited longitudinal 
visibility, and delayed recognition of worsening thyroid function or treatment failure. As a result, clinicians may miss important trends, 
increasing the risk of both complications and delayed clinical interventions.

#### Stakeholders / Users :
* Endocrinologists
* Primary care providers
* Patients with diagnosed hyperthyroidism

## Goal / Solution :
A cloud-based system that collects thyroid-related data, standardizes and stores it in a centralized database, and provides dashboards for 
trend analysis. This system allows providers and patients to visualize hormone levels, symptoms, and the treatment processes over time.

## Data Source :
| **Data Type** | **Source** | **Key Field Names** |
|:----------:|:----------:|:----------:|
| Thyroid Labs (TSH, Free T4, T3) | EHR Exports | thyroid_labs |
| Patient reported symptoms (Palpitations, fatigue, anxiety) | Survey Forms | symptoms |
| Vitals (Height, weight) | Manual Entry | vitals |
| Medication Data | Provider Input | medication |
| Timestamps| System Generated | timestamps |

## Basic Workflow :
1. Data Upload
   * User (provider or patient) accesses the Flask web application.
   * User uploads thyroid-related CSV files, including lab results (TSH, Free T4, T3), symptom survey data, vitals, and medication information.
2. File Storage
   * The system verifies uploaded files for format and required fields.
   * CSV files are stored in cloud storage and organized by data type and upload date.
3. Data Loading and Processing
   * The system cleans and standardizes the data by normalizing column names, validating data ranges, and handling missing values.
   * A processing log is generated to summarize rows processed and data quality issues.
   * Cleaned data is loaded into a managed SQL database and stored in structured tables for labs, symptoms, vitals, and medications.
4. Analytical Processing
   * System executes automated queries on the processed data.
   * Summary tables are generated to capture trends such as changes in thyroid hormone levels and abnormal lab patterns.
5. Dashboard Visualization
   * System retrieves summary data from the database.
   * The Flask dashboard displays trends, tables, and indicators for monitoring hyperthyroidism over time.



     


