# Data Lake

## What is Data Lake?

Data Lake is a centralized storage system designed to store large volumes of structured, semi-structured and unstructured data at any scale.

Unlike traditional databases or data warehouses, data lakes store raw data before transformation.

Data lake supports:

- Batch analytics
- Machine Learning
- Streaming analytics
- Big data processing
- Data science workloads
- Business intelligence

---

## Why Data Lake?

Problems without data lake:

- Data stored across multiple silos
- Expensive storage systems
- Difficult large scale analytics
- Limited support for unstructured data
- Data duplication problems

Data lake improves:

- Scalability
- Cost optimization
- Centralized storage
- Flexible analytics
- Machine learning support

---

## High Level Architecture

```text
+----------------+
| Data Sources   |
| API            |
| Database       |
| Logs           |
| IoT            |
+-------+--------+
        |
        v
+----------------+
| Ingestion      |
| Kafka / ETL    |
+-------+--------+
        |
        v
+----------------+
| Data Lake      |
| S3 / ADLS      |
| GCS            |
+-------+--------+
        |
+-------+-------+
|               |
v               v
Analytics     ML Platform
```

---

## Data Types

### Structured Data

Examples:

- Relational database tables
- CSV files

---

### Semi Structured Data

Examples:

- JSON
- XML
- Event logs

---

### Unstructured Data

Examples:

- Images
- Videos
- Audio
- Documents

---

## Core Components

### Storage Layer

Stores raw data.

Examples:

- Amazon S3
- Azure Data Lake Storage
- Google Cloud Storage
- HDFS

Requirements:

- Durable storage
- Scalability
- Cost efficiency

---

### Data Ingestion

Moves data into lake.

Methods:

- Batch ingestion
- Streaming ingestion

Examples:

- Kafka
- Spark
- Flink
- ETL pipeline

---

### Metadata Catalog

Maintains dataset information.

Examples:

- AWS Glue Catalog
- Hive Metastore

Metadata includes:

- Schema
- Ownership
- Table definition
- Data lineage

---

### Processing Layer

Processes large datasets.

Examples:

- Spark
- Flink
- Presto
- Hive

---

## Data Lake Zones

### Raw Zone

Stores original source data.

Example:

```text
/customer/raw/
/orders/raw/
```

---

### Processed Zone

Contains cleaned and transformed data.

Example:

```text
/customer/processed/
/orders/processed/
```

---

### Curated Zone

Business ready datasets.

Example:

```text
/customer/gold/
/revenue/gold/
```

---

## Data Lake vs Data Warehouse

| Feature | Data Lake | Data Warehouse |
|----------|------------|----------------|
| Schema | Schema on Read | Schema on Write |
| Data Type | All Data Types | Structured Data |
| Storage Cost | Lower | Higher |
| Analytics | Flexible | BI Focused |
| Processing | Raw Data | Processed Data |

---

## Production Challenges

Common issues:

- Data quality issues
- Data swamp problem
- Metadata inconsistency
- Large scale governance
- Access control complexity

Solutions:

- Data catalog
- Data quality validation
- Governance framework
- Access policy management

---

## Production Examples

Examples:

- Enterprise analytics platform
- Recommendation systems
- AI training pipeline
- Fraud analytics
- Data science platform
- Real time analytics

---

## Interview Questions

1. What is Data Lake?

2. Data Lake vs Data Warehouse?

3. What is schema on read?

4. Why metadata catalog is important?

5. What is data swamp?

6. Raw vs processed vs curated zone?

---

## Quick Revision

- Data lake stores raw structured and unstructured data
- Data lake supports machine learning and analytics
- Schema on read provides flexibility
- Metadata improves discoverability
- Data lake zones separate raw and processed data
- Data quality prevents data swamp problems
- Data lake enables large scale analytics
