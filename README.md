# Weather ETL Pipeline with Apache Airflow

This project implements an ETL (Extract, Transform, Load) pipeline using **Apache Airflow** to fetch, process, and store weather data from the **Open-Meteo API** into a **PostgreSQL** database.

---

## 🚀 Features
- **Extract**: Fetches current weather data using the Open-Meteo API.
- **Transform**: Processes and formats the weather data.
- **Load**: Stores the processed data into a PostgreSQL database.
- **Scheduled**: Automatically runs daily using Airflow's scheduler.

---

## 🛠️ Requirements
- Python 3.8+
- Apache Airflow
- PostgreSQL
- Required Python Packages:
  - `apache-airflow`
  - `apache-airflow-providers-http`
  - `apache-airflow-providers-postgres`
  - `requests`

---

## ⚙️ Installation & Setup

1. **Clone the Repository**
```bash
git clone <your-repo-url>
cd <project-directory>
```

2. **Create and Activate a Virtual Environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install Dependencies**
```bash
pip install -r requirements.txt
```

4. **Configure Airflow**
```bash
airflow db init
```

5. **Set Airflow Connections**
- **PostgreSQL Connection**:
```bash
airflow connections add 'postgres_default' \
    --conn-uri 'postgresql://username:password@localhost:5432/your_db'
```

- **HTTP API Connection**:
```bash
airflow connections add 'open_meteo_api' \
    --conn-type 'http' \
    --conn-host 'https://api.open-meteo.com'
```

6. **Start Airflow Scheduler and Webserver**
```bash
airflow scheduler &
airflow webserver --port 8080
```

7. **Access Airflow UI**
- Navigate to `http://localhost:8080` in your browser.

---

## 📄 DAG Structure
- **DAG ID**: `weather_etl_pipeline`
- **Schedule**: Runs daily

### Tasks:
1. `extract_weather_data`: Fetches weather data from the API.
2. `transform_weather_data`: Processes and formats the fetched data.
3. `load_weather_data`: Loads the transformed data into PostgreSQL.

---

## 📊 Database Schema
```sql
CREATE TABLE IF NOT EXISTS weather_data (
    latitude FLOAT,
    longitude FLOAT,
    temperature FLOAT,
    windspeed FLOAT,
    winddirection FLOAT,
    weathercode INT,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## ✅ Running the DAG
- Enable the DAG in the Airflow UI.
- Trigger the DAG manually or let it run as per the defined schedule.

---

## 📚 API Reference
- **Open-Meteo API**: [https://open-meteo.com](https://open-meteo.com)

---

## 🔄 Updating the Pipeline
- Modify the DAG file as required.
- Restart the Airflow services if necessary.

---

## 🐞 Troubleshooting
- Check Airflow logs for detailed error messages.
- Verify connection configurations in the Airflow UI.
- Ensure PostgreSQL is running and accessible.

---

## 📃 License
This project is licensed under the MIT License.

---

## 🙌 Acknowledgements
- [Apache Airflow](https://airflow.apache.org/)
- [Open-Meteo API](https://open-meteo.com)
- [PostgreSQL](https://www.postgresql.org/)

---

## 📬 Contact
For any queries, contact me at sudheermsdvk@gmail.com.
