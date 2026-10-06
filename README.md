# SmartPlant Monitor PCB

A custom ESP32-based environmental monitoring system for real-time plant health tracking.

## Overview

SmartPlant Monitor is a compact, IoT-enabled PCB that measures soil moisture, ambient light, temperature, and humidity to help users keep their plants thriving. The device communicates wirelessly via WiFi and stores data in the cloud for trend analysis.

## Key Features

- **Real-time Monitoring**: Continuous tracking of 4 environmental parameters
- **Compact Design**: 50mm x 80mm form factor fits seamlessly into any plant pot
- **Low Power**: Sleep modes for extended battery life
- **Cloud Integration**: MQTT protocol for easy cloud connectivity
- **Accessible Interface**: Simple web dashboard for data visualization
- **Modular**: Easy to extend with additional sensors

## Hardware Specifications

### Microcontroller
- **XIAO ESP32-C3**: Dual-core processor, WiFi/BLE capable, 4MB flash

### Sensors
- **Capacitive Soil Moisture Sensor**: 0-100% range, analog input
- **BH1750 Ambient Light Sensor**: I2C interface, 1-65535 lux range
- **BME680 Environmental Sensor**: Temperature, humidity, pressure, and air quality via I2C
- **Battery Monitoring**: ADC input for LiPo voltage monitoring

### Power
- **LiPo Battery**: 3.7V 1000mAh rechargeable
- **TP4056 Charging Module**: USB-C charging input
- **MCP73871**: Battery management IC

### Connectivity
- **ESP32-C3 WiFi**: 802.11b/g/n @ 2.4GHz
- **Antenna**: PCB trace antenna for compact design

## PCB Design

### Schematic Details
- Power management with LDO regulator (AMS1117-3.3V)
- I2C bus with pull-up resistors for dual sensors
- ADC filtering capacitors for battery monitoring
- ESD protection on all sensor inputs

### Layout Strategy
- 2-layer PCB optimized for manufacturing cost
- Sensor placement on bottom layer for better environmental contact
- Battery connector positioned for easy access
- Charging port on edge for accessibility

### Manufacturing
- Board size: 50mm × 80mm
- Thickness: 1.6mm
- Copper weight: 1oz
- Surface finish: HASL

## Firmware Architecture

### Core Functionality
- Deep sleep between measurements (10-minute intervals)
- MQTT publish to Home Assistant or custom server
- Local data buffering during WiFi disconnects
- Over-the-air (OTA) firmware updates

### Libraries Used
- ESP32 Arduino Core
- Adafruit BME680 & BH1750 drivers
- PubSubClient for MQTT

## Development Timeline

- **Week 1-2**: Schematic design & component selection
- **Week 3**: PCB layout & routing
- **Week 4**: Design review & Gerber export
- **Week 5-6**: Manufacturing & assembly
- **Week 7**: Firmware development & testing
- **Week 8**: Integration & deployment

## Bill of Materials (BOM)

| Qty | Reference | Part Number | Description |
|-----|-----------|------------|-------------|
| 1 | U1 | ESP32-C3-XIAO | Microcontroller |
| 1 | U2 | BME680 | Environmental sensor |
| 1 | U3 | BH1750 | Light sensor |
| 1 | U4 | AMS1117-3.3 | 3.3V LDO regulator |
| 1 | U5 | MCP73871 | Battery charger |
| 1 | J1 | USB-C | Power/charging connector |
| 1 | J2 | 2-pin JST | Battery connector |
| 1 | J3 | 4-pin JST | Moisture sensor header |
| 10 | R1-R10 | 10kΩ 0805 | Pull-ups, filtering |
| 5 | C1-C5 | 100nF 0805 | Decoupling caps |
| 2 | C6-C7 | 10µF 1206 | Power supply caps |
| 1 | BT1 | 1000mAh LiPo | Rechargeable battery |

## Project Goals

This project demonstrates:
- **Full hardware design cycle** from concept to manufacturing
- **Sensor integration** and analog signal conditioning
- **Power management** for IoT devices
- **Cloud connectivity** best practices
- **Real-world IoT application** solving an actual problem

## Lessons Learned

- Importance of proper decoupling for stable ADC readings
- I2C bus timing and pull-up resistor selection
- Battery voltage monitoring and charge protection
- Antenna design trade-offs in compact PCBs

## Future Enhancements

- Add humidity-triggered watering alerts
- Implement image recognition for plant species identification
- Multi-plant network with mesh communication
- Solar charging for completely autonomous operation

---

**Author**: SmartPlant Development Team  
**Start Date**: October 2026  
**Repository**: websitewallah/custom-pcb-half-ife
