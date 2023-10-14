# Ex-04-Multivariate-Analysis

## Aim: 
To perform Multivariate EDA on the given data set.

## Explanation:
Exploratory data analysis is used to understand the messages within a dataset. This technique involves many iterative processes to ensure that the cleaned data is further sorted to better understand the useful meaning.The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
### STEP 1
Import the built libraries required to perform EDA and outlier removal.
### STEP 2
Read the given csv file
### STEP 3
Convert the file into a dataframe and get information of the data.
### STEP 4
Return the objects containing counts of unique values using (value_counts()).
### STEP 5
Plot the counts in the form of Histogram or Bar Graph.
### STEP 6
Use seaborn the bar graph comparison of data can be viewed.
### STEP 7
Find the pairwise correlation of all columns in the dataframe.corr()
### STEP 8
Save the final data set into the file

## PROGRAM:
```
import pandas as pd
from scipy import stats
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```
```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/99a13ea7-789c-4ce5-9256-c07a88c791a0)

```
df = pd.read_csv('diabetes.csv')
df
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/9356f687-1954-42bb-af24-f3849f8ddcae)

```
df.isnull().sum()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/9373c3eb-849b-4268-86eb-3a1db6e2c6a4)

```
q1 = df.quantile(0.25)
q3 = df.quantile(0.75)
iqr = q3 - q1
iqr
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/33eebbb0-8d87-4c51-a11f-3ae457219dc2)

```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
df = df[(df >= low) & (df <= high)]
df
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/459083de-40d1-473c-bb28-4fba773eaaef)

```
sns.boxplot(df)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/5ac2bc56-6837-4e55-989a-0dc089c9622a)

```
plt.figure(figsize = (14,6))
sns.scatterplot(x = 'Glucose',y='BloodPressure',data = df)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/6257b016-49b8-46c2-849b-b740508b2d77)

```
sns.scatterplot(x = 'Glucose',y='Insulin',data = df)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/fb3bee2a-d00f-448b-ab8e-241cc32677af)

```
sns.scatterplot(x = 'Glucose',y='DiabetesPedigreeFunction',data = df)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/9abd93c2-cec8-4e37-95c6-5206a734afb1)

```
sns.scatterplot(x = 'Glucose',y='Age',data = df)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/bc6076e6-3bc8-4bc2-abcb-6c916cc01b47)

```
sns.heatmap(df.corr(),annot = True)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/0cb85069-a635-4a05-a216-7a85ceb5eca1)

```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/8ba06eb1-94a7-4768-8513-a64dc97acd0e)

```
df = pd.read_csv('employeesal.csv')
df
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/ba7e3871-0b70-4d70-8586-1438f612a825)

```
df.isnull().sum()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/16afdf57-25cc-4b17-b86b-f8f39dba3271)

```
numeric_cols = df.select_dtypes(include=[int, float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/bdf0d6ce-dbb7-4970-bd96-18bdad14d9ff)

```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
numeric_cols.dropna()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/8a9074c1-ed58-4b89-b539-73d01f1a2136)

```
sns.boxplot(numeric_cols)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/563ca362-9721-457d-9964-3ce7f0c3eb85)

```
sns.scatterplot(x = 'Salary',y='Age',data = numeric_cols)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/829e9c3d-e71c-4a00-9e37-887ce58264f6)

```
sns.scatterplot(x = 'Experience_Years',y='Salary',data = numeric_cols)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/3f3b3e2d-606c-447a-a91b-2e2293a6b363)

```
sns.scatterplot(x = 'Experience_Years',y='Age',data = numeric_cols)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/28e41989-8ac6-4564-9757-3f67f22f3289)

```
sns.heatmap(numeric_cols.corr(),annot = True)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/c919d1cc-c1f7-46d9-b6cd-d05d18f970c6)

```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/fc96fac6-c669-43fa-8914-4642ad9329de)

```
df = pd.read_csv('employeesal.csv')
df
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/7f516fbf-d78c-4dad-b606-20c6cb719838)

```
df.isnull().sum()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/559ece5b-9de5-4565-84b4-944f17427cb9)

```
numeric_cols = df.select_dtypes(include=[int, float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/58c01a46-994e-4ccf-8a23-efda052447e6)

```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
numeric_cols.dropna()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/280b06a5-b39b-4d9f-a1c7-f808331dccfd)

```
sns.boxplot(numeric_cols)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/28ff043b-b07d-4cfd-9563-0ee1d5360279)

```
sns.scatterplot(x = 'Salary',y='Age',data = numeric_cols)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/1c48b49c-66e5-4787-8e88-f73ce2022f77)

```
sns.scatterplot(x = 'Experience_Years',y='Age',data = numeric_cols)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/7fa4e104-2cc6-4a21-aecc-c8e6c08c8d14)

```
sns.heatmap(numeric_cols.corr(),annot = True)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/e5dc77de-893e-4a87-8876-03200594c123)

```
from google.colab import files
uploaded = files.upload()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/279f9856-e645-4c84-8585-e82b5a7266aa)

```
df = pd.read_csv('SuperStore.csv')
df
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/f16b0982-692b-4409-a5a4-e17b0f72c67a)

```
df.isnull().sum()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/d43c076e-70f8-4350-b95c-d8b59c82f813)

```
df.dropna()
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/aecf78df-b00a-4fb9-87ef-f84745fd0229)

```
df.dtypes
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/51610679-8b18-46b8-85f7-04f0d5a3a0d8)

```
numeric_cols = df.select_dtypes(include=[int,float])
q1 = numeric_cols.quantile(0.25);
q3 = numeric_cols.quantile(0.75);
iqr = q3 - q1
iqr
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/dc8f81ea-82e1-4386-b5cb-83f63f07a10a)

```
low = q1 - 1.5*iqr
high = q1 + 1.5*iqr
numeric_cols = numeric_cols[(numeric_cols >= low) & (numeric_cols <= high)]
```
```
sns.boxplot(numeric_cols)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/849c2f19-b849-4801-8caa-2731a4b9f2bf)

```
sns.heatmap(numeric_cols.corr(),annot = True)
```
![image](https://github.com/mathes6112004/ODD2023-Datascience-Ex-04/assets/119477782/7ab15678-e575-4c7d-ac59-ac4f03832047)

## RESULT:
Thus we have read the given data and performed the multivariate analysis with different types of plots
