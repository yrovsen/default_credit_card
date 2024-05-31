# Credit Card Default Prediction

This project focuses on predicting credit card defaults using various classification models. The main objective is to classify whether a client will default on their credit card payment based on a set of features. The project involves several steps, including data import, preprocessing, model building, and optimization.

## Table of Contents

1. [Data Import](#data-import)
2. [Preprocessing Steps](#preprocessing-steps)
   - [Outlier Treatment (Capping method)](#outlier-treatment-capping-method)
   - [Feature Creation](#feature-creation)
   - [Normal Distribution Checking](#normal-distribution-checking)
   - [Correlation Check](#correlation-check)
   - [WOE Transformation](#woe-transformation)
3. [Train Test Splitting](#train-test-splitting)
4. [Model Building](#model-building)
5. [Model Optimization](#model-optimization)
6. [Stacking Classifier](#stacking-classifier)
7. [Univariate Analysis](#univariate-analysis)

## Data Import

The dataset used in this project contains information on whether clients defaulted on their credit card payments. It consists of 30,000 rows and 24 features, along with 1 target column, which is the default column. We have checked the data in terms of statistics using the `describe` command. Finally, the meanings of each columns have been placed in the excel file (second sheet).

## Preprocessing Steps

### Outlier Treatment (Capping method)

Outliers in the dataset were treated using the capping method. The interquartile range (IQR) was calculated for each numeric feature to determine the upper and lower boundaries. For each numeric column, if the values exceeded the upper boundary, they were capped at the upper boundary. Similarly, values below the lower boundary were capped at the lower boundary. This approach ensures that extreme values do not adversely affect the model performance.

### Feature Creation

New features were created to enhance the predictive power of the model by leveraging the relationships between existing features. Specifically, statistical analysis was used to create new columns based on the relationships between `EDUCATION` and `LIMIT_BAL`, as well as `MARRIAGE` and `LIMIT_BAL`.

For each category in `EDUCATION`, new columns were created to capture the mean, sum, minimum, and maximum values of `LIMIT_BAL`. This was done by grouping the data by `EDUCATION` and calculating these statistics, which were then merged back into the main dataset.

Similarly, new columns were created for each category in `MARRIAGE`, capturing the mean, sum, minimum, and maximum values of `LIMIT_BAL` by grouping the data by `MARRIAGE` and performing the same statistical calculations. These new features provide additional insights into the relationships between these variables, which can improve the model's performance.

### Normal Distribution Checking

The normal distribution of numeric columns was assessed using the Kolmogorov-Smirnov test (Smirnov test). This statistical test compares the distribution of each column against a normal distribution hypothesis.

For each numeric column, the Kolmogorov-Smirnov test statistic (`kstest_statistic`) and its associated p-value (`kstest_p_value`) were computed. A p-value greater than 0.05 indicates that the data follows a normal distribution. Columns with p-values less than or equal to 0.05 were identified as not normally distributed.

In cases where the data was not normally distributed, Spearman correlation was chosen instead of Pearson correlation for assessing relationships between variables. Spearman correlation is suitable for ordinal and non-normally distributed data, providing robustness against outliers and non-linear relationships.

This approach ensures that appropriate statistical methods are used depending on the distribution characteristics of the data, thereby enhancing the reliability of the analysis.

### Correlation Check

In this project, two types of correlation analyses were conducted: target correlation and intercorrelation among features.

**Target Correlation:** 
Target correlation assesses the relationship between each feature and the target variable (`default` in this case). Features with an absolute correlation coefficient of 10% or higher with the target are considered to have a significant influence on predicting credit card defaults.

**Intercorrelation Among Features:** 
Intercorrelation examines relationships between pairs of features in the dataset. Features with intercorrelation coefficients of 80% or higher are considered highly correlated. Managing such high intercorrelation helps prevent multicollinearity, ensuring that the model remains robust and interpretable.

**Variance Inflation Factor (VIF):**
Additionally, VIF was used to detect multicollinearity among features. A VIF coefficient below 10 indicates that the variance of a feature is not significantly inflated by its correlations with other features. Features with high VIF scores were carefully reviewed or excluded from the model to enhance its stability and predictive accuracy.

**Selected Columns for Analysis:** 
Based on these analyses, several key features were chosen for further modeling and analysis. These columns strike a balance between their significant correlation with the target variable, moderate intercorrelation with other features, and low VIF scores, ensuring a robust and interpretable predictive model.

This comprehensive approach ensures that the model effectively captures relevant relationships while mitigating issues related to multicollinearity.

### WOE Transformation

WOE transformation plays a crucial role in transforming categorical variables into a form that is more suitable for predictive modeling. Here's how it's implemented:

**Numeric Values:**
- Numerical features are binned based on quartiles (q1, q2, q3).
- Each bin is assigned a category, and WOE values are calculated to capture the relationship between the feature and default status.
- This transformation helps in identifying how each numerical feature contributes to predicting credit card defaults.

**Categorical Values:**
- Categorical features are grouped by their unique values.
- WOE values are computed to quantify the predictive strength of each category in relation to credit card default.
- Missing values and categories with sparse data are handled to ensure robust WOE transformation.

## Train Test Splitting

The dataset is split into training and testing sets to evaluate the performance of the models. Here I have taken 3 inputs depending on the models: Logistic Regression inputs, Catboost custom model inputs declaring categoric features, and inputs for other models.

## Model Building

Several classification models are built to predict the likelihood of credit card defaults, including logistic regression, decision trees, and random forests.

## Model Optimization

Hyperparameters of the models are tuned using cross-validation techniques to achieve the best performance.

## Stacking Classifier

A stacking classifier is implemented to combine the predictions of multiple models and improve overall accuracy.

## Univariate Analysis

Univariate analysis is performed to understand the distribution and central tendency of individual features.

## Results and Conclusion

The models are evaluated based on various metrics, and the best-performing model is identified. The project demonstrates the effectiveness of combining multiple preprocessing and modeling techniques to improve classification accuracy.

## About Me

I am a data scientist with expertise in machine learning and data analysis. This project is a part of my portfolio showcasing my skills in building and optimizing classification models.

Feel free to explore the project and reach out if you have any questions or suggestions!

[Contact Me](mailto:your.email@example.com)
