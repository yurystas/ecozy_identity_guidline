# Open Architecture

<img src="/assets/illustrations/architecture.jpeg" alt="eCozy System Architecture" width="66%" />

*eCozy smart climate control system architecture diagram*

## System Overview

The eCozy smart climate control system is built on a modern, open architecture that integrates multiple components across different technology layers. The architecture is designed for scalability, reliability, and seamless integration with smart home ecosystems.

## Architecture Components

### Device Layer (Hardware)

#### 1. **eCozy Thermostats**
- **Microcontroller:** Nordic nRF5340 (dual-core ARM Cortex-M33)
- **Firmware:** Zephyr RTOS-based Nordic SDK v2.6.0
- **Connectivity:** Matter-over-Thread protocol
- **Power:** Battery-powered with low-power design
- **Functions:**
  - Temperature sensing and control
  - Valve actuation for radiator control
  - Local decision-making capabilities
  - Communication with central unit and sensors

#### 2. **eCozy Climate Sensors**
- **Microcontroller:** Nordic nRF52840 SoC
- **Firmware:** Matter-compatible firmware
- **Sensors:** Temperature and humidity sensing
- **Connectivity:** Matter protocol (Thread), future-ready for Zigbee/Bluetooth
- **Functions:**
  - Accurate remote temperature and humidity monitoring
  - Wireless data transmission to central unit
  - Integration with Apple, Google, Amazon Matter ecosystems

#### 3. **Central Unit (Gateway)**
- **Platform:** Embedded Linux system
- **Functions:**
  - Data aggregation from thermostats and sensors
  - Climate control algorithm execution
  - Matter-over-Thread network coordination
  - Cloud connectivity and data synchronization
  - Local processing and decision-making

### Communication Layer

#### Matter-over-Thread Protocol
- **Standard:** Matter (formerly Project CHIP) - unified smart home standard
- **Network:** Thread mesh networking
- **Benefits:**
  - Low power consumption
  - Reliable mesh topology
  - Interoperability with major smart home platforms
  - Secure device-to-device communication
  - Local control without cloud dependency

### Backend Layer (Cloud Services)

#### Server Infrastructure
- **Technology Stack:** Node.js / TypeScript
- **Database:** PostgreSQL with TypeORM
- **Hosting:** AWS infrastructure
- **API:** RESTful APIs for device and user management
- **Functions:**
  - User authentication and authorization
  - Device registration and management
  - Historical data storage and analytics
  - Remote control and monitoring
  - Firmware update distribution

### Application Layer

#### Mobile Applications
- **Platforms:** iOS and Android
- **Architecture:** Clean Architecture with MVVM pattern
- **Features:**
  - Device setup and onboarding
  - Real-time temperature monitoring
  - Schedule and automation management
  - Remote control (cloud mode)
  - Local control (local mode)
  - Energy consumption analytics

### Integration Layer

#### Smart Home Ecosystem Integration
- **Apple HomeKit:** Native Matter support
- **Google Home:** Matter device integration
- **Amazon Alexa:** Matter-compatible control
- **Third-party integrations:** Open API for custom integrations

## Key Architecture Principles

### 1. **Open Standards**
- Built on Matter protocol for maximum interoperability
- Support for multiple communication protocols (Thread, Zigbee, Bluetooth)
- RESTful API design for easy third-party integration

### 2. **Modular Design**
- Each component (thermostat, sensor, central unit, cloud) operates independently
- Easy to scale by adding more devices
- Firmware and software updates can be deployed independently

### 3. **Dual-Mode Operation**
- **Cloud Mode:** Remote access, cloud analytics, multi-location management
- **Local Mode:** Privacy-focused, operates without internet, low latency

### 4. **Security & Privacy**
- End-to-end encryption for device communication
- Secure boot and firmware signing
- GDPR-compliant data handling
- User choice between cloud and local operation

### 5. **Energy Efficiency**
- Battery-powered devices with optimized power consumption
- Thread mesh network reduces radio transmission overhead
- Intelligent scheduling reduces unnecessary heating

### 6. **Developer-Friendly**
- Well-documented APIs
- Open development standards
- CI/CD pipeline for automated testing and deployment
- GitLab-based version control and collaboration

## Data Flow

1. **Sensing:** Climate sensors and thermostats measure temperature and humidity
2. **Local Processing:** Central unit receives data via Matter-over-Thread
3. **Decision Making:** Central unit executes climate control algorithms
4. **Actuation:** Commands sent to thermostats to adjust heating
5. **Cloud Sync:** Data synchronized to cloud for analytics and remote access
6. **User Interaction:** Mobile apps display status and allow user control

## Technology Stack Summary

| Component | Technology |
|-----------|------------|
| Thermostat MCU | Nordic nRF5340 |
| Sensor MCU | Nordic nRF52840 |
| Firmware OS | Zephyr RTOS |
| Communication | Matter-over-Thread |
| Central Unit OS | Embedded Linux |
| Backend | Node.js, TypeScript |
| Database | PostgreSQL |
| Mobile Apps | iOS (Swift), Android (Kotlin) |
| Cloud Infrastructure | AWS |
| CI/CD | GitLab CI |
| Version Control | GitLab |

## Benefits of This Architecture

✅ **Interoperability:** Works with major smart home platforms  
✅ **Scalability:** Easy to add more devices to the system  
✅ **Reliability:** Mesh network ensures robust communication  
✅ **Privacy:** Local operation mode for privacy-conscious users  
✅ **Energy Efficiency:** Optimized for battery-powered operation  
✅ **Future-Proof:** Based on open standards with migration path to newer hardware  
✅ **Developer-Friendly:** Clear separation of concerns, well-documented APIs
