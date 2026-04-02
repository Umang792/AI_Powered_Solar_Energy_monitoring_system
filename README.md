 <img width="1230" height="298" alt="image" src="https://github.com/user-attachments/assets/f11a5a6d-0db0-4b62-8c9d-4839c459615d" />
 

  <h1>🌱 AI Powered Renewable Energy Monetoring System for Microgrid</h1>
  <h3>AI-Powered Renewable Energy Monitoring System for Smart Villages</h3>
  <p><i>Democratizing energy intelligence for off-grid communities</i></p>

  ![HTML](https://img.shields.io/badge/HTML-5-E34F26?logo=html5\&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-3-1572B6?logo=css3\&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-F7DF1E?logo=javascript\&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-18+-339933?logo=node.js\&logoColor=white)
![Express.js](https://img.shields.io/badge/Express.js-Backend-000000?logo=express\&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.9+-3776AB?logo=python\&logoColor=white)
![Embedded C++](https://img.shields.io/badge/Embedded%20C++-ESP32-00599C?logo=c%2B%2B\&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32-Microcontroller-735DF0?logo=espressif\&logoColor=white)

</div>

---

## 📋 Table of Contents
- [Project Vision](#-project-vision)
- [Key Features](#-key-features)
- [Hardware Bill of Materials](#-hardware-bill-of-materials)
- [AI/ML Models](#-aiml-models)
- [System Workflow](#-system-workflow)
- [Quick Start](#-quick-start)
- [Project Structure](#-project-structure)
- [Future Enhancements](#-future-enhancements)
- [Contributors](#-contributors)
- [License](#-license)

---

## 🏞️ Project Vision

Bringing **Solar Intelligence** to rural households. This system combines IoT sensors, edge computing, and cloud-based AI to monitor solar microgrids, predict generation, detect faults, and optimize power distribution—all through an intuitive dashboard.

---

## ✨ Key Features

### 🔹 Real-Time Monitoring
- Power (kW), Solar Yield (kWh)
- Panel Temperature
- Humidity, Irradiance (W/m²)
- Live Weather API integration

### 🔹 AI Intelligence
- **Random Forest** → Power Prediction  
- **Isolation Forest** → Fault Detection  
- Detects:
  - Sensor faults  
  - Dust/shading issues  
  - Theft/tilt (MPU6050)

### 🔹 Smart Load Management
- Automatic relay control
- Priority-based appliance usage
- Peak hour optimization (12PM–3PM)

### 🔹 Weather Integration
- Real-time weather data
- Solar impact prediction
- Dynamic adjustment of output

### 🔹 Energy Analytics
- CO₂ savings
- Efficiency tracking
- Historical + future predictions

---

## 🛠️ Hardware Bill of Materials

| Component | Qty | Cost (₹) | Purpose |
|----------|----|---------|--------|
| ESP32 | 1 | 500 | Controller |
| INA219 | 1 | 700 | Current sensor |
| DS18B20 | 1 | 200 | Temperature |
| DHT22 | 1 | 350 | Humidity |
| BH1750 | 1 | 250 | Light sensor |
| MPU6050 | 1 | 250 | Tilt detection |
| Solar Panel | 1 | 800 | Energy source |
| Battery | 1 | 2200 | Storage |
| Relay Module | 1 | 300 | Load control |

**Total ≈ ₹6,250**

---



## 📸 System Preview

## 📸 System Preview

| 🏠 Home Page | ⚙️ Real Device Setup |
|-------------|---------------------|
| <p align="center"><img src="https://github.com/user-attachments/assets/19e4bc8b-1caf-45cf-8386-f02875bb2a80" width="100%"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/1a5cacc0-8d83-4bb0-866b-5f53307541de" width="100%"/></p> |
| *Main dashboard showing overview of features, system status, and navigation.* | *Actual hardware implementation of the system with sensors and microcontroller in real environment.* |



## 📸 Project Screenshots

## 📊 System Preview

| 📊 Real-Time Data Monitoring | 🔌 Hardware Connections |
|----------------------------|------------------------|
| <p align="center"><img src="https://github.com/user-attachments/assets/619134bc-b400-4298-88a8-80f3ebe18b58" width="90%"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/e392965d-6fa8-4a19-98c0-1291ef762e80" width="90%"/></p> |
| *Live sensor data visualization including voltage, current, power, temperature, humidity, and light intensity.* | *Circuit diagram showing connections between ESP32, sensors (INA219, DHT22, BH1750, etc.).* |
## 🤖 AI/ML Models

| Model | Algorithm | Purpose |
|------|----------|--------|
| Power Predictor | Random Forest | Predict solar output |
| Fault Detector | Isolation Forest | Detect anomalies |
| Tilt Monitor | Isolation Forest | Detect theft/misalignment |

### 🧪 Sample Input (Simulation)

```python
ac_power = random.randint(200, 1500)
battery = random.randint(50, 90)
irradiation = random.randint(200, 1000)
temp_module = random.randint(25, 65)
temp_ambient = random.randint(20, 40)
x_axis = random.uniform(-180, 180)
y_axis = random.uniform(-180, 180)
z_axis = random.uniform(-180, 180)
```

---

## ⚙️ System Workflow

```
HARDWARE → ESP32 → Flask API → ML Models → React Dashboard → Relay Control
```

---

## 🚀 Quick Start

```bash
git clone https://github.com/your-username/microgrid-guardian.git
cd microgrid-guardian
```

### Backend

```bash
cd backend
pip install -r requirements.txt
python app.py
```

### Frontend

```bash
cd frontend
npm install
npm start
```

---

## 📁 Project Structure

```
microgrid-guardian/
│
├── backend/
│   ├── app.py
│   ├── models/
│   ├── data/
│   ├── utils/
│   └── requirements.txt
│
├── frontend/
│   ├── src/
│   └── public/
│
├── hardware/
│   └── esp32_code/
│
├── notebooks/
├── images/
└── README.md
```

---

## 📊 Dashboard Features

* Real-time Power Monitoring
* Solar Yield Tracking
* System Health Status
* CO₂ Savings
* Smart Suggestions
* Fault Alerts

---

## 🧠 Future Enhancements

* 📱 Mobile App (React Native)
* 📩 WhatsApp Alerts
* 📊 Advanced Analytics
* 🔋 Battery Prediction
* 🌦️ LSTM Forecasting
* 🎙️ Voice Assistant (Hindi)
* 🔐 User Authentication

---

## 🤝 Contributors

* **Umang Raj** – Frontend  + IoT
* **Chaitanya Tyagi** – Backend + AI
* **Shruti Shukla** - Research & System Design

---

## 📜 License

MIT License

---

## 🙏 Acknowledgments

* Real dataset
* OpenWeather API
* Arduino IDE
* Scikit-learn
* ESP32

---

## 📧 Contact

GitHub: https://github.com/your-username/microgrid-guardian

---

<div align="center">

⭐ Star this repo | 🐛 Report Bug | 💡 Request Feature

Made with ❤️ for sustainable rural energy ❤️

</div>
