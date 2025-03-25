**UCW HR Professional Development: Data Analytics Portfolio**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Welcome to my portfolio project, where I showcase how I implemented a Data Analytics Platform (DAP) on Amazon Web Services (AWS) for the HR Department’s Professional Development domain at University Canada West (UCW). This project aligns with the weekly teachings from our Cloud Computing course, in which we covered:
	•	Designing data pipelines with S3 buckets (raw, transform, curated)
	•	Managing data ingestion, transformation, and storage using AWS Glue, AWS DataBrew, AWS KMS, and other AWS components
	•	Performing Exploratory, Descriptive, Diagnostic analyses, as well as Data Wrangling and Data Quality Control
	•	Ensuring security, replication, cost optimization, and architecture best practices on AWS
	•	Deploying or testing services such as Beanstalk, EC2, and logging (HR app logs, user logs, etc.)
 
⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Below is a comprehensive explanation of each major section of the project, along with placeholders where I include relevant architecture diagrams, AWS console screenshots, data analysis results, and course completion badge at the end.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Table of Contents**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻
	
 1.	Project Description
	
 2.	Project Title

 3.	Objective

 4.	Dataset

 5.	Architecture Overview

 6.	Methodology
	
 7.	Exploratory Data Analysis

 8.	Descriptive Analysis
	
 9.	Diagnostic Analysis
	
 10.	Data Wrangling
	
 11.	Data Quality Control
	
 12.	Tools and Technologies
	
 13.	Deliverables
	
 14.	Timeline
	
 15.	Screenshots & Diagram Placeholders
	
 16.	Course Completion Badge
	
 17.	Conclusion

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Project Description**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Department: HR – Professional Development
Focus: Building an end-to-end data analytics platform and pipelines for HR’s professional development programs at UCW.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

In our Cloud Computing course, each student group was assigned a department. My team was assigned HR, and my specific role targeted the Professional Development subset of HR data. Throughout the course, we learned how to architect solutions in AWS, using S3 for storage (with separate buckets for raw, transformed, and curated data), AWS Glue for ETL/ELT tasks, AWS DataBrew for data profiling and cleaning, AWS IAM/KMS for security and encryption, and so on. We also explored cost optimization strategies, usage logs, and partial application deployments via AWS Elastic Beanstalk and EC2 for demonstration purposes.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Project Title**

“Implementing a Cloud-Based Data Analytics Platform for HR Professional Development at UCW”


⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Objective**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

The main goal is to gather, process, analyze, and gain insights into professional development activities within the UCW HR department, ensuring data is secure, well-structured, and readily available for advanced analytics. This covers:

	1.	Data Ingestion of CSV files and other structured data
	2.	Data Storage in AWS S3 (raw, transform, curated buckets)
	3.	ETL using AWS Glue (Glue crawlers, jobs) and AWS DataBrew for data cleaning
	4.	Data Quality, Validation, and Security with AWS KMS, IAM roles, and versioning/replication
	5.	Exploratory, Descriptive, and Diagnostic Analysis on the professional development dataset
	6.	Data Wrangling to merge and transform data for deeper insights
	7.	Data Quality Control measures for ongoing reliability and consistency
	8.	Cost Optimization evaluation for the chosen AWS services
	9.	Deployment of relevant prototypes or dashboards for end users (if needed)

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Dataset Overview**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

I worked primarily with Professional Development data stored in CSV format (e.g., Professional_Development_Activities.csv). The dataset typically includes fields like:

	•	Employee ID / Name
	•	Training/Workshop Name
	•	Dates
	•	Duration of the activity (e.g., hours, days)
	•	Cost (e.g., for external training)
	•	Feedback or Evaluation metrics
	•	Any Additional Fields relevant to staff development

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Other auxiliary datasets might include:**

	•	Employees-List.csv (general HR employee data)
	•	Financial_Support-List.csv (funding or reimbursements for professional development)

All these CSVs were stored initially in the Raw S3 bucket and then moved through the pipeline for cleaning, transformation, and curation.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Architecture Overview**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Below is a high-level look at the AWS architecture for the HR Professional Development data analytics pipeline:

	1.	S3 Buckets:
	•	ucw-hr-zul-raw: Original ingestion of CSV or JSON data files (raw format)
	•	ucw-hr-zul-transform: Intermediate, cleaned files (after DataBrew or Glue jobs)
	•	ucw-hr-zul-curated: Final curated data, ready for analytics and consumption
	2.	AWS Glue:
	•	Glue Crawlers to detect schema and create table definitions in the Data Catalog
	•	Glue ETL Jobs to transform data (e.g., partitioning, column renaming, etc.)
	3.	AWS DataBrew:
	•	Profiling the raw data (missing values, outliers, quality metrics)
	•	Recipe-based transformations for data cleaning
	4.	Security & Governance:
	•	AWS KMS to encrypt S3 objects at rest
	•	IAM roles and policies for controlling access to S3, Glue, DataBrew, etc.
	•	Versioning & Replication to handle possible data recovery and high availability
	5.	Additional Services:
	•	Amazon EC2 / Elastic Beanstalk for hosting potential data applications or HR dashboards
	•	CloudWatch logs for monitoring HR user logs, application logs, and cost optimization metrics
	6.	Cost Analysis / Optimization:
	•	Evaluate S3 storage class usage (Standard vs. Infrequent Access)
	•	Consider Glue job triggers and usage patterns to reduce overhead
	•	Track hours for running DataBrew sessions
	•	Evaluate EC2 instance types for possible cost savings
	7.	Data Consumption:
	•	Visualization or further analysis can be done using Amazon QuickSight, local Jupyter notebooks, or any BI tools.

(See the placeholder below where I have included an example draw.io architectural diagram. In my actual project, I replaced all references to “Registrar” with “HR” and “MAH” with “ZUL.”)

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Methodology**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

1. Exploratory Data Analysis

Project Description (EDA):
Conduct an Exploratory Data Analysis on the HR Professional Development dataset to discover patterns, anomalies, or interesting trends. This corresponds to investigating factors such as which employees are most active in training, the most expensive workshops, or seasonal trends in professional development.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Steps:

	1.	Data Collection & Preparation
	•	Loaded CSV files from the Raw S3 bucket (e.g., Professional_Development_Activities.csv) using Python (Pandas) or AWS DataBrew.
	•	Handled missing values (e.g., missing cost or duration).
	•	Checked data types, ensuring columns like Date or Duration are properly cast.
	2.	Descriptive Statistics
	•	Computed means, medians, and other summary stats on cost, duration, attendance.
	•	Frequency distribution for training categories or types of workshops.
	3.	Data Visualization
	•	Created histograms (duration, cost)
	•	Bar charts (training count by department, or by region if available)
	•	Heatmaps/correlation analyses (e.g., cost vs. satisfaction scores)
	4.	Insights & Findings
	•	Found top 5 training programs with highest cost or highest attendance.
	•	Observed peaks in certain months when HR invests in professional development.
	5.	Conclusion
	•	Summarized potential next steps like advanced predictive modeling or trend forecasting.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**2. Descriptive Analysis**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Project Description (Descriptive Analysis):
Provide a detailed overview of how professional development activities have been used by the HR department over a certain period. Summarize the key patterns in terms of cost, frequency, popularity, and outcomes.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Steps:

	1.	Data Collection & Cleaning
	•	Use AWS Glue or DataBrew to remove duplicates, standardize activity names.
	2.	Descriptive Statistics
	•	Total training count, average cost per employee, distribution of training topics.
	3.	Data Visualization
	•	Time-series graphs showing monthly or quarterly training spend.
	•	Bar charts for most popular workshop categories (soft skills, technical, leadership, etc.).
	4.	Customer (Employee) Segmentation (optional)
	•	Segment employees by the amount of training completed or by performance feedback.
	5.	Recommendations
	•	Provide suggestions to HR on which types of training yield the most positive feedback.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**3. Diagnostic Analysis**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Project Description (Diagnostic Analysis):
Investigate if there are any decreases or abnormal trends in professional development participation or expenditures. For instance, if the HR department sees lower participation in certain quarters, we identify root causes (budget constraints, scheduling conflicts, etc.).

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Steps:

	1.	Trend Analysis
	•	Compare data over the last year or last few quarters to spot any declines.
	2.	Correlation Analysis
	•	Check if decreased participation correlates with other factors (e.g., busy academic periods, lack of manager approval).
	3.	Root Cause Analysis
	•	Possibly apply “5 Whys” technique or gather feedback from employees or managers.
	•	Evaluate if certain training types repeatedly show lower enrollment.
	4.	Synthesis of Findings
	•	Summarize possible reasons for the drop.
	5.	Actionable Recommendations
	•	Suggest additional communication channels, better scheduling, or improved budget allocation.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**4. Data Wrangling**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Project Description (Data Wrangling):
Gather and unify data from multiple HR sources (e.g., main employee list, professional development activities, finance/reimbursement data) to create a clean “single source of truth” for analyzing professional development.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Steps:

	1.	Data Collection
	•	Pull CSV or database exports from multiple sources.
	•	Consolidate them in S3 raw bucket.
	2.	Data Cleaning
	•	Remove duplicates, fix inconsistent naming conventions, handle missing or invalid data.
	•	Possibly use AWS DataBrew recipes to automate some cleaning transformations.
	3.	Data Transformation
	•	Convert string dates to datetime.
	•	Derive new fields, e.g., “Total Training Hours,” “Cost per Hour,” “Employee Tenure.”
	4.	Data Consolidation
	•	Merge data with unique IDs to keep employee-level details consistent.
	•	Store resulting cleaned dataset in the S3 transform bucket.
	5.	Validation
	•	Run quick EDA checks or summary stats to ensure final dataset matches expectations.
	•	Document transformations (in Jupyter Notebook or DataBrew jobs).

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**5. Data Quality Control**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Project Description (Data Quality Control):
Implement measures that ensure the data is accurate, consistent, and reliable over time. This includes Data Profiling, Cleansing, Validation Rules, and Monitoring.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Steps:

	1.	Current State Assessment
	•	Evaluate existing data for duplicates, missing values, or incorrect formatting.
	2.	Data Profiling
	•	Use AWS DataBrew or other data profiling tools to systematically assess completeness, uniqueness, and overall data health.
	3.	Quality Metrics & KPIs
	•	Define acceptable error rates or thresholds for missing data.
	4.	Data Cleansing Processes
	•	Standardize naming conventions for departments or training modules.
	•	Fill missing values where possible or remove outliers if they are truly erroneous.
	5.	Validation Rules
	•	Ensure new records inserted follow consistent data types and mandatory fields.
	6.	Monitoring & Reporting
	•	Create scheduled AWS Glue/DataBrew jobs that validate data.
	•	Provide dashboards (e.g., QuickSight, Power BI) to track quality metrics in real time.
	7.	Training & Best Practices
	•	Educate team members on correct data entry methods.
	•	Encourage a culture of accountability for data cleanliness.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Tools and Technologies**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

	1.	Amazon S3: Raw, transform, curated buckets
	2.	AWS Glue: Crawlers for schema, ETL jobs for transformations
	3.	AWS DataBrew: Data profiling, cleaning, recipe creation
	4.	AWS KMS: Encryption at rest for S3 objects
	5.	IAM: Role-based access control
	6.	AWS Elastic Beanstalk / EC2 (optional demos)
	7.	Python (Pandas, NumPy, Matplotlib) and/or Jupyter Notebooks for local EDA
	8.	SQL (if needed for advanced queries)
	9.	Tableau / Power BI / QuickSight for data visualization (optional)

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Deliverables**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

	1.	Comprehensive AWS Architecture Diagram (modified from the professor’s draw.io, updated for HR/Professional Development).
	2.	Cleaned and Curated Datasets in the S3 curated bucket.
	3.	Data Analysis Notebooks (for EDA, descriptive, diagnostic) or DataBrew job definitions.
	4.	Data Quality Control Documentation describing how we manage duplicates, missing data, or invalid entries.
	5.	Presentation Slides or Reports summarizing findings, recommendations, and cost optimization strategies.

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

**Timeline**

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻
A rough breakdown of the project phases:

	1.	Week 1–2: Data ingestion planning, creating S3 buckets, setting up IAM & KMS
	2.	Week 3–4: Initial ingestion, DataBrew profiling, basic EDA
	3.	Week 5–6: Glue ETL jobs, deeper descriptive & diagnostic analyses
	4.	Week 7–8: Data Wrangling completion, Data Quality Control measures, final curated dataset
	5.	Week 9–10: Architecture finalization, cost optimization review, presentation preparation

(Adjust as needed if your actual schedule differs.)

⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻⸻

Screenshots & Diagram Placeholders

Below are placeholders where you can paste screenshots from your actual AWS environment, draw.io diagrams, or any relevant images:
	1.	Project Architecture Diagram

![Architecture Diagram Placeholder](path/to/your/architecture-diagram.png)

Short description:
Insert your draw.io diagram here, showing the raw/transform/curated S3 buckets, AWS Glue, DataBrew, IAM, KMS, etc.

	2.	DataBrew Screenshot

![DataBrew Profiling Job](path/to/data-brew-profile.png)

Short description:
Show how you profiled the HR Professional Development CSV to find missing data, outliers, etc.

	3.	AWS Glue Crawler / ETL Job

![Glue Crawler Screenshot](path/to/glue-crawler.png)

Short description:
Insert your screenshot demonstrating your crawler’s success in identifying schema or a snippet from your ETL job.

	4.	Cost Analysis Screenshot

![Cost Analysis Placeholder](path/to/cost-analysis.png)

Short description:
Show your cost explorer or any cost optimization measure you performed.

	5.	Final Curated Dataset

![Curated Data Placeholder](path/to/curated-data.png)

Short description:
Illustrate the final version of your data with consistent schema and no duplicates.

(Feel free to add or remove placeholders depending on the number of images you have.)

⸻

Course Completion Badge

Please find below a placeholder where I will add my AWS Academy CF course completion badge:

![AWS Course Completion Badge](path/to/badge.png)

(Claim your badge in “Badges and completion certificates” under the AWS Academy CF course and insert the screenshot here.)

⸻

**Conclusion**

Through this project, I demonstrated the end-to-end implementation of a Data Analytics Platform for the UCW HR Department (Professional Development) on AWS. The solution follows best practices for:
	•	Scalability (using S3, Glue, DataBrew, and optional deployment services)
	•	Security (IAM, KMS, encryption at rest)
	•	Data Quality (cleaning, validation, and profiling steps)
	•	Analytics (exploratory, descriptive, diagnostic analyses, plus thorough data wrangling)
	•	Cost Optimization (appropriate storage classes, job scheduling, instance sizing)

This portfolio reflects the key learning outcomes from my Cloud Computing course and demonstrates how AWS services can be orchestrated to handle large-scale HR data effectively.

Thank you for reviewing my portfolio! If you have any questions or need further clarification on any part of the implementation, please feel free to reach out.

⸻

