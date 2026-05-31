
# ⚖️ AI-Powered Smart Weight Platform & Access Control System
An end-to-end IoT platform integrating real-time hardware sensor data with cloud AI and n8n automation. This project bridges physical hardware and software systems to provide automated nutritional analysis and a two-factor (Biometric/OTP) security access system.
## 🚀 Core Systems
### 1. 🏥 Smart Health Advisor (Data Acquisition & AI Analysis)
 * Acquires physical weight data via load cells and interfaces with a custom ESP32 system.
 * Integrates with Cloud AI to process user-submitted meal images for real-time nutritional breakdown.
 * Automates data logging and generates personalized health insights stored in Google Sheets.
### 2. 🔐 Smart Door Security (2-Factor Authentication)
 * **Biometric Verification:** Utilizes real-time body weight as the primary authentication factor.
 * **Dynamic OTP:** Triggers an automated OTP via Gmail API upon passing weight tolerance thresholds.
 * **Adaptive Reference:** Automatically recalibrates the user's baseline weight reference after successful authentications to account for natural variations.
## 🛠️ System Architecture & Technologies
 * **Hardware & Edge:** ESP32, HX711 ADC, Load Cells, Relay Modules
 * **Network & Protocols:** MQTT (Mosquitto Broker), Cloudflare Tunnels
 * **Backend & Automation:** n8n, PostgreSQL, Docker Compose
 * **External APIs:** Google Gemini/Cloud AI, Gmail API, Google Sheets API
## 🚀 Quick Start
**1. Clone the Repository**
```bash
git clone https://github.com/Luckamoi/Iot-ai-automation.git
cd Iot-ai-automation

```
**2. Environment Configuration**
Copy .env.example to .env and configure your credentials (e.g., POSTGRES_USER, TUNNEL_TOKEN).
```bash
cp .env.example .env

```
**3. Deploy Services**
Initialize the complete stack using Docker Compose:
```bash
docker-compose up -d

```
**4. Import Automation Workflows**
Access the n8n dashboard (http://localhost:5678) and import the JSON workflows located in the /n8n-workflows/ directory.
## 🔌 Hardware Integration Schema
 * **Signal Conditioning (HX711):** DT → GPIO 21 | SCK → GPIO 22
 * **Actuator Control (Door Relay):** ESP32 GPIO 18 → 5V Relay Module
## 📄 License
Published under the MIT License.
**Developer:** @Luckamoi
