## final_project-madrid_traffic

#Traffic Prediction Project
#Overview
This project focuses on predicting traffic intensity using a Recurrent Neural Network (RNN) based on historical data collected from traffic measurement points in Madrid since 2013. The data provides insights into the evolution of traffic over time and includes complementary datasets such as real-time traffic intensity, location of measurement points, and traffic maps.

Dataset
The dataset used for this project is named traffic_2019_model and includes the following columns:

id: Numerical identifier for the measurement point.
date: Timestamp representing the date and time in Madrid.
intensity: Target variable representing traffic intensity.
occupancy: Percentage of time a traffic detector is occupied by a vehicle.
load: Traffic load parameter indicating congestion.
velocity: Average velocity of vehicles in a 15-minute period.
integration_period: Numerical scaled column.
district: Categorical variable representing the district of the sensor.
Data Preprocessing
Feature Scaling:
Numerical features (occupancy, load, velocity, integration_period) are standardized using StandardScaler.

Date Conversion:
The date column is converted to datetime format and set as the index.

Train-Test Split:
The dataset is split into training and testing sets with an 80:20 ratio.

Model Architecture
The RNN model is built using TensorFlow and Keras, consisting of an LSTM layer with 50 units and a Dense layer with 1 unit for regression. The model is compiled using the Adam optimizer and Mean Squared Error (MSE) as the loss function.

Training and Evaluation
The model is trained for 50 epochs with a batch size of 32. Training and validation loss are monitored during the training process. After training, the model is evaluated on the test set, and the Mean Squared Error (MSE) on the test data is reported.

Results
The model predictions are obtained on the test set and stored in the predictions variable.

Issues
If predictions are coming out as nan, check for missing values, appropriate data types, data range, and potential overfitting. Adjust hyperparameters and model architecture accordingly.

Next Steps
Experiment with different hyperparameters to improve model performance.
Explore additional features or data sources for enhanced prediction accuracy.
Consider implementing more advanced time series models or ensembling techniques.
Dependencies
Python 3.x
NumPy
Pandas
scikit-learn
TensorFlow
How to Run
Install dependencies: pip install -r requirements.txt
Run the Jupyter Notebook or Python script.
Feel free to reach out for any questions or improvements!
