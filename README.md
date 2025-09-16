# POC-on-Slowly-Changing-Dimensions-using-Snowflake-
Implement Type 1 and Type 2 SCDs in Snowflake by leveraging Streams and Tasks.

## Project Description

This project involves building a comprehensive data pipeline in a modern data warehouse environment using **Snowflake**. The goal is to demonstrate the implementation of **Slowly Changing Dimensions (SCDs)**, specifically **Type 1 and Type 2**, to track historical data changes.

### Tech Stack and Data Flow

The data pipeline utilizes the following technologies and a specific flow:

* **Data Generation:** Synthetic user data is created using the **Faker** library and stored as timestamped CSV files.
* **Ingestion:** **Apache NiFi** streams this data into an **Amazon S3** bucket.
* **Data Loading:** **Snowpipe** automates the loading of data from S3 into a staging table in **Snowflake**.
* **SCD Logic:** The core of the project uses **Snowflake Streams, Tasks, and Stored Procedures** to dynamically apply the SCD Type 1 and Type 2 logic, updating records or preserving historical versions as needed.

The pipeline is designed to simulate real-world data warehousing scenarios using a mix of Python, Apache NiFi, Docker, and various cloud services.

---

### Data Warehousing Fundamentals
* **Facts:** A fact is a piece of numerical data, such as a sale or a click. Facts are stored in **fact tables**.
* **Dimensions:** Dimensions are companion tables that provide descriptive features for the facts, such as customer, geography, or employee data. They are linked to fact tables via foreign keys.
* **Dimension Attributes:** These are the columns within a dimension table that provide the descriptive features.

---

### Slowly Changing Dimensions (SCD)
* SCD is a method for maintaining both current and historical data over time within a data warehouse.
* It is considered a crucial part of the ETL (Extract, Transform, Load) process for monitoring the history of dimension records.
* **Project Context:** This project uses the **Snowflake Data Warehouse** to implement and support various types of SCDs.

---

### Types of Slowly Changing Dimensions
* **Type 0 (Passive):** No specific action is taken when dimensions change. Some data may be kept as is, while other parts may be updated.
* **Type 1 (Overwrite):** The new data overwrites the old data. History is not preserved, as the original data is lost. This is the most common SCD type.
* **Type 2 (Historical):** The complete history is preserved. When a value changes, the existing record is "closed" and a new record is created with the updated values. Each record is tracked using effective and expiry dates.
* **Type 3 (Previous Value):** Two copies of a value are maintained for selected attributes: the current value and the previous value, both stored in the same record. When a change occurs, the current value is updated, and the previous value is saved in a new column.

  ---
### Use Case Summary

This project demonstrates a cloud-native **ETL (Extract, Transform, Load)** pipeline built on **AWS** and **Snowflake**. The core purpose is to simulate and process **Slowly Changing Dimension (SCD)** data for customers, specifically tracking changes and preserving a historical record.

The system supports real-time data ingestion and is designed for use cases such as:
* Assessing creditworthiness.
* Generating personalized recommendations.
* Ensuring regulatory compliance.

### Real-World Example

A retail bank uses this system to capture periodic snapshots of customer profiles (e.g., name, income, address). The pipeline detects changes over time and applies **SCD logic** to maintain a versioned history in Snowflake. This historical data is then used for:
* Customer segmentation.
* Risk scoring.
* Personalized credit offers.
* Maintaining an auditable data trail.

  ---
  ---

  ### Key Features of the Project

* **Slowly Changing Dimensions (SCD):** The project implements both **SCD Type 1** (overwriting old data for real-time updates) and **SCD Type 2** (preserving historical records for auditing and trend analysis).

* **Automated ETL Pipeline:** This is a fully automated, end-to-end data pipeline. It handles everything from data generation using **Faker** to loading into **Snowflake**, with minimal manual intervention.

* **Hybrid Cloud Integration:** The system integrates services from multiple cloud platforms, including **AWS (S3, EC2)** and **Snowflake**, demonstrating interoperability between different cloud environments.

* **Orchestration and Containerization:** The pipeline is orchestrated using **Apache NiFi** and uses **Docker** for containerization, which ensures consistency and portability.

* **Schema-Driven Data Handling:** The architecture is based on a **dimensional model**, which cleanly separates transactional data (facts) from descriptive data (dimensions) to enable scalable analytical queries.

* **Real-Time and Batch Support:** The pipeline is designed to handle both **streaming (near real-time)** and **batch** data, making it suitable for a wide range of analytical and reporting use cases.

  ---
  
### DataPipeline:
A data pipeline is a system designed to automate the movement and processing of data from one system to another.

<img width="1091" height="632" alt="Screenshot 2025-09-17 at 3 02 08 AM" src="https://github.com/user-attachments/assets/2d0b7dc0-9287-403e-9387-74230239175d" />



Here are the key functions of a data pipeline:

* **Extraction:** Data is captured or extracted from various sources, which can be done in either real-time (streaming) or in batches.
* **Storage & Validation:** The extracted data is stored in a raw format before it is cleaned and validated.
* **Transformation:** The data is transformed into a clean, structured, and **query-worthy format**, making it ready for analysis.
* **Visualization:** The processed data is used to create dashboards and reports for visualizing **Key Performance Indicators (KPIs)**.
* **Orchestration:** The entire end-to-end process—from ingestion to final reporting—is managed and automated by an **orchestration** tool.

  ---
### Dataset Description:

In this project, we use the faker library from Python to generate records of users and store the records in CSV format with the name, including the current system time.

The data includes the following parameters:

* Customer_id

* First_name

* Last_name

* Email

* Street

* State

* Country

  ---

### Tech Stack

This project leverages a modern and robust tech stack for data processing and infrastructure management.

#### **Languages**
* **Python3:** Used for scripting, data processing, and backend logic.
* **JavaScript:** Employed for front-end development or API interactions.
* **SQL:** Essential for querying and managing relational data within the data warehouse.

#### **Tools & Services**
* **Apache NiFi:** Utilized for building and automating data flow pipelines.
* **Amazon S3:** Serves as a highly scalable and durable object storage for raw and processed data.
* **Snowflake:** Our cloud data warehouse for data storage, transformation, and analytics.
* **Amazon EC2:** Provides scalable compute capacity for deploying applications and services.
* **Docker:** Used for containerization to ensure consistent and portable application deployment.

  ---
  ### WorkFlow :

  <img width="1265" height="658" alt="Screenshot 2025-09-17 at 3 00 32 AM" src="https://github.com/user-attachments/assets/03f4d419-d4cc-464d-a742-b0a3df5f3f5f" />


This project implemented a **Slowly Changing Dimension (SCD)** data pipeline using a hybrid cloud architecture. The pipeline automates the ingestion, transformation, and management of data changes within a **Snowflake** data warehouse.

The workflow is as follows:

* **Setup:** An **Amazon EC2** instance was set up to host **Apache NiFi** and **Jupyter Notebooks** in **Docker** containers, creating a portable environment for orchestration and scripting.
* **Data Ingestion:** Source data from CSV files and mock APIs was ingested by **NiFi** and then moved into an **Amazon S3** bucket, which served as an intermediate data lake.
* **Data Transformation:** **Jupyter Notebooks** with SQL and Python were used to clean and prepare the data. The processed data was then loaded into Snowflake staging tables.
* **SCD Implementation:** Both **SCD Type 1** (overwriting data) and **SCD Type 2** (preserving historical records) were implemented in Snowflake. The logic uses **Streams and Tasks** to automatically track and capture data changes, ensuring that the correct updates and inserts are performed on the dimension tables.


  
  
  
  
