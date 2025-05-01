# Predictive Modeling of Penicillin Yield with Apache Spark & Azure Databricks

> **David Farrar** • S00261259 • S00261259@atu.ie  
> Industrial-scale Penicillin Simulation (IndPenSim) dataset • Based on Goldrick _et al._ (2015)

---

## Project Overview
This repository contains an end-to-end Big Data application that predicts penicillin concentration during fed-batch fermentation using Apache Spark on Azure Databricks. A 2.5 GB synthetic IndPenSim dataset was leveraged to demonstrate how distributed, in-memory processing and machine learning can yield real-time insights for biopharmaceutical manufacturing.

## Key Features
- **Scalable Data Ingestion & Preprocessing**  
  - Reads large CSVs (custom “|” delimiter) from Azure Data Lake Storage  
  - Handles missing/corrupt rows, casts types, and engineers 36 numeric & binary features  
- **Machine Learning Pipeline**  
  - Assembles features with Spark’s `VectorAssembler`  
  - Trains and evaluates three regressors:  
    - Random Forest (100 trees)  
    - Gradient-Boosted Trees (`maxIter=100`)  
    - Linear Regression (baseline & final deployer)  
  - Computes RMSE for each model in a unified pipeline  
- **Reproducible Training & Evaluation**  
  - 80/20 train/test split with fixed seed  
  - `evaluate_model()` helper prints RMSE for quick model comparison  
- **Interactive Dashboard (Databricks Notebook)**  
  - Batch selector for different fermentation runs  
  - Actual vs. predicted concentration plots  
  - RMSE comparison table and raw prediction logs  
- **Production-Ready Deployment**  
  - Final Linear Regression model logged to MLflow and saved under `/dbfs/models/`  
  - Ready for future Structured Streaming integration
