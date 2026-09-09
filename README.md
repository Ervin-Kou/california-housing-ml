# California Housing Price Prediction

This project builds and evaluates machine learning regression models to predict median house values in California.

## Project Overview

The workflow includes:

- Data cleaning
- Exploratory data analysis
- Feature engineering
- Linear Regression baseline
- Random Forest regression
- Cross-validation
- Hyperparameter tuning with GridSearchCV
- Feature importance analysis
- Final model evaluation

## Dataset

The dataset contains California housing information such as:

- Median income
- Housing median age
- Total rooms
- Total bedrooms
- Population
- Households
- Geographic location
- Ocean proximity

The target variable is `median_house_value`.

## Data Preparation

Missing values in `total_bedrooms` were removed because they represented a small portion of the dataset.

Additional features were created, including:

- `bedroom_ratio`
- `household_rooms`

Skewed count-based variables were log-transformed, and `ocean_proximity` was converted using one-hot encoding.

## Exploratory Data Analysis

The analysis showed that:

- Median income has the strongest positive relationship with house value.
- Inland locations tend to have lower house values.
- Geographic location plays an important role.
- Several count-based housing features are strongly correlated with each other.
- House values appear capped near $500,000.

## Models

### Linear Regression

Linear Regression was used as a baseline model.

Test RMSE:

$67,230

### Random Forest Regressor

The default Random Forest significantly improved performance.

Test RMSE:

$48,970

The large gap between training and testing RMSE suggested some overfitting.

## Cross-Validation

5-fold cross-validation was used to estimate generalization performance.

Mean CV RMSE:

$49,746

## Hyperparameter Tuning

GridSearchCV tested multiple Random Forest parameter combinations.

Best parameters:

- `max_depth=None`
- `min_samples_leaf=2`
- `n_estimators=200`

Final tuned Random Forest test RMSE:

$48,772

This represents approximately a 27% reduction in RMSE compared with the Linear Regression baseline.

## Feature Importance

The most important feature was `median_income`, followed by:

- Inland location
- Longitude
- Latitude

This suggests that income and geographic location are major predictors of median house value.

## Limitations

The dataset contains an apparent ceiling near $500,000 for median house values. This makes it difficult for the model to accurately represent variation among higher-value districts.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook