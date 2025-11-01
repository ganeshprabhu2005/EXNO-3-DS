## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.

STEP 2:Clean the Data Set using Data Cleaning Process.

STEP 3:Apply Feature Encoding for the feature in the data set.

STEP 4:Apply Feature Transformation for the feature in the data set.

STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding:
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding:
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding:
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding:
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
       # INCLUDE YOUR CODING AND OUTPUT SCREENSHOTS HERE
       import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
<img width="548" height="543" alt="image" src="https://github.com/user-attachments/assets/92ae53f0-9030-4d92-983b-b98f6c710e6e" />
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
 pm=['Hot','Warm','Cold']
 e1=OrdinalEncoder(categories=[pm])
 e1.fit_transform(df[["ord_2"]])
<img width="308" height="319" alt="image" src="https://github.com/user-attachments/assets/83b3455a-3869-4239-b39a-b745047193da" />
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
<img width="548" height="509" alt="image" src="https://github.com/user-attachments/assets/1bedbb6f-13ad-44bb-a767-1cf6e1160895" />
le=LabelEncoder()
 dfc=df.copy()
 dfc['ord_2']=le.fit_transform(dfc['ord_2'])
 dfc
 <img width="555" height="502" alt="image" src="https://github.com/user-attachments/assets/a2efb631-ee82-4e83-8588-df6095ce60e7" />
 from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse_output=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[["nom_0"]]))
df2=pd.concat([df2,enc],axis=1)
df2
<img width="556" height="468" alt="image" src="https://github.com/user-attachments/assets/e489d023-e5e0-4b0a-a56d-b7d97e7e594e" />
pd.get_dummies(df2,columns=["nom_0"])
<img width="537" height="234" alt="image" src="https://github.com/user-attachments/assets/59f512a7-f6ac-497c-a8ad-ea1aaed9c6d4" />
from category_encoders import BinaryEncoder
df=pd.read_csv("Encoding Data.csv")
df
<img width="545" height="473" alt="image" src="https://github.com/user-attachments/assets/05d8b4cc-85f2-42c0-ac85-f02cc3f7fc6b" />
be=BinaryEncoder()
nd=be.fit_transform(df['ord_2'])
df
<img width="550" height="538" alt="image" src="https://github.com/user-attachments/assets/cef8656d-94c2-48cd-9a66-db4977659a7e" />
pip install --upgrade category-encoders
from category_encoders import BinaryEncoder
df=pd.read_csv("data.csv")
df
<img width="555" height="333" alt="image" src="https://github.com/user-attachments/assets/90bdbfd8-067c-42dd-bcf7-57114bc41daa" />
 be=BinaryEncoder()
 nd=be.fit_transform(df['Ord_2'])
 df

<img width="531" height="308" alt="image" src="https://github.com/user-attachments/assets/0d60bbc4-07bd-4486-bc92-fa5ddff88f12" />
dfb=pd.concat([df,nd],axis=1)
dfb
<img width="555" height="232" alt="image" src="https://github.com/user-attachments/assets/6e47e8d0-3cd5-40d3-9d2c-9e0ee94b1c27" />
from category_encoders import TargetEncoder
 te=TargetEncoder()
 CC=df.copy()
 new=te.fit_transform(X=CC["City"],y=CC["Target"])
 CC=pd.concat([CC,new],axis=1)
 CC
 <img width="557" height="324" alt="image" src="https://github.com/user-attachments/assets/f302de05-6b46-4b30-b38e-144b6ddd0405" />
 import pandas as pd
 from scipy import stats
 import numpy as np
 df=pd.read_csv("Data_to_Transform.csv")
 df
 <img width="530" height="388" alt="image" src="https://github.com/user-attachments/assets/7752d216-5507-4517-bc36-ca0df9b016f1" />
 df.skew()
 <img width="526" height="261" alt="image" src="https://github.com/user-attachments/assets/40d5bec5-aa4e-4889-9569-e3419d441dcb" />
 np.log(df["Highly Positive Skew"])

<img width="545" height="618" alt="image" src="https://github.com/user-attachments/assets/88e486fb-9f05-4477-9dd3-fa20c3f9e1cf" />
np.reciprocal(df["Moderate Positive Skew"])
<img width="579" height="642" alt="image" src="https://github.com/user-attachments/assets/84241bdb-34f7-40a1-bf25-f8cb75c70f6a" />
np.sqrt(df["Highly Positive Skew"])
<img width="591" height="592" alt="image" src="https://github.com/user-attachments/assets/8b8f90e9-f029-4c33-85df-6ace9e15080c" />
np.square(df["Highly Positive Skew"])

<img width="551" height="561" alt="image" src="https://github.com/user-attachments/assets/da36fe0c-4b62-4710-be2e-825f304ccfe3" />
df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
df
<img width="533" height="415" alt="image" src="https://github.com/user-attachments/assets/372ea3db-5d94-4b0e-8604-d1aa38079ef3" />
df.skew()
<img width="533" height="318" alt="image" src="https://github.com/user-attachments/assets/16b0d1d9-14a5-4f15-95af-f470b2a3df98" />
df["Highly Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Highly Negative Skew"])
df.skew()
<img width="544" height="319" alt="image" src="https://github.com/user-attachments/assets/39fd6395-fe76-4cbb-9e98-8809b3395640" />
from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal')
 df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate  Negative Skew"]])
 df
<img width="550" height="244" alt="image" src="https://github.com/user-attachments/assets/6c1139e1-8415-4901-a11a-48e71c1b029b" />
import seaborn as sns
 import statsmodels.api as sm
 import matplotlib.pyplot as plt
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()
<img width="552" height="400" alt="image" src="https://github.com/user-attachments/assets/3aa57019-afca-4e60-a212-5f0adf8c72f4" />
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
<img width="560" height="393" alt="image" src="https://github.com/user-attachments/assets/8a8cd43f-af5e-4d87-a287-7cf27e1800cb" />
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
 sm.qqplot(df["Moderate Negative Skew"],line='45')
 plt.show()
<img width="532" height="409" alt="image" src="https://github.com/user-attachments/assets/2440ce5b-6b1a-4664-b084-c49be1648e6a" />
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
 sm.qqplot(df["Highly Negative Skew"],line='45')
 plt.show()
<img width="552" height="413" alt="image" src="https://github.com/user-attachments/assets/698c8bdf-1c57-4170-91a2-25e0740b1559" />
dt=pd.read_csv("titanic_dataset.csv")
 dt
 from sklearn.preprocessing import QuantileTransformer
 qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
 dt["Age_1"]=qt.fit_transform(dt[["Age"]])
 sm.qqplot(dt['Age'],line='45') 
 plt.show()
<img width="584" height="362" alt="image" src="https://github.com/user-attachments/assets/9b2e1980-e3fb-4ac5-91a0-95a93afd6bf3" />
 dt=pd.read_csv("titanic_dataset.csv")
 dt
 sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
<img width="545" height="450" alt="image" src="https://github.com/user-attachments/assets/8e1d2230-998a-4a38-b5ef-8edea94f34b4" />



















 

 







 




       
# RESULT:
        Thus the given data, Feature Encoding, Transformation process and save the data to a file
 was performed successfully
       

       
