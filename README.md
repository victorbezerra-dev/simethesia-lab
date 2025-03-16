# 🧠 Simethesia Lab

**Simethesia** is a modular and interactive platform for simulating anesthesia control systems, combining advanced pharmacokinetic/pharmacodynamic (PK/PD) models, realistic clinical challenges, and a virtual patient responding in real time.

Built for students and professionals in control engineering, biomedical engineering, medical enthusiasts, and healthcare professionals interested in clinical simulation, Simethesia bridges theory and practice by enabling hardware-in-the-loop simulation to develop, test, and refine anesthesia control algorithms in a safe, realistic, and interactive environment.

## 🔗 Project Structure

The **Simethesia** ecosystem is divided into three complementary repositories:

| Repository | Description |
|------------|-------------|
| [`simethesia-simulator`](https://github.com/simethesia/simethesia-simulator) | Real-time patient simulation using PK/PD models (Arduino-based). |
| [`simethesia-controller`](https://github.com/simethesia/simethesia-controller) | Control algorithms (PID, LQR, MPC, etc.) for regulating anesthesia depth |
| [`simethesia-app`](https://github.com/simethesia/simethesia-app) | Mobile application to configure patient data, manage simulations, and visualize results |

## ⚙️ How It Works

The Simethesia system comprises three integrated components:

- **Patient Simulator:** Computes real-time BIS responses using advanced PK/PD models.
- **Controller:** Calculates drug infusion rates based on the difference between desired and actual patient BIS values.
- **Mobile App**: Offers intuitive interfaces for configuring simulations, activating clinical challenges, and visualizing real-time data.


## 🧪 Pharmacokinetic & Pharmacodynamic Models

Simethesia uses a validated 3-compartment pharmacokinetic (PK) model combined with a pharmacodynamic (PD) effect-site compartment. These models realistically simulate how propofol distributes throughout the body and influences brain activity, measured through the Bispectral Index (BIS), a common anesthetic depth indicator.

### 1. Pharmacokinetic Model (3-Compartment)

The PK model describes drug distribution and elimination dynamics in three compartments: central, shallow peripheral, and deep peripheral.

```text
dc₁/dt = (u / V₁) − (k₁₀ + k₁₂ + k₁₃) × c₁ + (V₂ / V₁) × k₂₁ × c₂ + (V₃ / V₁) × k₃₁ × c₃  
dc₂/dt = (V₁ / V₂) × k₁₂ × c₁ − k₂₁ × c₂  
dc₃/dt = (V₁ / V₃) × k₁₃ × c₁ − k₃₁ × c₃
```
**Where:**

- `c₁`, `c₂`, `c₃`: Drug concentrations in central, shallow peripheral, and deep peripheral compartments  
- `V₁`, `V₂`, `V₃`: Volumes of each compartment  
- `k₁₀`: Elimination rate constant from central compartment  
- `k₁₂`, `k₂₁`, `k₁₃`, `k₃₁`: Inter-compartmental transfer rate constants  
- `u`: Infusion rate (drug input)

### 2. Effect-site compartment (Pharmacodynamic Model)

The PD model introduces a delay between the plasma concentration (central compartment) and the observed clinical effect (e.g., BIS):

```text
dCe/dt = ke₀ × (c₁ − Ce)
```
**Where:**

- `Ce`: Effect-site concentration (responsible for clinical effect)  
- `ke₀`: Rate constant determining the speed of drug equilibration between plasma and effect-site compartment

### 📈 BIS Calculation (Drug Effect Model)

The BIS (Bispectral Index) quantifies the patient's depth of anesthesia, calculated by a sigmoid relationship with the effect-site concentration:

```text
BIS = E₀ − (Emax × Ce^γ) / (Ce₅₀^γ + Ce^γ)
```

**Where:**

- `BIS`: Bispectral Index (ranges approximately from 0 to 100)  
- `E₀`: Baseline BIS (awake state, typically ~95–100)  
- `Emax`: Maximum achievable drug effect  
- `Ce₅₀`: Effect-site concentration associated with 50% of maximal effect  
- `γ` (gamma): Steepness factor of the drug response curve  
- `Ce`: Effect-site concentration computed from the PD model

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




