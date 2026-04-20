Asteroid Impact Ejecta Modeling – Boom Challenge
This project builds a machine learning system for predicting asteroid impact ejecta behavior and generating valid impact scenarios under physical constraints.
The system solves two tasks
•	Forward prediction of ejecta outcomes from impact parameters 
•	Inverse design of impact scenarios that satisfy target constraints 

Problem Setup
Each impact scenario has 8 input parameters
energy, angle_rad, coupling, strength, porosity, gravity, atmosphere, shape_factor
The model predicts 6 ejecta outcomes
P80, fines_frac, oversize_frac, R95, R50_fines, R50_oversize

Method
A supervised learning regression model is trained to learn the mapping from inputs to outputs.
Supervised Learning
The model is implemented as a neural network and acts as a surrogate for physical simulation of asteroid impacts.
Input and output features are scaled to improve numerical stability and training performance.
A physics-inspired loss component is included to encourage physically consistent predictions.

Inverse Design Approach
Inverse design is performed using a sampling and filtering pipeline:
1.	Random sampling of candidate scenarios within input bounds 
2.	Forward prediction using the trained model 
3.	Strict constraint filtering on outputs 
o	96 ≤ P80 ≤ 101 
o	R95 ≤ 175 
4.	Ranking of valid candidates using a scoring function 
5.	Selection of top 20 scenarios 
Constrained Optimization
This ensures all submitted designs satisfy the required physical constraints.

Files
•	notebook.ipynb → full implementation 
•	prediction_submission.csv → forward prediction results 
•	design_submission.csv → inverse design results 
•	requirements.txt → dependencies 

How to Run
Install dependencies
pip install -r requirements.txt
Run the notebook
jupyter notebook notebook.ipynb
Execute all cells from top to bottom.
This will:
•	load dataset 
•	train the model 
•	generate forward predictions 
•	generate inverse design scenarios 
•	export both CSV submission files 
Reproducibility
The full pipeline can be reproduced by running the notebook sequentially without modification.
All outputs including prediction_submission.csv and design_submission.csv are generated directly from the notebook.

Software Requirements
•	Python 3.10+ 
•	numpy 
•	pandas 
•	scikit-learn 
•	torch 
•	matplotlib 
Dependencies are listed in requirements.txt.

Hardware Requirements
•	CPU execution supported 
•	Minimum 8GB RAM 
•	GPU optional (used in Google Colab if available) 
•	Training time approximately 5–10 minutes 
•	No specialized hardware required 

External Dependencies
•	No external APIs used 
•	No pre-trained models required 
•	Dataset provided by challenge repository 

Data Submission
Final outputs are provided as:
•	prediction_submission.csv 
•	design_submission.csv 
Both files follow the exact format specified in the challenge dataset repository.

Limitations
•	model is data driven, not a full physics simulation 
•	performance depends on training data distribution 
•	extrapolation outside training range may reduce accuracy 
•	inverse design uses stochastic sampling and does not guarantee global optimality
