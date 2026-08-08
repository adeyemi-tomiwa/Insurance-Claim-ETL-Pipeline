# Insurance-Claim-ETL-Pipeline
This project focuses on analyzing vehicle insurance claims to identify fraudulent claims and uncover patterns across different customer, policy, vehicle, and accident characteristics.
## Project Overview
The project follows an end-to-end ETL and analytics workflow. The insurance claim dataset was extracted and processed using Python, loaded into PostgreSQL, analyzed using SQL, and finally visualized through an interactive Grafana dashboard.

The analysis focuses on understanding claim volumes, fraudulent claims, fraud rates, vehicle characteristics, accident areas, policyholder demographics, and other factors associated with insurance claims.

The dataset contains 33 columns, including information such as vehicle make, accident area, policy type, vehicle category, policyholder age, gender, marital status, claim information, and fraud status.
## Project Workflow

Vehicle Insurance Dataset

          ↓
       Python
       
   Extract & Transform
   
          ↓
          
      PostgreSQL
      
          ↓
          
         SQL
         
       Analysis
       
          ↓
          
       Grafana
       
     Visualization
     
    ## Project Objectives
    
The main objectives of this project were to:

Analyze the overall volume of vehicle insurance claims.

Identify the number and proportion of fraudulent claims.

Examine fraudulent claims across different policyholder demographics.

Analyze claims by vehicle make and vehicle category.

Investigate claims based on accident area and fault.

Examine claim trends across different years.

Analyze claims across different policy types.

Use SQL to answer key insurance business questions.

Build an interactive Grafana dashboard to communicate the findings.

The SQL analysis includes queries for fraudulent claims by gender, marital status, and policyholder age, as well as broader claim analysis by vehicle category, vehicle make, accident area, fault, year, and policy type.
## Dataset
The project uses a vehicle insurance claims dataset containing 15,420 insurance claim records across 33 columns. The dataset contains information about policyholders, vehicles, accidents, insurance policies, claims, and whether a claim was identified as fraudulent.

The original dataset is stored as:
- <a href="https://docs.google.com/spreadsheets/d/1fz-LsBSFCzwrjIqq-BqD4AwQ9PPuPueh/edit?usp=drive_link&ouid=112581567316939365415&rtpof=true&sd=true" >Dataset</a>
## Data Preparation
The dataset was first loaded into Python using Pandas. As part of the transformation stage, duplicate records were removed using Pandas' drop_duplicates() function before the data was loaded into PostgreSQL.

The cleaned dataset was then loaded into a PostgreSQL database named Insurance Claim, where it became the source for the subsequent SQL analysis and Grafana dashboard.
## ETL Process
The ETL pipeline was developed in Python and consists of three main stages: Extract, Transform, and Load.
1. Extract
The dataset was extracted from the CSV file using Pandas' read_csv() function.
def extract():
    Data = pd.read_csv(
        r"C:\Users\hp\Desktop\Datasets\Vehicle insurance claim\Vehicle Insurance Case Fraud.csv"
    )
    return Data
2. Transform
The transformation stage focused on removing duplicate records from the dataset.
def load(df):
    connection = psycopg2.connect(
        host="localhost",
        dbname="Insurance Claim",
        user="postgres",
        password="1234"
    )
3. Load
The transformed data was loaded into a PostgreSQL database using
def load(df):
    connection = psycopg2.connect(
        host="localhost",
        dbname="Insurance Claim",
        user="postgres",
        password="1234"
    )
   The records were inserted into the Insurance_Claim table, and the transaction was committed after the loading process.

## Complete ETL Workflow

Raw CSV Dataset

      ↓
      
   EXTRACT
   
    Pandas
    
      ↓
      
   TRANSFORM
   
 Remove Duplicates
 
      ↓
      
     LOAD
     
  PostgreSQL
  
      ↓
      
 Insurance_Claim
 
The complete ETL workflow was executed by calling the three functions sequentially:
 raw_data = extract()
clean_data = transform(raw_data)
load(clean_data)
## Technologies Used in the ETL Process
  Python — ETL development
  Pandas — Data extraction and transformation
  psycopg2 — PostgreSQL database connection
  PostgreSQL — Data storage
# Dashboard
<img width="779" height="360" alt="Insurance Claim Dashboard" src="https://github.com/user-attachments/assets/b17d5f45-81d7-44fa-9925-d192b0a416ad" />
## Key Insights
The analysis and Grafana dashboard provided several insights into the vehicle insurance claims dataset:

The dataset contains 15,420 total claims, of which 14,497 were classified as valid and 923 as fraudulent.

The overall fraud rate was 5.99%.

Fraudulent claims were analyzed across gender, marital status, and policyholder age groups to identify differences in fraud occurrence.

Claims were also compared across vehicle categories and vehicle makes, allowing differences between valid and fraudulent claims to be observed.

The analysis examined claims by accident area, providing a comparison of valid and fraudulent claims between different accident locations.

Claim patterns were analyzed across months and years to understand how claim activity varied over time.

Claims were also analyzed by policy type and fault, providing additional context around the characteristics of reported claims.
## Recommendations

Based on the analysis, the following actions could support further investigation and monitoring of insurance claims:

Monitor fraudulent claim patterns using demographic, vehicle, policy, and accident-related attributes identified in the analysis.

Prioritize further investigation of unusual claims rather than treating any single demographic or vehicle characteristic as evidence of fraud.

Continue monitoring fraud trends over time using the dashboard to identify changes in claim and fraud patterns.

