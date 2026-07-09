# FairPay AI Salary Benchmarking Engine

A compensation analytics and anomaly detection project built in Python to benchmark expected salary and identify unusual pay patterns using global salary data.

## Overview

This project analyzes 151K+ global salary records to estimate market salary for data-related roles and flag compensation cases that may be under-market, over-market, or otherwise unusual. The project combines salary benchmarking with anomaly detection to create a more business-focused analytics workflow rather than a basic prediction notebook.

## Business Problem

Compensation decisions are difficult because salary is influenced by multiple factors such as role, experience, location, company size, and work arrangement. Organizations need better ways to:

- benchmark expected pay across similar roles
- identify salaries that appear unusually high or low
- support compensation review with data-driven signals
- detect possible outliers or inconsistencies in salary records

This project addresses those needs by building a salary benchmark model and a supplementary anomaly scoring layer.

## Dataset

The dataset contains 151,445 salary records with the following fields:

- `work_year`
- `experience_level`
- `employment_type`
- `job_title`
- `salary`
- `salary_currency`
- `salary_in_usd`
- `employee_residence`
- `remote_ratio`
- `company_location`
- `company_size`

For modeling, `salary_in_usd` was used as the target because it provides a standardized compensation measure across currencies.

## Project Goals

The project has two connected objectives:

1. **Salary Benchmarking**  
   Estimate expected market salary using job, experience, location, company, and remote-work attributes.

2. **Compensation Anomaly Detection**  
   Flag unusual salary cases using model residuals, peer comparisons, z-scores, and Isolation Forest.

## Workflow

The notebook follows this pipeline:

1. Load and audit the salary dataset  
2. Clean and standardize the data  
3. Create a deduplicated modeling dataset  
4. Engineer features for salary benchmarking  
5. Train and compare regression models  
6. Evaluate performance using a time-based holdout framework  
7. Generate predicted salary and error diagnostics  
8. Detect compensation anomalies using multiple methods  
9. Save outputs for reporting and future dashboard use  

## Key Methods

### Salary Benchmarking
- Target: `salary_in_usd`
- Time-based holdout split
- Deduplicated modeling dataset
- Benchmark models including Dummy Regressor and Ridge Regression

### Anomaly Detection
- residual analysis
- peer-gap comparison
- z-score thresholds
- Isolation Forest

## Results

- Built a compensation analytics pipeline on **151K+ global salary records**
- Created a deduplicated **71,913-row modeling dataset**
- Selected **Ridge Regression** as the benchmark model
- Achieved **$47.2K MAE** on holdout data
- Identified **853 priority pay anomalies**
- Flagged under-market and over-market salary cases through an anomaly scoring layer

## Why This Project Matters

This project is designed to be more than a salary prediction exercise. It shows how machine learning can support real business use cases in compensation analytics by combining:

- salary benchmarking
- anomaly detection
- interpretable model outputs
- business-facing review metrics

The result is a workflow that could support HR analytics, compensation review, workforce planning, or labor-market benchmarking.

## Repository Structure

```text
.
├── notebook/
├── outputs/
│   ├── figures/
│   ├── metrics/
│   ├── models/
│   └── predictions/
├── fairpay_ai_salary_benchmark_notebook.ipynb
├── fairpay_ai_salary_benchmark_notebook.py
└── README.md
