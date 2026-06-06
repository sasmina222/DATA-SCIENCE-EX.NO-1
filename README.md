#EX.NO:1
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
df=pd.read_csv("SAMPLEIDS.csv")
df
```
<img width="902" height="705" alt="image" src="https://github.com/user-attachments/assets/31c7e9d6-4dc0-4a18-a9f2-755a0384f367" />
```
df.head(4)
```
<img width="923" height="192" alt="image" src="https://github.com/user-attachments/assets/4602aa9c-8c3e-4108-9214-9590558cbebc" />
```
df.isnull().sum()
```
<img width="265" height="302" alt="image" src="https://github.com/user-attachments/assets/ca2dc3d2-5332-4ad3-9922-74c93fadab61" />
```
df.isnull().any()
```
<img width="259" height="294" alt="image" src="https://github.com/user-attachments/assets/789e8282-c0f2-434a-ae42-0ee8c77c530a" />
```
df.dropna(axis=1)
```
<img width="393" height="728" alt="image" src="https://github.com/user-attachments/assets/f67f399f-221f-4225-9056-2c77051f3a96" />
```
df.fillna(method="ffill")
```
<img width="929" height="726" alt="image" src="https://github.com/user-attachments/assets/d96aea0a-fa95-4c45-969f-9ca288d007cc" />
```
df.bfill()
```
<img width="937" height="747" alt="image" src="https://github.com/user-attachments/assets/b9303d3e-35ea-46e0-8299-e954a709b295" />
```
df.fillna({'REGNO':0, 'NAME':'PRAVEEN'})
```
<img width="942" height="750" alt="image" src="https://github.com/user-attachments/assets/e40c6779-3859-4652-9bcc-af5e86a1ba9c" />
```
ir=pd.read_csv("iris.csv")
ir
```
<img width="612" height="458" alt="image" src="https://github.com/user-attachments/assets/38794b30-39de-4a37-96fb-f016828d3050" />
```
ir.describe()
```
<img width="522" height="322" alt="image" src="https://github.com/user-attachments/assets/ad47032d-e2ef-4ce3-aa00-fc4dd1d34449" />
```
import seaborn as sns
sns.boxplot(x="sepal_width",data=ir)\
```
<img width="709" height="597" alt="image" src="https://github.com/user-attachments/assets/5b03daa4-779d-407c-97d7-b5aaa962aaf7" />
```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```
<img width="112" height="41" alt="image" src="https://github.com/user-attachments/assets/ecf941ff-5248-4472-b29d-b99333ea3a90" />
```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="376" height="137" alt="image" src="https://github.com/user-attachments/assets/0dbbb0d4-2bda-4e49-80f3-f6d36e64da35" />
```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```
<img width="607" height="476" alt="image" src="https://github.com/user-attachments/assets/d0700d98-5588-4b8a-b7e8-b6d797245893" />
```
rid=ir[((ir.sepal_width>(q1-1.5*iqr))&(ir.sepal_width<(q3+1.5*iqr)))]
rid['sepal_width']
```
<img width="480" height="276" alt="image" src="https://github.com/user-attachments/assets/b809075f-6f8d-4074-b6ec-1559c41fa46e" />
```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir.sepal_width))
z
```
<img width="480" height="274" alt="image" src="https://github.com/user-attachments/assets/8c08a13b-945d-464d-8d8f-31690c14eed7" />


# Result
Thus we have cleaned the data and removed the outliers by detectionusing IQR and Z-score method
