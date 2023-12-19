# Traffic Prediction Project - Madrid

## Overview

This project focuses on predicting traffic intensity using a Recurrent Neural Network (RNN) based on historical data collected from traffic measurement points in Madrid since 2019. The data provides insights into the evolution of traffic over time and includes complementary datasets such as real-time traffic intensity, location of measurement points, and traffic maps. There is also a complementary dataset regarding traffic accident reports in Madrid.

## Dataset

The datasets used for this project were taken from [Madrid Traffic Data](https://datos.madrid.es/portal/site/egob/menuitem.9e1e2f6404558187cf35cf3584f1a5a0/?vgnextoid=374512b9ace9f310VgnVCM100000171f5a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD&vgnextfmt=default). Below are the links to the specific datasets used:

- [2019 Traffic History Madrid](https://datos.madrid.es/portal/site/egob/menuitem.c05c1f754a33a9fbe4b2e4b284f1a5a0/?vgnextoid=02f2c23866b93410VgnVCM1000000b205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD)
- [Accidents in 2019](https://datos.madrid.es/portal/site/egob/menuitem.c05c1f754a33a9fbe4b2e4b284f1a5a0/?vgnextoid=7c2843010d9c3610VgnVCM2000001f4a900aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD)
- [Sensor Information and Location](https://datos.madrid.es/portal/site/egob/menuitem.c05c1f754a33a9fbe4b2e4b284f1a5a0/?vgnextoid=ee941ce6ba6d3410VgnVCM1000000b205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD)

### Traffic Intensity

Traffic history and sensor information were combined for the traffic prediction model. The number of sensors was reduced to consider the main streets leading to the M-30 from the inside of its perimeter.

The datasets used for this project are named `traffic_2019` for data cleaning and EDA, and `traffic_2019_model` for the RNN model. They include the following columns:

- `id`: Numerical identifier for the measurement point.
- `date`: Timestamp representing the date and time in Madrid.
- `intensity`: Target variable representing traffic intensity.
- `occupancy`: Percentage of time a traffic detector is occupied by a vehicle.
- `load`: Traffic load parameter indicating congestion.
- `velocity`: Average velocity of vehicles in a 15-minute period.
- `integration_period`: Numerical scaled column.
- `district`: Categorical variable representing the district of the sensor.

## Data Preprocessing

### Feature Scaling

Numerical features (`occupancy`, `load`, `velocity`, `integration_period`) are standardized using `StandardScaler`.

Please note that the original dataset is in Spanish and has been translated. Within the provided links to the Madrid data website, the respective README files can be found as well.

### Model Creation

#### Date Conversion

The `date` column is converted to datetime format and set as the index.

#### Train-Test Split

The dataset is split into training and testing sets with an 80:20 ratio.

## Model Architecture

The RNN model is built using TensorFlow and Keras, consisting of an LSTM layer with 50 units and a Dense layer with 1 unit for regression. The model is compiled using the Adam optimizer and Mean Squared Error (MSE) as the loss function.

## Training and Evaluation

The model is trained for 50 epochs with a batch size of 32. Training and validation loss are monitored during the training process. After training, the model is evaluated on the test set, and the Mean Squared Error (MSE) on the test data is reported.

## Results

TBD.

## Next Steps

- Experiment with different hyperparameters to improve model performance.
- Explore additional features or data sources for enhanced prediction accuracy.
- Consider implementing more advanced time series models or ensembling techniques.

## Dependencies

- Python 3.x
- NumPy
- Pandas
- scikit-learn
- TensorFlow

---

## Dataset Translation and Severity Level Imputation

For the accident dataset, an API connection to DeepL was utilized to translate the content, ensuring a standardized and comprehensible dataset. The translated dataset was then processed to handle missing values, specifically in the severity level column.

### Data Translation

The original dataset was in Spanish, and to enhance accessibility and understanding, an API connection to DeepL was established to perform the translation. This step involved translating column names, descriptions, and other textual content, making the dataset more user-friendly for English-speaking audiences.

### Imputation of Severity Level

The severity level column contained NaN (Not a Number) values, which required imputation for a comprehensive analysis. A machine learning model was employed to predict and fill in the missing severity levels. The challenge encountered was the highly unbalanced distribution of severity levels, requiring careful consideration during model selection.

### Model Selection

Several machine learning models were considered for severity level imputation, including Logistic Regression, MLP Classifier, Support Vector Classifier (SVC), and Decision Tree. Each model was trained and evaluated on its ability to predict severity levels accurately.

The model selection process involved comparing performance metrics, such as accuracy, precision, recall, and F1 score. The model with the best overall performance on the imbalanced dataset was chosen for severity level imputation.

## Chosen Model

[Specify the model chosen, e.g., Decision Tree]

The Decision Tree model demonstrated superior performance in handling the imbalanced dataset and accurately predicting severity levels. This model was selected for the imputation of severity levels in the translated accident dataset.

Feel free to explore the Jupyter Notebook or Python script for detailed implementation and evaluation of the chosen model.

### Challenges

- Unbalanced Severity Levels: The significant imbalance in the distribution of severity levels posed a challenge during model training. Techniques such as oversampling, undersampling, or the use of specialized algorithms were considered to address this issue.

- Model Evaluation: The choice of evaluation metrics was crucial, considering the imbalanced nature of the dataset. Precision, recall, and F1 score were prioritized to ensure a comprehensive assessment of the model's performance.

## How to Run

To replicate or explore the translation and imputation process, follow the steps mentioned in the main README file.

Feel free to reach out for any questions, insights, or improvements!
