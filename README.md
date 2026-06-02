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
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.

2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.

3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.

4. One Hot Encoding
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

```
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
pm=['Hot','Warm','Cold']
e1=OrdinalEncoder(categories=[pm])
e1.fit_transform(df[["ord_2"]])
df['bo2']=e1.fit_transform(df[["ord_2"]])
df
le=LabelEncoder()
dfc=df.copy()
dfc['ord_2']=le.fit_transform(dfc['ord_2'])
dfc
from sklearn.preprocessing import OneHotEncoder
ohe=OneHotEncoder(sparse=False)
df2=df.copy()
enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
df2=pd.concat([df2,enc],axis=1)
df2=pd.concat([df2,enc],axis=1)
df2
pd.get_dummies(df2,columns=["nom_0"])
pip install --upgrade category_encoders
from category_encoders import BinaryEncoder
df=pd.read_csv("data.csv")
df
be=BinaryEncoder()
nd=be.fit_transform(df['Ord_2'])
dfb=pd.concat([df,nd],axis=1)
dfb1=df.copy()
dfb
from category_encoders import TargetEncoder
te=TargetEncoder()
CC=df.copy()
new=te.fit_transform(X=CC["City"],y=CC["Target"])
CC=pd.concat([CC,new],axis=1)
CC
import pandas as pd
from scipy import stats
import numpy as np
df=pd.read_csv("Data_to_Transform.csv")
df
df.skew()
np.log(df["Highly Positive Skew"])
np.reciprocal(df["Moderate Positive Skew"])
np.sqrt(df["Highly Positive Skew"])
np.square(df["Highly Positive Skew"])
df["Highly Positve Skew_boxcox"],parameters=stats.boxcox(df["Highly Positive Skew"])
df
df["Moderate Negative Skew_yeojohnson"],parameters=stats.yeojohnson(df["Moderate Negative Skew"])
df.skew()
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal')
df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
df
import seaborn as sns
import statsmodels.api as sm
import matplotlib.pyplot as plt
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
plt.show()
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
sm.qqplot(df["Moderate Negative Skew"],line='45')
plt.show()
df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
sm.qqplot(df["Highly Negative Skew"],line='45')
plt.show()
dt=pd.read_csv("titanic_dataset.csv")
dt
from sklearn.preprocessing import QuantileTransformer
qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
dt["Age_1"]=qt.fit_transform(dt[["Age"]])
sm.qqplot(dt['Age'],line='45') 
plt.show()
sm.qqplot(df["Highly Negative Skew_1"],line='45')
plt.show()
```

<img width="498" height="560" alt="Screenshot 2026-06-02 184345" src="https://github.com/user-attachments/assets/593bac93-85ab-487f-8879-3d8ad7cfc5bf" />
<img width="360" height="362" alt="Screenshot 2026-06-02 184353" src="https://github.com/user-attachments/assets/9c2b96f8-8edb-4a8e-81af-25d736ed20bb" />
<img width="625" height="553" alt="image" src="https://github.com/user-attachments/assets/bb558e78-7ee8-4cdd-9ca9-594203492a39" />
<img width="589" height="570" alt="image" src="https://github.com/user-attachments/assets/e9780d4c-3543-4290-8b1e-c61a32799c2a" />
<img width="1037" height="158" alt="image" src="https://github.com/user-attachments/assets/2d3ca868-1110-4467-9118-16252b0bc51a" />
<img width="543" height="567" alt="image" src="https://github.com/user-attachments/assets/f7e80d99-270c-4525-94e4-727964f363c1" />
<img width="865" height="556" alt="image" src="https://github.com/user-attachments/assets/3c65db0c-5833-4c64-95c6-eeda19a69b9c" />
<img width="827" height="560" alt="image" src="https://github.com/user-attachments/assets/1e77811d-5703-4ec3-a8cc-3a04689bdc21" />
<img width="1063" height="472" alt="image" src="https://github.com/user-attachments/assets/ed3b7058-6845-4e7c-836f-e81054c3c1d3" />
<img width="1078" height="543" alt="image" src="https://github.com/user-attachments/assets/bcda3a8d-ee93-4203-936e-f6b89c08889a" />
<img width="923" height="558" alt="image" src="https://github.com/user-attachments/assets/615b14f3-f7d7-4d4a-b488-479fe76b666a" />
<img width="1076" height="605" alt="image" src="https://github.com/user-attachments/assets/9538799c-aafd-491d-b081-062af3787584" />
<img width="537" height="187" alt="image" src="https://github.com/user-attachments/assets/e1852fdf-bc8c-472a-98dd-8c0b9c1c218f" />
<img width="948" height="411" alt="image" src="https://github.com/user-attachments/assets/6b58f1b5-ba3a-4aae-8c4a-8795aeaed0f5" />
<img width="921" height="405" alt="image" src="https://github.com/user-attachments/assets/984c2206-b6b4-4a10-9cc4-eb9aa53306fa" />
<img width="895" height="425" alt="image" src="https://github.com/user-attachments/assets/e34c3db1-d450-43cb-962a-580a9a587e41" />
<img width="1067" height="631" alt="image" src="https://github.com/user-attachments/assets/cf923a46-8b8e-4474-b92e-f48ddfd80a0e" />
<img width="823" height="254" alt="image" src="https://github.com/user-attachments/assets/93e21a1f-ec20-4a06-bf48-c4f6c23102db" />
<img width="1060" height="330" alt="image" src="https://github.com/user-attachments/assets/4fd5b78e-e945-4a66-8365-fffe870ee131" />
<img width="1079" height="794" alt="image" src="https://github.com/user-attachments/assets/bb41c052-9ea4-4ec3-b070-77969f21251e" />
<img width="1047" height="746" alt="image" src="https://github.com/user-attachments/assets/0ccfe1b8-0481-4d63-bcbd-2e0700637b70" />
<img width="1084" height="782" alt="image" src="https://github.com/user-attachments/assets/60704750-6547-412a-bc83-05ec1b80ad9a" />
<img width="1087" height="796" alt="image" src="https://github.com/user-attachments/assets/7e5034b3-8d78-4010-bf72-9e1408cafb9f" />
<img width="1061" height="762" alt="image" src="https://github.com/user-attachments/assets/4664922b-458d-410c-b377-184fa9130ad4" />
<img width="1081" height="777" alt="image" src="https://github.com/user-attachments/assets/c5c5f979-a793-484b-b2ab-f6d2d5d484f4" />

# RESULT:

Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.

       
