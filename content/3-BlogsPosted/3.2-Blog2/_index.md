---
title: "Blog 2"
date: 2024-07-07
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# Automating the Training of a Recommendation System with Amazon Personalize and AWS Glue

Personalizing the user experience always brings clear revenue growth for businesses. However, bringing Machine Learning (ML) into building a real-world Recommendation Engine is a major barrier. The combination of AWS Glue and Amazon Personalize offers a fully serverless architecture that automates data preparation and model training without having to build a complex Data Lake.

Below is a detailed breakdown of this approach:

## 1. Challenges in building a real-world recommendation system

When starting to implement personalization, organizations often run into the following technical barriers:

* **Data fragmentation:** In modern microservices systems, data is often scattered across many different sources (Relational DB, NoSQL, Data Warehouse). Collecting and synchronizing them takes a lot of effort.
* **Limitations of rule-based systems:** Many companies still use manual rules (rule-based) to recommend products. These systems are not very intelligent and are hard to maintain as the product catalog grows.
* **Lack of ML expertise:** Building, training, and optimizing recommendation algorithms requires a specialized team of Data Scientists, which not every business has on hand.

## 2. How do AWS Glue and Amazon Personalize solve the problem?

This architecture clearly separates the data processing flow from the AI training flow, making the most of fully-managed services:

* **Automated data integration (AWS Glue):** Acts as a serverless ETL service. AWS Glue Crawlers automatically scan the fragmented data sources to detect the schema. Then, Glue ETL Jobs (running on Apache Spark) clean, standardize, and export the data into CSV format stored in Amazon S3.
![alt](/images/blog1_fg2.png)

*Using AWS Glue to export datasets from heterogeneous data sources to Amazon S3.*


* **Automated ML training (Amazon Personalize):** Once the data converges in S3, Personalize takes over all the complex Machine Learning work. It automatically selects the most suitable algorithm based on three datasets: Interactions, Users, and Items.
![alt](/images/blog1_fg1.png)

*Amazon Personalize: from datasets to a recommendation API*


* **End-to-End Serverless architecture:** Both services scale automatically based on actual demand, completely removing the burden of server management for the engineering team.
![alt text](/images/blog1_fg3.png)

*A comprehensive architecture combining the data export process using AWS Glue, the MLOps training process, and Amazon Personalize.*

## 3. Key points to grasp

* **Smoothly solving the "Cold Start" problem:** By combining the required Interactions data with the Metadata of Users and Items, the system can make accurate recommendations even for brand-new customers or newly launched products.
* **Preventing data pipeline breakage:** The automatic schema update feature of the AWS Glue Data Catalog keeps the Data Pipeline from being interrupted when microservices teams change their database structures independently.
* **Providing a direct Inference API:** Amazon Personalize not only trains the model but also automatically packages and provides an Inference API so applications can call it and retrieve recommendation results in real time.

## 4. Value delivered to businesses

This architecture allows organizations to quickly deploy a Proof of Concept (POC) using their own existing historical data. It shortens time-to-market, optimizes operating costs, and helps businesses own an intelligent Recommendation Engine without having to invest in building a massive Data Lake or a large team of ML experts from the start.

## 5. Basic implementation and usage steps

To apply this solution to a real-world project, the general process includes the following steps:

* **Step 1 - Extract the data structure:** Use AWS Glue Crawlers to scan the current data sources (from S3, RDS, DynamoDB...) and automatically create metadata tables in the AWS Glue Data Catalog.
* **Step 2 - Transform and export the data:** Configure AWS Glue ETL Jobs (Python or Scala) to map the data columns to the exact format that Personalize requires. Then, export these CSV files into an Amazon S3 bucket.
* **Step 3 - Create a Dataset Group:** In Amazon Personalize, create a new Dataset Group and define the corresponding Schemas for the Interactions, Users, and Items datasets.
* **Step 4 - Train the model (Training):** Import the data from S3 into Personalize and proceed to create a Solution. The service automatically trains and fine-tunes the Machine Learning model.
* **Step 5 - Deploy the Endpoint:** Create a Campaign from the newly trained Solution. Personalize provides an API Endpoint so your application can integrate and query product recommendations immediately.

The figure below is an overview of the automated data flow and training process carried out in this article.

Link to the post on the AWS Study Group group: [AUTOMATING A RECOMMENDATION SYSTEM WITH AMAZON PERSONALIZE AND AWS GLUE](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2201959723902321/)