# IoT-Based Air Quality Monitoring & Alert System

This is a self-initiated **IoT Air Quality Monitoring System** built using various AWS cloud services to practice and prepare for real-world IoT-based internship projects. It collects simulated environmental data (e.g., temperature, humidity, PM2.5, PM10) and processes it through AWS IoT Core, Lambda, DynamoDB, and S3. The data is visualized using QuickSight, and alerts are sent via SNS.

---

## 🔧 Tech Stack

| Component     | Service/Tool      |
| ------------- | ----------------- |
| Language      | Python            |
| IoT Broker    | AWS IoT Core      |
| Compute       | AWS Lambda        |
| Storage       | DynamoDB, S3      |
| Visualization | Amazon QuickSight |
| Alerts        | Amazon SNS        |
| Repo Hosting  | GitHub            |

---

## 🧠 Architecture

![System Architecture](assets/architecture-diagram.png)

> The sensor simulator publishes environmental data to AWS IoT Core via MQTT. A Rule triggers a Lambda function that processes and stores data in DynamoDB, and backs it up to S3. The data is then visualized in QuickSight. Threshold breaches trigger alerts via SNS.

---

## 📆 Features

* Real-time sensor data simulation (Python)
* MQTT publishing to AWS IoT Core
* Lambda function to filter and process data
* DynamoDB for structured storage
* S3 for data backup/archive
* Dashboard visualization using QuickSight
* Alerts via Amazon SNS when AQI exceeds safe levels

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/saish-adav/iot-air-quality-monitoring.git
cd iot-air-quality-monitoring
```

### 2. Set up AWS credentials

```bash
aws configure
```

### 3. Create and attach the IoT Policy & Thing

* Create an IoT Thing
* Attach a policy with publish/subscribe permissions
* Download certificates
* Attach policy to the certificate

📘 Setup details are in `docs/setup-instructions.md`

---

## 🧪 Run the Simulator

```bash
cd data-simulator
python simulator.py
```

This publishes fake sensor data to AWS IoT Core at regular intervals.

---

## 📝 Example Payload

```json
{
  "device_id": "device-01",
  "timestamp": "2025-07-08T10:30:00Z",
  "temperature": 32.5,
  "humidity": 68,
  "pm2_5": 54.3,
  "pm10": 70.1
}
```

---

## 📊 QuickSight Dashboard Preview

![QuickSight Dashboard](assets/quicksight-dashboard.png)

---

## 🔔 Alert Logic (SNS)

* **If PM2.5 > 50 or PM10 > 60**:

  * Trigger an email or SMS alert using **Amazon SNS**

---

## 📁 Repository Structure

```
iot-air-quality-monitoring/
│
├── data-simulator/           # MQTT publisher (sensor simulator)
│   └── simulator.py
│
├── lambda/                   # AWS Lambda function code
│   └── processor_function.py
│
├── docs/                     # Documentation & setup guides
│   └── setup-instructions.md
│
├── assets/                   # Architecture diagrams, dashboard screenshots
│   ├── architecture-diagram.png
│   └── quicksight-dashboard.png
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## 🎯 Future Enhancements

* Telegram/WhatsApp integration for alerts
* Mobile or web dashboard
* Connect to real sensors like MQ135 or SDS011 using Raspberry Pi
* Add historical trends, forecasting with ML

---

## 📜 License

This project is licensed under the MIT License. See `LICENSE` for more info.

---

## 🙋‍♂️ Author

**Saish Adav**
BTech CSE (IoT and Intelligent Systems), Manipal University Jaipur
e-mail - saish.adav01@gmail.com
LinkedIn - www.linkedin.com/in/saish-adav | GitHub - https://github.com/saish-adav

