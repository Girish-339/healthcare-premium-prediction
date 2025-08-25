HEALTHCARE-PREMIUM-PREDICTION
Project Overview
The application utilizes two separate machine learning models to provide accurate predictions. The models are trained on distinct age groups to improve performance:

model_young: Used for individuals aged 25 or younger.
model_rest: Used for individuals older than 25.

The models and their corresponding data scalers were pre-trained and saved as 
joblib files in the artifacts/ directory. The application loads these pre-trained artifacts at runtime, which is a common practice for deploying machine learning models.

The prediction logic is encapsulated in the prediction_helper.py script, which handles all data preprocessing steps necessary before the models make a prediction. This includes:
Categorical Variable Encoding: The script converts categorical inputs like Gender and Region into a numerical format using a one-hot encoding approach.
Risk Score Calculation: A normalized_risk_score is calculated based on the user's Medical History. Different diseases (e.g., diabetes, heart disease) are assigned specific risk values, which are then summed and normalized to a score between 0 and 1.
Feature Scaling: Numerical features such as Age and Income in Lakhs are scaled using the appropriate scaler_young or scaler_rest object, ensuring the data is in the correct format for the loaded models.

File Structure
main.py: The main Python script for the Streamlit web application. It defines the layout and user input fields for the predictor.
prediction_helper.py: Contains all the backend logic for data preprocessing and making predictions using the pre-trained models.

How to Run the Application
Clone the Repository:
git clone https://github.com/your-username/ml-project-premium-prediction.git
cd ml-project-premium-prediction

Install Dependencies:
Make sure you have Python installed. The required libraries are listed in 
requirements.txt.
pip install -r requirements.txt
Run the Streamlit App:

streamlit run main.py
This command will launch the web application in your default browser.

Dependencies
The project's dependencies are managed using 
pip and are listed in the requirements.txt file:
joblib==1.3.2
pandas==2.0.2
streamlit==1.22.0
numpy==1.25.0
scikit-learn==1.3.0
xgboost==2.0.3
requirements.txt: A list of all necessary Python libraries for the project, including Streamlit, scikit-learn, joblib, and xgboost.

