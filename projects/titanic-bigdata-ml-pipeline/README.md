# Titanic Big-Data ML Pipeline

> An end-to-end big-data engineering and machine learning pipeline built on a production-style Hadoop/Spark stack using Docker.

---

## Overview

This project demonstrates how the tools used in real-world enterprise data engineering — Apache NiFi, HDFS, Hive, Apache Spark, and HBase — work together in a coordinated pipeline. Using the classic Titanic dataset as a vehicle, the pipeline ingests raw CSV data, transforms it through a distributed file system and query layer, trains a machine learning classifier, and writes model performance metrics to a NoSQL store.

While the Titanic dataset is familiar, the goal here is not the model itself — it is demonstrating that each layer of a big-data stack can be wired together reliably and repeatably inside a containerized environment that mirrors production infrastructure.

---

## Architecture

```
[GitHub CSV Source]
        |
        v
[Apache NiFi] --- InvokeHTTP --> GetFile --> PutHDFS
        |
        v
[HDFS] --- Raw data storage
        |
        v
[Apache Hive] --- CREATE EXTERNAL TABLE over HDFS
        |
        v
[Apache Spark ML] --- LogisticRegression classifier
        |
        v
[Apache HBase] --- Model metrics table
```

---

## Data

| File | Description |
|------|-------------|
| `titanic_custom.csv` | Modified Titanic passenger dataset hosted on GitHub |

**Key features used:**
- `Pclass` — passenger class (1st, 2nd, 3rd)
- `Sex` — gender (encoded)
- `Age` — age in years (imputed where missing)
- `SibSp` — number of siblings/spouses aboard
- `Parch` — number of parents/children aboard
- `Fare` — ticket price
- `Survived` — binary target (0 = did not survive, 1 = survived)

---

## Pipeline Components

### 1. Data Ingestion – Apache NiFi
- Built a NiFi flow using **InvokeHTTP** to pull `titanic_custom.csv` directly from a GitHub raw URL.
- Output routed through **PutHDFS** to write the file into a designated HDFS directory.
- Flow configured with error-handling connections and logging for observability.

### 2. Data Storage – HDFS
- Raw CSV stored in `/user/maria_dev/titanic/` on HDFS.
- File confirmed via HDFS CLI (`hdfs dfs -ls`) before downstream processing.

### 3. Query Layer – Apache Hive
- Created an **external Hive table** pointing to the HDFS directory:
  ```sql
  CREATE EXTERNAL TABLE titanic (
    PassengerId INT,
    Survived    INT,
    Pclass      INT,
    Name        STRING,
    Sex         STRING,
    Age         FLOAT,
    SibSp       INT,
    Parch       INT,
    Ticket      STRING,
    Fare        FLOAT,
    Cabin       STRING,
    Embarked    STRING
  )
  ROW FORMAT DELIMITED
  FIELDS TERMINATED BY ','
  STORED AS TEXTFILE
  LOCATION '/user/maria_dev/titanic/'
  TBLPROPERTIES ('skip.header.line.count'='1');
  ```
- Verified row counts and data types with HiveQL queries.

### 4. Machine Learning – Apache Spark ML
- Loaded the Hive table into a Spark DataFrame via `spark.sql()`.
- Applied feature preprocessing:
  - StringIndexer for `Sex`
  - Imputer for missing `Age` values
  - VectorAssembler to combine features
- Trained a **Logistic Regression** model using `pyspark.ml.classification.LogisticRegression`.
- Split: 80% training / 20% test.
- Evaluated with **BinaryClassificationEvaluator** (area under ROC).

### 5. Metrics Storage – Apache HBase
- Created HBase table `titanic_metrics` with column family `metrics`.
- Wrote model evaluation results (AUC, accuracy, timestamp) as a row in HBase using the HappyBase Python client.
- Verified storage with HBase shell `scan` command.

---

## Results

| Metric | Value |
|--------|-------|
| Model | Logistic Regression (Spark ML) |
| AUC (Area Under ROC) | ~0.84 |
| Training set size | ~712 records |
| Test set size | ~179 records |
| Feature count | 6 |

> Note: The Titanic dataset is small by big-data standards. The value of this project is in the pipeline architecture and tool integration, not the model performance itself.

---

## Environment & Setup

This pipeline runs inside the **Hortonworks Data Platform (HDP) Sandbox** Docker container, which bundles:

- HDFS (Hadoop Distributed File System)
- Apache NiFi
- Apache Hive
- Apache Spark
- Apache HBase
- Ambari (cluster management UI)

### Prerequisites

- Docker Desktop installed and running
- HDP Sandbox image pulled and started
- Port mappings: `4200` (NiFi), `8080` (Ambari), `8888` (Jupyter)

### Quick Start

```bash
# 1. Start the HDP Sandbox container
docker start sandbox-hdp

# 2. SSH into the container
ssh root@localhost -p 2222

# 3. Verify HDFS is running
hdfs dfs -ls /user/

# 4. Import the NiFi flow template (see nifi_flow/ folder)
# Navigate to http://localhost:4200/nifi

# 5. Run the Spark ML script
spark-submit titanic_model.py

# 6. Check HBase metrics
hbase shell
> scan 'titanic_metrics'
```

---

## Repository Structure

```
titanic-bigdata-ml-pipeline/
├── README.md                   # This file
├── data/
│   └── titanic_custom.csv      # Source dataset
├── nifi_flow/
│   └── titanic_ingest.xml      # Exported NiFi flow template
├── hive/
│   └── create_table.hql        # Hive DDL script
├── spark/
│   └── titanic_model.py        # PySpark ML training script
└── hbase/
    └── write_metrics.py        # HBase metric write script
```

---

## Future Work

- Extend the model to include ensemble methods (Random Forest, GBT) and compare AUC across classifiers.
- Add a Kafka streaming layer: simulate real-time passenger data arriving and score each record as it lands.
- Automate the full pipeline with Oozie or Airflow so it can run on a schedule without manual steps.
- Export model predictions back to HDFS/Hive for downstream dashboard consumption.

---

*Part of the [Data Science Portfolio](https://github.com/loganbap/data-science-portfolio) | Big-data engineering and machine learning pipeline project.*
