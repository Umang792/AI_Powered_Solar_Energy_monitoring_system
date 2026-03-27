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
- [API Endpoints](#-api-endpoints)
- [Project Structure](#-project-structure)
- [Dashboard Features](#-dashboard-features)
- [Future Enhancements](#-future-enhancements)
- [Contributors](#-contributors)
- [License](#-license)

---

## 🏞️ Project Vision

Bringing **Solar Intelligence** to rural households. This system combines IoT sensors, edge computing, and cloud-based AI to monitor solar microgrids, predict generation, detect faults, and optimize power distribution—all through an intuitive dashboard. Designed for villagers, built with precision.

| 🖥️ Dashboard Preview | 📊 Tech Stack |
| :---: | :---: |
| ![Dashboard Screenshot](Screenshot%202026-03-27%20at%206.15.34%E2%80%AFPM.png) | ![Tech Stack](image.png) |

---

## ✨ Key Features

### 1. Real-Time Monitoring
- **Energy Metrics**: Instant Power (kW), Solar Yield (kWh), Panel Temperature, System Health
- **Environmental**: Humidity, Wind Speed, Irradiance (W/m²), Visibility
- **Live Weather Data**: Integrated with OpenWeatherMap API

### 2. AI-Powered Intelligence
- **Power Prediction**: `Random Forest` model forecasts solar output using irradiation & temperature
- **Anomaly Detection**: `Isolation Forest` identifies:
  - **Fault Detection**: Sensor malfunction, dust accumulation, shading issues
  - **Theft/Tilt Detection**: MPU6050 data flags physical tampering or wind misalignment
  - **Performance Degradation**: -41.8% production drop alerts
- **Smart Suggestions**: Best times to run heavy appliances based on predicted generation

### 3. Smart Load Management
- **Fair Distribution**: 2-channel relay automates power allocation based on battery percentage and priority (Fan → TV → Water Pump)
- **Timing Permissions**: Schedule high-consumption devices during peak solar hours (12:00 PM – 3:00 PM)
- **Critical Alerts**: Immediate notification for output degradation

### 4. Weather Integration
- Live weather data via **OpenWeatherMap API**
- Solar impact assessment (Moderate/High/Low)
- Humidity, wind speed, visibility tracking
- Adjust predictions based on real-time weather conditions

### 5. Energy Analytics
- CO₂ savings tracking (kg)
- Efficiency percentage calculation
- Historical performance data
- Tomorrow's forecast based on weather & historical patterns

---

## 🛠️ Hardware Bill of Materials

| Component | Quantity | Approx Cost (₹) | Purpose |
| :--- | :---: | :---: | :--- |
| **ESP32 DevKit** | 1 | 500 | Central microcontroller with WiFi/Bluetooth |
| **INA219** | 1 | 700 | High-side current/power measurement (I²C) |
| **Voltage Divider Parts** | — | 150 | Resistors/caps for voltage sensing |
| **DS18B20** | 1 | 200 | Waterproof temperature probe for panel temp |
| **DHT22** | 1 | 350 | Ambient temperature & humidity |
| **BH1750** | 1 | 250 | Light intensity / Irradiance sensor |
| **MPU6050** | 1 | 250 | 6-axis accelerometer & gyroscope (tilt detection) |
| **10W Solar Panel** | 1 | 800 | Energy source for node |
| **12V 7Ah Battery** | 1 | 2,200 | Energy storage for demo |
| **10A PWM Charge Controller** | 1 | 700 | Regulates battery charging from solar |
| **2-Channel Relay Module** | 1 | 300 | Load control (Fan, TV, Water Pump) |
| **Buzzer & LEDs** | 1 set | 100 | Visual/audio alerts |
| **Total** | | **~₹6,250** | |

### Connection Diagram

---

## 🤖 AI/ML Models

We leverage two main models, trained on both **Kaggle solar data** and **simulated MPU sensor data**.

| Model | Algorithm | Purpose | Features Used | Output |
| :--- | :--- | :--- | :--- | :--- |
| **Solar Power Predictor** | Random Forest Regressor | Predicts solar power output | irradiation, temp_module, temp_ambient | ac_power (W) |
| **System Anomaly Detector** | Isolation Forest | Detects abnormal power drop or sensor spikes | irradiation, temp_module, ac_power, battery | Fault alert |
| **Panel Health Monitor** | Isolation Forest | Analyzes panel tilt/vibration | x_axis, y_axis, z_axis rotation angles | Theft/storm alert |

### Model Training Pipeline
1. **Data Collection**: Kaggle solar dataset + simulated MPU data
2. **Preprocessing**: Merge datasets, handle missing values, feature scaling
3. **Training**: 
   - Random Forest Regressor (n_estimators=100, max_depth=10)
   - Isolation Forest (contamination=0.1, random_state=42)
4. **Serialization**: Models saved as `.pkl` files for Flask API
5. **Inference**: Real-time predictions with simulated sensor data

### Simulated Sensor Values (for testing)
```python
ac_power = random.randint(200, 1500)      # Watts
battery = random.randint(50, 90)          # Percentage
irradiation = random.randint(200, 1000)   # W/m²
temp_module = random.randint(25, 65)      # °C
temp_ambient = random.randint(20, 40)     # °C
x_axis = random.uniform(-180, 180)        # Degrees
y_axis = random.uniform(-180, 180)        
z_axis = random.uniform(-180, 180)

┌─────────────────────────────────────────────────────────────────┐
│                         HARDWARE LAYER                          │
│  Solar Panel → PWM Controller → Battery → ESP32 → Sensors      │
│                              ↓                                  │
│                    Serial Data Output                           │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│                      BACKEND LAYER (Flask)                      │
│  • Receive sensor data (or simulate)                           │
│  • Load trained .pkl models                                     │
│  • Random Forest → Power Prediction                            │
│  • Isolation Forest → Anomaly Detection                        │
│  • Rule-based logic → Smart Suggestions                        │
│  • Weather API integration                                      │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│                     FRONTEND LAYER (React)                      │
│  • Real-time dashboard (updates every 2 seconds)               │
│  • Visualize: Power, Weather, Alerts, Predictions              │
│  • Display: CO₂ savings, efficiency, device usage              │
│  • Critical alerts & smart suggestions                         │
└─────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────┐
│                      ACTUATION LAYER                            │
│  • 2-Channel Relay controls appliances based on:               │
│    - Battery percentage (<30% → cut non-essential)             │
│    - Peak hours (12PM-3PM → allow heavy appliances)            │
│    - Predicted generation (low → conserve power)               │
└─────────────────────────────────────────────────────────────────┘
git clone https://github.com/your-username/microgrid-guardian.git
cd microgrid-guardian


# Upload code to ESP32 using Arduino IDE
# Install required libraries:
# - Adafruit INA219
# - OneWire
# - DallasTemperature
# - DHT sensor library
# - BH1750
# - MPU6050
# - WiFi
# - HTTPClient

# Configure WiFi credentials in the code
# Set API endpoint to your Flask server IP
microgrid-guardian/
│
├── backend/
│   ├── app.py                 # Flask main application
│   ├── models/                # Saved trained models
│   │   ├── random_forest.pkl
│   │   ├── isolation_fault.pkl
│   │   └── isolation_tilt.pkl
│   ├── data/                  # Data handling
│   │   ├── preprocess.py      # Data preprocessing
│   │   ├── simulate.py        # Simulated sensor data
│   │   └── weather_api.py     # Weather API integration
│   ├── utils/                 # Utility functions
│   │   ├── alerts.py          # Alert generation logic
│   │   └── predictions.py     # Model inference
│   ├── requirements.txt       # Python dependencies
│   └── config.py              # Configuration file
│
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/
│   │   │   ├── Dashboard.js   # Main dashboard
│   │   │   ├── PowerCard.js   # Power metrics display
│   │   │   ├── WeatherCard.js # Weather information
│   │   │   ├── AlertsCard.js  # System alerts
│   │   │   ├── Predictions.js # AI predictions
│   │   │   └── DeviceUsage.js # Device tracking
│   │   ├── hooks/
│   │   │   └── useApiData.js  # API data fetching
│   │   ├── App.js             # Main React component
│   │   ├── index.js           # Entry point
│   │   └── index.css          # Tailwind styles
│   ├── package.json
│   └── tailwind.config.js
│
├── hardware/
│   ├── esp32_code/
│   │   └── microgrid_monitor.ino  # ESP32 firmware
│   ├── wiring_diagram.png          # Connection diagram
│   └── sensor_test/                # Individual sensor tests
│
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_model_training.ipynb
│   └── 03_model_evaluation.ipynb
│
├── images/
│   ├── Screenshot_2026-03-27_at_6.15.34_PM.png
│   └── image.png
│
├── requirements.txt            # Overall requirements
├── README.md                   # This file
└── LICENSE
LICENSE
📊 Dashboard Features Explained
Feature	Description
Current Power	Real-time power output in kW
Solar Yield	Total energy generated today (kWh)
Panel Temperature	Current solar panel temperature (°C)
System Health	Overall system status (Optimal/Warning/Critical)
Instant Power	Current instantaneous power (kW)
Energy Today	Cumulative energy generated today
Efficiency	System efficiency percentage
Irradiance	Solar irradiance (W/m²)
CO₂ Saved	Carbon emissions offset (kg)
Device Usage	Daily usage hours for fans, TV, water pump
Smart Suggestion	AI-powered recommendations for appliance usage
Critical Alert	Immediate attention notifications
Tomorrow's Forecast	Predicted solar yield for next day
Evening Battery	Projected battery level by end of day
🧠 Future Enhancements
📱 Mobile App: React Native app for wider accessibility

📱 WhatsApp Alerts: Send critical fault notifications to villagers

📈 Historical Analytics: Track monthly CO₂ savings and efficiency trends

🔋 Battery Swap Scheduling: Predict when battery replacement is needed

🌦️ Advanced Weather Forecast: LSTM models for better prediction accuracy

🎙️ Voice Assistant: Hindi/regional language support for alerts

📊 Community Dashboard: Compare multiple households in a village

🔐 User Authentication: Secure access for different households

📤 Data Export: CSV/PDF reports for system performance

🤖 Auto-Calibration: Self-calibrating sensors for accuracy

🤝 Contributing
Contributions are welcome! Please follow these steps:

Fork the repository

Create a feature branch (git checkout -b feature/AmazingFeature)

Commit changes (git commit -m 'Add AmazingFeature')

Push to branch (git push origin feature/AmazingFeature)

Open a Pull Request

👥 Contributors
Your Name – Hardware Integration, AI Models, Backend Development

Open for contributions!

📜 License
This project is licensed under the MIT License – see the LICENSE file for details.

🙏 Acknowledgments
Kaggle for solar generation datasets

OpenWeatherMap for weather API

Arduino community for sensor libraries

Scikit-learn for ML algorithms

ESP32 community for IoT support

📧 Contact
Project Link: https://github.com/your-username/microgrid-guardian

<div align="center"> Made with ❤️ for sustainable energy access in rural communities <br/> <br/>
⭐ Star this repo |
🐛 Report Bug |
💡 Request Feature

<br/> <br/>
<sub>© 2024 MicroGrid Guardian | Empowering villages with AI-powered solar intelligence</sub>

</div> ```
