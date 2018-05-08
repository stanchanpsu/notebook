# Big Data

## Lifecycle of Big Data

1. Ingest
2. Store
3. Process & Analyze
4. Explore & Visualize

## Cloud IOT Core

* Fully-managed service to connect, manage, and ingest data from IOT devices
* Device Manager handles device identity, authentication, config & control
* Protocol Bridge publishes incoming telemetry to Cloud Pub/Sub for processing
* Connect securely using IoT industry standard MQTT or HTTPS protocols
* CA signed certificates can be used to verify device ownership on first connect
* two-way device communication enables configuration & firmware updates
* device shadows enable querying & making control changes while devices are offline
* pay per MB of data exchanged with devices

## Cloud Pub/Sub (SNS, SQS)

* Infinitely-scalable at-least-once messaging for ingestion, decoupling, etc
* Global by default. Publish and consume from anywhere with consistent latency
* Messages can be up to 10MB and undelivered ones stored for 7 days. But no Dead Letter Queue
* Push mode delivers to HTTPS endpoint & succeeds on HTTP success status code
    * slow start - algorithm ramps up on success and backs off & retries, on failures
* pull mode delivers messages to requesting clients and waits for acknowledgment to delete
    * lets clients set rate of consumption, supports batching and long-polling
* pay for data volume. minimum 1KB per publish/push/pull request

## Cloud Dataprep

* Visually explore, clean, and prepare data for analysis without running servers
* This is a Data Wrangler for business analysts not IT pros
* Managed version of Trifacta Wrangler - managed by Trifacta not Google
* Source data from GCS, BQ, or file upload - formatted in CSV and JSON, or relational
* Automatically detects schemas, datatypes, possible joins, and various anomalies
* pay for underlying dataflow job, plus management overhead charge
* pay for other accessed services

## Cloud Dataproc (AWS EMR)

* Batch MapReduce processing via configurable, managed Spark & Hadoop clusters
* Handles being told to scale (adding or remove nodes) even while running jobs
* Integrated with GCS, BQ, BigTable and some stackriver services
* Image Versioning - switch between versions of Spark, Hadoop, & other tools
* pay directly for underlying GCE servers used in cluster
* pay a Cloud Dataproc mangement fee per vCPU-hour in the cluster
* best for moving existing spark/hadoop setups to GCP

## Cloud Dataflow

* Smartly-autoscaled & fully-managed batch or stream MapReduce-like processing
* Released as open-source Apache Beam
* autoscales & dynamically redistributes lagging work, mid-job, to optimize run time
* integrated with cloud pub/sub, datastore, BQ, Bigtable, Cloud ML, Stackdriver
* dataflow shuffle service for batch offloads Shuffle ops from workers for big gains
* Pay for underlying worker GCE via consolidated charges
    * pay per second for vCPUs, RAM GBs PD/PD-SSD (more for streaming)
* dataflow shuffle charged for time per GB used

## Cloud Datalab

* Interactive tool for data exploration, analysis, visualizaion and machine learning
* Uses Jupyter Notebook
* Supports Iterative development of data analysis algorithms in Python
* Pay for GCE/GAE instancing hosting and storing notebooks
* pay for any other resources accessed (BigQuery)

## Cloud Data Studio

* Big Data Visualization tool for dashboards and reporting
* meaningful data stories/presentations enable better business decision making
* many sources and visualizations
* templates for quick start; customization options for impactful finish
* Collaborate and share in real time
* pay for services accessed

## Cloud Genomics

* Store and process genomes and related experiments
* query complete genomic information of large research projects in seconds
* process many genomes and experiments in parallel
* open industry standard
* supports requestor pays