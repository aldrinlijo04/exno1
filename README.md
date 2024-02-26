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
## PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
data = pd.get_dummies(data)
data.isnull().sum()
columns_with_null = data.columns[data.isnull().any()]
```

### VISUALIZATION:
```
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
### NULL IMPUTATION
```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
### IQR
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
ir.describe()

sns.boxplot(x='sepal_width',data=ir)
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']

delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
sns.boxplot(x='sepal_width',data=delid)
```
### Z SCORE
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset

df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)

iqr = q3-q1
iqr
low = q1 - 1.5*iqr
low
high = q3 + 1.5*iqr
high
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
z = np.abs(stats.zscore(df['height']))
z
```
# Result

![image](https://github.com/aldrinlijo04/exno1/assets/118544279/88b65592-25fc-4591-8a05-a21b213fa238)


![image](https://github.com/aldrinlijo04/exno1/assets/118544279/a4fa7709-cab0-48c7-95a1-dff645113e57)


 ![image](https://github.com/aldrinlijo04/exno1/assets/118544279/2542129d-4099-4b98-8b5e-fd12fedc95d8)


![image](https://github.com/aldrinlijo04/exno1/assets/118544279/fd6fe5f9-d90a-4063-bd4b-978cfb6e3b09)


