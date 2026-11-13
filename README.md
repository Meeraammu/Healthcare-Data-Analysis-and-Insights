# Healthcare-Data-Analysis-and-Insights
Healthcare Data Analysis and Insights (Excel Dashboard)

An end-to-end exploratory data analysis, data cleaning, feature engineering, and interactive dashboard project built in Microsoft Excel. This project consolidates patient medical examinations, hospitalization records, and customer profile tables to uncover key drivers of healthcare costs, chronic conditions, and clinical risk factors.

📌 Project Overview

Healthcare providers and policymakers generate vast amounts of clinical and billing data daily. By cleaning, transforming, and integrating multi-table patient records, this project delivers an interactive Excel dashboard designed to answer critical clinical and financial questions—enabling stakeholders to evaluate how lifestyle factors (smoking, weight status), chronic conditions (diabetes, cancer history, transplant history), age, and regional hospital tiers influence medical charges.

📂 Dataset Structure

The raw dataset consists of three relational tables linked via a common Customer ID primary key:

Medical Examinations: Clinical metrics including BMI, HBA1C, Heart Issues, Any Transplants, Cancer history, NumberOfMajorSurgeries, and smoker.

Hospitalization Details: Admission and billing details including birth date components (year, month, date), charges, Hospital tier, City tier, and State ID.

Customer Names: Patient demographic identifiers containing full names and Customer ID.

🛠️ Methodology & Workflow

1. Data Cleaning

Missing Value Audit: Identified and quantified placeholder missing values (?) across all columns in the Medical Examinations and Hospitalization Details tables using COUNTIF.

Date Imputation: Replaced missing month values with "Sep" and missing year values with the column's mean rounded to the nearest integer (ROUND(AVERAGE(...), 0)).

Categorical Mode Imputation: Determined the most frequently occurring categories (mode) for smoker, Hospital tier, and City tier to impute missing entries accurately.

Geographic Standardization: Handled missing State ID entries by assigning "Unknown" to preserve record completeness without skewing regional averages.

2. Data Transformation & Feature Engineering

Name Parsing: Split the names column in Customer Names into three distinct fields: Title, First Name, and Last Name.

Numeric Standardization: Converted NumberOfMajorSurgeries into clean numeric values by replacing text strings (e.g., "No major surgery") with 0.

Consistency Validation: Audited Heart Issues and smoker fields to standardize casing and inconsistent labels (Yes/No).

BMI Classification (Weight Status): Engineered clinical weight brackets using nested IF logic:

Below 18.5: Underweight

18.5 – 24.9: Normal Weight

25.0 – 29.9: Overweight

30.0 and Above: Obesity

Glycemic Classification (Diabetes Status): Categorized HBA1C levels into clinical risk tiers:

Below 5.7: Normal

5.7 – 6.4: Prediabetes

6.5 and Above: Diabetes

Date of Birth & Age Calculation: Merged year, month, and date into a unified Date of Birth column formatted as DD-MMM-YYYY, then calculated exact patient Age relative to the dataset collection date (8th June 2023) using DATEDIF.

Currency Formatting: Standardized the charges column into US Dollar currency format ($).

3. Data Integration (Healthcare Master Sheet)

Consolidated all three cleaned tables into a unified Healthcare worksheet using VLOOKUP on Customer ID.

Retained the 17 core analytical columns: Customer ID, First Name, BMI, HBA1C, Heart Issues, Any Transplants, Cancer history, NumberOfMajorSurgeries, smoker, Weight Status, Diabetes Status, Date of Birth, charges, Hospital tier, City tier, State ID, and Age.

📊 Exploratory Analysis & Visualizations

Using dynamic Pivot Tables and Pivot Charts, six key business and clinical questions were analyzed:

Cancer History Among Smokers vs. Non-Smokers (Pie/Donut Chart)

Evaluates the proportional breakdown of cancer history across smoking statuses to highlight lifestyle risk patterns.

Major Surgeries & Average HbA1c by Transplant History (Pie/Donut & Combo Analysis)

Compares surgical volume (1,417 vs. 162 major surgeries) and mean glycemic levels (6.67% vs. 5.19% HbA1c) between non-transplant and transplant patients.

Healthcare Charges by Weight Status & Diabetes Status (Column/Bar Chart)

Examines how compounding metabolic risk factors impact average and total patient medical expenditure.

Average Charges by Hospital Tier Across States (Clustered Column/Bar Chart)

Benchmarks regional healthcare pricing disparities across Tier 1, Tier 2, and Tier 3 facilities by State ID.

Correlation Between Age, BMI, and HbA1c (Line/Scatter Plot & =CORREL)

Tracks metabolic progression across patient age brackets and quantifies linear correlation strength.

Relationship Between Age and Healthcare Charges (Line/Scatter Plot)

Models how medical costs scale across patient life stages.

🎛️ Interactive Dashboard Features

Executive KPI Cards: Top-level summary metrics tracking Total Patients, Total Major Surgeries, Overall Average HbA1c, and Average Healthcare Charges.

Cross-Filtering Slicers: Interactive horizontal slicers for Weight Status and Diabetes Status connected via Report Connections across all Pivot Tables—allowing stakeholders to dynamically filter every chart on the dashboard simultaneously.
