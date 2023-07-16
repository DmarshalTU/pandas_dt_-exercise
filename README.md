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

- os, dotenv: Used for reading environment variables from a .env file.
- pandas: A software library for data manipulation and analysis. Used for reading the data files, handling missing values, and merging the datasets.
- sklearn.preprocessing: Provides the StandardScaler class for standardizing features by removing the mean and scaling to unit variance.
- sklearn.decomposition: Provides the PCA class for applying Principal Component Analysis on the standardized features.

## Disclaimer

In this exercise, the `.env` file is visible for demonstration purposes. However, in a real-world scenario, it's important to add the `.env` file to your `.gitignore` file to prevent it from being committed to your git repository. This helps to prevent sensitive information like API keys, database credentials, etc., from being exposed.

## Output

```bash
python app.py

Data Information for Excel File:
Number of rows: 13
Number of columns: 4

First two rows:
   ID  NUM_CHILDREN  SALARY_PER_MONTH  CAR_VALUE
0   1             4            4343.0    23232.0
1   2             3            6464.0    35353.0

Last two rows:
    ID  NUM_CHILDREN  SALARY_PER_MONTH  CAR_VALUE
11  12             1           34543.0    64564.0
12  13             3           53436.0     5343.0

Sample of five random rows:
    ID  NUM_CHILDREN  SALARY_PER_MONTH  CAR_VALUE
1    2             3            6464.0    35353.0
10  11             2            6456.0    46456.0
3    4             4           36456.0     4654.0
0    1             4            4343.0    23232.0
6    7             1           10943.0     7576.0

Data Information for CSV File:
Number of rows: 13
Number of columns: 2

First two rows:
   ID  Years_of_education
0   1                10.0
1   2                 NaN

Last two rows:
    ID  Years_of_education
11  12                20.0
12  13                21.0

Sample of five random rows:
   ID  Years_of_education
0   1                10.0
8   9                 9.0
6   7                13.0
1   2                 NaN
3   4                18.0
    ID  NUM_CHILDREN  SALARY_PER_MONTH      CAR_VALUE  Years_of_education  PCA_Score
0    1             4           4343.00   23232.000000           10.000000   0.938192
1    2             3           6464.00   35353.000000           14.272727  -0.001245
2    3             2           7657.00   53234.000000           15.000000  -0.404391
3    4             4          36456.00    4654.000000           18.000000  -0.956621
4    5             5           4564.00   75458.166667           14.272727   0.868232
5    6             2           5355.00   53453.000000           16.000000  -0.492186
6    7             1          10943.00    7576.000000           13.000000  -0.705206
7    8             3           9000.00    3353.000000           12.000000   0.142969
8    9             5           5454.00   64757.000000            9.000000   1.545231
9   10             6          15389.25  543523.000000            5.000000   3.971494
10  11             2           6456.00   46456.000000           18.000000  -0.821169
11  12             1          34543.00   64564.000000           20.000000  -1.996270
12  13             3          53436.00    5343.000000           21.000000  -2.089031
```