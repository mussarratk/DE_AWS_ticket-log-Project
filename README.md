

# End-to-End AWS Data Engineering & BI Pipeline: CarePlus Support Analytics

<details>

***

## 📌 Project Overview
This project demonstrates the design and implementation of a robust, scalable data pipeline on AWS, taking raw operational data all the way to a highly interactive Business Intelligence dashboard. 

The objective was to extract customer support data from a traditional RDBMS (MySQL) and flat log files, process them through a serverless Data Lake architecture, incrementally load the refined data into an **Amazon Redshift** Data Warehouse, and surface actionable insights using **Power BI**. This architecture enables data-driven decision-making by turning fragmented logs into high-performance analytical assets.

## 🏗️ Architecture & Workflow
The pipeline follows a modern data architecture, smoothly moving data from raw ingestion to a structured, query-ready state for BI consumption.

1. **Data Extraction & Ingestion:** Python scripts extract relational data from an on-premise MySQL database (`careplus_support_db`) and push raw payloads to an **Amazon S3** landing zone (`raw/` bucket).
2. **Event-Driven Micro-Batch ETL:** Uploading `.log` files to S3 triggers an **S3 Event Notification**, which automatically invokes an **AWS Lambda** function to clean, transform, and convert the logs into columnar Parquet format.
3. **Batch Processing ETL:** **AWS Glue** (PySpark) handles heavier transformations of the support ticket data, applying visual and script-based ETL to land data in the `processed/` bucket.
4. **Data Warehousing & Incremental Load:** Processed data in S3 is loaded into **Amazon Redshift**. To ensure efficiency, an **incremental loading (UPSERT)** strategy is used, staging new data and merging it with existing tables to capture only new or updated records.
5. **Business Intelligence:** **Power BI** connects directly to the Redshift cluster to visualize key support metrics, SLA compliance, and agent performance.

## 🛠️ Tech Stack & Services Used
* **Data Sources:** MySQL, Local Flat Files (.log)
* **Storage & Data Lake:** Amazon S3
* **Compute & Serverless ETL:** AWS Lambda, AWS Glue (Serverless PySpark)
* **Data Warehouse:** Amazon Redshift
* **Data Cataloging & Ad-Hoc Analytics:** Amazon Athena
* **Business Intelligence:** Power BI
* **Languages & Libraries:** Python (boto3, pandas), SQL (Window Functions, MERGE), PySpark

## 🚀 Key Features & Implementation Details

### 1. Automated Data Ingestion (MySQL to S3)
* Developed Python scripts using `boto3` to programmatically extract operational data and load raw datasets into designated S3 buckets (`careplus-data-q1/support-tickets/raw/`).

### 2. Event-Driven Lambda Transformations
* Configured S3 Event Triggers to fully automate log ingestion. A new `.log` file instantly triggers an AWS Lambda function (`automate_support_log_ETL`).
* Integrated the **AWS Data Wrangler / Pandas Lambda Layer** to execute complex DataFrame operations in a serverless environment, outputting highly optimized `.parquet` files.

### 3. Scalable ETL with AWS Glue
* Designed a PySpark ETL pipeline using AWS Glue Studio to map schemas, handle null values, and transform datatypes, successfully troubleshooting Py4J runtime errors to ensure reliable job execution.

### 4. Incremental Data Loading into Redshift
* Designed a scalable data warehouse schema in **Amazon Redshift** optimized for OLAP workloads.
* Implemented an **incremental data load (Change Data Capture)** strategy. Using the `COPY` command, new data is loaded from S3 into a temporary staging table in Redshift.
* Utilized SQL `MERGE` (or `DELETE` and `INSERT`) operations to update existing records and insert new ones into the target production tables. This minimizes compute overhead and ensures the dashboard always reflects the most current state without requiring full historical reloads.

### 5. Interactive Power BI Dashboard
* Connected **Power BI** to the Redshift data warehouse using DirectQuery/Import modes depending on data volume.
* Engineered the narrative by creating dynamic DAX measures and visualizations to track ticket volumes, resolution times, and customer satisfaction, empowering stakeholders with a real-time view of support operations.

## 💡 Business Impact
* **Cost & Performance Optimization:** Leveraged Serverless compute (Lambda, Glue) and Parquet formatting to reduce storage footprint. The incremental load strategy in Redshift drastically reduced daily processing time and database compute costs.
* **Automated Insights:** Replaced manual MIS reporting with a fully automated, trigger-based pipeline that feeds directly into a live Power BI dashboard.
* **Scalable Data Foundation:** Architected a pipeline capable of seamlessly handling varying data velocities—from small event-driven log drops to large historical batch loads—proving a strong capability in building modern, cloud-native data pipelines.

***

### 📝 Note to Recruiters
This project highlights my passion for engineering the narrative and building scalable data pipelines. It showcases a comprehensive understanding of the AWS ecosystem, from raw data ingestion and PySpark transformations to advanced data warehousing techniques and BI reporting.

 
</details>
 
---
AWS Bucket S3 - : dir/folder - careplus_datasql -- subdir --support-logs/ -- support tickets/ - raw/ - processed/

<img width="1310" height="412" alt="image" src="https://github.com/user-attachments/assets/806659ea-5f78-44e9-b6e3-657be36c33a8" />
<img width="1314" height="527" alt="image" src="https://github.com/user-attachments/assets/94ee2d61-bd46-4f64-acaf-dc71e34fd63b" />
<img width="1322" height="526" alt="image" src="https://github.com/user-attachments/assets/ff8d8404-1ada-48ba-b9a8-cb0650abdf5f" />

----
Git Bash to run 

<img width="1366" height="308" alt="image" src="https://github.com/user-attachments/assets/f20cfc23-b73d-4cab-aaf5-adc273054543" />

---
Ingested from MySQL to AWS S3
<img width="1361" height="711" alt="image" src="https://github.com/user-attachments/assets/892ea3d0-3b07-41e4-b75c-eb3b2ea51236" />

---
jupyter notebook - ipynb file 

<img width="1259" height="714" alt="image" src="https://github.com/user-attachments/assets/349699ce-4e00-41b6-a1ed-ab5898cb481d" />
<img width="1187" height="417" alt="image" src="https://github.com/user-attachments/assets/64273d93-9379-4e22-894e-5cb92106c5ba" />

---
ETL - read downloaded from S3 logs - Transform done - save to S3 via Lambda (Function as a service - ETL) file from raw to save parquet file to processed
<img width="1092" height="624" alt="image" src="https://github.com/user-attachments/assets/0f1f1ab4-36dc-4afa-ab0f-5d875279553a" />

<img width="1270" height="720" alt="image" src="https://github.com/user-attachments/assets/3cf0e8bc-556a-4000-a426-cd7752980d7a" />
<img width="1294" height="567" alt="image" src="https://github.com/user-attachments/assets/bc7e6ec4-40bf-43e9-b649-b3564060ecc7" />
<img width="1257" height="702" alt="image" src="https://github.com/user-attachments/assets/7dd0daa1-f875-433b-bfe9-befeef56b274" />
<img width="1281" height="510" alt="image" src="https://github.com/user-attachments/assets/c4ee1364-6d76-436a-9b26-1123d102a5ed" />
<img width="622" height="526" alt="image" src="https://github.com/user-attachments/assets/9aaafca7-c09e-4533-9c24-5f0847244758" />

<img width="1309" height="531" alt="image" src="https://github.com/user-attachments/assets/e121fb6f-2404-4d59-8b71-7370c5a8e516" />

----
automated workflow function will be trigger whenever new is file upload in s3 - Lambda function to trigger automatically - event trigger put : support_log_ETL

<img width="597" height="576" alt="image" src="https://github.com/user-attachments/assets/f935a165-50f7-4bd5-b592-41c47277878a" />


 ----
ingested new files in raw to fully automate the ingestion and transformation 
<img width="978" height="535" alt="image" src="https://github.com/user-attachments/assets/cd11588d-51cb-43d2-bc4a-5f0688720054" />

got timed out error in lambda increase the time to 14 mins
<img width="1311" height="588" alt="image" src="https://github.com/user-attachments/assets/d5a916ee-5bd2-4f0b-afac-bc3180fc0cd8" />
<img width="1205" height="568" alt="image" src="https://github.com/user-attachments/assets/e55e2268-2874-42fe-a88b-a43c84bd6d94" />
<img width="1000" height="605" alt="image" src="https://github.com/user-attachments/assets/87de0989-12f5-479f-a75b-edd576e57808" />
<img width="1267" height="719" alt="image" src="https://github.com/user-attachments/assets/b352776b-cce4-4930-be6c-5fb3d6156635" />

<img width="1127" height="405" alt="image" src="https://github.com/user-attachments/assets/c1af04eb-bfb9-465f-9945-db41ed5fa6ee" />
<img width="1172" height="408" alt="image" src="https://github.com/user-attachments/assets/4e286206-e559-4273-b8a7-fb0bf4b4baa5" />

----
Project architecture

---
Support Tickets - raw dir aws glu is an etl tool (visual etl/ notebook) processed transformed cleaned file save as parquet in processed dir in s3
first - IAM - create roles - glue service need access to s3
x<img width="1304" height="562" alt="image" src="https://github.com/user-attachments/assets/c384b02f-79d0-4837-94a1-f16ef6fea141" />

<img width="1313" height="498" alt="image" src="https://github.com/user-attachments/assets/bcff6214-9815-4d79-8702-d8396f44bbac" />
<img width="1187" height="561" alt="image" src="https://github.com/user-attachments/assets/0fed6de2-1268-4918-8e25-81a9f42a54e1" />

<img width="1308" height="617" alt="image" src="https://github.com/user-attachments/assets/45b1302d-a819-4b76-8bd8-923b2673d4c8" />

<img width="1316" height="467" alt="image" src="https://github.com/user-attachments/assets/957b70d9-389d-4539-ae59-6dcbaedca2e7" />

---

automated_etl - from visual to edit script mode

<img width="1347" height="581" alt="image" src="https://github.com/user-attachments/assets/8f2ae96e-852b-484a-b891-febbc38d5808" />
<img width="1316" height="559" alt="image" src="https://github.com/user-attachments/assets/ab0f4331-7aa8-4c6d-9452-ed594b36f390" />
<img width="1303" height="469" alt="image" src="https://github.com/user-attachments/assets/c3162f11-e8f0-4b4f-ad7a-4bf30d1b8df4" />

<img width="1298" height="549" alt="image" src="https://github.com/user-attachments/assets/5877b86f-1d17-48b5-9883-ca1593dcf18a" />

<img width="1336" height="634" alt="image" src="https://github.com/user-attachments/assets/f2e136b9-9601-4ded-8a43-0288157f5867" />
<img width="1362" height="575" alt="image" src="https://github.com/user-attachments/assets/e1f40dfc-16f6-43cc-a61e-9dd2c34b72a4" />

<img width="1317" height="567" alt="image" src="https://github.com/user-attachments/assets/ec5af104-57af-46d0-a45c-829b2153919e" />


<img width="1332" height="613" alt="image" src="https://github.com/user-attachments/assets/d7167f72-f1a4-4b83-9b37-00c0d2659c8b" />
<img width="1330" height="547" alt="image" src="https://github.com/user-attachments/assets/76f83772-2919-4795-ba08-f97057fd6a13" />
<img width="1162" height="455" alt="image" src="https://github.com/user-attachments/assets/f729b04e-5bdd-476f-a7dc-3e1206818269" />
<img width="1328" height="421" alt="image" src="https://github.com/user-attachments/assets/7cab7633-437a-4650-8715-903f3893004b" />
<img width="1195" height="469" alt="image" src="https://github.com/user-attachments/assets/74a6ef75-1db6-4614-8e72-8c25df895820" />

---
aws athena - adhoc in memory query db - can preview parquet files run query on s3 processed folder

<img width="1360" height="563" alt="image" src="https://github.com/user-attachments/assets/3540d3fc-06a1-4a5c-b11a-de3bc5e433d8" />

<img width="1040" height="520" alt="image" src="https://github.com/user-attachments/assets/8a91b2b2-2053-494c-84e1-346b32519540" />
<img width="1305" height="587" alt="image" src="https://github.com/user-attachments/assets/3260b3a9-41bc-43d8-9523-087fca05185c" />
<img width="1319" height="606" alt="image" src="https://github.com/user-attachments/assets/413aa586-2e74-4169-a4e0-622e55320f99" />

----
redshift db is serverless managed data warehouse for olap - columnar storage distributed computing - Load data s3 processed from parquet file to redshift 
