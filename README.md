# 🌬️ Horizontal Axis Wind Turbine Blade – CFD, FSI & Modal Analysis

This folder contains our **Computer-Aided Design and Engineering (CAD)** final project, where we analyzed a **Horizontal Axis Wind Turbine (HAWT) blade** using ANSYS for 3D steady-state CFD, structural analysis, and modal analysis.

## 📌 Course

- Course: Computer-Aided Design and Engineering – Fall 2024  
- University: University of Science and Technology – Zewail City  
- Project: Final Project – Group 7  
- Supervisor: Dr. Mohamed Abdelnaby  
- TA: Eng. Omar Khattab  
- Students: Phelopater Ramsis, Manar Tarek, Marwa Ali :contentReference[oaicite:0]{index=0}  

---

## 🧾 Project Overview

The project investigates the **aeromechanical performance, structural stresses, and vibration behavior** of a wooden HAWT blade at:

- Wind speed: **9 m/s**  
- Rotational speed: **400 rpm**  

Main objectives:

1. **3D Steady CFD Analysis** – predict aerodynamic loads, torque, and power.  
2. **Fluid–Structure Interaction (FSI)** – estimate stresses and deformation.  
3. **Modal Analysis** – compute natural frequencies and mode shapes to check resonance.  
4. **Power & Efficiency** – compute turbine power and power coefficient. :contentReference[oaicite:1]{index=1}  

---

## 🧱 Geometry & Preprocessing

### ✏️ Blade Geometry

- Blade was first designed in **Autodesk Inventor** in a previous assignment.  
- Edges were **filleted** and curvature checked to avoid sharp features. :contentReference[oaicite:2]{index=2}  
- Geometry was then imported into **SpaceClaim (ANSYS)** and re-oriented to fit the CFD domain.

### 🕸️ Meshing & Grid Study

Steps:

1. Import geometry into ANSYS Meshing.  
2. Apply **local sizing** on blade surfaces.  
3. Generate **surface mesh** (triangular cells) and refine near the blade.  
4. Set **periodic boundaries** to model a rotor sector.  
5. Generate **volume mesh** with a controlled element size and quality.  
6. Report mesh statistics: element count, skewness, orthogonal quality, etc. :contentReference[oaicite:3]{index=3}  

An enhanced meshing procedure was used (multiple trials) to fix issues like sharp edges and low-quality elements. Surface quality limit was tightened to **0.9** to improve CFD reliability. :contentReference[oaicite:4]{index=4}  

---

## 🧮 CFD Setup (Fluent)

### 🌡️ Viscous Model

- Turbulence model: **k–ω SST (2-equation model)**  
  - Good compromise between accuracy near the wall and free-stream behavior. :contentReference[oaicite:5]{index=5}  

### 💨 Fluid Motion & Rotating Region

- Rotating cell zone used to impose angular speed (rpm converted to rad/s). :contentReference[oaicite:6]{index=6}  

### 🔁 Boundary Conditions

- **Inlet:**  
  - Velocity inlet, Z-direction speed = **9 m/s**  
- **Outlet:**  
  - Pressure outlet (gauge pressure = 0)  
- Blade surfaces set as **no-slip walls**. :contentReference[oaicite:7]{index=7}  

### 📉 Convergence Monitoring

- Residual monitors for: continuity, x/y/z-velocity, k, ω.  
- Several hundred iterations until all equations dropped to target residuals (see residual graph). :contentReference[oaicite:8]{index=8}  

### 📊 Surface Reports

- Surface-averaged **static pressure** monitored on the blade to check solution stabilization. :contentReference[oaicite:9]{index=9}  

---

## 📊 Results

### 🟥 Pressure Contours

- Pressure maps on:
  - **Outlet view**, **inlet view**, **XZ plane**, and **top view** of the blade.  
- High-pressure region on the **pressure side** and low pressure on the **suction side**, confirming lift generation and torque. :contentReference[oaicite:10]{index=10}  

### 🟦 Velocity Contours & Flow Features

- Velocity contours over the blade surface.  
- Streamlines showing flow attachment and wake structure.  
- Velocity vectors visualizing direction and magnitude of flow around the rotor sector. :contentReference[oaicite:11]{index=11}  

---

## 🌀 Torque, Power & Efficiency

### 🔧 Torque on the Blade

From ANSYS post-processing:

- **Torque on one blade:**  
  - `T ≈ −2.29432 N·m` (direction given by sign). :contentReference[oaicite:12]{index=12}  

### ⚡ Total Power of the Turbine

Using:

- `P = T × ω`  
- Multiply by **3 blades**:  

> **Total power ≈ 287.7 W** at 9 m/s and 400 rpm. :contentReference[oaicite:13]{index=13}  

### 📈 Power Coefficient (Cp)

Using:

- `Cp = P / (0.5 * ρ * A * V³)`  

With ρ = 1.225 kg/m³, r = 25 m:

- **Total turbine Cp ≈ 0.239**  
- **Per-blade Cp ≈ 0.08** (if power is split by 3) :contentReference[oaicite:14]{index=14}  

These values are within reasonable ranges for a small HAWT with a wooden blade and non-optimized design.

---

## 🧱 Structural & Modal (FSI)

- CFD pressure loads are exported to a **structural solver** (FSI step) to compute:
  - Stress distribution  
  - Blade deformation  
- **Modal analysis** determines natural frequencies and mode shapes to ensure they are far from operating frequency and its harmonics.  
- Detailed plots for stresses, deformation, and mode shapes were presented in-class (mentioned as “in the presentation”). :contentReference[oaicite:15]{index=15}  

---

## 📉 Resonance Risk & Literature Reflection

### 🔔 Resonance Risk Assessment

The report discusses how ANSYS is used to:

- Compute nat
