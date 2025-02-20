# Predictive-Analysis 
This document explains the entire workflow, from loading data to deploying a machine learning model using DVC for data versioning and FastAPI for serving the model in Google Colab.

1. Loading the Data
  Upload the dataset to Google Colab manually or access it from Google Drive.
  Use pandas to load the dataset into a DataFrame and perform basic exploratory data analysis (EDA).
2. Preprocessing the Data
  Handle missing values, duplicates, and outliers.
  Encode categorical variables if necessary.
  Split the data into training and testing sets using train_test_split from scikit-learn.
3. Training the Machine Learning Model
  Choose an ML algorithm (e.g., Decision Tree, Random Forest, XGBoost).
  Train the model using the training dataset.
  Evaluate the model on the test dataset using appropriate metrics (accuracy, F1-score, etc.).
  Save the trained model using joblib or pickle for later use in inference.
4. Setting Up DVC for Data Versioning
  Initialize a DVC repository using dvc init.
  Track the dataset using dvc add <dataset_file>.
  Commit the changes to Git so that DVC can version the data properly.
  Push the dataset to remote storage (Google Drive, AWS, etc.) using dvc remote add.
  Verify that the dataset can be pulled back later using dvc pull.
5. Creating a FastAPI Application for Model Deployment
  Install FastAPI and Uvicorn.
  Create a Python script (app.py) that:
  Loads the trained model.
  Defines an API endpoint to receive input data.
  Processes the input and returns predictions.
  Test the API locally using Uvicorn.
6. Running and Testing the API in Colab
  Use ngrok to expose the local FastAPI server to the internet.
  Start the FastAPI server using !uvicorn app:app --host 0.0.0.0 --port 8000.
  Copy the ngrok URL and test API endpoints using Postman or Python requests.
7. Automating Deployment Using a Shell Script
  Write a shell script (deploy.sh) that:
  Sets up the environment.
  Pulls the latest version of the dataset using DVC.
  Starts the FastAPI server automatically.
  Run the script in Colab using !bash deploy.sh.

