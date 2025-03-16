# 🧠 Simethesia Lab

**Simethesia** is a modular and interactive platform for anesthesia control simulation, combining pharmacokinetic/pharmacodynamic (PK/PD) models, clinical challenges, and a real-time simulated patient.

This project is built for students, researchers, and enthusiasts in biomedical engineering, control systems, and healthcare technology. It connects theory and practice by allowing you to apply and test control algorithms on a virtual patient that responds like a real one.

## 🔗 Project Repositories

| Repository | Description |
|------------|-------------|
| [`simethesia-simulator`](https://github.com/simethesia/simethesia-simulator) | Real-time BIS simulator using PK/PD models on Arduino |
| [`simethesia-controller`](https://github.com/simethesia/simethesia-controller) | Control algorithms (PID, LQR, etc.) to regulate anesthesia |
| [`simethesia-app`](https://github.com/simethesia/simethesia-app) | Mobile interface to configure patients and monitor simulations |

## ⚙️ How It Works

The architecture is divided into three modules:

- The **controller** calculates the optimal infusion rate based on the BIS error (target – current).
- The **simulator** updates the BIS in real time using PK/PD equations.
- The **app** allows users to configure the simulation, activate clinical events, and visualize results.

## 🧪 Mathematical Models

We use a 3-compartment PK model with an effect site (Ce) linked to the BIS calculation.

### 1. Pharmacokinetic Model

dc1/dt = (u / V1) - (k10 + k12 + k13) * c1 + (V2/V1) * k21 * c2 + (V3/V1) * k31 * c3  
dc2/dt = (V1/V2) * k12 * c1 - k21 * c2  
dc3/dt = (V1/V3) * k13 * c1 - k31 * c3

### 2. Effect Compartment

dCe/dt = ke0 * (c1 - Ce)

### 3. BIS Calculation

BIS = E0 - (Emax * Ce^gamma) / (Ce50^gamma + Ce^gamma)


Where:
- `u`: infusion rate  
- `Ce`: effect-site concentration  
- `E0`: baseline BIS  
- `Emax`: maximum drug effect  
- `Ce50`: concentration at 50% effect  
- `γ`: sensitivity parameter

## 📚 Future Features

### 🌐 Web Interface for Remote Simulation
- Monitor and interact with simulations via a browser.
- Access BIS trends, infusion rates, and performance metrics remotely.

### 👨‍🎓 Student Mode
- Simplified interface for learners.
- Step-by-step experiment guides with preset clinical scenarios.
- Real-time explanations of BIS responses and control effects.

### 👩‍🏫 Evaluator Mode
- Designed for instructors and researchers.
- Provides automatic performance metrics:
  - Response time
  - Mean Absolute Error (MAE)
  - Stability and overshoot
- Exportable logs and graphical results.
- Instant feedback and recommendations based on controller performance.

## 🧠 Why Simethesia?

- Built with real pharmacological models  
- Modular: use your own controller, interface, or patient profile  
- Educational focus with real-time interaction  
- Supports hardware-in-the-loop simulations  

## 🤝 Contribute

Want to help us improve Simethesia?

- Report bugs or suggest improvements  
- Add new control algorithms (PID, LQR, MPC, etc.)  
- Translate the app or documentation  
- Create new patient profiles or challenges  

We’re building an open, collaborative community.  
If you’re into control systems, healthcare, or simulation — **this project is for you.**

---

Crafted with 💡 science, 💉 curiosity, and ❤️ for learning that feels real.




