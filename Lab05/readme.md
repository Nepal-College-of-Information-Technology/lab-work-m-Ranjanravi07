<<<<<<< HEAD
# Lab: Integrating ESP32 Ultrasonic Sensor Data with Cloud-Based REST API and Dashboard Visualization

## Title

**Integrating ESP32 Ultrasonic Sensor Data with Cloud-Based REST API and Dashboard Visualization**

---

# Objectives

1. Interface the HC-SR04 ultrasonic sensor with the ESP32 or ESP8266.
2. Measure the distance of an object using the ultrasonic sensor.
3. Display the measured distance on the Serial Monitor.
4. Review the REST API developed and deployed on the AWS EC2 instance in Lab 2.
5. Transmit distance measurements from the ESP32 to the cloud using the REST API over the AWS EC2 public IPv4 address.
6. Store the uploaded distance data in the cloud database.
7. Retrieve the stored sensor data through the REST API.
8. Visualize real-time and historical distance measurements using the dashboard developed in Lab 3.
9. Understand the complete IoT data flow from sensor acquisition to cloud storage and dashboard visualization.

---

# Background Theory

## ESP32 Microcontroller

The ESP32 is a powerful, low-cost microcontroller developed by Espressif Systems with built-in Wi-Fi and Bluetooth connectivity. It is widely used in Internet of Things (IoT) applications because it can interface with various sensors and communicate with cloud servers through wireless networks.

In this laboratory, the ESP32 reads distance measurements from the HC-SR04 ultrasonic sensor and sends the collected data to a REST API hosted on an AWS EC2 instance.

---

## HC-SR04 Ultrasonic Sensor

The HC-SR04 is a non-contact distance measuring sensor that uses ultrasonic sound waves to determine the distance between the sensor and an object.

### Specifications

- Operating Voltage: 5V
- Measuring Range: 2 cm to 400 cm
- Accuracy: ±3 mm
- Measuring Angle: Approximately 15°
- Trigger Pulse: 10 µs

The sensor works by transmitting an ultrasonic pulse through the Trigger pin and measuring the time required for the echo to return to the Echo pin. The ESP32 calculates the distance using the speed of sound.

---

## Distance Measurement

The distance is calculated using the following equation:

```
Distance = (Time × Speed of Sound) / 2
```

Where:

- Speed of Sound = 343 m/s
- Time = Duration of the Echo pulse

The division by two accounts for the sound wave traveling to the object and back.

---

## Sensor Data Acquisition

Sensor data acquisition is the process of collecting measurements from physical sensors.

In this experiment:

1. The ultrasonic sensor emits ultrasonic waves.
2. The reflected signal is received by the Echo pin.
3. The ESP32 measures the pulse duration.
4. The distance is calculated and prepared for cloud transmission.

---

## Serial Communication

Serial communication enables the ESP32 to send measured values to a computer through USB.

The Arduino IDE Serial Monitor is used to:

- Display measured distance
- Verify sensor functionality
- Display HTTP response messages
- Debug communication errors

Example output:

```
Distance: 45.62 cm
HTTP Response Code: 200
Data uploaded successfully.
```

---

## REST API Communication

REST (Representational State Transfer) is a web service architecture that enables communication between devices over HTTP.

The ESP32 sends distance measurements to the cloud using HTTP requests.

The REST API receives sensor data, stores it in the database, and provides endpoints for retrieving stored records.

Typical endpoints include:

- POST `/sensor-data`
- GET `/sensor-data`

---

## HTTP POST and GET Methods

### HTTP POST

The POST method uploads sensor readings to the server.

Example JSON:

```json
{
  "distance": 45.62
}
```

---

### HTTP GET

The GET method retrieves previously stored sensor readings from the cloud database for dashboard visualization.

---

## Cloud Data Storage on AWS EC2

Amazon EC2 provides a virtual server for hosting the REST API and database.

The uploaded distance measurements are stored in the cloud database, enabling secure and centralized storage for future retrieval and analysis.

---

## API Integration with Embedded Systems

The ESP32 integrates with the cloud REST API using its built-in Wi-Fi module.

The workflow is:

- Connect to Wi-Fi
- Measure distance
- Create JSON payload
- Send HTTP POST request
- Receive server response
- Repeat periodically

This enables remote monitoring from anywhere with internet access.

---

## IoT Data Flow

The overall IoT system follows this sequence:

```
HC-SR04 Sensor
        │
        ▼
     ESP32
        │
        ▼
   Wi-Fi Network
        │
        ▼
 AWS EC2 REST API
        │
        ▼
 Cloud Database
        │
        ▼
 Web Dashboard
        │
        ▼
   User Monitoring
```

---

## Dashboard-Based Data Visualization

The dashboard developed in Lab 3 retrieves the stored distance measurements from the REST API and presents them graphically.

Features include:

- Real-time distance updates
- Historical distance records
- Interactive charts
- Sensor monitoring dashboard
- Remote data visualization

---

# Procedure

1. Connect the HC-SR04 ultrasonic sensor to the ESP32.
2. Upload the program to measure distance using the ultrasonic sensor.
3. Verify the measured distance using the Serial Monitor.
4. Review the REST API deployed on the AWS EC2 instance in Lab 2.
5. Configure the ESP32 with the Wi-Fi credentials and the REST API endpoint (AWS EC2 public IPv4 address).
6. Modify the ESP32 program to send distance measurements to the REST API using HTTP POST requests.
7. Upload the modified program to the ESP32.
8. Verify that the sensor data is successfully stored in the cloud database.
9. Access the dashboard developed in Lab 3.
10. Observe the uploaded distance measurements on the dashboard through graphical visualizations.
11. Analyze the recorded distance trends displayed on the dashboard.

---

# Output

- Successful acquisition of distance measurements from the HC-SR04 ultrasonic sensor.
- Distance readings displayed on the Serial Monitor.
- Successful transmission of sensor data from the ESP32 to the AWS EC2 REST API.
- Distance data stored in the cloud database.
- Distance measurements successfully displayed on the web dashboard.
- Real-time and historical graphs showing uploaded sensor data.

---

# Conclusion

In this laboratory, the ESP32 was successfully interfaced with the HC-SR04 ultrasonic sensor to measure the distance of nearby objects. The measured values were verified through the Serial Monitor and transmitted to a cloud-based REST API hosted on an AWS EC2 instance. The uploaded sensor data was stored in the cloud database and visualized using the dashboard developed in the previous lab. This experiment demonstrated the complete end-to-end IoT workflow, including sensor data acquisition, cloud communication, cloud storage, and remote monitoring through a web-based dashboard.
=======
# Lab: Integrating ESP32 Ultrasonic Sensor Data with Cloud-Based REST API and Dashboard Visualization

## Title

**Integrating ESP32 Ultrasonic Sensor Data with Cloud-Based REST API and Dashboard Visualization**

---

# Objectives

1. Interface the HC-SR04 ultrasonic sensor with the ESP32 or ESP8266.
2. Measure the distance of an object using the ultrasonic sensor.
3. Display the measured distance on the Serial Monitor.
4. Review the REST API developed and deployed on the AWS EC2 instance in Lab 2.
5. Transmit distance measurements from the ESP32 to the cloud using the REST API over the AWS EC2 public IPv4 address.
6. Store the uploaded distance data in the cloud database.
7. Retrieve the stored sensor data through the REST API.
8. Visualize real-time and historical distance measurements using the dashboard developed in Lab 3.
9. Understand the complete IoT data flow from sensor acquisition to cloud storage and dashboard visualization.

---

# Background Theory

## ESP32 Microcontroller

The ESP32 is a powerful, low-cost microcontroller developed by Espressif Systems with built-in Wi-Fi and Bluetooth connectivity. It is widely used in Internet of Things (IoT) applications because it can interface with various sensors and communicate with cloud servers through wireless networks.

In this laboratory, the ESP32 reads distance measurements from the HC-SR04 ultrasonic sensor and sends the collected data to a REST API hosted on an AWS EC2 instance.

---

## HC-SR04 Ultrasonic Sensor

The HC-SR04 is a non-contact distance measuring sensor that uses ultrasonic sound waves to determine the distance between the sensor and an object.

### Specifications

- Operating Voltage: 5V
- Measuring Range: 2 cm to 400 cm
- Accuracy: ±3 mm
- Measuring Angle: Approximately 15°
- Trigger Pulse: 10 µs

The sensor works by transmitting an ultrasonic pulse through the Trigger pin and measuring the time required for the echo to return to the Echo pin. The ESP32 calculates the distance using the speed of sound.

---

## Distance Measurement

The distance is calculated using the following equation:

```
Distance = (Time × Speed of Sound) / 2
```

Where:

- Speed of Sound = 343 m/s
- Time = Duration of the Echo pulse

The division by two accounts for the sound wave traveling to the object and back.

---

## Sensor Data Acquisition

Sensor data acquisition is the process of collecting measurements from physical sensors.

In this experiment:

1. The ultrasonic sensor emits ultrasonic waves.
2. The reflected signal is received by the Echo pin.
3. The ESP32 measures the pulse duration.
4. The distance is calculated and prepared for cloud transmission.

---

## Serial Communication

Serial communication enables the ESP32 to send measured values to a computer through USB.

The Arduino IDE Serial Monitor is used to:

- Display measured distance
- Verify sensor functionality
- Display HTTP response messages
- Debug communication errors

Example output:

```
Distance: 45.62 cm
HTTP Response Code: 200
Data uploaded successfully.
```

---

## REST API Communication

REST (Representational State Transfer) is a web service architecture that enables communication between devices over HTTP.

The ESP32 sends distance measurements to the cloud using HTTP requests.

The REST API receives sensor data, stores it in the database, and provides endpoints for retrieving stored records.

Typical endpoints include:

- POST `/sensor-data`
- GET `/sensor-data`

---

## HTTP POST and GET Methods

### HTTP POST

The POST method uploads sensor readings to the server.

Example JSON:

```json
{
  "distance": 45.62
}
```

---

### HTTP GET

The GET method retrieves previously stored sensor readings from the cloud database for dashboard visualization.

---

## Cloud Data Storage on AWS EC2

Amazon EC2 provides a virtual server for hosting the REST API and database.

The uploaded distance measurements are stored in the cloud database, enabling secure and centralized storage for future retrieval and analysis.

---

## API Integration with Embedded Systems

The ESP32 integrates with the cloud REST API using its built-in Wi-Fi module.

The workflow is:

- Connect to Wi-Fi
- Measure distance
- Create JSON payload
- Send HTTP POST request
- Receive server response
- Repeat periodically

This enables remote monitoring from anywhere with internet access.

---

## IoT Data Flow

The overall IoT system follows this sequence:

```
HC-SR04 Sensor
        │
        ▼
     ESP32
        │
        ▼
   Wi-Fi Network
        │
        ▼
 AWS EC2 REST API
        │
        ▼
 Cloud Database
        │
        ▼
 Web Dashboard
        │
        ▼
   User Monitoring
```

---

## Dashboard-Based Data Visualization

The dashboard developed in Lab 3 retrieves the stored distance measurements from the REST API and presents them graphically.

Features include:

- Real-time distance updates
- Historical distance records
- Interactive charts
- Sensor monitoring dashboard
- Remote data visualization

---

# Procedure

1. Connect the HC-SR04 ultrasonic sensor to the ESP32.
2. Upload the program to measure distance using the ultrasonic sensor.
3. Verify the measured distance using the Serial Monitor.
4. Review the REST API deployed on the AWS EC2 instance in Lab 2.
5. Configure the ESP32 with the Wi-Fi credentials and the REST API endpoint (AWS EC2 public IPv4 address).
6. Modify the ESP32 program to send distance measurements to the REST API using HTTP POST requests.
7. Upload the modified program to the ESP32.
8. Verify that the sensor data is successfully stored in the cloud database.
9. Access the dashboard developed in Lab 3.
10. Observe the uploaded distance measurements on the dashboard through graphical visualizations.
11. Analyze the recorded distance trends displayed on the dashboard.

---

# Output

- Successful acquisition of distance measurements from the HC-SR04 ultrasonic sensor.
- Distance readings displayed on the Serial Monitor.
- Successful transmission of sensor data from the ESP32 to the AWS EC2 REST API.
- Distance data stored in the cloud database.
- Distance measurements successfully displayed on the web dashboard.
- Real-time and historical graphs showing uploaded sensor data.

---

# Conclusion

In this laboratory, the ESP32 was successfully interfaced with the HC-SR04 ultrasonic sensor to measure the distance of nearby objects. The measured values were verified through the Serial Monitor and transmitted to a cloud-based REST API hosted on an AWS EC2 instance. The uploaded sensor data was stored in the cloud database and visualized using the dashboard developed in the previous lab. This experiment demonstrated the complete end-to-end IoT workflow, including sensor data acquisition, cloud communication, cloud storage, and remote monitoring through a web-based dashboard.
>>>>>>> f9f96c454f82ec92b253dcc00529e4c53390da85
