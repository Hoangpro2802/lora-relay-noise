# LoRa Relay Noise Monitoring System

This project implements a noise monitoring system using LoRa technology in a relay configuration with three nodes. It is designed to survey data transmission between nodes in a constrained space, ensuring data passes through each node sequentially rather than skipping directly from the source to the destination.

## Project Overview
- **Purpose**: Measure noise levels using a sound sensor, relay the data through intermediate nodes, and store it either locally (SD card) or online (Adafruit IO).
- **Note**: This is **not a true LoRa mesh network**. Instead, it uses a linear relay approach (Node 1 → Node 2 → Node 3) to enforce sequential transmission in a small-scale experiment, preventing direct communication from Node 1 to Node 3 that would bypass Node 2.

### Components
- **Node 1**: Collects noise data from a sound sensor, calculates dB, and sends it to Node 2 via LoRa.
- **Node 2**: Acts as a relay, receiving data from Node 1 and forwarding it to Node 3 via LoRa.
- **Node 3**: Receives data from Node 2, validates it, and logs it to an SD card and/or Adafruit IO via WiFi.

### Technologies
- **LoRa**: 433 MHz frequency for wireless communication between nodes.
- **ESP32**: Microcontroller platform for all nodes.
- **WiFi**: Used by Node 3 to upload data to the cloud.
- **SD Card**: Local storage on Node 3.
- **Adafruit IO**: Cloud platform for real-time data visualization.

## Hardware Requirements
- 3x ESP32 boards (e.g., ESP32 DevKit).
- 1x Sound sensor (connected to Node 1, pin 39).
- 3x LoRa modules (e.g., SX1278, 433 MHz).
- 1x MicroSD card module (connected to Node 3).
- Breadboards, jumper wires, and power supplies.

## Software Setup
1. **Install Arduino IDE** and add ESP32 board support.
2. **Libraries Required**:
   - `SPI.h`
   - `LoRa.h`
   - `esp_task_wdt.h` (Node 1, Node 2)
   - `WiFi.h`, `NTPClient.h`, `WiFiUdp.h`, `SD.h`, `HTTPClient.h`, `WiFiClientSecure.h` (Node 3)
3. Upload the respective `.ino` files to each ESP32:
   - `node1.ino` → Node 1
   - `node2.ino` → Node 2
   - `node3.ino` → Node 3
4. Configure WiFi credentials and Adafruit IO keys in `node3.ino`.

## Installation
1. Clone this repository:
   ```bash
   git clone https://github.com/Hoangpro2802/lora-relay-noise.git


