 Insurance Charges Prediction

 
This repository contains a machine learning project focused on predicting medical insurance charges based on various personal attributes. The project involves Exploratory Data Analysis (EDA), data preprocessing, feature engineering, model training, and deployment of a simple web application using Streamlit.

Table of Contents
Project Overview

Dataset

Methodology

Model

Project Structure

How to Run the Project

Running the Jupyter Notebook

Running the Streamlit Application

Dependencies

Key Insights

Project Overview
The goal of this project is to build a predictive model that estimates individual medical insurance charges. This can be useful for insurance companies to assess risk and for individuals to get an approximate idea of their potential costs. The project covers:

Data Loading and Initial Exploration: Understanding the dataset's structure and basic statistics.

Exploratory Data Analysis (EDA): Visualizing distributions, relationships between variables, and identifying patterns.

Data Cleaning and Preprocessing: Handling duplicates, encoding categorical features, and scaling numerical features.

Feature Engineering: Creating new features (e.g., BMI categories) to potentially improve model performance.

Feature Selection: Analyzing correlations and statistical tests (Pearson, Chi-squared) to select relevant features.

Model Training: Training a Linear Regression model.

Model Evaluation: Assessing the model's performance using R-squared and Adjusted R-squared.

Model Deployment: Creating a user-friendly web application using Streamlit for interactive predictions.

Dataset
The dataset used for this project is insurance.csv, which contains the following columns:

age: Age of the primary beneficiary.

sex: Gender of the beneficiary (male/female).

bmi: Body Mass Index, providing an understanding of body weight relative to height.

children: Number of children covered by health insurance / number of dependents.

smoker: Whether the beneficiary is a smoker (yes/no).

region: The beneficiary's residential area in the US (northeast, northwest, southeast, southwest).

charges: Individual medical costs billed by health insurance.

Methodology
The project follows a standard machine learning workflow:

EDA: Histograms, count plots, and box plots were used to understand the distribution and identify outliers in numerical and categorical features.

Data Cleaning: Duplicate rows were removed to ensure data integrity.

Data Preprocessing:

Categorical features (sex, smoker, region) were converted into numerical representations. sex and smoker were mapped to 0 and 1. region was one-hot encoded (pd.get_dummies) with drop_first=True to avoid multicollinearity.

Numerical features (age, bmi, children) were scaled using StandardScaler to normalize their ranges.

Feature Engineering: A new categorical feature bmi_category was created from bmi (Underweight, Normal, Overweight, Obese) and then one-hot encoded.

Feature Selection:

Pearson Correlation: Used for numerical features to understand their linear relationship with charges.

Chi-squared Test: Used for categorical features to assess their independence from binned charges.

Model Training: A LinearRegression model from scikit-learn was chosen for its interpretability and effectiveness for regression tasks.

Model Evaluation: The model's performance was evaluated using R2 (R-squared) and Adjusted R2 metrics.

Model Persistence: The trained model, scaler, and feature column names were saved using joblib for later use in the Streamlit application.

Model
The primary model used in this project is:

Linear Regression: A simple yet powerful algorithm for modeling the relationship between a dependent variable and one or more independent variables by fitting a linear equation to the observed data.

The model achieved an R2 score of approximately 0.80 and an Adjusted R2 score of 0.80, indicating that a significant portion of the variance in insurance charges can be explained by the selected features.

Project Structure
.
├── insurance.csv             # The raw dataset
├── insurance_prediction.ipynb # Jupyter Notebook with EDA, preprocessing, training      
├── LinearRegression_insurance.pkl # Saved trained Linear Regression model
├── scaler_insurance.pkl      # Saved StandardScaler object
├── columns_insurance_fit.pkl # Saved list of feature column names used during training
└── README.md                 # This README file

How to Run the Project
To run this project, you'll need Python installed along with the necessary libraries. It's highly recommended to use a virtual environment.

Running the Jupyter Notebook
Clone the repository:

git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
(https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git)
cd YOUR_REPO_NAME

(Replace YOUR_USERNAME and YOUR_REPO_NAME with your actual GitHub details)

Create and activate a virtual environment:

python -m venv venv
# On Windows:
.\venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

Install dependencies:

pip install -r requirements.txt

(If requirements.txt is not provided, see the Dependencies section below and install them manually.)

Start Jupyter Notebook:

jupyter notebook

Open insurance_prediction.ipynb in your browser and run the cells sequentially to see the analysis, preprocessing, and model training steps.

Running the Streamlit Application
Ensure you have followed steps 1-3 from "Running the Jupyter Notebook" to set up your environment and install dependencies.

Make sure the .pkl files are in the same directory as app.py.

Dependencies
The following Python libraries are required to run this project. It's best practice to install specific versions to ensure reproducibility. You can generate a requirements.txt file using pip freeze > requirements.txt after installing them.

numpy

pandas

seaborn

matplotlib

scikit-learn

streamlit

joblib

scipy

Key Insights
Smoker Status is a Dominant Factor: Being a smoker significantly increases insurance charges, highlighting its strong correlation.

Age and BMI Impact: Age and BMI also show positive correlations with charges, indicating that older individuals and those with higher BMI tend to have higher medical costs.

Children and Region: The number of children and geographical region (specifically southwest in this model) also play a role, though their impact might be less pronounced than smoker status, age, and BMI.

Feature Engineering Effectiveness: Creating bmi_category helped in understanding the distribution of BMI and could potentially be used for more complex models.
