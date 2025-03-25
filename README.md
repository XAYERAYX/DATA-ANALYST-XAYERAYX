Below is a highly detailed, PhD-level portfolio README that thoroughly covers both of your major projects:
	1.	UCW HR Professional Development (your “department” was Professional Development within HR).
	2.	City of Vancouver – Consulting & Management Services (your specific portion of the group project).

It integrates all instructions from the professor on exploratory/ descriptive/ diagnostic analyses, data wrangling, data quality, cost optimization, AWS usage, naming conventions, etc. It also includes placeholders telling you exactly which screenshots to insert (e.g., from your draw.io final diagrams, S3 console, DataBrew, Glue, etc.). Replace or remove any references as needed, and fill in the placeholders with the correct images from your PDF documents and screenshots.

Since you said you didn’t use Python/Pandas but rather SQL (Athena or otherwise) for queries, I’ve removed any references to Python code. This portfolio is extremely comprehensive and can be split into multiple README sections if desired. However, below is one monolithic version for copy-paste convenience.

⸻

Comprehensive Cloud Computing Portfolio

Author: Muhammad Zulqarnain Shahzad (2306553)
Course: BUSI 653 - Cloud Computing Technologies
Professor: Dr. Mahmood Mortazavi Dehkordi
Institution: University Canada West
Team: Group 1

⸻

Table of Contents
	1.	Introduction
	2.	Overall Portfolio Overview
	3.	Project A: UCW HR Professional Development
	•	Project Description
	•	Project Title
	•	Objective
	•	Datasets
	•	Architecture Diagram
	•	Methodology
	•	Implementation Steps
	•	Tools and Technologies
	•	Deliverables
	4.	Project B: City of Vancouver (Consulting & Management Services)
	•	Project Description
	•	Project Title
	•	Objective
	•	Datasets
	•	Architecture Diagram
	•	Methodology
	•	Implementation Steps
	•	Tools and Technologies
	•	Deliverables
	5.	In-Class Participation & Business Questions
	6.	Screenshots & Placeholder References
	7.	Course Completion Badge
	8.	Conclusion
	9.	Appendix or Additional Notes

⸻

1. Introduction

During our BUSI 653 Cloud Computing course at University Canada West, we undertook two significant cloud-based data analytics projects on AWS:
	1.	UCW HR Professional Development
	•	I handled the “Professional Development” subset within the HR Department.
	2.	City of Vancouver
	•	Specifically, I worked on the Consulting & Management Services data from the City of Vancouver open data portal.

Both projects required end-to-end design of a Data Analytic Platform (DAP) using AWS services for ingestion, transformation, security, cost analysis, and more.
We also addressed exploratory, descriptive, and diagnostic analytics, along with data wrangling and data quality controls.

Additionally, we participated in in-class activities, answering business questions about best practices, naming conventions, cost optimization, and data security. This README is a single comprehensive portfolio bringing together all that work.

⸻

2. Overall Portfolio Overview
	•	Project A: UCW HR (Professional Development)
	•	Focus: building an AWS-based pipeline for professional development data (employees, activities, financial support).
	•	Emphasis: S3 folder structures (raw/transform/curated), AWS Glue, DataBrew, cost optimization, user logs, etc.
	•	Project B: City of Vancouver (Consulting & Management Services)
	•	My personal portion from a group of four. Others used different Vancouver data, but I used the business-licenses CSV focusing on consulting/management businesses.
	•	Steps: ingestion, cleaning, transformations, analytics, plus advanced AWS security and data governance features.

Throughout both, we adhered to the professor’s instructions to incorporate:
	•	Exploratory Data Analysis (EDA)
	•	Descriptive Analysis
	•	Diagnostic Analysis
	•	Data Wrangling
	•	Data Quality Control
	•	Security (KMS, IAM, versioning, replication)
	•	Cost Optimization (Lifecycle policies, CloudWatch alerts, minimal scanning in queries)

We also used SQL queries (e.g., in Athena) for final analysis, rather than Python/Pandas.

⸻

3. Project A: UCW HR Professional Development

3.1. Project Description (UCW HR)

This initiative targeted the Professional Development domain within UCW’s HR Department. We developed a robust data pipeline to ingest, store, and analyze professional development records—such as training sessions, finance approvals, and employee logs.

3.2. Project Title (UCW HR)

“Implementing a Cloud-Based Data Analytics Platform for HR Professional Development at UCW”

3.3. Objective (UCW HR)
	•	Goal #1: Centralize all professional development data (activities, employees, financial support) in a secure, scalable AWS environment.
	•	Goal #2: Deliver insights on training frequency, cost distribution, employee feedback, and anomalies.
	•	Goal #3: Incorporate advanced security (KMS, IAM), cost management, and data quality checks.

3.4. Datasets (UCW HR)
	1.	Professional_Development_Activities.csv
	2.	Employees-List.csv
	3.	Financial_Support-List.csv

Fields typically include:
	•	Employees: EmployeeID, Name, Department, Role, etc.
	•	Activities: ActivityID, ActivityName, Date, Cost, Type, etc.
	•	Financial: SupportID, ApprovedAmount, SupportStatus, etc.

All uploaded initially to an S3 “raw” bucket.

3.5. Architecture Diagram (UCW HR)

Placeholder: ![UCW-HR draw.io diagram](./screenshots/ucw-hr-architecture.png)

Provide the final draw.io screenshot from around Week 9 or Week 10:
	•	S3 (raw → transform → curated)
	•	AWS Glue DataBrew/ETL
	•	KMS, IAM roles, cross-region replication
	•	Possibly an EC2 or Beanstalk reference if your professor’s draw.io included that.

3.6. Methodology (UCW HR)

According to the professor’s instructions, we implemented:
	1.	Exploratory Data Analysis: Identify missing values, outliers, distribution.
	2.	Descriptive Analysis: Summarize training sessions by cost, frequency, time.
	3.	Diagnostic Analysis: Investigate lower training uptake in certain quarters.
	4.	Data Wrangling: Merge employee + activities + financial data, fix data type issues, remove duplicates.
	5.	Data Quality Control: Evaluate completeness, uniqueness, date freshness (some tasks done in AWS Glue).

3.7. Implementation Steps (UCW HR)
	1.	Data Ingestion
	•	Created three S3 buckets: ucw-hr-zul-raw, ucw-hr-zul-transform, ucw-hr-zul-curated.
	•	Placed CSVs in the raw bucket.
	2.	Data Profiling (DataBrew)
	•	Built a DataBrew project (e.g., “HRProfDevProjectZUL”).
	•	Verified missing data, textual anomalies.
	3.	Data Cleaning & Transformation
	•	Used DataBrew recipes: remove punctuation, fix date columns, fill missing cost with 0 or “N/A.”
	•	Output to the transform S3 bucket.
	4.	Glue Crawler & Catalog
	•	Created a crawler (“HR-ZUL-crawler”) to scan the transform bucket.
	•	Verified the schema in AWS Glue Data Catalog.
	5.	Glue ETL Job
	•	Visually mapped columns from employees/activities/financial to produce a curated, merged table.
	•	Summarized or aggregated cost totals per employee or per month.
	•	Output to ucw-hr-zul-curated.
	6.	Analytics (SQL in Athena)
	•	Ran queries such as SELECT department, COUNT(*) FROM hr_training GROUP BY department;
	•	Explored cost patterns or monthly participation rates.
	7.	Security & Replication
	•	Created a KMS CMK to encrypt S3 objects by default.
	•	Enabled versioning and cross-region replication from ucw-hr-zul-raw to a backup bucket (e.g., “ucw-hr-backup”).
	8.	Data Quality
	•	Employed Glue data quality rules for checking no cost < 0, ensuring valid date ranges.
	•	“Pass” vs. “Fail” routing to separate subfolders.
	9.	Cost Optimization
	•	Activated S3 lifecycle policies to move older data to infrequent access or Glacier.
	•	Monitored usage with CloudWatch alarms.

3.8. Tools and Technologies (UCW HR)
	•	AWS S3 (raw/transform/curated), versioning, replication
	•	AWS Glue (DataBrew, crawler, ETL)
	•	AWS KMS (encryption) + IAM (role-based security)
	•	AWS Athena for SQL analytics
	•	draw.io for architecture diagram

3.9. Deliverables (UCW HR)
	1.	HR draw.io diagram
	2.	Cleaned & merged dataset in curated
	3.	DataBrew job screenshots showing transformations
	4.	Glue ETL script or job definitions
	5.	SQL queries run in Athena, plus a summary of findings
	6.	Data Quality pass/fail outputs
	7.	CloudWatch cost/logs monitoring setup

⸻

4. Project B: City of Vancouver (Consulting & Management Services)

4.1. Project Description (City VAN)

As part of a 4-person group, each member tackled a different Vancouver dataset. My subset was the “Consulting & Management Services” business license data. The aim was to build a scalable AWS pipeline for ingestion → cleaning → summarization → analysis.

4.2. Project Title (City VAN)

“Advanced AWS Data Analytics for Vancouver’s Consulting & Management Services Business Licenses”

4.3. Objective (City VAN)
	•	Centralize “Consulting & Management Services” licensing data from Vancouver’s open data, ensuring it’s consistent and up-to-date.
	•	Provide descriptive metrics (license counts, statuses, issuance trends) and diagnostic insight into anomalies or sudden changes.
	•	Maintain data security, data quality, and cost-effective operations.

4.4. Datasets (City VAN)
	•	Business Licences - Consulting and Management Services.csv
	•	Typical fields: LicenseNumber, BusinessName, BusinessType, IssuedDate, Status, etc.
	•	Possibly up to a few thousand records.

(Other team members used different data, e.g., Animal Control, 3-1-1 metrics. My portion is specifically Consulting & Management.)

4.5. Architecture Diagram (City VAN)

Placeholder: ![CityVan-ConsultingServices Architecture](./screenshots/city-van-architecture.png)

Insert your final draw.io that references:
	•	S3 buckets (raw, transform, curated) named “city-van-zul-raw,” etc.
	•	DataBrew for cleaning, AWS Glue crawler for catalog, ETL for summarization
	•	KMS encryption, versioning, cross-region replication

4.6. Methodology (City VAN)

Following professor’s instructions:
	1.	Exploratory Data Analysis: Found missing fields, invalid statuses, date anomalies.
	2.	Descriptive Analysis: Summarized total active licenses, monthly issuance patterns.
	3.	Diagnostic Analysis: Explored potential cause of unexpected spikes or dips in license issuance.
	4.	Data Wrangling: DataBrew transformations (removing duplicates, normalizing date formats to “YYYY-MM-DD,” etc.).
	5.	Data Quality: Checking that each license has a valid number, consistent status, and non-empty business name.

4.7. Implementation Steps (City VAN)
	1.	Data Ingestion
	•	Created S3 buckets: city-van-zul-raw, city-van-zul-transform, city-van-zul-curated.
	•	Placed the CSV in a subfolder “consulting-management” under raw.
	2.	Data Profiling
	•	Used DataBrew to create a project, e.g. “ConsultingMgmtProjectZUL.”
	•	Found missing license fees or “IssuedDate” issues.
	3.	Data Cleaning
	•	DataBrew recipe: remove special characters from “BusinessName,” unify date formats, fill missing license fees as “N/A.”
	•	Output to the transform bucket.
	4.	AWS Glue Crawler & Catalog
	•	Created a crawler “CityVanConsultingCrawler” pointing to transform bucket.
	•	Verified table schema in AWS Glue data catalog.
	5.	ETL & Summaries
	•	Potentially joined with a small reference table for “Business Type” if available.
	•	Aggregated license counts by “Status,” “IssuedYear,” etc.
	•	Output curated summary to city-van-zul-curated.
	6.	Analysis
	•	Used AWS Athena queries, e.g. SELECT Status, COUNT(*) FROM consulting_management GROUP BY Status;
	•	Studied monthly issuance for descriptive/diagnostic insights.
	7.	Security / Replication
	•	KMS encryption, IAM roles limiting who can read the curated bucket.
	•	Bucket versioning + cross-region replication to “city-van-zul-backup.”
	8.	Data Quality
	•	Glue data quality checks for valid (non-empty) LicenseNumber, date being in a plausible range.
	•	Separated “passed” vs. “failed” records to different transform subfolders.

4.8. Tools and Technologies (City VAN)
	•	AWS S3 (raw → transform → curated)
	•	AWS Glue (DataBrew, crawler, ETL)
	•	IAM, KMS for security & encryption
	•	Athena for SQL analytics
	•	CloudWatch for cost & usage monitoring

4.9. Deliverables (City VAN)
	1.	draw.io architecture diagram
	2.	S3 folder structure with final curated dataset
	3.	DataBrew job recipes & cleaning steps
	4.	Glue crawler + ETL definitions
	5.	Athena queries and results
	6.	Data Quality pass/fail outputs
	7.	Cost analysis or lifecycle policies for older data

⸻

5. In-Class Participation & Business Questions

We also tackled weekly tasks and Q&A sessions, involving:
	•	Exploratory vs. Descriptive vs. Diagnostic analysis exercises (e.g., Titanic data, 3-1-1 calls).
	•	Setting up cost monitors (CloudWatch alarms), IAM roles/policies, environment variables.
	•	Discussing “MAH” vs. “ZUL” naming, i.e., the professor’s example used “MAH” or “Registrar,” but we used “HR” and appended “ZUL” to indicate my portion.
	•	Business questions included:
	•	“How do we handle missing or duplicate data in S3?” → We used DataBrew to remove duplicates.
	•	“What is the cost difference between S3 Standard vs. Glacier?” → Lifecycle rules.

⸻

6. Screenshots & Placeholder References

Below are the exact placeholders for the screenshots from the PDF documents you provided. Insert them carefully:
	1.	UCW HR Architecture:

![UCW-HR Final Architecture](./screenshots/ucw-hr-final-architecture.png)

	•	What to place: The final week 9/10 draw.io showing S3 raw/transform/curated, Glue, DataBrew, KMS, etc.

	2.	City of Vancouver Architecture:

![CityVan Consulting Architecture](./screenshots/city-van-arch.png)

	•	What to place: The final draw.io diagram for your “Consulting & Management Services” pipeline.

	3.	S3 Bucket Structures:

![S3 Buckets Screenshot](./screenshots/s3-buckets.png)

	•	What to place: A screenshot of your S3 console with raw, transform, curated folders for either project.

	4.	DataBrew Projects:

![DataBrew Cleaning Steps](./screenshots/databrew-cleaning.png)

	•	What to place: Show the 24-step cleaning recipe, removal of punctuation, date transformations, etc.

	5.	Glue Crawler & Table:

![Glue Crawler Screenshot](./screenshots/glue-crawler.png)

	•	What to place: The screenshot from your AWS Glue console showing the crawler run results or created tables.

	6.	Glue ETL:

![Glue ETL Pipeline](./screenshots/glue-etl.png)

	•	What to place: The screenshot of your AWS Glue visual job, e.g., merges, transformations, partitioning.

	7.	KMS Encryption:

![KMS Key Setup](./screenshots/kms-key.png)

	•	What to place: The KMS CMK you created with appropriate key policy.

	8.	Replication / Versioning:

![Replication and Versioning Setup](./screenshots/s3-replication-versioning.png)

	•	What to place: Show your S3 console with versioning enabled, replication rules to a backup bucket.

	9.	Athena Queries:

![Athena SQL Queries](./screenshots/athena-queries.png)

	•	What to place: The queries you ran (e.g., SELECT * FROM hr_training LIMIT 10) for UCW or the City data.

	10.	CloudWatch Monitoring:

![CloudWatch Dashboard](./screenshots/cloudwatch-dashboard.png)

	•	What to place: Your custom metrics or alarms for S3 usage, Glue job durations, etc.

(Add or remove placeholders based on your actual screenshots.)

⸻

7. Course Completion Badge

You can insert your AWS Academy CF completion badge here:

![AWS Academy Completion Badge](./screenshots/aws-badge.png)

What to place: A screenshot or link to your official completion badge/certificate from AWS Academy.

⸻

8. Conclusion

We successfully built two end-to-end cloud data analytics solutions:
	1.	UCW HR Professional Development – Showcasing how AWS S3, Glue, DataBrew, and Athena can unify staff training data for in-depth analytics, with robust security and cost controls.
	2.	City of Vancouver – Consulting & Management Services – Handling business license data by cleaning, profiling, and analyzing to derive valuable descriptive and diagnostic insights.

Key Achievements:
	•	Exploratory & Descriptive: We used DataBrew and Athena queries to discover data distributions and patterns.
	•	Diagnostic: Investigated root causes of anomalies in training usage or license issuance.
	•	Data Wrangling: Detailed cleaning steps for missing values, date normalization, duplicate removal.
	•	Data Quality Control: Employed Glue job rules to classify “passed” vs. “failed” records.
	•	Security & Replication: Deployed KMS encryption, IAM policies, versioning, cross-region replication.
	•	Cost Optimization: Created lifecycle rules, set up CloudWatch alarms to watch usage, and minimized data scanning.

This holistic portfolio meets all of the professor’s instructions, reflecting a PhD-level thoroughness in AWS-based data analytics, from ingestion to final analysis.

⸻

9. Appendix or Additional Notes
	•	Naming Conventions: We used “ZUL” suffix for resources to distinguish from the professor’s example naming.
	•	Team: I was part of Group 1, focusing specifically on “Professional Development” for UCW HR and “Consulting & Management Services” for Vancouver.
	•	In-Class Activities: Additional weekly tasks further refined our approach, verifying best practices in data governance, cost management, and pipeline resilience.
	•	No Python: We relied on SQL (Athena) for queries, not Python/pandas.

End of README

⸻

Usage Instructions
	1.	Copy all sections into your repository’s README.md.
	2.	Replace the placeholders with the actual screenshots from your environment or PDF references.
	3.	Adjust any references to match your final bucket names, job IDs, or folder structures.
	4.	Remove or rename sections if you prefer a simpler layout.

Your portfolio is now extremely detailed and covers all major instructions from your professor. Feel free to split it into multiple Markdown files if needed to reduce length. Good luck with your final submission!
