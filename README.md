# 🚀 Big Data Pipeline Orchestration with Apache Airflow

## 📌 Overview

This repository contains a containerized Apache Airflow environment demonstrating the orchestration of Big Data pipelines. It showcases Extract, Transform, Load (ETL) processes, sequential task dependencies, and parallel execution workflows using Python.

## 📂 Project Structure

The project provides three DAGs in the `dags/` directory:

### `mon_premier_dag.py` — Basic linear pipeline

A foundational DAG used to verify that tasks execute sequentially.

**Flow:** Start Pipeline ➔ Process Data ➔ End Pipeline

### `pipeline_big_data_python.py` — Sequential ETL pipeline

This pipeline simulates processing raw sales data through ingestion, raw-zone storage, schema validation, transformation, revenue aggregation, loading, and report generation.

### `pipeline_big_data_parallele.py` — Parallel processing pipeline

This pipeline simulates a student enrollment workflow. After validation and cleaning, department assignment and statistical analysis run in parallel before the final report is compiled.

## 🛠️ Technologies

- Apache Airflow 2.8.1
- Python and `PythonOperator`
- Docker and Docker Compose
- PostgreSQL 13

## 🚀 Getting Started

### Prerequisites

Install [Docker Desktop](https://www.docker.com/products/docker-desktop/), including Docker Compose.

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/othmaneelwahidi/big-data.git
   cd big-data
   ```

2. Start PostgreSQL and initialize the Airflow metadata database:

   ```bash
   docker compose up -d postgres
   docker compose run --rm airflow-webserver airflow db migrate
   ```

3. Create the local workshop administrator account:

   ```bash
   docker compose run --rm airflow-webserver airflow users create \
     --username airflow \
     --password airflow \
     --firstname Admin \
     --lastname Admin \
     --role Admin \
     --email admin@example.com
   ```

4. Start the Airflow services:

   ```bash
   docker compose up -d
   ```

5. Open <http://localhost:8080> and sign in with username `airflow` and password `airflow`.

Unpause a DAG in the Airflow interface, trigger it with the play button, and use the Graph and Logs views to inspect its execution.

> The credentials and secret key in this repository are intended only for a local workshop environment. Change them before using this configuration outside a local development machine.

## 🛑 Stopping the Environment

```bash
docker compose down
```

To also remove the PostgreSQL container data created by this Compose project:

```bash
docker compose down --volumes
```
