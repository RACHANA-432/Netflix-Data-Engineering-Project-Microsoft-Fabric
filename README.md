# Netflix Data Engineering Project using Microsoft Fabric

## Project Overview

This project demonstrates an **end-to-end data engineering pipeline** built using Microsoft Fabric. The pipeline ingests raw Netflix dataset from Azure Data Lake Storage (ADLS), processes it using PySpark notebooks, and implements **Medallion Architecture (Bronze, Silver, Gold)**.

---

## Architecture

```
ADLS (Netflix Dataset)
        ↓
Fabric Data Pipeline (Copy Activity)
        ↓
Lakehouse - Bronze Layer (Raw Files)
        ↓
Notebook (PySpark Transformations)
        ↓
Lakehouse - Silver Layer (Cleaned Data)
        ↓
Lakehouse - Gold Layer (Aggregated Data)
        
```

---

## Tech Stack

* Microsoft Fabric (Data Pipeline, Lakehouse, Notebook)
* Azure Data Lake Storage (ADLS Gen2)
* PySpark
* Delta Lake

---

## 📂 Data Source

Netflix dataset containing:

* Title
* Type (Movie/TV Show)
* Director
* Cast
* Country
* Date Added
* Release Year
* Rating
* Duration
* Genre

---

## Medallion Architecture

### Bronze Layer

* Raw data ingested from ADLS using **Copy Activity**
* Stored in Lakehouse Files as **binary format**
* Path:

  ```
  Files/netflix/bronze/netflix_titles.csv
  ```

---

### Silver Layer

* Data cleaning and transformation using PySpark:

  * Removed duplicates
  * Handled missing values
  * Converted date formats
  * Standardized columns
* Stored as Delta table:

  ```
  Tables/silver_netflix
  ```

---

### Gold Layer

* Business-level aggregations created:

  * Content distribution (Movies vs TV Shows)
  * Country-wise content
  * Year-wise trend
  * Rating distribution

Tables:

```
Tables/gold_content_type
Tables/gold_country
Tables/gold_yearly_trend
Tables/gold_rating
```

---

## Data Pipeline

### Activities:

1. **Copy Data Activity**

   * Source: ADLS (Netflix dataset)
   * Destination: Lakehouse Bronze layer

2. **Notebook Activity**

   * Performs transformation and loads Silver & Gold layers

### Features:

* Orchestrated workflow
* End-to-end automation
* Scalable processing

---

## Logging & Monitoring

A custom logging framework is implemented in the notebook to track pipeline execution.

### Log Table:

```
Tables/pipeline_logs
```

### Captured Details:

* Pipeline name
* Step name
* Status (SUCCESS / FAILED)
* Row count
* Message
* Timestamp

### Benefits:

* Easy debugging
* Execution tracking
* Production-level monitoring

---

## Key Learnings

* Implemented Medallion Architecture in Fabric
* Built end-to-end pipeline with orchestration
* Worked with Delta Lake for efficient storage
* Designed logging mechanism for monitoring
  
---

## Challenges Faced

* Handling ADLS authentication and permissions
* Managing file formats during ingestion (Binary vs CSV)
* Debugging Spark session delays
* Correctly configuring Lakehouse connections

---

## Future Enhancements

* Incremental data loading
* Data quality validation checks
* Partitioning for performance optimization
* Parameterized pipelines
* Alerting mechanism for failures

---

## Conclusion

This project showcases a complete data engineering workflow from raw data ingestion to business insights, leveraging modern cloud tools and best practices.

---

## Author

Rachana Chavan

