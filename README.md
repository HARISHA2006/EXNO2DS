# EXNO2DS

# AIM:
 To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
df = pd.read_csv("/content/titanic_dataset.csv")  # Replace with actual path

# Display basic info
df.info()

# Display first few rows
df.head()

# Check shape
print(f"Dataset contains {df.shape[0]} rows and {df.shape[1]} columns")
```
```
# Set PassengerId as index
df.set_index("PassengerId", inplace=True)

# Summary statistics
df.describe()
```
![image](https://github.com/user-attachments/assets/4679d9d0-f489-4495-80b7-dccda7589f48)
```
# Count unique values in categorical columns
categorical_columns = ["Survived", "Pclass", "Sex", "Embarked"]
for col in categorical_columns:
    print(f"{col} unique values:\n", df[col].value_counts(), "\n")
```
![image](https://github.com/user-attachments/assets/60cec805-ff91-493c-84e1-faff11f8958f)
```
sns.countplot(data=df, x="Survived")
plt.title("Survival Count")
plt.show()
```
![image](https://github.com/user-attachments/assets/20d70188-0f3c-445e-96a6-c3e8e26d3c07)

```
df["Pclass"].unique()
```
![image](https://github.com/user-attachments/assets/310ecb77-d9d9-45a2-a711-79d93a2d74c8)
```
df.rename(columns={"Sex": "Gender"}, inplace=True)
```
```
sns.catplot(x='Survived', hue='Gender', data=df, kind='count')
plt.title("Survival by Gender")
plt.show()
```
![image](https://github.com/user-attachments/assets/b72c7bb0-b9c4-49f8-9575-4fc943ad2b43)

```
sns.boxplot(x="Survived", y="Age", data=df)
plt.title("Age Distribution by Survival")
plt.show()
```
![image](https://github.com/user-attachments/assets/c9105756-42d4-4731-922d-2ce52d11c917)
```
sns.boxplot(x="Pclass", y="Age", hue="Gender", data=df)
plt.title("Age Distribution Across Passenger Classes and Gender")
plt.show()
```
![image](https://github.com/user-attachments/assets/c2bdad4f-8176-48b0-9299-6ea54ac2fded)
```
sns.catplot(x="Pclass", y="Survived", hue="Gender", data=df, kind="bar")
plt.title("Survival Rate by Passenger Class and Gender")
plt.show()
```
![image](https://github.com/user-attachments/assets/d70f0dd0-ee49-43de-b04b-45ac906e5996)
```
plt.figure(figsize=(10,6))

# Select only numerical columns
numerical_df = df.select_dtypes(include=["number"])

# Compute correlation and plot heatmap
sns.heatmap(numerical_df.corr(), annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Feature Correlation Heatmap")
plt.show()
```
![image](https://github.com/user-attachments/assets/5c89b201-7d12-40d9-b726-99e4d32ed2f1)
```
sns.pairplot(df, hue="Survived", diag_kind="kde")
plt.show()
```
![image](https://github.com/user-attachments/assets/0f559cd0-e117-46e5-b78d-ac99472894e8)

# RESULT
Thus, the Exploratory Data Analysis on the given data set was performed successfully.
        
