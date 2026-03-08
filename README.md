# 🌤️ IoT Weather Station (ESP32 Firmware)
This repository contains the firmware and hardware configuration for an advanced IoT Weather Station. 
Built on the ESP32 platform, the system monitors 10 different environmental parameters and synchronizes data in real-time with a Firebase Realtime Database.  

## 🛠️ Hardware Architecture  
The project utilizes the ESP-WROOM-32 due to its integrated Wi-Fi, dual-core processing, and extensive ADC capabilities.  

## 🛰️ Sensor Suite  
The system integrates 9 physical sensors providing 10 functional readings:  


## 💻 Tech Stack & Libraries
Development Environment:  
- VS Code + PlatformIO: Primary environment for modular development.  
- Arduino IDE (v1): Used for rapid individual sensor testing.  
    
Core Libraries:  
- Firebase_ESP_Client.h: Handles authentication and RTDB communication.  
- WiFi.h: Manages ESP32 network connectivity.  
- Adafruit_Sensor.h & Adafruit_BMP085: For pressure and temperature mapping.  
- QMC5883LCompass.h: Optimized for magnetic North orientation.  
- Wire.h: Facilitates I2C communication (Address 0x39 for Lux, 0x0D for Compass).  

## 🚀 Key Implementation Details
1. Data Processing Pipeline  
The firmware follows a cyclic executive pattern:  
- Update Interval: Data is sampled and pushed to Firebase every 2.5 seconds to balance power and real-time accuracy.  
- Wind Speed: Uses a hardware interrupt on the A44E sensor to calculate RPM, which is then converted from circular to linear velocity (m/s).  
- Calibration: Includes software-level mapping for the MQ-4 gas sensor and an inverse reading logic for the rain sensor (resistance decreases as moisture increases).  
2. Firebase Connectivity   
The system connects via a secured API Key and Database URL.   
Data is structured in a JSON tree under the Sensor/ parent node.  
  
## 📦 Mechanical Design  
The system is housed in a custom-designed 3D-printed enclosure (PLA).  
Protection: Sensors are positioned to face the environment while the main board and wiring are isolated with electrical tape to prevent short circuits during rain.  
Anemometer: Features custom cup and vane attachments polished to fit 4mm steel rods and high-precision bearings.  
