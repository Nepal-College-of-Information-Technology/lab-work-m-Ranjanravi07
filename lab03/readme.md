# Lab 3: Visualizing IoT Sensor Data Using Interactive Dashboards

## Overview

This laboratory demonstrates how to retrieve weather sensor data from a REST API and visualize it through an interactive web dashboard. The dashboard provides both real-time and historical views of temperature and humidity data using graphical representations and tabular displays.

The application is developed using **FastAPI**, **TinyDB**, **HTML**, **JavaScript**, and **Chart.js**, and is deployed on an **AWS EC2 instance**.

---

## Objectives

1. Retrieve stored sensor data from the REST API developed in Lab 2.
2. Understand the importance of data visualization in IoT systems.
3. Develop a web-based dashboard to display sensor data.
4. Create real-time and historical visualizations of temperature and humidity data.
5. Deploy the dashboard on the AWS EC2 instance.
6. Analyze sensor trends using graphical representations.

---

## Background Theory

### Data Visualization in IoT

Data visualization transforms raw sensor readings into meaningful graphical representations, making it easier to monitor trends and analyze system behavior.

### API-Oriented Architecture

API-oriented architecture enables communication between different software components through RESTful APIs using HTTP methods.

### Dashboard Systems

Dashboards provide a centralized interface for displaying key information and sensor readings in real time.

### Designing Data Filters

Data filtering allows users to retrieve information for specific date and time ranges, making analysis more effective.

---

## Folder Structure

```text
/home/ubuntu/iot-lab
│
├── app.py
├── db.json
├── static
│   └── index.html
└── venv
    ├── bin
    ├── include
    ├── lib
    ├── lib64 -> lib
    └── pyvenv.cfg
```

---

## Procedure

### Step 1: Activate Virtual Environment

```bash
source venv/bin/activate
```

---

### Step 2: Install Required Packages

```bash
pip install fastapi uvicorn tinydb
```

---

### Step 3: Start the Server

```bash
uvicorn app:app --host 0.0.0.0 --port 8000
```

---

### Step 4: Open the Dashboard

Open a web browser and visit:

```text
http://<EC2-PUBLIC-IP>:8000/dashboard
```

---

## API Endpoints

### Home Endpoint

```http
GET /
```

Response:

```json
{
  "message": "Weather API Running"
}
```

---

### Add Weather Data

```http
POST /weather
```

Parameters:

* temperature
* humidity

Example:

```http
POST /weather?temperature=29.5&humidity=65
```

Response:

```json
{
  "status": "saved",
  "data": {
    "timestamp": "2025-06-01 12:30:00",
    "temperature": 29.5,
    "humidity": 65
  }
}
```

---

### Retrieve All Weather Data

```http
GET /weather
```

---

### Retrieve Filtered Data

```http
GET /weather?start=2025-05-28 00:00:00&end=2025-05-30 23:59:59
```

---

### Dashboard Endpoint

```http
GET /dashboard
```

Displays the interactive weather monitoring dashboard.

---

# Features

* Real-time temperature display.
* Real-time humidity display.
* Average temperature calculation.
* Average humidity calculation.
* Temperature trend visualization.
* Humidity trend visualization.
* Date and time filtering.
* Historical sensor data table.
* Interactive charts using Chart.js.

---

## Reference Code

### app.py

```python
from fastapi import FastAPI
from tinydb import TinyDB
from datetime import datetime
from fastapi.staticfiles import StaticFiles
from fastapi.responses import FileResponse

app = FastAPI()

app.mount("/static", StaticFiles(directory="static"), name="static")

db = TinyDB("db.json")

@app.get("/")
def home():
    return {"message": "Weather API Running"}

@app.get("/dashboard")
def dashboard():
    return FileResponse("static/index.html")

@app.post("/weather")
def add_weather(temperature: float, humidity: float):

    data = {
        "timestamp": datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
        "temperature": temperature,
        "humidity": humidity
    }

    db.insert(data)

    return {
        "status": "saved",
        "data": data
    }

@app.get("/weather")
def get_weather(start: str = None, end: str = None):

    data = db.all()

    if not start or not end:
        return data

    filtered = []

    for row in data:
        if start <= row["timestamp"] <= end:
            filtered.append(row)

    return filtered
```

---

## db.json

The database contains weather sensor readings collected over several days.

Each record contains:

* Timestamp
* Temperature
* Humidity

Example:

```json
{
    "timestamp":"2025-05-25 06:00:00",
    "temperature":19.8,
    "humidity":86
}
```

---

## Dashboard Components

### Sensor Summary Cards

* Current Temperature
* Current Humidity
* Average Temperature
* Average Humidity

### Graphs

#### Temperature Trend

Line chart displaying changes in temperature over time.

#### Humidity Trend

Line chart displaying changes in humidity over time.

### Data Filters

Users can select:

* Start Date
* End Date

to visualize data within a specific period.

### Data Table

Displays:

* Timestamp
* Temperature (°C)
* Humidity (%)

---

## Output

### Weather Monitoring Dashboard

The dashboard provides:

* Current sensor readings.
* Historical sensor records.
* Temperature trend chart.
* Humidity trend chart.
* Average values.
* Date-based filtering.

---

## Conclusion

In this experiment, an interactive IoT dashboard was successfully developed using FastAPI and Chart.js. The dashboard retrieves sensor data stored in TinyDB and presents it through graphical and tabular views. Date filtering and statistical summaries enable effective analysis of environmental conditions. The application demonstrates the practical integration of REST APIs, cloud computing, and data visualization techniques in IoT systems.

---

