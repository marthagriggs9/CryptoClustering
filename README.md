# CryptoClustering

In this challenge, you'll use your knowledge of Python and unsupervised learning to predict if cryptocurrencies are affected by 24-hour or 7-day price changes. 

## Instructions
1. Rename the `Crypto_Clustering_starter_code.ipynb` file as `Crypto_Clustering.ipynb`
2. Load the `crypto_market_data.csv` into a DataFrame
3. Get the summary statistics and plot the data to see what the data looks like before proceeding. 

![image](https://user-images.githubusercontent.com/115905663/236950988-a30b7d0a-5d4b-4219-a17e-65c8cb3c7310.png)

![image](https://user-images.githubusercontent.com/115905663/236951094-eac3b7e3-ae25-4d76-9c83-b28f0f15fcbb.png)

![image](https://user-images.githubusercontent.com/115905663/236951221-4a447970-3c37-453d-a854-ad623397fbee.png)

## Prepare the Data
* Use the `StandardScaler()` module from `scikit-learn` to normalize the data from the CSV file.
* Create a DataFrame with the scaled data and set the 'coin_id' index from the original DataFrame as the index for the new DataFrame. 

![image](https://user-images.githubusercontent.com/115905663/236951348-c21c9710-fddd-4b3a-9a34-ed45f3c84c68.png)

![image](https://user-images.githubusercontent.com/115905663/236951408-7e97fd6d-4bb5-4aef-b83e-04c3bb5a9b15.png)

## Find the Best Value for k Using the Original Scaled DataFrame
Use the elbow method to find the best value for `k` using the following steps:
  * Create a list with the number of k values from 1 to 11.
  * Create an empty list to store the inertia values. 
  * Create a `for` loop to compute the intertia with each possible value of `k`. 
  * Create a dictionary with the data to plot the elbow curve. 
  * Plot a line chart with all the inertia values computed with the different values of `k` to visually identify the optimal value for `k`. 
 
  ![image](https://user-images.githubusercontent.com/115905663/236951522-536a0d7a-73e0-4b2d-b682-b257a207d066.png)

  ![image](https://user-images.githubusercontent.com/115905663/236951606-02c4fb97-4580-4091-aab5-a24b4f4860bb.png)

  ![image](https://user-images.githubusercontent.com/115905663/236951688-e96a8311-d7b2-4416-aef4-53c17b3e38dd.png)

  * Answer the following question in your notebook: 
    * What is the best value for `k`?
  
  ![image](https://user-images.githubusercontent.com/115905663/236951879-08f9881f-0a87-47df-b12f-1b94c0ec8441.png)

## Cluster Cryptocurrencies with K-means Using the Original Scaled Data
Use the following steps to cluster the cryptocurrencies for the best vlaue for `k` on the original scaled data:
  * Initialize the K-means model with the best value for `k`. 
  * Fit the K-means model using the original scaled DataFrame. 
  * Predict the clusters to group the cryptocurrencies using the original scaled DataFrame.
  * Create a copy of the original data and add a new column with the predicted clusters. 
  * Create a scatter plot using hvPlot as follows:
    * Set the x-axis as "price_change_percentage_24h" and the y-axis as "price_change_percentage_7d". 
    * Color the graph points with the labels found using K-means. 
    * Add the "coin_id" column in the `hover_cols` parameter to identify the cryptocurrency represented by each data point. 
  
  ![image](https://user-images.githubusercontent.com/115905663/236951959-e4076ee6-36c6-4919-9d37-6c3ff8a4a315.png)
  
  ![image](https://user-images.githubusercontent.com/115905663/236952059-682513d5-678a-4b29-b2c9-72ce5e699202.png)
  
  ![image](https://user-images.githubusercontent.com/115905663/236952261-60680a5c-bc76-4a61-b27c-bf6486150b9c.png)
  
  ![image](https://user-images.githubusercontent.com/115905663/236952338-28041558-df18-4d43-9157-0c0b6b31d93a.png)

 ## Optimize Clusters with Principal Component Analysis
  * Using the original scaled DataFrame, perform a PCA and reduce the features to three principal components. 
  * Retriece the explained variance to determine how much information can be attributed to each principal component and then answer the following question in your notebook: 
    * What is the total explained variance of the three principal components?
  * Create a new DataFrame with the PCA data and set the "coin_id" index from the orginal DataFrame as the index for the new DataFrame. 
  
  ![image](https://user-images.githubusercontent.com/115905663/236952689-e1d788ba-3cfb-4f67-844c-11640b92c5a9.png)
  
  ![image](https://user-images.githubusercontent.com/115905663/236952780-54c77e86-68c9-412e-8bc2-bd99a3155b28.png)
  
  ![image](https://user-images.githubusercontent.com/115905663/236952843-e55b1e2f-6931-46e9-8813-354fddd008c1.png)
  
## Find the Best Value for k Using the PCA Data
Use the elbow method on the PCA data to find the best value for `k` using the following steps:
  * Create a list with the number of k values from 1 to 11.
  * Create an empty list to store the inertia values. 
  * Create a `for` loop to compute the intertia with each possible value of `k`. 
  * Create a dictionary with the data to plot the elbow curve. 
  * Plot a line chart with all the inertia values computed with the different values of `k` to visually identify the optimal value for `k`. 
  * Answer the following question in your notebook: 
   * What is the best value for `k` when using PCA data?
   * Does it differ from the best k value found using the original data?
 
  ![image](https://user-images.githubusercontent.com/115905663/236952931-29318303-d01b-45cb-8a5b-651e74ed7531.png)
  
  ![image](https://user-images.githubusercontent.com/115905663/236953017-36c248d3-c392-4f21-a488-43182e9575a6.png)
  
  ![image](https://user-images.githubusercontent.com/115905663/236953079-a2c4c06c-0802-47c8-a29f-8ab37cf77403.png)
  
  ![image](https://user-images.githubusercontent.com/115905663/236953156-590bae88-e937-4d3f-bb93-f49c193b0e31.png)

## Cluster Cryptocurrencies with K-means Using the PCA Data
Use the following steps to cluster the cryptocurrencies for the best vlaue for `k` on the PCA data:
 * Initialize the K-means model with the best value for `k`. 
 * Fit the K-means model using the PCA data. 
 * Predict the clusters to group the cryptocurrencies using the PCA data. 
 * Create a copy of the DataFrame with the PCA data and add a new column to store the predicted clusters. 
 * Create a scatter plot using hvPlot as follows:
  * Set the x-axis as "PC1" and the y-axis as "PC2". 
  * Color the graph points with the labeld found using K-means. 
  * Add the "coin_id" column in the `hover_cols` parameter to identify the cryptocurrency represented by each data point. 
 
 
 ![image](https://user-images.githubusercontent.com/115905663/236953296-7330b894-3f16-4bd0-b52f-d6bd9837f618.png)
 
 ![image](https://user-images.githubusercontent.com/115905663/236953368-3597bd9c-160d-45c1-bb98-f9f5758994ad.png)
 
 ![image](https://user-images.githubusercontent.com/115905663/236953441-8fbe4f8f-7248-48b6-8d43-b3a49e1ae38d.png)
 
 



 
## Visualize and Compare the Results
 * Create a composite plot by using hvPlot and the plus sign (`+`) operator to compare the elbow curve that you created from the original data with the one that your created from the PCA data. 
 * Create a composite plot by using hvPlot and the plus sign (`+`) operator to compare the cryptocurrency clusters that resulted from using the original data with those that resulted from the PCA data. 
 * Answer the following question:
   * What is the impact of using fewer features to cluster the data using K-Means?
 
 ![image](https://user-images.githubusercontent.com/115905663/236953542-27efb694-1f5a-4b4c-a61c-d44ecbdd5be1.png)
 
 ![image](https://user-images.githubusercontent.com/115905663/236953644-1afa83da-19bd-4c46-9600-c9658a2eb9ee.png)
 
 ![image](https://user-images.githubusercontent.com/115905663/236953753-d3003a0f-1cd7-47a5-a163-07761118200f.png)
 
 ![image](https://user-images.githubusercontent.com/115905663/236953839-f8eb4442-4906-41f7-9453-d16387c20d69.png)



 
