# ANSYS Mechanical: Structural & Topology Optimization Analysis of a Mounting Bracket

This repository contains the Finite Element Analysis (FEA) and Topology Optimization workflow for a 3D structural mounting bracket, performed using **ANSYS Mechanical 2026 R1 (Student Version)**.

---

## 📌 Project Overview

The primary objective of this project is to perform a static structural evaluation of a mounting bracket followed by topology optimization to minimize structural compliance while reducing overall mass by approximately **40%**.

* **Geometry Source:** SpaceClaim (`SYS.scdocx`)
* **Material:** Structural Steel
* **Analysis Types:** 
  1. Static Structural Analysis (A5)
  2. Structural Optimization / Topology Optimization (B5)

---

## 📐 Geometry & Mesh Specifications

### Geometry Bounding Box
* **$X$-length:** $18.263\text{ mm}$
* **$Y$-length:** $2.000\text{ mm}$
* **$Z$-length:** $25.394\text{ mm}$
* **Original Volume:** $556.91\text{ mm}^3$
* **Original Mass:** $4.3718 \times 10^{-3}\text{ kg}$ ($4.37\text{ g}$)

### Mesh Setup
* **Physics Preference:** Mechanical
* **Nodes:** $48,196$
* **Elements:** $9,960$
* **Mesh Refinement:** Face and edge sizing applied to boundary regions ($0.1\text{ mm}$ element size).

---

## 🛠️ Material Properties (Structural Steel)

| Property | Value | Unit |
| :--- | :--- | :--- |
| **Density** | $7.85 \times 10^{-6}$ | $\text{kg/mm}^3$ |
| **Young's Modulus ($E$)** | $2.00 \times 10^5$ | $\text{MPa}$ |
| **Poisson's Ratio ($\nu$)** | $0.30$ | — |
| **Tensile Yield Strength** | $250$ | $\text{MPa}$ |
| **Tensile Ultimate Strength** | $460$ | $\text{MPa}$ |

---

## ⚡ Static Structural Analysis (System A5)

### Boundary Conditions & Loads
1. **Cylindrical Support:** Applied on 2 pin holes (Radial: Fixed, Axial: Fixed, Tangential: Free).
2. **Bearing Load:** Applied on 1 face.
   * $X$-Component: $50\text{ N}$
   * $Z$-Component: $100\text{ N}$

### Static Analysis Results
* **Minimum von-Mises Stress:** $0.21179\text{ MPa}$
* **Maximum von-Mises Stress:** $85.024\text{ MPa}$ (well below the $250\text{ MPa}$ yield limit)
* **Average Stress:** $16.816\text{ MPa}$

---

## 🚀 Topology Optimization (System B5)

### Optimization Setup
* **Objective:** Minimize Compliance (Maximize Stiffness)
* **Response Constraint:** Mass constraint set to retain **$60\%$** of original mass.
* **Convergence Criterion:** $0.1\%$ across iterations.

### Optimization Results (Iteration 13)

| Metric | Original State | Optimized State | Reduction / Retained |
| :--- | :--- | :--- | :--- |
| **Volume** | $556.79\text{ mm}^3$ | $330.81\text{ mm}^3$ | **$59.41\%$** retained ($40.59\%$ mass reduction) |
| **Mass** | $4.3708\text{ g}$ | $2.5968\text{ g}$ | **$59.41\%$** retained |
| **Iterations to Converge** | — | 13 | — |

