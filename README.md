# Used_-Car_Prediction
# Used Car Price Prediction – Data Science Capstone

## 1. Project Overview

This project focuses on analysing used vehicle listings and developing machine learning models to predict vehicle asking prices.

The project uses vehicle characteristics such as brand, model, manufacturing year, mileage, transmission type, ownership and fuel type to investigate the factors associated with asking prices.

The objective is to demonstrate the data science workflow, from data cleaning and exploratory data analysis to machine learning model development and evaluation.

## 2. Project Objectives

- Inspect and understand the used car dataset.
- Clean and prepare the data for analysis.
- Investigate distributions, missing values and potential outliers.
- Explore relationships between vehicle characteristics and asking prices.
- Develop and compare regression models.
- Evaluate model performance using appropriate regression metrics.
- Save the selected model for future use.

## 3. Dataset Description

The original dataset contains 24,575 records and 11 columns.

The dataset includes:

| Variable | Description |
|---|---|
| Brand | Vehicle manufacturer |
| model | Vehicle model |
| Year | Manufacturing year |
| Age | Vehicle age |
| kmDriven | Recorded vehicle mileage |
| Transmission | Manual or automatic transmission |
| Owner | Previous ownership category |
| FuelType | Vehicle fuel type |
| PostedDate | Listing publication date |
| AdditionInfo | Additional listing information |
| AskPrice | Vehicle asking price (target variable) |

After removing duplicate records, the working dataset contained 14,988 records.

The cleaned dataset is provided separately as `used_cars_cleaned.csv`.

## 4. Data Cleaning and Preparation

The following cleaning activities were performed:

- Removed exact duplicate records.
- Converted asking prices into numerical values.
- Cleaned mileage values and converted them into numerical format.
- Standardised selected categorical values and removed unnecessary whitespace.
- Investigated missing values across the dataset.
- Corrected invalid year entries, including the placeholder value 9999.
- Investigated unusually high and low asking prices and mileage values.
- Retained potentially legitimate extreme observations rather than automatically deleting statistical outliers.
- Examined the relationship between vehicle year and age.

The `Age` variable was excluded from the initial model because it was found to be exactly redundant with `Year` in records where both values were available.

`PostedDate` and `AdditionInfo` were also excluded from the initial model.

## 5. Exploratory Data Analysis

Exploratory data analysis was conducted to understand the structure and characteristics of the dataset.

The visualisations included:

- Distribution of asking prices.
- Box plot of asking prices.
- Top 10 most frequently listed vehicle brands.
- Relationship between mileage and asking price.
- Asking price by transmission type.
- Percentage of missing values by variable.
- Actual versus predicted asking prices.

The analysis identified a positively skewed asking-price distribution, substantial missingness in several predictor variables and differences in listing frequency across vehicle brands.

## 6. Machine Learning Approach

The target variable was `AskPrice`.

Seven predictor variables were selected:

- Brand
- model
- Year
- kmDriven
- Transmission
- Owner
- FuelType

The dataset was divided into training and testing sets using an 80:20 split, with a random state of 42.

| Dataset | Records |
|---|---:|
| Training set | 11,990 |
| Testing set | 2,998 |

A preprocessing pipeline was developed to:

- Impute missing numerical values using the median.
- Impute missing categorical values using the most frequent category.
- Standardise numerical variables.
- Apply one-hot encoding to categorical variables.

## 7. Models Developed

Four regression models were developed and compared:

1. Linear Regression
2. Random Forest Regression
3. Random Forest Regression with a log-transformed target
4. Gradient Boosting Regression

## 8. Model Evaluation

The models were evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Coefficient of Determination (R²)

### Model Comparison

| Model | MAE | RMSE | R² |
|---|---:|---:|---:|
| Linear Regression | 492,755 | 1,349,119 | 0.3724 |
| Random Forest | 490,792 | 1,394,349 | 0.3296 |
| Log-Transformed Random Forest | 452,417 | 1,427,601 | 0.2973 |
| Gradient Boosting | 533,020 | 1,385,617 | 0.3380 |

Linear Regression was selected as the preferred overall model because it achieved the highest R² and lowest RMSE.

The log-transformed Random Forest achieved the lowest MAE, demonstrating a trade-off between average absolute prediction error and the other evaluation metrics.

## 9. Key Findings

- Asking prices are positively skewed.
- Maruti Suzuki is the most frequently represented vehicle brand.
- Higher vehicle mileage generally tends to be associated with lower asking prices.
- Automatic vehicles generally have higher median asking prices than manual vehicles in this dataset.
- Several predictor variables contain substantial missing values.
- The selected Linear Regression model explains approximately 37.24% of the variation in asking prices.

## 10. Limitations

The project has several limitations:

- Missing information in some predictor variables may affect model performance.
- The dataset contains extreme asking prices and a wide range of vehicle categories.
- The selected model has modest explanatory power.
- The model may not predict premium and luxury vehicle prices as accurately as lower-priced vehicles.
- The dataset represents asking prices, which may differ from actual transaction prices.
- Further feature engineering, model tuning and additional data could improve predictive performance.

## 11. Project Files

The project repository contains the following deliverables:

- `CAPSTONE EDA.ipynb` – Jupyter Notebook containing data cleaning, exploratory data analysis, modelling and evaluation.
- `used_cars_cleaned.csv` – Cleaned dataset.
- `used_car_price_model.pkl` – Saved Linear Regression model.
- `README.md` – Project documentation.
- `presentation.pptx` – Capstone presentation.

## 12. Tools and Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook
- Joblib

## 13. Conclusion

This project demonstrates the application of data science and machine learning techniques to used vehicle asking-price prediction.

The modelling process involved data preparation, exploratory analysis, preprocessing, regression model development and performance evaluation.

Although the Linear Regression model performed best overall among the models tested, its predictive performance indicates opportunities for further improvement. The project provides a foundation for additional experimentation and the development of more effective vehicle price prediction approaches.
