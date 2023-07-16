# Python Script for Data Merging and PCA Scoring

This Python script reads data from two files (an Excel file and a CSV file), handles missing values, merges the data into a single DataFrame, and applies a Principal Component Analysis (PCA) model to assign a single score to each row.

## Steps

- Read Data: The script reads data from an Excel file and a CSV file using the pandas library's read_excel and read_csv functions, respectively.
- Handle Missing Values: The script checks for missing values in the datasets. If any are found in the 'SALARY_PER_MONTH', 'CAR_VALUE', or 'Years_of_education' columns, they are filled with the mean of the respective columns. This is done using the fillna function in pandas. The reason for using the mean is that it does not significantly distort the data when the number of missing values is relatively small.
Data Merging: The script merges the two datasets into a single DataFrame based on the 'ID' column using the merge function in pandas.
- Standardization: Before applying PCA, the features are standardized to have a mean of 0 and a variance of 1. This is important because PCA is sensitive to the variances of the initial variables. This is done using the StandardScaler class in the sklearn.preprocessing module.
- Apply PCA: The script applies PCA to the standardized features and retrieves the first principal component. This is done using the PCA class in the sklearn.decomposition module. The first principal component is the linear combination of the features that captures the maximum variance in the data.
- PCA Scoring: The script adds the PCA score as a new column in the merged DataFrame. Each row's PCA score is a single metric that can be used to compare different rows.

The script finally prints out the merged DataFrame with the PCA scores.

## Libraries Used

- pandas: A software library for data manipulation and analysis. Used for reading the data files, handling missing values, and merging the datasets.
- sklearn.preprocessing: Provides the StandardScaler class for standardizing features by removing the mean and scaling to unit variance.
- sklearn.decomposition: Provides the PCA class for applying Principal Component Analysis on the standardized features.
