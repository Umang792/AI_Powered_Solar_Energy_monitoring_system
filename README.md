# 🌞 AI-Powered Renewable Energy Monitoring System for Microgrids

## 📌 Overview

This project is an **AI + IoT-based smart energy monitoring system** designed for rural microgrids.
It collects real-time data from sensors, analyzes system conditions using Machine Learning, and provides **actionable insights in a simple dashboard (Hindi/English)** for villagers.

---

## 🚀 Features

* 🔌 Real-time monitoring of voltage, current, and power
* 🌞 Solar energy generation tracking
* 🔋 Battery health monitoring
* 🌡 Environmental sensing (temperature, humidity, light)
* 📳 Panel condition detection using vibration (dust/tampering)
* 🤖 AI-based fault detection:

  * Normal
  * Dust on panel
  * Overload
  * Theft detection
  * Sensor fault
* 💡 Smart energy usage suggestions
* ⚠ Real-time alerts
* 💰 Monthly savings and CO₂ reduction estimation
* 🌐 User-friendly dashboard (Hindi for rural users)

---

## 🧠 System Architecture

```
Sensors → ESP32 → Backend (Node.js) → ML Model (Python) → Dashboard
```

---

## 🧰 Hardware Components

| Component         | Description                          |
| ----------------- | ------------------------------------ |
| ESP32 DevKit      | Microcontroller for data collection  |
| INA219            | Current & voltage sensor             |
| DS18B20           | Solar panel temperature sensor       |
| DHT22             | Temperature & humidity sensor        |
| BH1750            | Light intensity sensor               |
| MPU6050           | Vibration detection (dust/tampering) |
| Solar Panel (10W) | Energy generation                    |
| 12V Battery       | Energy storage                       |
| Charge Controller | Battery regulation                   |
| Relay Module      | Load control                         |

---

## 📊 Dataset Features

### 🔹 Input Features

* voltage_v
* current_a
* power_w
* battery_pct
* power_flow
* light_lux
* temperature_c
* humidity_pct
* mpu_x, mpu_y, mpu_z

### 🔹 Derived Features

* efficiency = power / light
* vibration_score = |x| + |y| + |z|
* abnormal_current

### 🔹 Output Labels

* status (normal, dust, overload, theft, fault)

---

## 🤖 Machine Learning Model

* Model Used: **Random Forest Classifier**
* Task: Classification (System Status Prediction)
* Accuracy: ~90% (depending on dataset)

---

## ⚙️ Installation & Setup

### 1️⃣ Clone Repository

```
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

---

### 2️⃣ Install Dependencies

#### Python (ML Model)

```
pip install pandas scikit-learn joblib
```

#### Node.js Backend

```
npm install
```

---

### 3️⃣ Run Model Training

```
python train_model.py
```

---

### 4️⃣ Start Backend Server

```
node server.js
```

---

## 📡 API Workflow

1. ESP32 sends sensor data
2. Backend calculates derived features
3. Data sent to ML model
4. Model predicts system status
5. Backend generates:

   * Suggestions
   * Alerts
   * Dashboard data

---

## 📊 Example Output

```
🌞 सोलर ऊर्जा डैशबोर्ड

Status: 🟢 सिस्टम ठीक है
Battery: 🔋 72%

Solar Produced: 5.6 kWh
Home Usage: 4.1 kWh

💡 सुझाव:
आप वॉशिंग मशीन चला सकते हैं

⚠ अलर्ट:
पैनल पर धूल हो सकती है

💰 बचत:
₹1200 | 22kg CO₂
```

---

## 🧠 Key Concepts Used

* IoT (ESP32 + Sensors)
* Machine Learning (Random Forest)
* Feature Engineering
* Real-time Data Processing
* Smart Recommendation System

---

## 🌍 Impact

* Helps villagers **save electricity cost**
* Improves **solar panel efficiency**
* Detects **faults and energy theft**
* Promotes **sustainable energy usage**

---

## 🔮 Future Improvements

* 📱 Mobile App Integration
* 🌐 Cloud Dashboard
* 🔊 Voice Assistant (Hindi)
* 📊 Advanced AI predictions (energy forecasting)

---

## 👨‍💻 Author

**Your Name**
B.Tech Student | AI + IoT Enthusiast

---

## ⭐ Contribute

Contributions are welcome! Feel free to fork and improve the project.

---

## 📜 License

This project is open-source and available under the MIT License.
