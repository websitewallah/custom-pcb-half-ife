# SmartPlant Monitor

A compact custom PCB for intelligent plant health monitoring and automatic care assistance.

## Overview

SmartPlant Monitor is a battery-powered embedded system designed to track the condition of a plant in real time. The board combines environmental sensing, wireless connectivity, and low-power design in a compact form factor suitable for indoor gardens, balconies, greenhouses, and home automation use cases.

The project focuses on solving a very practical problem: plants often need consistent monitoring, but users do not always notice when they are under-watered, over-watered, or exposed to poor lighting conditions. SmartPlant Monitor addresses this by collecting plant health data and making it available locally or through the cloud.

## Problem It Solves

Traditional plant care is often manual and inconsistent. Users forget to check moisture, light, and temperature, which leads to poor plant health. This device helps by continuously measuring the environment around the plant and reporting useful insights in a simple, automated way.

## Core Features

- Soil moisture measurement
- Ambient light detection
- Temperature and humidity tracking
- Low-power operation for battery use
- Wireless communication over WiFi
- Compact PCB layout for easy integration
- Optional cloud dashboard or local data logging

## Hardware Concept

### Microcontroller
- XIAO ESP32-C3
- Small form factor
- Built-in WiFi for remote reporting
- Easy to program and integrate with sensors

### Sensors
- Capacitive soil moisture sensor
- Ambient light sensor
- Temperature and humidity sensor
- Battery voltage monitoring circuit

### Power Design
- 3.7V LiPo battery
- Charging circuit with USB-C input
- 3.3V regulated supply for the MCU and sensors
- Power-saving sleep mode between readings

### Connectivity
- ESP32 WiFi connectivity
- MQTT or HTTP-based data upload
- Optional dashboard integration for live monitoring

## PCB Design Goals

The PCB is designed around a simple but robust architecture:

- keep the MCU and sensor interfaces close together
- minimize trace length for analog sensor inputs
- isolate noisy power paths from sensitive measurement lines
- use a ground plane for stable operation
- optimize the board for 2-layer fabrication and easy assembly

The final board is intended to be compact, clean, and manufacturable without being overly complex.

## System Behavior

1. The board wakes up on a timer interval.
2. It measures soil moisture, ambient light, and environmental conditions.
3. The readings are processed by the microcontroller.
4. The system logs the values and transmits them wirelessly.
5. The user can view trends and plant status through a dashboard or mobile-friendly interface.
6. The device remains in a low-power state between measurements.

## Possible Applications

- Smart indoor plant monitoring
- Balcony garden automation
- Greenhouse sensor nodes
- Home automation integration
- Educational IoT prototyping

## Why This Is a Good Student Project

This project demonstrates several important skills:

- PCB schematic design
- Component selection and layout planning
- Power management design
- Sensor interfacing
- Embedded firmware development
- Wireless communication
- Real-world product thinking

It is practical, understandable, and relevant to modern electronics and IoT work.

## Target Components

| Quantity | Component | Purpose |
| --- | --- | --- |
| 1 | XIAO ESP32-C3 | Main controller |
| 1 | Capacitive soil moisture sensor | Detect root hydration |
| 1 | BH1750 / similar | Measure ambient light |
| 1 | BME680 / similar | Temperature, humidity, and air data |
| 1 | TP4056 | Battery charging |
| 1 | 3.3V regulator | Power conversion |
| 1 | LiPo battery | Main power source |
| 1 | USB-C connector | Charging and programming |
| Various | Resistors, capacitors, headers | Supporting circuitry |

## Future Improvements

- Add an automatic watering relay
- Include soil pH sensing
- Add solar charging support
- Extend to a multi-plant network
- Add a mobile app or web dashboard
- Support OTA firmware updates

## Project Summary

SmartPlant Monitor is a realistic custom PCB concept that combines sensing, power management, and IoT connectivity in a small, practical device. It is a strong student project because it is easy to explain, useful in the real world, and demonstrates meaningful engineering skills across hardware and software.

This project reflects a complete product mindset: identify a real problem, design a solution, prototype it, and prepare it for future refinement.

---

SmartPlant Monitor PCB project
