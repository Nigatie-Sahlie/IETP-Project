# CO₂ Capture and Air Purification System

> **Integrated Engineering Team Project (IETP) — Group 36**  
> Addis Ababa Science and Technology University, College of Engineering  
> Submitted: January 2024 | Advisor: Inst. Melaku Enyeayhu

---

## Table of Contents

- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Objectives](#objectives)
- [System Architecture](#system-architecture)
- [Hardware Components](#hardware-components)
- [Software Stack](#software-stack)
- [How It Works](#how-it-works)
- [Engineering Analysis](#engineering-analysis)
- [Results](#results)
- [SDG Alignment](#sdg-alignment)
- [Limitations & Future Work](#limitations--future-work)
- [Team](#team)
- [Repository Contents](#repository-contents)

---

## Overview

This project presents the design and prototyping of a **chemical CO₂ absorption system** that captures and removes carbon dioxide from ambient air. The system uses a **sodium hydroxide (NaOH) solution** as the primary absorbent, housed in a PVC chamber, combined with an **Arduino-controlled sensor and fan assembly** for automated monitoring and airflow regulation. A companion **Flutter mobile application** enables real-time CO₂ data visualization and remote monitoring.

The project targets urban air quality improvement and is designed to be modular and scalable — from small indoor deployments to large industrial settings.

---

## Problem Statement

Atmospheric CO₂ concentration reached **0.04% (400 ppm)** in 2024, driven primarily by fossil fuel combustion, deforestation, and industrial processes. Rising CO₂ levels are a leading driver of global warming and urban air quality degradation. This project addresses the need for **practical, cost-effective carbon capture solutions** deployable in real-world environments.

---

## Objectives

### General Objective
Design, develop, and test a functional prototype of a CO₂ capture system using NaOH to measurably reduce carbon dioxide concentration in the surrounding environment.

### Specific Objectives
1. Design a structural enclosure suitable for various deployment environments.
2. Engineer a chemical mechanism to effectively capture and remove CO₂ from inlet air.
3. Integrate real-time CO₂ monitoring via sensors and a mobile application.
4. Simulate the circuit design using **Proteus** prior to physical implementation.
5. Program sensors to accurately measure CO₂ levels at both inlet and outlet air streams.
6. Implement a feedback loop to dynamically adjust system operation based on sensor readings.
7. Optimize the system for ease of installation, maintenance, and scalability.

---

## System Architecture

```
[ Ambient Air (Inlet) ]
         │
         ▼
  [ Air Pump + Fans ]  ──── Regulated by Arduino
         │
         ▼
[ NaOH Solution Chamber ]  ──── CO₂ reacts with NaOH
         │                        CO₂ + 2NaOH → Na₂CO₃ + H₂O
         ▼                        Na₂CO₃ + CO₂ + H₂O → 2NaHCO₃
  [ MQ-135 Gas Sensor ]  ──── Measures outlet CO₂ concentration
         │
         ▼
  [ Arduino Uno ]  ──── Processes sensor data, controls pump/fans
         │
         ▼
  [ Flutter Mobile App ]  ──── Real-time monitoring dashboard
```

---

## Hardware Components

| Component | Description |
|---|---|
| **Arduino Uno** | Central microcontroller; reads sensor data and controls actuators |
| **MQ-135 Gas Sensor** | Measures CO₂ (and other gas) concentrations at inlet and outlet |
| **Air Pump** | Drives airflow through the NaOH absorption chamber |
| **Fans** | Maintain consistent airflow rate for optimal CO₂ exposure |
| **NaOH Solution** | Primary chemical absorbent for CO₂ |
| **PVC Chamber** | Enclosure for the NaOH solution |
| **Breadboard & Jumper Wires** | Circuit prototyping connections |
| **DC Power Supply** | Powers the system |
| **Plastic Enclosure** | Structural housing for all components |

---

## Software Stack

| Tool / Technology | Purpose |
|---|---|
| **Arduino IDE (C/C++)** | Microcontroller programming |
| **Flutter (Dart)** | Cross-platform mobile monitoring app |
| **Proteus** | Circuit simulation and validation |
| **Microsoft Visio** | System design and workflow visualization |

---

## How It Works

1. **Airflow**: An air pump and fans draw ambient air into the system at a calculated flow rate, determined by:

   ```
   Q = A × v
   ```
   where `Q` is the airflow rate, `A` is the cross-sectional area of the chamber, and `v` is the air velocity.

2. **Absorption**: CO₂-laden air passes through the NaOH solution chamber. CO₂ reacts chemically with NaOH:

   ```
   CO₂ + 2NaOH  →  Na₂CO₃ + H₂O      (primary reaction)
   Na₂CO₃ + CO₂ + H₂O  →  2NaHCO₃    (secondary reaction)
   ```

3. **Sensing**: The MQ-135 sensor measures CO₂ concentration at the outlet. Readings are sent to the Arduino as an analog signal.

4. **Control Loop**: The Arduino adjusts pump and fan operation in real time based on sensor readings. When CO₂ levels exceed a predefined threshold, the system intensifies airflow.

5. **Monitoring**: Sensor data is transmitted to the Flutter mobile app, providing a real-time dashboard of CO₂ concentration, system status, and historical trends.

6. **Maintenance Alert**: When the NaOH solution becomes saturated (converts to Na₂CO₃), the system signals the need for solution replacement to maintain absorption efficiency.

---

## Engineering Analysis

- **Absorption Efficiency**: Validated through comparative measurement of inlet vs. outlet CO₂ concentrations in ppm (see *Figure 4.2* in the final report).
- **Power Consumption**: The system is designed for minimal energy use through optimized fan and pump control logic.
- **Material Selection**: NaOH was chosen for its high CO₂ absorption capacity, wide availability, and relatively low cost.
- **Economic Analysis**: Includes operating costs and a cost-benefit analysis demonstrating the viability of the system for practical deployment (see *Chapter 4* of the final report).
- **Simulation**: All circuit designs were validated in Proteus before hardware assembly.

---

## Results

- Measurable reduction in CO₂ concentration between inlet and outlet air streams was demonstrated in testing.
- The MQ-135 sensor successfully detected CO₂ level changes and triggered appropriate system responses.
- The Flutter app displayed real-time CO₂ readings from the Arduino over the monitoring period.
- The prototype confirmed the feasibility of NaOH-based chemical absorption as a compact CO₂ capture solution.

> Detailed test data, CO₂ concentration graphs, and result discussion can be found in **Chapter 5** of the final report.

---

## SDG Alignment

| SDG | Relevance |
|---|---|
| **SDG 13 – Climate Action** | Directly reduces atmospheric CO₂, contributing to climate change mitigation |
| **SDG 9 – Industry, Innovation & Infrastructure** | Advances sustainable engineering through interdisciplinary innovation |
| **SDG 3 – Good Health and Well-being** | Improves air quality in urban environments, supporting public health |

---

## Limitations & Future Work

**Current Limitations:**
- Prototype scale is limited to small-scale indoor environments.
- NaOH regeneration (requiring temperatures >600°C) is energy-intensive and not yet implemented in the prototype.
- Budget and material constraints affected initial prototype quality.
- Team coordination across 11 members from different engineering disciplines posed integration challenges.

**Planned Improvements:**
- Integrate renewable energy (solar/geothermal) to power NaOH regeneration.
- Explore electrochemical regeneration methods to reduce energy costs.
- Develop hybrid capture systems combining NaOH with other sorbent technologies.
- Scale the system for industrial and large-scale urban deployment.
- Improve the Flutter app with historical data logging and alert notifications.

---

## Team

| Name | Student ID |
|---|---|
| Abraham Tilksew Taye | ETS0105/14 |
| Michael Addis Aniley | ETS1060/14 |
| Rehima Aman Awol | ETS1352/14 |
| Nigatie Sahlie Azezew | ETS1302/14 |
| Bona Tariku Jaleta | ETS0399/14 |
| Lencho Habtamu Namara | ETS0959/14 |
| Bersabeh Abebe Mulugeta | ETS0305/14 |
| Sagni Rago Terefa | ETS1391/14 |
| Henok Solomon Asgodom | ETS0778/14 |
| Elam Workiye Abayneh | ETS0512/14 |
| Abel Addis Gebreegziabher | ETS0036/14 |

**Advisor:** Inst. Melaku Enyeayhu  
**Institution:** Addis Ababa Science and Technology University, College of Engineering

---

## Repository Contents

| File | Description |
|---|---|
| `IETP proposal.pdf` | Initial project proposal outlining objectives, methodology, timeline, and budget |
| `IETP_Group_36_Final_Report.pdf` | Comprehensive final report covering literature review, engineering analysis, testing, and results |

---

*This project was developed as part of the Integrated Engineering Team Project (IETP) program at ASTU.*
