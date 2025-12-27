# Reaction-Diffusion Project

This project simulates **reaction-diffusion systems** using Python. It includes three models: **Gray-Scott**, **Multi-fate**, and **EMT**. The goal is to visualize pattern formation, explore parameter effects, and analyze diffusion dynamics.

---

## Table of Contents
1. [Gray-Scott Model](#gray-scott-model)  
2. [Multi-fate Model](#multi-fate-model)  
3. [EMT Model](#emt-model)  
4. [Installation](#installation)  
5. [Usage](#usage)  
6. [Data & Results](#data--results)  
7. [Analysis & Insights](#analysis--insights)  
8. [Future Work](#future-work)

---

## Gray-Scott Model

**Description:**  
The Gray-Scott model simulates activator-inhibitor dynamics producing complex patterns.

**Equations:**  
∂u/∂t = Du ∇²u - uv² + F(1-u),

∂v/∂t = Dv ∇²v + uv² - (F+k)v


**Numerical Method:** Finite difference with explicit Euler integration.  
**Boundary Conditions:** Periodic   

**Sample Output:**  
See the folders Images and videos.

---

## Multi-fate Model

**Description:**  
The Multi-fate model simulates multiple cell fate decisions with diffusion-coupled reaction dynamics.

**Equations / Dynamics:**  
∂A/∂t = Du ∇2 A + fA(A,B),

∂B/∂t = Dv ∇2 B + fB(A,B)

where Du and Dv are the diffusion coefficients for species A and B, respectively.

The nonlinear reaction terms are defined as:

fA(A,B) = α + (β tA) / (1 + tA) - A
fB(A,B) = α + (β tB) / (1 + tB) - B

with:

tA = (A2)^n 
tB = (B2)^n 

A2 = 2*A^2 / [(K + 4(A + B) + sqrt(K^2 + 8 Kd (A + B))]
B2 = 2*B^2 / [(K + 4(A + B) + sqrt(K^2 + 8 Kd (A + B))]

**Numerical Method:** Finite difference / Euler or other as implemented.  
**Boundary Conditions:** Periodic / Neumann

**Sample Output:**  
See the folders Images and videos.

---

## EMT Model

**Description:**  
The EMT (Epithelial-Mesenchymal Transition) model simulates diffusion-driven EMT patterns in cells.

**Equations / Dynamics:**  
∂[mir200]/∂t = GMIR200 hmir200 zeb hmir200 sna - [mir200]1 mir2000 - KMIR200 [mir200]0 + Dmir200 ∇2[mir200]

∂[mzeb]/∂t = GMZEB hmzeb zeb hmzeb sna - [mir200]1 mir2001 - KMZEB [mzeb] + Dmzeb ∇2[mzeb]

∂[ZEB]/∂t = GZEB [mir200]1 mir2002 - KZEB [ZEB] + DZEB ∇2[ZEB]

∂[SNAIL]/∂t = GSNAIL [mir34]4 mir342 - KSNAIL [SNAIL] + DSNAIL ∇2[SNAIL]

∂[MSNAIL]/∂t = GMSNAIL hmsnai hmsna sna - [mir34]4 mir341 - KMSNAIL [MSNAIL] + DMSNAIL ∇2[MSNAIL]

∂[mir34]/∂t = GMIR34 hmir34 zeb hmir34 sna - [mir34]4 mir340 - KMIR34 [mir34] + Dmir34 ∇2[mir34]

∂[I]/∂t = 0


**Numerical Method:** Finite difference / Euler.  
**Boundary Conditions:** Neumann

**Sample Output:**  
See the folders Images and videos.

---

## Installation

pip install -r requirements.txt

## Usage

Open the corresponding notebook in notebooks/ (in Google Colab for interactivity)
Adjust parameters using sliders (e.g., Du, Dv, F, k)
Run the notebook → visualize patterns
Save results as arrays, images, or gifs in data/

## Data & Results

Output videos: videos/
Sample images: Images/
Interactive widgets allow parameter exploration in real-time.

**Note on Notebooks:**
Due to interactive widgets and long-running simulations, the notebooks are also provided as exported PDFs for static viewing on GitHub.
The original interactive versions are intended to be run in Google Colab.

## Analysis & Insights

Gray-Scott: Increasing F accelerates pattern formation.
Multi-fate: Different diffusion constants produce distinct fate domains.
EMT: Varying reaction rates changes cluster morphology.

## Future Work

Add more reaction-diffusion models.
Explore 3D pattern formation.
Optimize simulation speed for larger grids.
Compare parameter sensitivity across models.
