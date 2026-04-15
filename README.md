# Asteroid Impact Ejecta Modeling – Boom Challenge

This project builds a machine learning system for predicting asteroid impact ejecta behavior and generating valid impact scenarios under physical constraints.

The system solves two tasks:
- Forward prediction of ejecta outcomes from impact parameters
- Inverse design of impact scenarios that satisfy target constraints

---

## Problem Setup

Each impact scenario has 8 input parameters:
energy, angle_rad, coupling, strength, porosity, gravity, atmosphere, shape_factor

The model predicts 6 ejecta outcomes:
P80, fines_frac, oversize_frac, R95, R50_fines, R50_oversize

---

## Method

A supervised machine learning model is trained to learn the mapping from inputs to outputs.

This acts as a surrogate model for physical simulation of asteroid impacts.

:contentReference[oaicite:0]{index=0}  

For inverse design, new impact scenarios are randomly sampled within physical bounds, passed through the model, and filtered based on constraints:

- 96 ≤ P80 ≤ 101  
- R95 ≤ 175  

Best valid scenarios are selected for submission.

:contentReference[oaicite:1]{index=1}  

---

## Files

- notebook.ipynb → full implementation  
- prediction_submission.csv → forward prediction results  
- design_submission.csv → inverse design results  
- requirements.txt → dependencies  

---

## How to Run

Install dependencies:
pip install -r requirements.txt

Run notebook:
jupyter notebook notebook.ipynb

Execute cells in order to:
- train model  
- generate predictions  
- generate inverse design outputs  

---

## Hardware

- CPU is sufficient  
- 8GB RAM minimum  
- GPU optional  

---

## Limitations

- model is data driven, not full physics simulation  
- accuracy depends on training data distribution  
- inverse design is stochastic and not globally optimal  
