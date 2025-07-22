# Spotify_ETL_Pipeline_on_AWS-Python-

This project implements a serverless ETL (Extract, Transform, Load) pipeline to ingest and analyze data from the Spotify API using AWS cloud services.

## 📌 Overview

The ETL pipeline extracts music data from the Spotify API, transforms the raw data, and loads it into AWS Athena for analytics using the following services:

- **Amazon CloudWatch** for daily triggers
- **AWS Lambda** for extraction and transformation
- **Amazon S3** for raw and transformed data storage
- **AWS Glue** for schema inference and data cataloging
- **Amazon Athena** for querying and analysis

---

## 📊 Architecture Diagram

![ETL Diagram](./Screenshot%202025-07-21%20at%209.00.13 PM.png)

---

## ⚙️ Components Breakdown

### 🔹 Extract

- **Trigger**: Amazon CloudWatch triggers the ETL process daily.
- **Lambda Function**: Python script connects to the **Spotify API** to extract data.
- **Raw Data Storage**: Extracted JSON/CSV is stored in **Amazon S3 (raw)**.

### 🔹 Transform

- **Trigger**: Object creation in S3 triggers another Lambda function.
- **Lambda Function**: Transforms raw Spotify data into a structured format (e.g., flattening nested JSON).
- **Transformed Data Storage**: Processed data is stored in **Amazon S3 (transformed)**.

### 🔹 Load

- **AWS Glue Crawler**: Scans the transformed S3 bucket to infer schema and update the **AWS Glue Data Catalog**.
- **Amazon Athena**: Enables SQL queries on Spotify data using the cataloged schema.

---

