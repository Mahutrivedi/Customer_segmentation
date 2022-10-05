Customer segmentation: Clustering

![segments](https://user-images.githubusercontent.com/86886343/194060118-5a92ff5c-f79c-4b3f-8287-642bdc628bf1.jpg)




Customer personality analysis is an in-depth understanding of company’s customers.  This analysis helps the company to understand their customer base better and also, they can offer more relevant products to each customer based on the cluster (Customer segment) they fall in.  Customer personality analysis helps the company to make a better product.  This is a win-win situation for both customer and company because, customers get better recommendations and experience this in turn increases the revenue for the company.

This is an unsupervised machine learning project where we have to identify customer segments using clustering technique.  We have to find out hidden insights of customer’s personal traits based on various clusters.


The dataset is from a marketing campaign of a company.  
Dataset source:  https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis

There are 4 kinds of details provided:

1.	Customer’s personal details: Birth year, Education, Marital status, Income, Kidhome, teenhome, The date they became customer for the company, Recency, Complain by customer
2.	Product information: Amount spent by customer on Wine, Fruit, Meat, Fish, Sweet, Gold since last 2 years
3.	Promotions details: Number of deals purchased by customer, Promotion acceptance rate for 1st to 5th promotion
4.	Place details: Count of web based purchases, catalog based purchases, purchase made in store, web visits per month

Customer’s personal details and product details are used in the clustering.

Steps in the project and its details are given below:

Importing the required libraries

o	In this stage of project various libraries required for the project are imported, such as PANDAS, NUMPY, MATPLOTLIB, SEABORN, SCIKITLEARN.

Loading the data

o	This is a very simple stage of project, in which theS csv file is read.
o	Although it’s simple file to read, after loading it in notebook it was found that the file is a tab separated one and not a comma separated. 
o	Just by specifying sep = “\t” the file was correctly loaded into the Jupyter notebook.

Data cleaning and feature engineering

o	This was a very crucial stage of the project as it involved creation of new features from existing features and removing redundant features.
o	Converted birth year to age column
o	Instead of multiple degree converted them all into either undergraduate, graduate or postgraduate
o	Converted Married, Together, Divorced, Widow, Single into either Partner or Alone
o	Using teenhome and kidhome created a new column as children count
o	Created a column family size using living_with column and children count
o	Date time conversion of dt_customer column
o	All the spending on wine, fruit, gold etc. are summed up and put into new column total_spending
o	A new column is created for customer duration by subtracting each date from newest date.
o	Removed outliers from Age (few people were having age > 120 years) and income (few people were having income > 600000)




Data preprocessing

o	Label encoding for Education column and living_with column
o	Removing redundant columns
o	Scaling the data before clustering (Standard scaler is used)

EDA on data

o	In this part of the project two kinds of plots are used to identify relation of each feature with total_spending target:
1.	All Numeric columns are plotted against total_spending on scatter plot
2.	All categorical columns are plotted against total_spending on bar plot

Dimensionality reduction 

o	Even after removing redundant columns, still there are many columns.
o	To cluster the data and visualization purpose PCA is used. 
o	3 PCA components are kept for dimensionality reduction

Clustering of data

o	Before clustering, number of clusters needs to be identified so for that elbow plot and silhouette score visualizer is used.
o	4 no. of clusters are selected.
o	K-means clustering is used for clustering the data.

![segments_3d](https://user-images.githubusercontent.com/86886343/194063207-5daab3f8-1cd5-49a2-b171-31e8397cb9d9.png)


Customer personality analysis based on clusters found

![segments_4](https://user-images.githubusercontent.com/86886343/194063234-dff15a7d-06a7-4f9a-b8f5-daa124bbe0df.png)


o	After clustering is done 4 kinds of clusters are found

1.	High-income high spending group
2.	Medium-income low spending group
3.	Low-income low spending group
4.	Medium-income medium-high spending group


Conclusion

o	Low-income low spending group:
Comparatively younger
0 or 1 child
Majority living with partner
Majority is parent
Family size 1 to 3

o	High income high spending group:
No children 
All age range
More people living with partner than alone
Definitely not a parent
Family size 1 to 2

o	Medium income medium-high spending group:
Majority have 1 teen at home
Comparatively high aged
1 - 2 children
Definitely a parent
Family size 2 to 4

o	Medium income low spending group
Comparatively high aged
Majority living with partner
1 to 3 children
 Family size 3 to 5




