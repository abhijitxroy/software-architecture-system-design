

# Data Warehouse

## What is Data Warehouse?

Data Warehouse is a centralized analytical storage system designed to store structured and processed data optimized for reporting, business intelligence and large scale analytics.

Unlike transactional databases, data warehouses are built for analytical queries across massive datasets.

Data warehouse supports:

- Business intelligence
- Reporting systems
- Historical analytics
- Dashboard systems
- Data analytics
- Enterprise decision making

---

## Why Data Warehouse?

Problems without data warehouse:

- Data scattered across systems
- Slow analytical queries on OLTP databases
- Difficult reporting workflows
- Inconsistent business metrics
- Poor historical analysis capability

Data warehouse improves:

- Query performance
- Centralized analytics
- Historical trend analysis
- Data consistency
- Enterprise reporting

---

## High Level Architecture

```text
+----------------+
| Data Sources   |
| Database       |
| CRM            |
| ERP            |
| API            |
+-------+--------+
        |
        v
+----------------+
| ETL / ELT      |
| Spark / Airflow|
+-------+--------+
        |
        v
+----------------+
| Data Warehouse |
| Snowflake      |
| Redshift       |
| BigQuery       |
+-------+--------+
        |
+-------+-------+
|               |
v               v
BI Tools      Analytics
Dashboard     Queries
```

---

## Core Components

### Data Sources

Input systems generating business data.

Examples:

- OLTP databases
- CRM systems
- ERP systems
- Event streams
- APIs

---

### ETL / ELT Layer

Moves and transforms data.

ETL:

```text
Extract
 → Transform
 → Load
```

ELT:

```text
Extract
 → Load
 → Transform
```

Examples:

- Airflow
- Spark
- dbt
- Informatica

---

### Storage Layer

Stores cleaned analytical datasets.

Examples:

- Snowflake
- Amazon Redshift
- BigQuery
- Azure Synapse

Requirements:

- High query performance
- Compression
- Scalability
- Partitioning

---

### Query Layer

Enables analytical access.

Examples:

- SQL engine
- BI dashboard
- Reporting tools

---

## Data Modeling Approaches

### Star Schema

Central fact table connected to dimension tables.

Example:

```text
         Customer
             |
Product -- Sales -- Date
             |
         Location
```

Advantages:

- Faster analytics
- Simple query model

---

### Snowflake Schema

Dimension tables normalized further.

Advantages:

- Reduced redundancy
- Better storage optimization

Disadvantages:

- Higher query complexity

---

## OLTP vs Data Warehouse

| Feature | OLTP | Data Warehouse |
|----------|------|----------------|
| Purpose | Transactions | Analytics |
| Data Type | Current Data | Historical Data |
| Query Type | Small Queries | Large Queries |
| Schema | Normalized | Denormalized |
| Optimization | Write Performance | Read Performance |

---

## Partitioning Strategy

Partitioning improves analytical performance.

Examples:

```text
Orders_2024
Orders_2025
Orders_2026
```

Strategies:

- Date partition
- Region partition
- Business unit partition

---

## Production Challenges

Common issues:

- Slow analytical queries
- Data freshness delays
- Schema evolution
- Data quality problems
- Storage growth

Solutions:

- Partitioning
- Compression
- Incremental loading
- Data validation
- Query optimization

---

## Production Examples

Examples:

- Enterprise reporting platform
- Financial analytics system
- Business intelligence platform
- Product analytics dashboard
- Customer analytics platform
- Executive reporting systems

---

## Interview Questions

1. What is Data Warehouse?

2. Data Warehouse vs Data Lake?

3. ETL vs ELT?

4. Star schema vs Snowflake schema?

5. OLTP vs OLAP?

6. Why partitioning is important?

---

## Quick Revision

- Data warehouse optimizes analytical workloads
- Historical data drives business analytics
- ETL transforms data before analytics
- ELT transforms data after loading
- Star schema improves analytical performance
- Partitioning improves scalability
- Data warehouse powers BI and reporting systems