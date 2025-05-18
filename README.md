# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import the necessary packages using import statement.

2.Read the given csv file using read_csv() method and print the number of contents to be displayed using df.head().

3.Import KMeans and use for loop to cluster the data.

4.Predict the cluster and plot data graphs.

5.Print the outputs and end the program
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Navinkumar V
RegisterNumber:  212223230141
*/
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv("Mall_Customers.csv")
data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i, init = "k-means++")
  kmeans.fit(data.iloc[:, 3:])
  wcss.append(kmeans.inertia_)
  
plt.plot(range(1, 11), wcss)
plt.xlabel("No. of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:, 3:])

y_pred = km.predict(data.iloc[:, 3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"] == 0]
df1 = data[data["cluster"] == 1]
df2 = data[data["cluster"] == 2]
df3 = data[data["cluster"] == 3]
df4 = data[data["cluster"] == 4]
plt.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], c = "red", label = "cluster0")
plt.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], c = "black", label = "cluster1")
plt.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], c = "blue", label = "cluster2")
plt.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], c = "green", label = "cluster3")
plt.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], c = "magenta", label = "cluster4")
plt.legend()
plt.title("Customer Segments")
```
## Output:
## Dataset:
![image](https://github.com/user-attachments/assets/f1f3f3a4-244e-4d4e-877b-8c26cb476f0a)
## Info:
![image](https://github.com/user-attachments/assets/987b4822-4fa3-4b10-ac86-52cc9c903f17)
## Null values:
![image](https://github.com/user-attachments/assets/a73fd51b-e90d-45eb-9e7b-7af138b94091)
## Elbow Plot:
![image](https://github.com/user-attachments/assets/6e9a78b3-b100-4424-91e6-f5353c1e0d1d)
## Kmeans :
![image](https://github.com/user-attachments/assets/2c0b4e33-c345-48d8-bbd3-8f46dafb48fb)
## Predict :
![image](https://github.com/user-attachments/assets/b882aa7f-e8d7-4323-8765-dc2a9acaa4d7)
## Cluster Plot:
![image](https://github.com/user-attachments/assets/0972a921-afd2-43e3-9849-91af932f7697)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
