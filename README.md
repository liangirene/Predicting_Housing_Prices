# Predicting Housing Prices

This project involves the iterative process of specifying, fitting, and analyzing the performance of a model using data science techniques. The goal is to predict housing prices based on various features of the houses. The project is divided into different parts, including exploratory data analysis (EDA), feature engineering, model specification, and regression analysis.

- One-Hot Encoding: The categorical variable "Roof Material" is encoded using one-hot encoding to prepare it for model training.
- Linear Regression from scikit-learn: Linear regression models are used to predict housing prices based on selected features.
- Building a Data Pipeline using pandas: The pandas library is used to manipulate and preprocess the dataset, including data cleaning, feature extraction, and transformation.

## Data Source
The dataset used in this project is obtained from the Cook County Assessor's Office (CCAO) in Illinois. The dataset consists of over 500,000 records describing houses sold in Cook County in recent years. The data includes 61 features related to the properties. The property tax assessments in Cook County are based on property values estimated using statistical models that consider factors such as real estate value and construction cost. The dataset has been split into training and test sets, with 204,792 and 68,264 observations, respectively.

To access the dataset, the data files have been compressed in the cook_county_data.zip file. After extracting the data, we can proceed with the analysis.

## Part 1: Exploratory Data Analysis
In this section, I performed exploratory data analysis (EDA) on the training data to gain insights and make informed modeling decisions. The EDA includes the following steps:

Sale Price Distribution: I examined the distribution of the target variable, "SalePrice," by visualizing it using both a histogram and a box plot. The initial visualization showed that most data points were clustered at the left-end of the plot, making it difficult to interpret. To overcome this issue, I rescaled and zoomed in on the region where most of the data are located by adjusting the x-axis.

Log Transformation: To further enhance the visualization and handle the skewed distribution of the target variable, I applied a logarithmic transformation to the "SalePrice" column. This transformed column is referred to as "Log Sale Price."

Correlation Analysis: I explored the correlation between the "Log Sale Price" and the total area occupied by the household, represented by the "Log Building Square Feet" column. A joint plot with a linear regression line was created to visualize the relationship between these variables. Based on the plot, it was observed that there is a positive correlation between "Log Sale Price" and "Log Building Square Feet," indicating that the latter could be a good candidate as a feature for our model.

## Part 2: Feature Engineering
In this section, I performed feature engineering techniques to enhance the predictive power of the model. The following techniques were applied:

Bedrooms Extraction: The total number of bedrooms was extracted from the "Description" column and assigned to a new column called "Bedrooms." This feature was included as one of the inputs for the model.

One-Hot Encoding: Since the "Roof Material" column is categorical, it was one-hot encoded to represent each category as a separate binary column. This encoding allows the model to consider the different roof materials as individual features. The new columns were named "rfm_MATERIAL," where "MATERIAL" represents each unique roof material.

## Part 3: Modeling
In this section, I specified the model and prepared the data for training and testing. The following steps were performed:

Train-Test Split: The dataset was split into a training set and a test set. The training set, which contains 80% of the data, was used to fit the model's parameters, while the test set was used to evaluate the model's performance on unseen data.

Preprocessing: Both the training and testing sets underwent preprocessing steps, including the removal of outliers in the "Sale Price" column (considering only households with prices greater than $499), log transformations of the "Sale Price" and "Building Square Feet" columns, and extraction of the total number of bathrooms into a new column called "Bedrooms."

Feature Selection: The selected features for the model were the "Log Sale Price" and "Bedrooms" columns. If it was the second model, the "Log Building Square Feet" column was also included.

Design Matrix and Observed Vector: The final step involved creating the design matrix "X" and the observed vector "y" from the selected features in the training and test sets. These matrices are either represented as numpy arrays or pandas dataframes.

## Part 4: Regression Analysis
Finally, in this section, I performed linear regression analysis using the scikit-learn library. Two linear regression models were initialized, each with a different set of features. The models were fitted using the training data, allowing estimation of the coefficients and intercepts. The models were then ready to make predictions on unseen data and analyze their performance.
