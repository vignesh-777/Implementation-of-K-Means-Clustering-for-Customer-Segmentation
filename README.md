# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Start the program
2. Import the necessary python libraries
3. Read the dataset of Mall_Customers csv file
4. From sklearn libraary select the cluster and import KMeans Clustering
5. Find the sum of squared distance between each points and the centroid in a cluster using Elbow Method
6. Plot the graph x and y as Number of Clusters and wcss respectively
7. Using the matplotlib library draw the scatter plot for the given number of clusters (ie. here n_clusters = 5)
8. Stop the program

## Program:
```py
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Vignesh R
RegisterNumber: 212223240177
*/

import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
    kmeans=KMeans(n_clusters=i,init="k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)
plt.plot(range(1,11),wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")
km=KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="red",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="red",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="red",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="red",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
![WhatsApp Image 2024-10-18 at 14 31 14_e2ba9c58](https://github.com/user-attachments/assets/3e61d38e-c9d2-414b-bf68-3fbe61e825d1)

![WhatsApp Image 2024-10-18 at 14 31 14_f9ac370a](https://github.com/user-attachments/assets/4cdb6de1-7216-4c8d-b674-3ac7a3f8c81e)

![WhatsApp Image 2024-10-18 at 14 31 14_1c2b388d](https://github.com/user-attachments/assets/885bb26b-0ceb-4180-8b4d-31d37750c60a)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
