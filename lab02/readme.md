
# Lab 2: Developing and Deploying a REST API to Store Data on Cloud

## Overview

This laboratory exercise demonstrates how to develop and deploy a REST API on a cloud server using AWS EC2, FastAPI, and TinyDB. The API is designed to store and retrieve weather data (temperature and humidity) along with timestamps.

The project introduces cloud computing concepts for IoT applications and provides hands-on experience with API development and deployment.

---

## Objectives

* Launch and configure an AWS EC2 instance.
* Create and manage a Python virtual environment (venv).
* Install and configure FastAPI, Uvicorn, and TinyDB.
* Develop REST API endpoints using FastAPI.
* Store temperature and humidity data with timestamps.
* Test API functionality using HTTP GET and POST requests.
* Deploy the API on a cloud platform.

---

## Background Theory

### 1. Cloud Computing in IoT Systems

Cloud computing enables IoT devices to store, process, and access data remotely. It provides scalability, reliability, and real-time accessibility for sensor data.

### 2. AWS EC2 (Elastic Compute Cloud)

Amazon EC2 is a cloud computing service that allows users to launch virtual servers (instances) and deploy applications on the cloud.

### 3. REST API Architecture

REST (Representational State Transfer) is a web service architecture that enables communication between clients and servers using standard HTTP methods.

### 4. FastAPI Framework

FastAPI is a modern, high-performance Python framework used for building APIs. It supports automatic validation, documentation, and asynchronous processing.

### 5. TinyDB Database

TinyDB is a lightweight document-oriented database that stores data in JSON format, making it ideal for small-scale applications and educational projects.

### 6. HTTP Methods

#### GET

Used to retrieve data from the server.

Example:
GET /weather

#### POST

Used to send data to the server.

Example:
POST /weather

---

## System Requirements

* AWS Account
* Ubuntu EC2 Instance
* Python 3.8 or later
* FastAPI
* Uvicorn
* TinyDB
* Web Browser or API Testing Tool (Postman/cURL)

---

## Installation and Setup

### Step 1: Launch an AWS EC2 Instance

1. Log in to AWS Management Console.
2. Navigate to EC2 Dashboard.
3. Launch a new Ubuntu instance.
4. Configure Security Group:
   * HTTP (Port 80)

---

### Step 2: Update the Server

```bash
sudo apt update
sudo apt upgrade -y
```

---

### Step 3: Install Python and Virtual Environment

```bash
sudo apt install python3-pip python3-venv -y
```

Create a virtual environment:

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

---

### Step 4: Install Required Packages

```bash
pip install fastapi uvicorn tinydb
```

---


## Reference Code

```python
from fastapi import FastAPI
from tinydb import TinyDB
from datetime import datetime

app = FastAPI()

db = TinyDB("db.json")

@app.get("/")
def home():
    return {"message": "Weather API Running"}

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
def get_weather():
    return db.all()
```

---

## Running the Application

Start the FastAPI server:

```bash
uvicorn main:app --host 0.0.0.0 --port 80
```

The API will be accessible at:

```text
http://<EC2-Public-IP>:80
```

---

## API Endpoints

### Home Endpoint

**Request**

```http
GET /
```

**Response**

```json
{
  "message": "Weather API Running"
}
```

---

### Add Weather Data

**Request**

```http
POST /weather?temperature=28.5&humidity=65
```

**Response**

```json
{
  "status": "saved",
  "data": {
    "timestamp": "2026-06-04 12:30:00",
    "temperature": 28.5,
    "humidity": 65
  }
}
```

---

### Retrieve Weather Data

**Request**

```http
GET /weather
```

**Response**

```json
[
  {
    "timestamp": "2026-06-04 12:30:00",
    "temperature": 28.5,
    "humidity": 65
  }
]
```

---

## Testing the API

### Using Browser

Open:

```text
http://<EC2-Public-IP>:8000/docs
```

FastAPI automatically generates Swagger UI documentation.

### Using cURL

Add Weather Data:

```bash
curl -X POST "http://<EC2-Public-IP>:8000/weather?temperature=30&humidity=70"
```

Retrieve Data:

```bash
curl "http://<EC2-Public-IP>:8000/weather"
```

---

## Output

### Successful API Deployment

* FastAPI server runs on AWS EC2.
* Weather data is stored in TinyDB.
* Temperature and humidity values are saved with timestamps.
* Users can retrieve stored records through REST API endpoints.
* API documentation is accessible through Swagger UI.

---

## Conclusion

In this laboratory exercise, a cloud-hosted REST API was successfully developed and deployed using FastAPI on an AWS EC2 instance. TinyDB was used to store weather data, including temperature, humidity, and timestamps. The project demonstrated practical implementation of cloud computing concepts, RESTful web services, and database integration for IoT applications.
