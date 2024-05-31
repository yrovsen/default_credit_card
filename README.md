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

The distribution of the features is checked for normality to decide if any transformations are needed.

### Correlation Check

A correlation check is performed to identify and handle multicollinearity between features.

### WOE Transformation

Weight of Evidence (WOE) transformation is applied to convert categorical variables into continuous variables, aiding in model performance.

## Train Test Splitting

The dataset is split into training and testing sets to evaluate the performance of the models.

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
