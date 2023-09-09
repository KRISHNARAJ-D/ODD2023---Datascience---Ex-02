# Ex02-Outlier
## AIM:
You are given bhp.csv which contains property prices in the city of banglore, India. You need to examine price_per_sqft column and do following,

(1) Remove outliers using IQR

(2) After removing outliers in step 1, you get a new dataframe.

(3) use zscore of 3 to remove outliers. This is quite similar to IQR and you will get exact same result

(4) for the data set height_weight.csv find the following

(i) Using IQR detect weight outliers and print them

(ii) Using IQR, detect height outliers and print them

## ALGORITHM:
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
```python
DEVELOPED BY: KRISHNARAJ D
REGISTER NUMBER: 212222230070

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
![265179270-4e314b3c-05b0-4907-aaed-4924bf1e808f](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/3b834c84-e735-4b4b-9954-c1da1eb355cf)


### df.describe():
![265179300-953b4538-7d46-42e5-b3d9-6b2ea3b07c89](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/43de1bf1-a9d6-4b1b-b301-50df5add564f)


### df.info():
![265179357-595aefb2-eb19-4840-b1e1-338da4710359](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/dd4a4057-e403-486e-91bb-69558b45a26c)


### df.shape:
![265179362-926e4cc7-6fb6-4c10-8be0-84887c4c2b03](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/a4025d74-08f3-4c05-bf59-5b623d5270de)


### BOXPLOT BEFORE REMOVING OUTLIERS:
![265179375-d47f2495-7344-44a0-88ab-306ed1a482ac](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/0466d9e9-b5c6-4350-844e-0066004fe5ea)

### NEWDATA USING IQR:
![265179389-3d3592e1-250f-40f0-b8e2-d7dddb532250](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/9b9fb486-d915-4cbb-8122-120d23c10013)


### OUTLIERS:
![265179405-7880f687-7ae1-4c4c-af5b-a3b2207a35da](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/3146182d-d8dc-4afe-8942-4a00b53f686d)


### newdata.shape: 

![265179441-842c7703-1b40-49e5-9a72-cfb2f54d9ba0](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/994eb23b-320a-477c-b826-9e4d5c65cf8b)

### BOXPLOT AFTER REMOVING OUTLIERS USING IQR:
![265179451-06c8968e-3b65-4fbb-b3bb-ccd6987554fe](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/68f78787-3de5-4f18-9ee0-9e1b926d5eeb)


### NEWDATA USING Zscore:
![265179489-e94b8539-1376-4b28-96ef-60af6f64eb2c](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/c787bb98-7142-498f-8888-3b4e07c47081)


### OUTLIERS:
![265179502-7bbc90bb-e0ab-4124-80ba-0070a5e05f78](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/eafc1854-d6d9-433e-b1bc-0698d1743232)


### newdata2.shape:
![265179513-81f3d73a-b1b6-4876-8c64-65783c3b11eb](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/ffcd8287-181b-4d50-b3ea-39e8dc6a0c71)


### BOXPLOT AFTER REMOVING OUTLIERS USING Zscore:
![265179542-2d272e58-3229-47c5-bd38-f942dedae6b2](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/ec6ea2a1-cc9b-4f34-8fa6-135b30f6f678)


### height_weight.csv:
![265179617-7116c094-6648-4057-b2fe-d57124fb22b6](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/e2f6c784-1e72-494b-bbec-b9a8d68d0a7d)

### dataset.describe():
![265179797-43c98585-7aa3-4f4d-abc8-77eec662ff73](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/818a6e56-9726-4780-bdec-608d115c0acb)


### BOXPLOT BEFORE REMOVING OUTLIERS:
![265179816-3fe33e2d-bc7d-42c7-911f-64dce7e775ba](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/613249b5-c1ef-4457-aa15-0cfb57b5285c)


### HEIGHT OUTLIERS:

![265179831-e70ae5e9-ab96-4c5f-ad88-8a5f1d6be6b8](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/0c264788-9e36-49d5-a5bc-2e921fed9901)

### DATASET AFTER REMOVING HEIGHT OUTLIERS:

![265179861-08c5f0e0-b615-433c-85c1-dbba24754298](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/bcd83877-1ff6-4d56-9a7d-d4b2e41959d4)

### BOXPLOT AFTER REMOVING HEIGHT OUTLIER:
![265179886-591245c4-6e4b-414f-ab41-7a880b80066a](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/f88d94e3-f570-402f-840b-391381cbd840)


### WEIGHT OUTLIERS:
![265179898-980890b1-3296-4230-9a0a-fc4d456760c7](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/97a99fbd-92f6-43a7-be07-c3abadb37f30)


### DATASET AFTER REMOVING WEIGHT OUTLIERS:
![265179910-0e0fd6a5-9a19-4a48-b514-6a2842dd57bd](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/7fb46f9d-06af-4fd1-8e54-026478dc4f94)


### BOXPLOT AFTER REMOVING WEIGHT OUTLIERS:
![265179931-61d14c1a-0c8f-4761-b7d4-37a0eed8eda6](https://github.com/KRISHNARAJ-D/ODD2023---Datascience---Ex-02/assets/119559695/cb4f6081-c105-4f8b-9126-c9139901f42d)


## RESULT:
The given datasets are read and outliers are detected and are removed using IQR and z-score methods.
