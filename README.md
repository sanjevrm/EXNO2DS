# EXNO2DS_Exploratory Data Analysis

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


# CODING AND OUTPUT:
```
Developed by : Sanjev R M
Register Number: 212223040186
```
~~~
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/titanic_dataset.csv")
df
~~~


![image](https://github.com/user-attachments/assets/e5aeef52-d800-4d6b-9126-f0bd89ad84b3)

df.info()

![image](https://github.com/user-attachments/assets/ed040f87-7f68-4372-9820-03cb074a21f2)

df.shape()

![image](https://github.com/user-attachments/assets/9443a79e-9514-403a-a2fa-a2565121b935)
~~~
df.set_index("PassengerId",inplace=True)
df.describe()
~~~

![image](https://github.com/user-attachments/assets/d3fd1e15-ac3d-4903-9f7f-c2b666f69826)

df.shape

![image](https://github.com/user-attachments/assets/2896e6f0-13c8-4145-82ea-d0ed5fe0af56)

# Categorical data analysis

df.nunique()

![image](https://github.com/user-attachments/assets/a27b805c-a9ac-4afd-a294-7e3d4a95b335)

df["Survived"].value_counts()

![image](https://github.com/user-attachments/assets/5f2b026d-8e39-4fcb-ac0b-31ee1fe23a12)
~~~
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
~~~

![image](https://github.com/user-attachments/assets/5c442f50-c953-4f63-9faf-36e7e1fa0314)

sns.countplot(data=df,x="Survived")

![image](https://github.com/user-attachments/assets/3a0d7a9e-de35-4525-8664-3ce7701d1769)

df

![image](https://github.com/user-attachments/assets/84a4b88d-45a4-4b69-a6f8-9484af6f999e)

df.Pclass.unique()

![image](https://github.com/user-attachments/assets/a1e4472e-3b4f-4fbc-a8f2-74a7886bc6ee)
~~~
df.rename(columns={'Sex':'Gender'},inplace=True)
df
~~~

![image](https://github.com/user-attachments/assets/bf8a5458-42b2-4e9c-b4f7-3fd2c811daac)

sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)

![image](https://github.com/user-attachments/assets/e08d530d-c594-4ac1-827d-5c4429ace290)

# Bivariate Analysis

sns.catplot(x="Survived",hue="Gender",data=df,kind="count")

![image](https://github.com/user-attachments/assets/a98b823c-86ee-4525-8ed3-5b225e0ba9f9)

df.boxplot(column="Age",by="Survived")

![image](https://github.com/user-attachments/assets/8356dc83-b94a-478b-94e8-9305396541fe)

sns.scatterplot(x=df["Age"],y=df["Fare"])

![image](https://github.com/user-attachments/assets/3dc9ccc8-cf29-4a4b-92e6-b17a9bae0668)

sns.jointplot(x="Age",y="Fare",data=df)

![image](https://github.com/user-attachments/assets/ac1865ad-69e8-4566-b350-707118a4b5c5)

# Multivariate Analysis
~~~
fig, ax1 = plt.subplots(figsize=(8,5))
plt = sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)
~~~

![image](https://github.com/user-attachments/assets/38ee5d29-7cf2-4a20-af05-a6ef0d8fa168)

sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")

![image](https://github.com/user-attachments/assets/b1f20b7a-7e8e-4ccc-9158-1df371071d0c)
~~~
df_numeric = df.select_dtypes(include=['number'])
corr=df_numeric.corr()
sns.heatmap(corr,annot=True)
plt.show()
~~~

![image](https://github.com/user-attachments/assets/54903f6a-a3f0-42ea-991f-75b13fac0e05)

sns.pairplot(df)

![last](https://github.com/user-attachments/assets/dedb81fb-d2ec-4ee3-bdcb-9e43956e8413)
# RESULT:
      We have performed Exploratory Data Analysis on the given data set successfully.
