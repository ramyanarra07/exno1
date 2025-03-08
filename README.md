# Exno:1
# Data Cleaning Process

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
import pandas as pd

ramya = pd.read_csv("/content/SAMPLEIDS.csv")

print(ramya)

![image](https://github.com/user-attachments/assets/6ce0b364-a812-4748-9af4-ea48d71724ae)

ramya.head()

![image](https://github.com/user-attachments/assets/0d8e5b85-4aee-470a-ba5a-508f3b668069)

ramya.tail()

![image](https://github.com/user-attachments/assets/5986b68e-d820-4b3a-a55d-fd3ead7d0207)

ramya.shape

![image](https://github.com/user-attachments/assets/b2dab315-23e5-42a2-b6b3-58225470c7db)

ramya.isnull()

![image](https://github.com/user-attachments/assets/5792af52-c098-4850-ba22-914b7666b3fd)

ramya.fillna(50)

![image](https://github.com/user-attachments/assets/828a7a13-00b7-416b-9312-ef80ba164092)

ramya.dropna(axis=0)

![image](https://github.com/user-attachments/assets/3cf701bf-0e4d-417e-9120-a7fe6a3a9f9c)

ramya.dropna(axis=1)

![image](https://github.com/user-attachments/assets/d3150364-91af-425c-a0cc-794331877633)

ramya.isnull().sum()

![image](https://github.com/user-attachments/assets/b66ac12a-0783-46e1-b286-7358a8c5a1c4)

ramya.isnull().any()

![image](https://github.com/user-attachments/assets/34a59dcc-d7fa-4658-8246-a93e0e6a7669)

ramya.fillna(method = 'ffill')

![image](https://github.com/user-attachments/assets/41c905f7-3e50-4aa2-b8a3-01dfaed68f28)

ramya.fillna(method = 'bfill')

![image](https://github.com/user-attachments/assets/0f4bb8c4-a9a6-4ba6-a348-1d7d19d36f95)

ramya.fillna({'NAME':'RAMYA','ADDRESS':'TIRUPATHI','GENDER':'FEMALE','M1':'36','M2':'88','M3':'99','M4':'100'})

klara=pd.read_csv("/content/iris.csv")

print(klara)

![image](https://github.com/user-attachments/assets/03be418e-33d1-45e6-b9f7-7038327c1508)

klara.shape

![image](https://github.com/user-attachments/assets/515d0dbd-930a-4e8f-afcb-b13b30ee369e)

klara.info()

![image](https://github.com/user-attachments/assets/cba20c14-06a4-4a84-9e30-b3ef53a4fda3)

klara.describe()

![image](https://github.com/user-attachments/assets/d7313abf-a36c-4a5e-beda-4dd4f7700465)

import seaborn as sns

sns.boxplot(x='sepal_width',data=klara)

![image](https://github.com/user-attachments/assets/3806019b-c5bf-411b-8734-b0095452560f)

klara.isnull().sum()

![image](https://github.com/user-attachments/assets/b5605008-5fb9-4900-be08-e22a28341ba4)

Q1=klara.sepal_width.quantile(0.25)

Q3=klara.sepal_width.quantile(0.75)

IQR=Q3-Q1

print(IQR)

![image](https://github.com/user-attachments/assets/0a434552-5d82-4a4f-b7b6-a01684b584e0)

OUTLIER=klara[((klara.sepal_width<(Q1-1.5*IQR))|(klara.sepal_width>(Q3+1.5*IQR)))]

OUTLIER['sepal_width']

![image](https://github.com/user-attachments/assets/f9a70c72-b7c2-44b1-a6ce-67e345bb65eb)

OUTLIER=klara[~((klara.sepal_width<(Q1-1.5*IQR))|(klara.sepal_width>(Q3+1.5*IQR)))]

OUTLIER['sepal_width']

![image](https://github.com/user-attachments/assets/e6179424-8eaa-4570-986c-fa1f86826c6d)

sns.boxplot(x='sepal_width',data=OUTLIER)

![image](https://github.com/user-attachments/assets/54d6a659-011c-4098-b225-542a9f8188c9)

import numpy as np

import scipy.stats as stats

Z=np.abs(stats.zscore(klara['sepal_width']))

print(Z)

![image](https://github.com/user-attachments/assets/23b51464-9a3b-44dc-a571-f0f6c6cdbf8e)

df1=klara[Z<1]

print(df1)

![image](https://github.com/user-attachments/assets/934fd6b4-1a0b-4f04-ae5c-56d9ae514a2d)


# Result
Thus the Data Cleaning Process is executed Successfully.
