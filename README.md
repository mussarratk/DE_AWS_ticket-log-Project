# DE_AWS_ticket-log-Project
---
AWS Bucket S3 - Dir : careplus_datasql -- subdir --support-logs/ -- support tickets/ - raw/ - processed/

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

