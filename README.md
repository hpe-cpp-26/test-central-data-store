# ML Training Pipeline — Experiment Tracking Design

## Data Ingestion
An ML (Machine Learning) training pipeline is an automated, end-to-end workflow that transforms raw data into a deployable model. It standardizes the steps required to train and retrain models, ensuring reproducibility, consistency, and scalability.

Here is the breakdown of the core stages in a standard ML training pipeline, structured into 6 clear phases:


This is the starting point where raw data is gathered from various sources (databases, data lakes, APIs, streaming services, or logs) and consolidated into a centralized storage area.

## Key Tasks: Syncing data sources, versioning the raw data, and handling



4. Model Training
Once the dataset is prepared, it is typically split into training, validation, and testing sets. The training data is fed into the machine learning algorithm to learn patterns.

Key Tasks: * Running the training algorithm.

Hyperparameter Tuning: Searching for the best configuration settings (like learning rate or tree depth) using methods like Grid Search or Bayesian Optimization.

5. Model Evaluation & Validation
Before a model goes anywhere near production, its performance must be rigorously tested on a "holdout" validation dataset it has never seen before.

Key Tasks: Checking evaluation metrics (such as Accuracy, F1-Score, ROC-AUC, or MAE) and checking for signs of overfitting or underfitting.

##tesitng again

Key Tasks: Containerization (e.g., Docker), exposing the model via an API endpoint, and setting up monitoring for data drift.

testing 
Prevents Data Leakage: By separating steps cleanly, you ensure information from your test dataset doesn't accidentally leak into your training dataset.
