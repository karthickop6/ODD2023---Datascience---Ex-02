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

![1](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/245b914e-7916-4b9a-9247-0eac127b87fe)

### df.describe():

![2](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/78d34a75-f890-437e-8b2f-c9e8bf45a146)


### df.info():

![3](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/da200df6-4b2a-422c-a85b-ca45e28ed8c2)


### df.shape
![4](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/cc80cd5e-b57a-40fd-9dae-63c621306d73)


### BOXPLOT BEFORE REMOVING OUTLIERS
![5](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/1c5889e8-bf17-49d1-b409-e5c97d6e008b)


### NEWDATA USING IQR

![6](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/365deb2e-f372-4450-83a9-252fbceef671)

### OUTLIERS

![7](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/1f745df4-3b38-4fe9-ae7e-09b31e581c05)

### newdata.shape

![8](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/a579e8f5-5f44-43e8-99e5-80897909213f)

### BOXPLOT AFTER REMOVING OUTLIERS USING IQR
![9](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/71f7624f-cf8f-4118-9947-54f1ddcca192)

### NEWDATA USING Zscore
![10](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/5117b6d2-2dc1-44fb-a1d8-a619c98c0240)

### OUTLIERS
![11](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/67ab584d-08c8-4eed-a42c-27aec0958dd8)

### newdata2.shape
![12](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/f026f8c3-eb6c-405e-8cf3-b9648157af07)

### BOXPLOT AFTER REMOVING OUTLIERS USING Zscore
![13](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/cc312d3d-b779-47be-977c-1bb75e54a7df)

### height_weight.csv
![14](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/ced41e14-2c9c-467d-9e47-95095cdafb2a)


### dataset.describe()
![15](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/86755f64-b57d-46f8-b211-17a6d8004e5a)


### dataset.info()

![16](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/5222f8c1-2bb0-422a-b8af-035c45d3de98)

### BOXPLOT BEFORE REMOVING OUTLIERS

![17](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/7aff9165-f34a-4b75-8e9d-4bf9342de4d6)

### HEIGHT OUTLIER
![18](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/5fa2e309-941c-4a65-999f-bf40dad3754f)
S

### DATASET AFTER REMOVING HEIGHT OUTLIERS

![19](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/8151b1c7-9d48-4291-b72e-e252fe3907ba)

### BOXPLOT AFTER REMOVING HEIGHT OUTLIERS
![20](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/d66d11a0-e503-4016-92f4-3e5bc582a9bb)


### WEIGHT OUTLIERS
![21](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/bce91c05-19ab-43d0-968f-a661196cdc3a)

### DATASET AFTER REMOVING WEIGHT OUTLIERS
![22](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/53cfed54-afa2-4f7d-8f88-31a4221b59e6)

### BOXPLOT AFTER REMOVING WEIGHT OUTLIERS
![23](https://github.com/karthickop6/ODD2023---Datascience---Ex-02/assets/72570119/d079893c-205d-4c14-b225-fe201e9b2d80)

# RESULT:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
