# AETHER UAV

**Advanced Electronic Tactical Hybrid Emergency Reconnaissance Unmanned Aerial Vehicle**
![AETHER UAV](images/Drone.jpg)

---

## Table of Contents

1. [Introduction](#introduction)  
2. [Background & Motivation](#background--motivation)  
3. [Objectives](#objectives)  
4. [System Architecture](#system-architecture)  
5. [Components & Modules](#components--modules)  
6. [Integrations & Data Flow](#integrations--data-flow)  
7. [Tools & Technologies](#tools--technologies)  
8. [Getting Started](#getting-started)  
9. [Future Improvements](#future-improvements)  
10. [License & Contributing](#license--contributing)  

---

## Introduction

AETHER UAV is a versatile, multi-role drone platform designed to support civil and military operations such as surveillance, rescue missions, firefighting, and real-time threat assessment. It is designed for modularity, portability, and adaptability, allowing it to function in hazardous environments where human intervention is difficult or risky.

---

## Background & Motivation

Bangladesh has been increasingly affected by fire incidents and natural disasters. Between 2015 and 2024, fire-related incidents rose sharply (≈ 50 %), with many lives and properties at risk. Rapid urbanization, industrial growth, and climate challenges (e.g. flooding) have made timely reconnaissance and emergency response systems more critical than ever. A system like AETHER UAV aims to fill this need with a cost-effective, reliable, real-time response tool.

---

## Objectives

- Design and build a modular UAV platform for reconnaissance, defense, firefighting, and emergency response.  
- Integrate thermal imaging capabilities for detection of fire and locating survivors.  
- Support payload customization (e.g., fire retardant, beacon droppers).  
- Provide real-time thermal and visual feed, GPS navigation, and environmental sensing (smoke, CO).  
- Demonstrate real-world applications of embedded systems, mechatronics, and communication technologies in emergencies.

---

## System Architecture

- **Frame**: Modular carbon fiber, foldable for portability.  
- **Motors**: VELOX V2812 925 KV BLDC for efficient propulsion.  
- **Flight Controller**: GEPRC F722, supporting PID tuning and GPS-based navigation.  
- **Camera**: Walksnail 4K for live visual feed / FPV monitoring.  
- **Thermal Sensor**: MLX90640 for detecting heat/ fire signatures.  
- **mmWave Radar**: Seeed Studio 24 GHz to detect presence in low visibility.  
- **Communication Links**:  
  - 5.8 GHz digital FPV for video.  
  - 2.4 GHz ELRS for telemetry / RC control.  
  - LoRa SX1278 for long-range beacon / location telemetry.  
- **Power**: 6S LiPo battery (2200–5000 mAh).  
- **Environmental Sensors**: Smoke (MQ-2), Carbon Monoxide (MQ-9).  
- **Navigation**: Foxeer M10Q GPS with waypoint support.  

---

## Components & Modules

| Module | Model / Spec | Purpose |
|---|---|---|
| Flight Controller | GEPRC F722 | Control, stabilize flight, interpret sensor data |
| Motors | VELOX V2812 925 KV | Propulsion and maneuvering |
| Camera System | Walksnail Avatar 4K | Visual and FPV feed |
| Thermal Sensor | MLX90640 | Fire detection & heat mapping |
| Radar Sensor | Seeed Studio 24 GHz | Presence detection in low visibility |
| GPS | Foxeer M10Q | Position, navigation, waypoint support |
| Remote System | Radiomaster RP3 v2 ELRS | Low-latency control link |
| Microcontroller | ESP32 Dev Kit | Handling sensors, thermal frame capture, communications |
| Environmental Sensors | MQ-2, MQ-9 | Smoke, CO detection |
| Beacon Module | SX1278 + GPS + LED + Buzzer | Long-range beacon for rescue signalling |

---

## Integrations & Data Flow

- Thermal frames are captured via the MLX90640 sensor using I²C by ESP32.  
- Due to processing constraints, thermal capture is limited to **~8 Hz**.  
- Frames are sent from the UAV to a base station (e.g., laptop) via WebSocket over a wireless access point.  
- At base station: JavaScript parses the frames, draws to a canvas, renders thermal imagery visually.  
- Additional telemetry (GPS, environmental data) sent via LoRa or ELRS as appropriate.  

---

## Tools & Technologies

- **Hardware**:  
  VELOX motors, GEPRC F722 FC, MLX90640, Walksnail FPV, Radar module, GPS, etc.

- **Firmware / Embedded Software**:  
  ESP32 (for sensors, telemetry), Betaflight (for flight control tuning), PID loops.

- **Languages / Platforms**:  
  C / C++ (firmware), Python (visualization, backend), JavaScript (dashboard / UI).

- **Communication Protocols**:  
  I²C, UART, PWM for sensors & motor control; ELRS, LoRa, FPV links; WebSocket for data transmission.

---

## Getting Started

To run or build the system, follow these steps:

1. **Hardware Assembly**  
   - Assemble frame, mount motors, ESCs, flight controller, sensors.  
   - Integrate power supply (battery), ensure proper wiring, connectors.

2. **Firmware Setup**  
   - Configure flight controller (GEPRC F722) via Betaflight for motor, ESC calibration.  
   - Flash ESP32 with code to capture thermal sensor data and communicate via WiFi / LoRa.

3. **Communication Setup**  
   - Configure ELRS for RC control.  
   - Set up LoRa module and GPS beacon.  
   - Establish wireless AP for thermal frame transmission.

4. **Dashboard / Visualization**  
   - Run a WebSocket server on base station or laptop.  
   - Use provided JavaScript / Python scripts to receive frames, render thermal display.  
   - Display telemetry, environmental sensor read-outs.

5. **Testing & Calibration**  
   - Calibrate PID, motor thrust, sensor accuracy.  
   - Test in safe environment before field deployment.  

---

## Future Improvements

- Payload delivery / drop mechanism (e.g., small packages, first-aid kits, beacons).  
- Longer endurance modules (e.g., solar panels, hybrid power).  
- Enhanced autonomy: obstacle avoidance (via vision / LiDAR), mission planning.  
- Improved thermal resolution or frame rate.  
- More robust case / weather protection, waterproofing.  

---

## License & Contributing

- **License**: *(Add your license here, e.g. MIT, Apache-2.0, etc.)*  
- **Contributing**: Contributions are welcome! If you wish to add features or fix issues:  
  1. Fork the repo  
  2. Create a branch for your feature/fix (`feature/…` or `bugfix/…`)  
  3. Make commits with clear messages  
  4. Submit a Pull Request with description of changes  

---
