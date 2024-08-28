# Amazon Black Friday Sales Insights: Real-time Projection and Near Real-time Analytics

## Overview

This project implements a robust ETL pipeline that enables real-time and near real-time analytics for Amazon Black Friday sales data. Utilizing AWS services such as DynamoDB, Kinesis, EventBridge, Lambda, Athena, and S3, the pipeline processes and analyzes sales data to provide valuable insights. The project is designed to efficiently handle change data capture (CDC) from DynamoDB Streams, allowing for real-time updates and projections.

## Features

- **Real-time Data Processing:** The pipeline captures and processes real-time data using DynamoDB Streams and Kinesis, ensuring up-to-date sales insights.
- **Near Real-time Analytics:** By integrating AWS Firehose and Athena, the system supports near real-time analytics, making it possible to analyze sales trends with minimal delay.
- **Optimized Data Transformation:** A custom data transformation layer, implemented via AWS Lambda, reduces data processing time by 40%, enabling quicker and more accurate analytics.

## Architecture

The architecture consists of the following components:

1. **DynamoDB:** The primary data store for sales data.
2. **DynamoDB Streams:** Captures changes in DynamoDB tables and sends them to Kinesis.
3. **Kinesis Data Stream:** Acts as the ingestion layer for real-time data processing.
4. **AWS Lambda:** Handles data transformation and preparation for further processing.
5. **AWS Firehose:** Delivers transformed data to S3 for long-term storage.
6. **S3:** Stores raw and processed data, enabling further analysis via Athena.
7. **Athena:** Provides an SQL interface to analyze the data stored in S3.
8. **EventBridge:** Manages the event-driven architecture, triggering Lambda functions for processing.

## Project Structure 
amazon-black-friday-sales-insights/
│
├── dynamodb/
│   └── mock_data_generator_for_dynamodb.py   # Script to generate mock data for DynamoDB
│
├── lambda/
│   └── transformation_layer_with_lambda.py   # Lambda function for data transformation
│
├── kinesis/
│   └── kinesis-to-s3-delivery-1-2024-02-16-05-43-56-3b663ffd-54cc-4c76-8f17-134c6f1376cb # Kinesis Firehose configuration
│
├── assets/
│   └── architecture_diagram.png              # Architecture diagram
│
└── README.md                                 # Project documentation

## Prerequisites

- **AWS Account:** Ensure you have an active AWS account.
- **Python 3.8+:** The scripts and Lambda functions are written in Python.
- **AWS CLI:** For managing AWS resources from the command line.

## Setup and Deployment

1. **DynamoDB Table Creation:**
   - Create a DynamoDB table with the appropriate schema for storing sales data.
   - Enable DynamoDB Streams on the table to capture changes.

2. **Deploy Lambda Function:**
   - Use the `transformation_layer_with_lambda.py` script to create a Lambda function.
   - Configure the Lambda function to be triggered by Kinesis Data Stream events.

3. **Configure Kinesis Data Stream:**
   - Set up a Kinesis Data Stream to ingest data from DynamoDB Streams.
   - Configure AWS Firehose to deliver data from Kinesis to an S3 bucket.

4. **Mock Data Generation:**
   - Use the `mock_data_generator_for_dynamodb.py` script to generate mock sales data and populate the DynamoDB table.

5. **Athena Setup:**
   - Set up Athena to query the processed data stored in S3.
   - Create the necessary tables and partitions in Athena.

6. **EventBridge Configuration:**
   - Configure EventBridge rules to trigger the Lambda function based on specific events.

## How It Works

1. **Data Ingestion:**
   - Sales data is ingested into DynamoDB. Any changes to the data (inserts, updates, deletes) are captured by DynamoDB Streams.

2. **Real-time Processing:**
   - DynamoDB Streams feed data into Kinesis, which triggers the Lambda function for transformation.

3. **Data Transformation:**
   - The Lambda function processes the incoming data, performing necessary transformations such as filtering, enrichment, and formatting.

4. **Data Delivery:**
   - Transformed data is delivered to an S3 bucket via AWS Firehose.

5. **Near Real-time Analytics:**
   - Data stored in S3 is queried using Athena, enabling near real-time insights into sales trends.

## Benefits

- **Efficiency:** The system reduces data processing time by 40%, allowing for faster insights and decision-making.
- **Scalability:** Built on AWS services, the solution can easily scale to handle large volumes of sales data.
- **Real-time Insights:** The integration of real-time and near real-time processing ensures that sales data is always up to date.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue if you have any suggestions or improvements.
