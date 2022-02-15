# Customer-Segmentation

# Abstract:

Customer Segmentation is the process of dividing customers into groups based on common characteristics so companies can market to each group effectively and appropriately. Customers are segmented according to their similarities in behaviour and habits. A primary goal for any company and business is to understand their targeted customers. How their consumers operate and use their services. Every consumer may use a company’s services differently. The problem we’re trying to solve is to define this delivery company’s consumers. To define certain behaviours and methods these consumers use the companies services for.

# Problem statement:
We will be using Online retail dataset to explore customer segmentation through the interesting task of unsupervised learning method. These customer segmentation can be used to make interesting and useful decisions as far as user interest is concerned.

The Online Retail a transnational data set which contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail. The company mainly sells unique all-occasion gifts. Many customers of the company are wholesalers.

In this project, our task is to identify major customer segments on a transactional data of a online retail store. 

# Packages Required:

1. Numpy
2. Pandas
3. Matplotlib
4. Seaborn
5. Datetime
6. Sklearn Packages:
7. Cluster
8. Kmeans
9. PCA
10. Gaussian Mixture
11. Silhouette samples 
12. Silhouette score

# Approaches:

--> After loading and reading the dataset in pandas Data Frame, we know that our dataset has 541909 rows
and 8 columns.

--> We first imported all the necessary libraries in our notebook which required for the analysis.

--> During data exploration, we got to know the following things:

1. Number of transactions: 25900
2. Number of products bought: 4070
3. Number of customers: 4372
4. Number of countries: 38

--> **Null values treatment:**

We have missing values in the customeID and description columns
Since 25% of the customer IDs are missing, we created a new column that has a 1 when customer ID is
null and 0 when it is not.

Since we won’t be doing analysis on the description of the orders, we can leave the null values as it is.

Since the customer ID's are missing, we assumed these orders were not made by the customers already
in the data set because those customers already have ID's. We also don't want to assign these orders to
those customers because this would alter the insights we draw from the data. Instead of dropping the
null CustomerID values, we assigned those rows a unique customer ID per order. This will act as a new
customer for each unique order.

Using the values in the InvoiceNo column would be the most straightforward approach. We created a
new customer ID column called NewID with the invoice numbers filling in for the missing values. Then we
add the number of unique orders in df1 and to number of unique values in CustomerID and see if it equals the number of unique values in NewID. This will check if any of the new values match the existing
values in the column and make sure we didn't add more orders to an existing customer.

--> **Exploratory Data analysis:**

1. There are negative values in the Quantity and UnitPrice columns. We assumed these are orders that were
cancelled and items that were returned.

2. Since nothing came back when we filtered the cancelled orders by Quantity > 0, this confirms that the
negative values mean the order was cancelled.

3. 9288 or about 36% of the orders were cancelled. Looking deeper into why these orders were cancelled
may prevent future cancellations.

4. The average number of orders per customer is 3.

5. The average number of items per order is 20.5 and the average number of items per customer is 50.

6 United Kingdom has significantly more customers than the other countries in our data set, so their
total cost should look similar.
7. The UK not only has the most sales revenue, but also the most customers. Since the majority of this data
set contains orders from the UK, we can explore the UK market further by finding out what products the
customers buy together and any other buying behaviors to improve our sales and targeting strategy.

Percentage of customers from UK: 93.88%

Number of transactions: 23494

Number of products bought: 4065

Number of customers: 7587

# Models:

We started with RFM Analysis and then compliment our findings with predictive analysis using K-Means
Clustering Algorithms.
The simplest way to create customer segments from an RFM model is by using Quartiles. We will assign a
score from 1 to 4 to each category (Recency, Frequency, and Monetary) with 4 being the highest/best
value. The final RFM score is calculated by combining the individual RFM values.
A score of 4 represents the customer being in the 75th percentile for that category.
After doing the RFM Analysis, we got following insights:

1. Best customers: 370

2. Loyal customers: 791

3. Big spenders: 980

4. Almost lost: 65

5. Lost customers: 11

6. Lost cheap customers: 377

**Correlation analysis:**
Looking at this heatmap, we see that there is a negative correlation between Recency : Frequency and
Recency : Monetary, but there is a positive correlation between Frequency : Monetary

Then we used **K-Means clustering** implementation and we got the best Silhouette score obtained is when
there are 2 clusters.

# Conclusion:

We were able to build a model that can classify new customers into "low value" and "high value" groups. Generally, if a customer only transacted with us a few times, they needed to be at least in the top 50th percentile in monetary spending to be considered a "high value customer". The clusters assignments are muddled, which may be due to outliers that weren't removed.




