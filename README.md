# POC-on-Slowly-Changing-Dimensions-using-Snowflake-
Implement Type 1 and Type 2 SCDs in Snowflake by leveraging Streams and Tasks.

## Project Description

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
  ### Implementation Flow :

  <img width="1265" height="658" alt="Screenshot 2025-09-17 at 3 00 32 AM" src="https://github.com/user-attachments/assets/03f4d419-d4cc-464d-a742-b0a3df5f3f5f" />


  
  
  
  
