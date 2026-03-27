<div align="center">
  <img src="https://img.icons8.com/fluency/96/solar-panel.png" alt="Solar Panel Icon" width="80"/>
  <h1>🌱 MicroGrid Guardian</h1>
  <h3>AI-Powered Renewable Energy Monitoring System for Smart Villages</h3>
  <p><i>Democratizing energy intelligence for off-grid communities</i></p>

  ![Python](https://img.shields.io/badge/Python-3.9+-blue?logo=python)
  ![Flask](https://img.shields.io/badge/Flask-2.0+-black?logo=flask)
  ![React](https://img.shields.io/badge/React-18.0+-61DAFB?logo=react)
  ![Tailwind](https://img.shields.io/badge/Tailwind-3.0+-06B6D4?logo=tailwindcss)
  ![Scikit Learn](https://img.shields.io/badge/Scikit--Learn-1.0+-F7931E?logo=scikit-learn)
  ![ESP32](https://img.shields.io/badge/ESP32-Enabled-735DF0?logo=espressif)
  ![MongoDB](https://img.shields.io/badge/MongoDB-4.4+-47A248?logo=mongodb)
  ![TypeScript](https://img.shields.io/badge/TypeScript-5.0+-3178C6?logo=typescript)
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

* **Umang Raj** – Full Stack + AI + IoT

---

## 📜 License

MIT License

---

## 🙏 Acknowledgments

* Kaggle (datasets)
* OpenWeatherMap API
* Arduino Community
* Scikit-learn

---

## 📧 Contact

GitHub: https://github.com/your-username/microgrid-guardian

---

<div align="center">

⭐ Star this repo | 🐛 Report Bug | 💡 Request Feature

Made with ❤️ for sustainable rural energy ❤️

</div>
