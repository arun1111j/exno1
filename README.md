# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![image](https://github.com/arun1111j/exno1/assets/128461833/9e826176-ba10-4af2-86d3-e9df0e12c392)
```
data = pd.get_dummies(data)
data.isnull().sum()
```
![Screenshot 2024-03-04 135206](https://github.com/arun1111j/exno1/assets/128461833/172a9dea-4d5a-4220-9803-b43196225c73)

```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![Screenshot 2024-03-04 135311](https://github.com/arun1111j/exno1/assets/128461833/b5451ce4-69f3-434e-920d-e99976495321)
```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
![Screenshot 2024-03-04 135406](https://github.com/arun1111j/exno1/assets/128461833/c9082b65-cf01-479a-a844-6be2094fd769)
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![Screenshot 2024-03-04 135444](https://github.com/arun1111j/exno1/assets/128461833/75a87488-288c-4738-bdbe-c024fdfb39dc)
```
ir.describe()
```
![Screenshot 2024-03-04 135515](https://github.com/arun1111j/exno1/assets/128461833/17dce9a0-36cb-43e9-9df7-55e1910a7388)
```
sns.boxplot(x='sepal_width',data=ir)
```
![Screenshot 2024-03-04 140541](https://github.com/arun1111j/exno1/assets/128461833/163db3ed-706c-4ea3-b42e-18d476e8bc6c)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![Screenshot 2024-03-04 140605](https://github.com/arun1111j/exno1/assets/128461833/258f6135-2b70-489a-8cdb-e39cf2828aaf)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![Screenshot 2024-03-04 140633](https://github.com/arun1111j/exno1/assets/128461833/8ad00042-b58b-43f0-9a9e-81a52acd09db)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![Screenshot 2024-03-04 140707](https://github.com/arun1111j/exno1/assets/128461833/b536b51f-27ea-4bef-83b6-b2d8d8bcc48f)
```
sns.boxplot(x='sepal_width',data=delid)
```
![Screenshot 2024-03-04 140745](https://github.com/arun1111j/exno1/assets/128461833/867a8a1c-72f3-4904-b582-bbe91eed1d04)
## Z Score:
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![Screenshot 2024-03-04 141713](https://github.com/arun1111j/exno1/assets/128461833/accf3722-79f3-4745-b817-f5c3ff179e7d)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```







# Result
        Thus the given data is read,cleansed and the cleaned data is saved into the file.
