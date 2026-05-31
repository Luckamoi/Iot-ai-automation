# ⚖️ IoT-AI Telemetry & Automated Access Control Architecture
> An end-to-end IoT platform demonstrating edge-to-cloud data orchestration, integrating real-time physical sensor telemetry with Large Language Models (LLMs) and automated workflows for intelligent analytics and biometric security.
> 
## 💡 Why This Project? (Engineering Problem & Solution)
Traditional digital access systems (like standard OTPs) are vulnerable to remote attacks, while standalone biometrics are expensive and inflexible. This platform introduces an **Adaptive 2-Factor Authentication (MFA)** architecture to solve these vulnerabilities:
 * **Physical Presence Required:** Using real-time body mass as the primary biometric gate ensures the user is physically present. A remotely stolen OTP is useless without matching the physical weight threshold on-site.
 * **Resource Optimization (Edge Pre-filtering):** The hardware scale acts as a physical filter. Expensive Cloud API calls (OTP generation) are only triggered when the weight threshold is met, preventing spam and saving system resources.
 * **Self-Calibrating System (Closed-Loop):** Body weight fluctuates naturally. Upon a successful OTP entry, the system automatically recalibrates the user's baseline weight in the database, creating a maintenance-free, adaptive security loop.
## 🎯 Engineering Highlights & Core Systems
### 1. 🏥 Intelligent Biometric & Nutritional Telemetry
 * **Edge Data Acquisition:** Captures high-precision physical weight data using load cells interfaced with an ESP32 microcontroller via a 24-bit ADC (HX711) for precise signal conditioning.
 * **LLM Integration:** Processes unstructured data (user-submitted meal images) through Cloud AI to extract and analyze nutritional metrics in real-time.
 * **Automated Orchestration:** Utilizes n8n to route edge data and AI outputs into PostgreSQL and Google Sheets, creating a fully automated, zero-touch data pipeline.
### 2. 🔐 Adaptive 2-Factor Authentication (Biometric + Out-of-Band)
 * **Dynamic Mass Verification:** Implements a novel physical security layer by using the user's real-time body weight as the primary biometric verification factor.
 * **Out-of-Band (OOB) OTP:** Upon passing the weight tolerance threshold, the system triggers a dynamic OTP via the Gmail API.
 * **Closed-Loop Calibration:** The system automatically recalibrates the user's baseline weight reference in the database after each successful authentication, accounting for natural physiological variations over time.
## 🛠️ System Architecture & Tech Stack
The project is built on a microservices-inspired architecture, deployed entirely via Docker for scalability and environment consistency.
 * **Edge / Hardware Tier:** ESP32 (Microcontroller), 50kg Load Cells, HX711 (24-bit ADC), 5V Relay Actuator.
 * **Telemetry & Network Tier:** MQTT Protocol (Mosquitto Broker) for low-latency pub/sub messaging, Cloudflare Tunnels for secure external access.
 * **Data & Orchestration Tier:** n8n (Workflow Automation), PostgreSQL (Relational Database), Docker & Docker Compose.
 * **External Integration:** Large Language Models (Cloud AI), Google Workspace APIs (Sheets, Gmail).
## 🚀 Deployment Guide
**1. Repository Initialization**
```bash
git clone https://github.com/Luckamoi/Iot-ai-automation.git
cd Iot-ai-automation

```
**2. Environment Configuration**
Copy the .env.example file to .env and configure your credentials (e.g., database credentials, API tokens).
```bash
cp .env.example .env

```
**3. Container Orchestration**
Deploy the complete backend infrastructure using the provided docker-compose.yml:
```bash
docker-compose up -d

```
**4. Workflow Provisioning**
Access the n8n instance (http://localhost:5678) and import the pre-configured automation workflows from the /Workflows/ directory.
## 🔌 Hardware Schematic / Signal Flow
 * **Signal Conditioning (HX711):** Data (DT) → GPIO 21 | Clock (SCK) → GPIO 22
 * **Actuator Control (Relay):** Control Signal → ESP32 GPIO 18 → Door Lock Mechanism
## 📄 License
This project is licensed under the MIT License (see the LICENSE file).

**Developed by:** @Luckamoi - *Electrical  Engineer*

