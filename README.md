# NexusFlow 🚀
> **Visual IoT Orchestration & Automation Platform**

NexusFlow is a full-stack IoT platform designed to remove the code barrier from building custom IoT systems. It allows users to visually configure ESP32 microcontrollers, author dynamic automation flows, execute sandboxed custom scripts, and receive real-time mobile notifications without writing low-level firmware C++ code.

---

## 📁 Repository Ecosystem

The NexusFlow ecosystem is modularized into four main sub-repositories:

| Sub-Repository | Tech Stack | Description |
| :--- | :--- | :--- |
| 🌐 **[NexusFlow Frontend](https://github.com/ahmedelzaky/nexusflow-frontend)** | React, React Flow, CSS | Visual drag-and-drop flow editor, device management dashboard, and real-time telemetry visualizations. |
| ⚙️ **[NexusFlow Backend](https://github.com/ahmed-atef-gad/nexusflow-backend)** | NestJS, TypeScript, MongoDB, Aedes (MQTT) | Control plane hosting REST APIs, embedded MQTT broker, VM JavaScript sandbox, and FCM notification engine. |
| 📱 **[NexusFlow Mobile](https://github.com/ahmadkasimeng/nexusflow-mobile)** | React Native, Firebase SDK | Native mobile app for receiving push notifications, incident tracking, and acknowledgment handshakes. |
| 🔌 **[ESP32 IoT Firmware](https://github.com/ahmedelzaky/ESP32_iot_firmware)** | C++ (Arduino / FreeRTOS) | Standardized firmware image running on ESP32 microcontrollers that pulls dynamic setup profiles and executes tasks. |

---

## 🏗️ System Architecture

NexusFlow connects hardware, cloud backend, and client interfaces in a unified architecture:

```
                  +-----------------------------------+
                  |        User Interfaces            |
                  |  - Web Editor (React / WebSockets)|
                  |  - Mobile App (FCM Push Alerts)   |
                  +-----------------+-----------------+
                                    |
                            HTTPS / WebSockets / FCM
                                    |
                  +-----------------+-----------------+
                  |      NexusFlow Backend            |
                  |  - NestJS REST API Control Plane  |
                  |  - Embedded MQTT Broker (Port 8883)|
                  |  - Sandboxed JS Execution Engine  |
                  |  - MongoDB Persistence Layer      |
                  +-----------------+-----------------+
                                    |
                             MQTT over TCP / HTTPS
                                    |
                  +-----------------+-----------------+
                  |        Edge Hardware              |
                  |  - ESP32 Microcontrollers         |
                  |  - Sensors (DHT11, MQ2, PIR, etc.)|
                  |  - Actuators (Relays, Servos)     |
                  +-----------------------------------+
```

---

## ✨ Key Features

- **Visual Drag-and-Drop Editor**: Build automation flows visually by connecting hardware inputs, logic nodes, and outputs.
- **Dynamic Hardware Setup**: The backend compiles visual graphs into pin-mode configurations that ESP32 hardware dynamically downloads at startup.
- **Secure Hardware Onboarding**: Onboard new devices using temporary 8-character registration codes, exchanging them for secure, long-lived device tokens.
- **Embedded MQTT Communication**: A built-in MQTT broker handles high-throughput telemetry and real-time commands under a single access-control layer.
- **Sandboxed Custom Scripting**: Advanced users can write custom JavaScript snippets to process data. Code is pre-screened with AST checks and run inside isolated VM containers.
- **Incident-Aware Notifications**: Smart alert system powered by Firebase Cloud Messaging (FCM) featuring cooldown rules, exponential backoffs, and auto-handling to prevent alert fatigue.
- **Over-The-Air (OTA) Updates**: Upload compiled `.bin` firmware files from the admin portal and trigger secure, rate-limited OTA updates to devices.
