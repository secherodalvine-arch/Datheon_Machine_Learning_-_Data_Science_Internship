
# California Housing Price Prediction Using Machine Learning

## 1. Introduction

The objective of this project was to develop a machine-learning model that predicts median house values in California districts using housing, geographical and demographic information.

This is a supervised machine-learning regression problem because the target variable, `median_house_value`, contains numerical values.

## 2. Dataset Description

The project used the California Housing dataset.

- Original records: 20,640
- Original columns: 10
- Final columns after encoding: 14
- Target variable: `median_house_value`

The dataset included features such as longitude, latitude, housing_median_age, total_rooms, total_bedrooms, population, households, median_income and ocean_proximity.

## 3. Data Cleaning and Preparation

The following preprocessing steps were performed:

1. Inspected the dataset and checked its dimensions.
2. Checked for missing values.
3. Identified 207 missing values in `total_bedrooms`.
4. Replaced missing `total_bedrooms` values with the median (435).
5. Checked for duplicate records.
6. Investigated numerical outliers without automatically removing potentially legitimate observations.
7. Applied one-hot encoding to `ocean_proximity`, creating five numerical columns.
8. Separated the input features (X) from the target variable (y).
9. Split the data into training and testing sets using an 80:20 ratio.

The final encoded dataset contained 20,640 rows and 14 columns.

## 4. Machine Learning Models

Three regression algorithms were trained and evaluated.

### 4.1 Linear Regression

Linear Regression was used as the first baseline model. It estimates house values by learning relationships between the input features and the target variable.

### 4.2 Decision Tree Regressor

The Decision Tree Regressor learns decision rules from the training data and uses them to estimate house values.

### 4.3 Random Forest Regressor

Random Forest combines predictions from multiple decision trees. It was evaluated to determine whether combining trees could improve prediction performance.

## 5. Model Evaluation

The models were evaluated using three metrics:

- **Mean Absolute Error (MAE):** Measures the average absolute difference between predicted and actual values. Lower is better.
- **Mean Squared Error (MSE):** Measures squared prediction errors and penalizes large errors more heavily. Lower is better.
- **R-squared (R²):** Measures the proportion of variation in the target variable explained by the model. Higher is generally better.

### Model Comparison Results

| Model | MAE | MSE | R² |
|---|---:|---:|---:|
| Linear Regression | 50,670.74 | 4,908,476,721.16 | 0.6254 |
| Decision Tree | 43,577.56 | 4,766,379,581.68 | 0.6363 |
| Random Forest | 31,636.19 | 2,398,820,115.38 | 0.8169 |

## 6. Best Performing Model

Random Forest achieved the best results among the three models tested.

Its performance was:

- MAE: 31,636.19
- MSE: 2,398,820,115.38
- R²: 0.8169 (approximately 81.69%)

The results indicate that Random Forest explained approximately 81.69% of the variation in median house values in the test dataset.

Its average absolute prediction error was approximately 31,636.19 in the dataset's dollar units.

Therefore, Random Forest was selected as the best-performing model in this experiment.

## 7. Feature Importance Analysis

Feature importance was examined using the trained Random Forest model.

The leading features were:

| Feature | Importance |
|---|---:|
| median_income | 49.06% |
| ocean_proximity_INLAND | 14.09% |
| longitude | 10.59% |
| latitude | 10.16% |
| housing_median_age | 5.19% |

Median income was the most important feature according to the model, followed by inland location and geographical coordinates.

These importance scores describe how useful the features were to the model. They do not establish that the features cause changes in house prices.

## 8. Model Saving and Reusability

The trained Random Forest model was saved using the Joblib library.

The saved file was:

`california_housing_model.pkl`

The saved model was subsequently loaded using `joblib.load()` and successfully used to generate predictions on the test data.

This demonstrated that the trained model could be reused without repeating the training process.

## 9. Limitations and Future Improvements

Although Random Forest performed best, the project has several limitations:

1. The dataset represents California districts rather than individual houses.
2. Median house values have an upper limit of $500,001 in the dataset.
3. The model may not perform equally well across all geographical areas.
4. Further hyperparameter tuning could improve performance.
5. Additional regression algorithms could be tested.
6. Further analysis of prediction errors could identify areas where the model performs poorly.

Future work could include model tuning, cross-validation and testing on additional housing data.

## 10. Conclusion

This project demonstrated an end-to-end supervised machine-learning regression workflow, covering data exploration, cleaning, preprocessing, feature preparation, model training, evaluation, comparison, feature importance and model saving.

Three regression models were evaluated. Random Forest achieved the strongest performance, with an R² score of approximately 0.8169.

The project showed how machine learning can use geographical, demographic and housing information to estimate median house values.

The selected model is a useful experimental prediction model, but it would require further validation before being used for real-world property valuation.
