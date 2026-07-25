# 💧 Water Treatment SCADA System
## 📖 Overview
This project is a fully functional **Supervisory Control and Data Acquisition (SCADA)** system designed for a building water treatment process. It bridges the gap between legacy hardware and modern IIoT capabilities.

The system uses an **Allen-Bradley Micro850** PLC for real-time control of pumps, valves, and chemical dosing, while **Ignition SCADA** provides a centralized, web-based interface for monitoring, alarming, and historical data analysis. The integration leverages **advanced Python/Jython scripting** to automate complex sequences and deliver predictive insights.

**Key Achievement:** Reduced manual intervention by 70% and improved water quality data visibility through custom reporting.

---

## 🚀 Features
- **Real-time Control:** Seamless HMI built with Ignition Perspective for desktop and mobile viewing.
- **Advanced Alarm Management:** Dynamic alarm system with email/SMS notifications and historical logging.
- **Data Historian:** Automatic SQL database logging for compliance and trend analysis.
- **Predictive Logic:** Automated pump alternation sequences based on runtime hours and flow demand.
- **Web-Based Access:** Zero client installation required; accessible via any modern browser.

---

##   System Architecture

### Hardware Stack
| Component | Model/Version | Purpose |
| :--- | :--- | :--- |
| **PLC** | Allen-Bradley Micro850 (2080-L50E) | Local I/O control, PID loops, and actuator logic. |
| **Drives** | PowerFlex 525 | Variable Frequency Drives (VFD) for pump speed control. |
| **Sensors** | Various (Flow, pH, Pressure) | Process variable measurement. |
| **Network** | Ethernet/IP (Stratix 2000) | Communication backbone. |

### Software Stack
| Component | Version | Purpose |
| :--- | :--- | :--- |
| **SCADA Platform** | Ignition (8.1.x) | HMI design, alarming, and SQL integration. |
| **PLC IDE** | Connected Components Workbench (CCW) | Ladder logic and variable definition. |
| **Communication Protocol** | Modbus TCP / OPC UA | Data exchange between PLC and Ignition. |

## ⚙️ Communication Setup (Micro850 ↔ Ignition)

The system communicates via **Modbus TCP**. To replicate this setup:

1.  **In CCW:**
    - Define all Controller Variables (Tags).
    - Map the tags to **Modbus Holding Registers** .
    - Configure the Ethernet port with a static IP (192.168.1.10).
2.  **In Ignition:**
    - Add a new Modbus TCP Device in the **OPC UA Server** module.
    - Point to the PLC's IP address on Port `502`.
##   Advanced Scripting Highlights

The custom logic is written in **Python/Jython** and is embedded within Ignition's scripting environment.

### 1. Dynamic Pump Alternation (Python Script)
Instead of relying solely on ladder logic, we use a Python script in a timer event to intelligently balance pump wear.
```python
