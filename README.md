# PCA (Principal component analysis)

The main aim of using PCA is to go in deep of the data and know what features exactly are effecting the data 

PCA is a systematic way of transforming input features into principal component with max variance and less information loss

![image](https://user-images.githubusercontent.com/82372055/121944693-8ec15c00-cd70-11eb-89e1-36d761e0f891.png)

## Lets understand PCA with a breast cancer dataset step by step

Step 1 : Importing important libraries
```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import seaborn as sns
```
Step 2 : Importing breat-cancer dataset from sklearn 
```python 
from sklearn.datasets import load_breast_cancer
cancer = load_breast_cancer()
```
Step 3 :Changing into dataset
```python
df=pd.DataFrame(cancer['data'],columns=cancer['feature_names'])
```
### We are not from medical background so we use PCA to know about the date deeply that which features are effecting the most 

the data should be Standardised so that intensity of the data will be equal   

Step 4 : Import StandardScaler from sklearn.preprocessing and make an intance and fit and transform the dataset 
```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
x= scalar.fit_transform(df) 
```

step 5 : Again change to dataset 
```python
df_scaled=pd.DataFrame(scaled_data,columns=cancer['feature_names'])
```
## Now lets use PCA 

Step 6 : Import PCA from sklearn.decomposition and make a instance of it 
```python 
from sklearn.decomposition import PCA
pca = PCA(n_components=2)
```

Step 7 : Now fitting and transforming the data

```python
pca.fit(scaled_data)
x_pca = pca.transform(scaled_data)
```

# Now lets visualize 

```python 
plt.scatter(x_pca[:,0],x_pca[:,1] , c=cancer['target'])

plt.xlabel("1st principal component")
plt.ylabel("2nd principal component")
```

![image](https://user-images.githubusercontent.com/82372055/121944804-b284a200-cd70-11eb-870b-f7cab08ffc50.png)


x_pca[:,0],x_pca[:,1], c=cancer['target']

means we want to grab everything in col1 and grab everything in col2 
and hue it on the basis of target

### Visualizing using the heat map to know the correlations

```python
plt.figure(figsize=(5,6))
sns.heatmap(df_compo)
```
![image](https://user-images.githubusercontent.com/82372055/121944866-c6300880-cd70-11eb-993c-fba969dfddef.png)

Heat map is telling about



Which column is having more effect and which column has less effect 
darker the bar more the correlation


# NEXT I HAVE APPLIED LOGISTIC REGRESSION TO THE DATA WHICH IS DONE PCA YOU CAN FIND IT IN CODE 

The scores were good and the misclassifications are very less when observed using a confusion matrix

![image](https://user-images.githubusercontent.com/82372055/121945099-07281d00-cd71-11eb-80d8-f8f1390b5723.png)
