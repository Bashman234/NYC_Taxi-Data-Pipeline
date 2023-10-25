
# Building a Data Pipeline for NYC Taxi Data




## Overview

This is the New York taxi data engineering project! In this project, I aim to create a scalable and automated data pipeline to process and analyze New York taxi trip records from 2019-2020. The goal of this project is to build a reliable and efficient data infrastructure that can handle large volumes of taxi trip data. The taxi trip data used in this project was sourced from the New York City Taxi and Limousine Commission (TLC). The data set consists of millions of taxi trips spanning two years and includes information such as pickup and dropoff times, locations, fares, and payment methods.

#### Data Sets 
* [Yellow and Green Taxi Trip Records for 2019, 2020](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
* [Taxi Zone Maps and Lookup Tables](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
* [Taxi Zone Lookup Data](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)

## Tech Stack

* Google Cloud Platform
* Google Storage buckets as Data Lake
* Google Bigquery datasets as Data Warehouse
* Google Looker Studio reports for Data Visualization
* Google Compute Engine, if you use a VM on Google's Cloud Platform

* Terraform as Infrastructure as Code, to deploy Buckets and Datasets on Google Cloud Platform
* Python script is used to develop our pipeline from extraction to data ingestion
* Prefect as the orchestration tool
* dbt for some data quality testing, data modelling and transformation, and promotion of data to Production BigQuery dataset.

## Data Source 

| Data Set | Format | Description |
| ---      | ---    | ---         |
|[TLC Trip Record Data](https://travel.trade.gov/research/reports/i94/historical/2016.html)| Parquet | Yellow and green taxi trip records include fields capturing pick-up and drop-off dates/times, pick-up and drop-off locations, trip distances, itemized fares, rate types, payment types, and driver-reported passenger counts. The data used in the attached datasets were collected and provided to the NYC Taxi and Limousine Commission (TLC) by technology providers authorized under the Taxicab & Livery Passenger Enhancement Programs (TPEP/LPEP).
|[Taxi Zone Maps and Lookup Tables](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)| CSV | This dataset contains dimension information about the trip records that are being collected. The data used in the attached datasets were collected and provided to the NYC Taxi and Limousine Commission (TLC) by technology providers authorized under the Taxicab & Livery Passenger Enhancement Programs (TPEP/LPEP).|

## Architecture
## ETL Pipeline
## Dashboard
![images](https://github.com/Bashman234/NYC_Taxi-Data-Pipeline/blob/main/images/Screenshot%202023-10-25%20at%2015.10.21.png)
## Reproduciblity 

* cd to terraform run the commands below.

terraform init
terraform plan
terraform apply

* cd to workflow and run this command to run the ETL pipeline and monitor the Job in Prefect UI.

* prefect server start
python gcp/etl_web_gcs.py 

* For BigQuery Datawarehouse run the biq_query.sql to create tables in the datawarehouse and perform more advanced queries.

* To build and transform data using dbt cloud visit dbt_analytics folder and run the following commands

dbt run
dbt test

