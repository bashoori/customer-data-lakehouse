# Customer Data Lakehouse ETL Pipeline

This project simulates a real-world data engineering scenario where customer, asset, and product lifecycle data are ingested from multiple sources, transformed, validated, and loaded into a unified analytics-ready data lakehouse.

The solution is designed to showcase modern data engineering practices using open-source tools like **Apache Airflow**, **PySpark**, **Delta Lake**, and **Python**.

---

## 🔍 Project Overview

**Goal:**  
Unify fragmented customer and asset data from internal databases, third-party APIs, and CSV files into a clean, reliable, and scalable data lakehouse system.

---

## 📊 Data Sources

| Source Type      | Description                                      |
|------------------|--------------------------------------------------|
| PostgreSQL        | Internal customer profiles and usage metrics     |
| REST API          | External warranty and lifecycle details          |
| CSV Files         | Weekly asset exports uploaded by teams           |

---

## ⚙️ Architecture
```
       +------------------+       +-----------------+
       |   PostgreSQL     |       |    API Source    |
       +------------------+       +-----------------+
               |                         |
        extract_postgres.py      extract_api.py
               |                         |
               +-----------+-------------+
                           |
                     [Raw Zone Storage]
                           |
                      ingest_csv.py
                           |
                    +-------------+
                    | Apache Airflow|
                    +-------------+
                           |
                 transform_assets_spark.py
                           |
                 [Delta Lake / SQLite Warehouse]
                           |
                 validate_data.py (Quality Checks)
                           |
                    Optional: Streamlit Dashboard
```
---

## 🧰 Tools & Technologies

- **Airflow** – Workflow orchestration
- **Python** – Ingestion scripts & API integration
- **PySpark** – Transformations and joins
- **Delta Lake** or **SQLite** – Storage (depending on local or cloud environment)
- **Great Expectations** – Data quality validation
- **Streamlit** – Optional interactive dashboard

---

## 🗂️ Repository Structure
```
customer-data-lakehouse/
├── dags/                      # Airflow DAGs
├── ingestion/
│   ├── extract_postgres.py
│   ├── extract_api.py
│   └── ingest_csv.py
├── transformation/
│   └── transform_assets_spark.py
├── data_quality/
│   └── validate_data.py
├── warehouse/
│   └── tables/
├── dashboard/
│   └── app.py
├── requirements.txt
├── README.md
└── architecture_diagram.png
```

---

## ✅ Key Features

- 🔄 Automated ETL pipeline using Airflow
- 🧹 Data standardization, schema alignment, and cleaning with PySpark
- ✔️ Data quality checks using custom validation rules
- 📦 Modular and scalable codebase ready for production deployment
- 📈 Optional dashboard to visualize final tables

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Apache Airflow
- Spark + Delta Lake
- PostgreSQL (local or hosted)
- Docker (optional for Airflow setup)

### Installation

```bash
# Clone the repo
git clone https://github.com/yourusername/customer-data-lakehouse.git
cd customer-data-lakehouse

# Set up Python environment
pip install -r requirements.txt

# Start Airflow (if using standalone setup)
airflow standalone
```
## 📌 Example Use Cases
	•	Unified view of customer health, asset age, and lifecycle status
	•	Early detection of expiring warranties
	•	Streamlined reporting for customer success and product teams


