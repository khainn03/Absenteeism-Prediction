# Absenteeism Prediction Project

## Project Overview
This project implements a predictive model for absenteeism, utilizing logistic regression. The model predicts whether an employee is likely to be absent from work for an excessive amount of time. The implementation includes data preprocessing, model training, and deployment for making predictions on new data. Additionally, SQL integration optimizes data management by storing predicted outputs in a MySQL database, streamlining analysis, and providing a centralized repository for efficient data retrieval.


## Data Files

### Data Sources
- **Original Dataset (`Absenteeism_data.csv`):** The raw absenteeism dataset used for the project.
- **New Dataset for Prediction (`Absenteeism_new_data.csv`):** A sample dataset provided for testing the trained logistic regression model, sharing the same structure as the original dataset. It is used to demonstrate the process of making predictions on new data using the implemented model. 

### Output Files
1. **Preprocessed Data:** The pre-processed dataset (`Absenteeism_preprocessed.csv`) produced from data preparation is provided, which is used to train and test the model.
2. **Model and Scaler:** The trained logistic regression model (`model`) and its corresponding scaler (`scaler`) are pickled from the model training and also included in this repository. These files are essential for making predictions on new data.

#### Usage:
- `Absenteeism_preprocessed.csv` demonstrates the processed dataset used for training and testing the model.
-  `model` and `scaler` are loaded in the `absenteeism_model` class in the absenteeism_module to make predictions on new data.
  
## Project Structure

### 1. Data Preparation (`Data preparation.ipynb`)

- **Objective:** Prepare the raw absenteeism dataset for modeling.

- **Steps:**
  - Load the raw data from 'Absenteeism_data.csv'.
  - Drop the 'ID' column.
  - Create dummy variables for 'Reason for Absence'.
  - Group and consolidate the reasons for absence.
  - Extract month and day of the week from the 'Date' column.
  - Reorder and preprocess columns.
  - Map 'Education' variables.
  - Save the preprocessed data to 'Absenteeism_preprocessed.csv'.

### 2. Logistic Model (`Logistic model.ipynb`)

- **Objective:** Train a logistic regression model to predict excessive absenteeism.

- **Steps:**
  - Load the preprocessed data.
  - Create binary targets based on the median of 'Absenteeism Time in Hours'.
  - Drop unnecessary variables.
  - Split the data into training and testing sets.
  - Implement logistic regression with sklearn.
  - Manually check the model accuracy.
  - Interpret the coefficients.
  - Test the model on the test set.
  - Save the trained model and custom scaler for later use.

### 3. Absenteeism Module (`absenteeism_module.py`)

- **Objective:** Create a modular class for absenteeism prediction.

- **Steps:**
  - Import necessary libraries.
  - Define a custom scaler class for standardization.
  - Create the `absenteeism_model` class:
    - Load pre-trained logistic regression model and scaler.
    - Define methods to load, clean, and preprocess new data.
    - Implement functions to output predicted probabilities, categories, and detailed outputs.

### 4. SQL Integration (`SQLintegreation.ipynb`)

- **Objective:** Integrate SQL for storing predicted outputs.

- **Steps:**
  - Import the `absenteeism_model` class.
  - Instantiate the class with the pre-trained model and scaler.
  - Load and clean new data for predictions.
  - Predict outputs and store them in a DataFrame.
  - Connect to a MySQL database ('predicted_outputs').
  - Execute SQL queries:
    - Check existing data in the 'predicted_outputs' table.
    - Build and execute an INSERT statement to add new predicted outputs.
  - Commit changes and close the database connection.

---

This project follows a systematic approach, covering data preparation, model training, modularity, and SQL integration. The modular structure allows for easy maintenance, and the SQL integration enhances data storage and accessibility for further analysis.
