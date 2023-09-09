# Ex02-Outlier
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

# ALGORITHM:


### STEP 1:

Read the given Data.
### STEP 2:

Get the information about the data.
### STEP 3:

Detect the Outliers using IQR method and Z score.
### STEP 4:

Remove the outliers:
### STEP 5:

Plot the datas using box plot.


## PROGRAM:

```
DEVELOPED BY: karthick P
REGISTER NUMBER: 212222100021

import pandas as pd
df=pd.read_csv("/content/bhp.csv")
df.head()
df.describe()
df.info()
df.shape

import seaborn as sns
sns.boxplot(x="price_per_sqft",data=df)

### removing ouliers of bhp.csv file using IQR
Q1=df['price_per_sqft'].quantile(0.25)
Q3=df['price_per_sqft'].quantile(0.75)
IQR=Q3-Q1
lower=Q1-1.5*IQR
upper=Q3+1.5*IQR
newdata=df[(df['price_per_sqft']>=lower) & (df['price_per_sqft']<=upper)] 
print(newdata)   #new dataframe.
outliers=df[(df['price_per_sqft']<lower) | (df['price_per_sqft']>upper)]
print(outliers)
newdata.shape
sns.boxplot(x="price_per_sqft",data=newdata)


### removing ouliers of bhp.csv file using Zscore of 3

from scipy import stats
import numpy as np
z_score=np.abs(stats.zscore(df['price_per_sqft']))
newdata2=df[(z_score<3)]
print(newdata2)
outlier2=df[(z_score>=3)]
print(outlier2)
newdata2.shape
sns.boxplot(x="price_per_sqft",data=newdata2)

import pandas as pd
dataset=pd.read_csv("/content/height_weight.csv")
dataset.shape
dataset.describe()
dataset.info()
import seaborn as sns
sns.boxplot(x='height',data=dataset)

### Using IQR detect height outliers and print them( height_weight.csv)

Q1_height=dataset['height'].quantile(0.25)
Q3_height=dataset['height'].quantile(0.75)
IQR_HEIGHT=Q3_height-Q1_height
l_height=Q1_height-1.5*IQR_HEIGHT
u_height=Q3_height+1.5*IQR_HEIGHT
outliers_height=dataset[(dataset['height']<l_height) | (dataset['height']>u_height)]
print(outliers_height)
newdata_height=dataset[(dataset['height']>=l_height) & (dataset['height']<=u_height)]
print(newdata_height)
sns.boxplot(x='height',data=newdata_height)


### Using IQR, detect weight outliers and print them( height_weight.csv)

Q1_weight=dataset['weight'].quantile(0.25)
Q3_weight=dataset['weight'].quantile(0.75)
IQR_WEIGHT=Q3_weight-Q1_weight
l_weight=Q1_weight-1.5*IQR_WEIGHT
u_weight=Q3_weight+1.5*IQR_WEIGHT
outliers_weight=dataset[(dataset['weight']<l_weight) | (dataset['weight']>u_weight)]
print(outliers_weight)
newdata_weight=dataset[(dataset['weight']>=l_weight) & (dataset['weight']<=u_weight)]
print(newdata_weight)
sns.boxplot(x='weight',data=newdata_weight)
```

## OUTPUT:

### bhp.csv:


### df.head():

### df.describe():


### df.info():


### df.shape


### BOXPLOT BEFORE REMOVING OUTLIERS


### NEWDATA USING IQR


### OUTLIERS


### newdata.shape


### BOXPLOT AFTER REMOVING OUTLIERS USING IQR

### NEWDATA USING Zscore

### OUTLIERS

### newdata2.shape

### BOXPLOT AFTER REMOVING OUTLIERS USING Zscore

### height_weight.csv


### dataset.describe()


### dataset.info()


### BOXPLOT BEFORE REMOVING OUTLIERS


### HEIGHT OUTLIERS

### DATASET AFTER REMOVING HEIGHT OUTLIERS


### BOXPLOT AFTER REMOVING HEIGHT OUTLIERS


### WEIGHT OUTLIERS

### DATASET AFTER REMOVING WEIGHT OUTLIERS

### BOXPLOT AFTER REMOVING WEIGHT OUTLIERS

# RESULT:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
