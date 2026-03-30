Real-Time Crypto Data Streaming Pipeline (GCP)
A fully automated, end-to-end data engineering pipeline that streams live Bitcoin (BTC) market data from a local environment into Google Cloud Platform (GCP) for real-time analytics.

🏗️ Architecture Overview
This project demonstrates a modern "event-driven" architecture:
Data Producer (Local): A Python script fetches live BTC prices via the CoinDesk API.
Ingestion (Pub/Sub): The producer publishes JSON messages to a Google Cloud Pub/Sub Topic.
Processing (Cloud Run Functions): A serverless Python function is triggered by the Pub/Sub events, decodes the Base64 payload, and handles data transformation.
Storage (BigQuery): The processed data is streamed into a BigQuery table, making it immediately available for SQL analysis.

🛠️ Tech Stack
Language: Python 3.11

Cloud Provider: Google Cloud Platform (GCP)
Messaging: Google Cloud Pub/Sub
Compute: Google Cloud Run Functions (2nd Gen)
Data Warehouse: Google BigQuery
Authentication: Google Application Default Credentials (ADC)

📂 Project Structure
crypto_producer.py: The local Python script that acts as the data source.
main.py: The serverless function code deployed in GCP.
requirements.txt: Necessary Python libraries (google-cloud-pubsub, google-cloud-bigquery, requests).

🚀 Key Learning Milestones
Infrastructure as Code (Manual): Configured IAM roles, Service Accounts, and permissions (BigQuery Data Editor) to ensure secure communication between services.
Streaming vs Batch: Implemented low-latency streaming to move away from traditional batch-processing limitations.
Troubleshooting: Resolved complex 403 Access Denied errors and handled SQL data-type mismatches (String vs Float64) using advanced SQL casting.
