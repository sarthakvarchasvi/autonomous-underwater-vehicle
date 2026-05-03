# 🌊 Autonomous Underwater Vehicle (AUV)

> **Blackvolt Technologies Pvt. Ltd.** | Aug 2025 – Present  
> Maritime Surveillance · GPS-Denied Autonomy · 150m Depth Target

[![Status](https://img.shields.io/badge/Status-Active_Development-red?style=flat-square)]()
[![Depth](https://img.shields.io/badge/Target_Depth-150m-0077B6?style=flat-square)]()
[![Endurance](https://img.shields.io/badge/Endurance-30_days-0077B6?style=flat-square)]()

> ⚠️ **Note:** Hardware designs and control code are proprietary to Blackvolt Technologies Pvt. Ltd. This repository documents the system architecture and design philosophy.

---

## Overview

Full-stack autonomous underwater vehicle development for maritime surveillance applications — designed, architected, and being built under **Blackvolt Technologies** (V-NEST incubated, VIT Chennai).

---

## Target Specifications

| Parameter | Target Value | Rationale |
|---|---|---|
| Depth Rating | 150 m | Coastal and shallow-sea surveillance coverage |
| Mission Endurance | 30 days | Persistent deployment without surface recovery |
| Navigation | GPS-denied (DVL + IMU) | Subsea environments have no GPS |
| Motion Profile | Sawtooth dive pattern | Battery efficiency via buoyancy cycling |
| Recharging | Inductive (under exploration) | Enables truly persistent deployment |

---

## System Architecture

```
┌─────────────────────────────────────────────────────┐
│                   Mission Computer                   │
│         (High-level autonomy · Mission planning)     │
└──────────────┬──────────────────────┬───────────────┘
               │                      │
┌──────────────▼──────┐    ┌──────────▼──────────────┐
│   Navigation Stack   │    │    Control Architecture  │
│  DVL Odometry        │    │  Propulsion Control      │
│  IMU Fusion          │    │  Thruster Allocation     │
│  Depth Sensing       │    │  Failure Handling        │
│  Localisation        │    │  Graceful Degradation    │
└─────────────────────┘    └─────────────────────────┘
               │
┌──────────────▼──────────────────────────────────────┐
│              Sensor Fusion Layer                      │
│   DVL (Doppler Velocity Log) · IMU · Depth Sensor   │
│   Redundant sensing · Cross-validation              │
└─────────────────────────────────────────────────────┘
```

---

## Key Design Decisions

**Sawtooth Motion Profile**  
Rather than constant-depth cruise, the AUV follows a sawtooth dive pattern — diving under power, gliding back up using buoyancy. This dramatically extends battery endurance by leveraging physics instead of fighting it.

**Graceful Degradation Architecture**  
The control architecture is designed to degrade gracefully rather than fail catastrophically. If DVL drops out, navigation falls back to IMU dead reckoning with increasing uncertainty bounds. If a thruster fails, the allocation matrix reconfigures automatically.

**Inductive Underwater Recharging (Research)**  
Exploring subsea inductive charging to enable indefinite persistent deployment — removing the fundamental constraint that currently limits AUV missions to battery endurance windows.

---

## Prior Relevant Experience

Before this project, underwater systems experience was built through:
- 6 months at **Mafkin Robotics** — NVIDIA Jetson Nano, ROS 2, encoder feedback for underwater actuators, FPV integration for ROV systems
- Hands-on with DVL, IMU, and depth sensors in embedded environments

---

## Status

🔴 Active development under Blackvolt Technologies  

---

*Blackvolt Technologies Pvt. Ltd. | V-NEST, VIT Chennai*
