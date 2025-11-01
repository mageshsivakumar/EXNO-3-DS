# EX.NO-3-DS
## AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

## ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

## FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

## Methods Used for Data Transformation:
  ## 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  ## 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

## CODING AND OUTPUT:
```
import pandas as pd
df=pd.read_csv("/content/Encoding Data.csv")
df
```
![image](https://github.com/22008837/EXNO-3-DS/assets/120194155/4117e05e-4992-450b-80e4-5b1be67d1814)
```
#ORDINAL ENCODER
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[['ord_2']])
```
![image](https://github.com/22008837/EXNO-3-DS/assets/120194155/8b67ad44-595e-4225-a26f-b6545a3461cb)
```
df['bo_2']=e1.fit_transform(df[['ord_2']])
df
```
![image](https://github.com/22008837/EXNO-3-DS/assets/120194155/c871c240-302d-4baa-8c04-4654628df411)
```
#LABEL ENCODER
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
```
![image](https://github.com/22008837/EXNO-3-DS/assets/120194155/4657f8e2-84fd-4e7d-92fe-7d46a693e406)
```
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))

df2=pd.concat([df,enc],axis=1)
df2
```
![image](https://github.com/22008837/EXNO-3-DS/assets/120194155/f1e870fe-51ae-4e4b-bfcb-b59def84d06d)
```
pd.get_dummies(df2,columns=['nom_0'])
```
![image](https://github.com/22008837/EXNO-3-DS/assets/120194155/4f57e48e-abe5-41c1-a63e-04875ffb6dde)
```
from category_encoders import  BinaryEncoder
df=pd.read_csv("/content/data.csv")
df
```
![image](https://github.com/22008837/EXNO-3-DS/assets/120194155/3d70e493-a46e-4536-9fb7-de486bea0e75)
```
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb
```
![image](https://github.com/22008837/EXNO-3-DS/assets/120194155/7cf9091a-b03e-4cf6-bc82-9761d5786562)
```
from category_encoders import TargetEncoder
te=TargetEncoder()
cc=df.copy()
new=te.fit_transform(X=cc['City'],y=cc['Target'])
cc=pd.concat([cc,new],axis=1)
cc
```
![image](https://github.com/22008837/EXNO-3-DS/assets/120194155/bf9e0f7f-dc6e-4a82-8fad-2ef71b59757d)

## RESULT:
Thus, performing Feature Encoding and Transformation process for the given data set is completed.

       
