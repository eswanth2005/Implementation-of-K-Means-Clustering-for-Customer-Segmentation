# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

   1. Load and preprocess data: Import data, inspect it, and handle missing values if any.
   2. Determine optimal clusters: Use the Elbow Method to identify the number of clusters by plotting WCSS against cluster numbers.
   3. Fit the K-Means model: Apply K-Means with the chosen number of clusters to the selected features. Assign cluster labels to each data point.
   4. Plot data points in a scatter plot, color-coded by cluster assignments for interpretation.

## Program:
```
Developed by: ESWANTH KUMAR K
Register No.: 212223040046
```

```
import pandas as pd
df=pd.read_csv("/content/Mall_Customers.csv")
df.head()
df.info()
df.isnull().sum()

from sklearn.cluster import KMeans
wcss = []
for i in range(1,11):
    kmeans = KMeans(n_clusters = i,init = "k-means++",n_init=10)
    kmeans.fit(df.iloc[:,3:])
    wcss.append(kmeans.inertia_)

import matplotlib.pyplot as plt
plt.plot(range(1,11),wcss)
plt.xlabel("NO of clusters")
plt.ylabel("wccc")
plt.title("Elbow method")

km=KMeans(n_clusters=5,n_init=10)
km.fit(df.iloc[:,3:])
y_pred=km.predict(df.iloc[:,3:])
y_pred

df["cluster"]=y_pred
dt0=df[df["cluster"]==0]
dt1=df[df["cluster"]==1]
dt2=df[df["cluster"]==2]
dt3=df[df["cluster"]==3]
dt4=df[df["cluster"]==4]

plt.scatter(dt0["Annual Income (k$)"],dt0["Spending Score (1-100)"],c="red",label="cluster1")
plt.scatter(dt1["Annual Income (k$)"],dt1["Spending Score (1-100)"],c="black",label="cluster2")
plt.scatter(dt2["Annual Income (k$)"],dt2["Spending Score (1-100)"],c="blue",label="cluster3")
plt.scatter(dt3["Annual Income (k$)"],dt3["Spending Score (1-100)"],c="green",label="cluster4")
plt.scatter(dt4["Annual Income (k$)"],dt4["Spending Score (1-100)"],c="magenta",label="cluster5")
plt.legend()
plt.title("Customer Segments")

```

## Output:
![image](https://github.com/user-attachments/assets/01865ca9-ccb7-4104-80b0-ddeb549810ac)
![image-1](https://github.com/user-attachments/assets/d88214e1-1192-4098-87c5-d4bec452a4d7)
![image-2](https://github.com/user-attachments/assets/fad39f50-ec54-43e6-8a4b-9633860800eb)
![image-3](https://github.com/user-attachments/assets/731a7684-0536-40e2-b53b-0439542c7b28)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
