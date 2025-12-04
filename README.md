# 7.5kW Asynchronous Motor Inverter with SVPWM Control

A comprehensive project for the design and implementation of a 7.5kW, 3-phase asynchronous motor inverter. This project features a robust control system based on Space Vector Pulse Width Modulation (SVPWM) for efficient and precise motor control.

![Project Image](placeholder.png)
*(To Be Added, Please check https://www.linkedin.com/in/dewapramudya/ -> Project for updated image)*

---

## Features
* **Power Rating:** 7.5 kW
* **Input Voltage:** 220V-AC, 315V-DC
* **Control Strategy:** Space Vector Pulse Width Modulation (SVPWM)
* **Microcontroller:** ARM Cortex M3+
* **Key Components:** IGBTs, Gate Drivers, Injected Current Sensor
* **Protections:** Power Limit, Under Voltage Lock-Out.

## Hardware
This section details the electronic components and hardware design.

* **MCU:** STM32F103C8T6 Barebone Chip
* **Gate Driver:** ONSemi FAN7842
* **Power Stage:** 2MBI100U4A-120-50
* **Sensors:** Shunt Biased Amplifier (OPA365), High Voltage Dividers, NTCs.

The schematic and PCB layout files can be found in the `/hardware` directory.

## Firmware
The firmware is developed using the STM32 HAL libraries in C. The core logic involves:

1.  **Center-Aligned Complementary PWM:** Great for motor control for reducing the Total Harmonic Distortion (THD) since it keeps the switch between phases happened in different timing.
2.  **Injected ADC Reading:** For current feedback, it is sampling the ADC right at the middle of High Side IGBT on state.
3.  **PI Controllers:** To regulate motor speed and torque.
4.  **SVPWM Generation:** Involving the Look-Up Table (LUT) to generate the correct PWM signals for the IGBT gate drivers.

## Theory of Operation
The control system uses SVPWM to reduce THD and optimize bus voltage utilization compared to standard SPWM. The LUT is being used to reduce the computational burden load. It shifted by 120° deg between each phase. These vectors are then used to calculate the appropriate PWM duty cycles for the six inverter switches.

## Demonstration
more image and testing on my LinkedIn: [dewapramudya](https://linkedin.com/in/dewapramudya)

## Project Status: **Complete**
---
*Created by Dewa Pramudya, 2025*
