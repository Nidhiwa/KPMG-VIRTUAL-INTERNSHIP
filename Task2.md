**Task 2**


Here, our focus will be on the second task, which involves data insights aimed at identifying high-value customers. To save time, I have already analyzed the data and made preparations beforehand.

The task requirements involve three main deliverables: **data exploration, model development, and model evaluation**. 
We will be working with three datasets: customer demographic, customer address, and transactions data. 
These datasets serve as the foundation for our analysis.

For a more structured approach, we will be following the KDD (Knowledge Discovery in Databases) process, which consists of seven key steps: data gathering, data cleaning, data transformation, data modeling, data evaluation, model deployment, and knowledge interpretation.

To begin, we have created two new columns in the transactions dataset: "Age" and "Profit." Age is derived from the date of birth(in CustomerDemographics Table), while Profit is calculated as the difference between list price and standard cost(in Transactions table). 

Age is calculated using formula below:

**=DATEDIF(F12,TODAY(),"Y")**


<img width="1232" alt="Screenshot 2023-07-28 at 11 20 07 AM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/c9b76ace-2669-417a-916f-888aa721c4ba">

Profit is calculated using formula below:

**= List_price-Standard_cost**

<img width="1259" alt="Screenshot 2023-07-28 at 11 21 23 AM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/6b4fcc9d-5ec9-40cd-85c5-a5abf4f3741b">

We have also merged the three datasets using the customer ID as a primary key.

For this we have used Vlookup function.

<img width="1372" alt="Screenshot 2023-07-28 at 11 29 20 AM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/ed788f52-1472-4a68-8409-0ee971ad2382">

Next, we perform an RFM (Recency, Frequency, Monetary) analysis to segment customers based on their behavior and value to the business. This analysis helps us target high-value customers more effectively.

RFM is a marketing technique that combines recency, frequency, and monetary aspects to determine the value of customers to a business. By evaluating these factors, it helps differentiate between more and less valuable customers. In this context, we will employ RFM analysis for this dataset. To initiate the analysis, we need to create a new column for recency, representing the number of days since the customer's last purchase. To do this, we will determine the most recent transaction date as a reference point and calculate the difference between the reference date and each transaction date to obtain the recency value. For this analysis, we will use December 30, 2017, as the reference date.

For this, What we intend to do is sort all the values of transaction date in descending order, which will reveal the most recent transaction date(December 30, 2017).

What we will do is subtract the comparison date from the transaction date, which will indicate how recently, in terms of the number of days, the customer purchased that product.


<img width="1245" alt="Screenshot 2023-07-28 at 11 52 41 AM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/46aa8dad-15ed-41a4-a541-4b7adac92d62">


Once the recency column is ready, we can proceed to create a pivot table. The pivot table will utilize customer ID as rows, count of product ID for frequency,the minimum value of recency, and the sum of profits for monetary value AS VALUES. With the pivot table set up, we can calculate the scores for recency (R), frequency (F), and monetary (M). 


Firstly, we calculate min,lower quartile, median, upper quartile and maximum for recency (R), frequency (F), and monetary (M) using the formulas as below.

MIN= =MIN(C:C)

LOWER QUATRILE = =QUARTILE.EXC(C:C,1)

MEDIAN= =MEDIAN(C:C)

UPPER QUATRILE= =QUARTILE.EXC(C:C,3)

MAX= =MAX(C:C)

<img width="1420" alt="Screenshot 2023-07-30 at 11 04 26 AM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/58579111-da02-4046-924f-159eeef7150a">

To assign scores based on certain conditions, we utilize the following approach:

For the R score:

If the value in cell C4 is greater than or equal to 85, we give it a score of 1. (VERY RECENTLY)

If the value is less than 85 and greater than or equal to 44, we assign a score of 2.

If the value is less than 44 and greater than 17, it gets a score of 3.

If the value is less than or equal to 17 and greater than 0, we assign a score of 4.(NOT RECENTLY)

**R-SCORE**
**=ifs(C4>=85,1,AND(C4<=85,C4>=44),2,AND(C4<=44,C4>=17),3,AND(C4<=17,C4>=0),4)**

For the F score and M score, the same approach is employed to categorize the products into different customer segments based on their frequency and monetary value.

**F-SCORE**
**=ifs(B4>=7,1,AND(B4<=7,B4>=6),2,AND(B4<=6,B4>=4),3,AND(B4<=4,B4>=1),4)**

**M-SCORE**
**=ifs(D4>=4274,1,AND(D4<=4274,D4>=2918),2,AND(D4<=2918,D4>=1905),3,AND(D4<=1905,D4>=15),4)**

These scores will be used to derive an RFM value by assigning weights and adding them together.

Essentially, the RFM value is the result of multiplying our R score by 100, then adding 10 times our F score to it, and finally adding the M score to the previous sum.

<img width="810" alt="Screenshot 2023-07-30 at 12 05 47 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/355c3fb9-dfd9-44bc-9e79-e29226a41d3b">


<img width="202" alt="Screenshot 2023-07-30 at 12 08 02 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/0c786cb2-ba21-4754-9f3a-c80643105fbd">


To classify different customers into distinct segments based on their RFM values, we can utilize the "Customer Profiles" column. Using the same "IF" statements, we can categorize customers into different segments. Each segment represents a specific combination of recency, frequency, and monetary value scores.

By applying appropriate conditions to the "Customer Profiles" column, we can group customers into segments such as "High-Value Customers," "Potential Loyal Customers," "Churned Customers," and so on. This segmentation will help us gain valuable insights into customer behavior and tailor marketing strategies accordingly.

=IFS(H11>=344,"High-Value Customers",AND(H11<=344,H11>=244),"Potential Loyal Customers",AND(H11<=244,H11>=144),"Churned Customer",AND(H11<=144,H11>=111),"Low-Value Customers")


<img width="1004" alt="Screenshot 2023-07-30 at 12 20 47 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/1f26e826-f93b-4ebd-a9be-44117b991508">


Once we have the "Customer Profiles" and "RFM Values" calculated for each customer, we can create a pivot table to visualize the data effectively. By summing up all the RFM values, we can get an overall view of customer segments and their corresponding total RFM scores. With this information, we can then proceed to create a graphical representation, such as a bar chart, to visually analyze the distribution of customers across different segments.

<img width="1392" alt="Screenshot 2023-07-30 at 12 24 57 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/19cce026-4605-4d4b-8a57-1843598b21a2">




Based on the pivot table and visualizations, we can identify that a significant number of customers fall into the "Platinum Customers" segment. These customers possess higher customer value compared to other segments, making them a priority for our marketing and retention strategies. By understanding these segments, we can tailor our approaches to enhance customer satisfaction and strengthen our relationship with them.


Additionally, we have conducted an analysis on age clusters and profitability, which provides insights into which age groups contribute the most to profit. Moreover, we have examined car ownership and bike-related purchases across different states and industries.

In this part of the analysis, we are working with the variables "Profit," "Age," and "Wealth Segment." We create a pivot table to examine the relationship between these variables. The pivot table is designed with "Profits" as values and "Wealth Segment" as columns and "Age" as rows. To better analyze the age data, we group individual ages into different age clusters for a more comprehensive view.

To group individual ages into different age clusters, follow these steps:

Select the "Age" column in the pivot table.

Right-click on the selected "Age" column.

From the context menu, click on "Group."

A dialog box will appear, allowing you to specify the age ranges for the clusters.

Enter the desired age range for each cluster and click "OK" to group the ages accordingly.

<img width="1440" alt="Screenshot 2023-07-30 at 12 59 01 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/053ba639-4a48-424d-9fe5-cdcbb2068585">



After grouping the ages into different age clusters, we can visualize the data using a graph. Based on this graph, we can observe that the age group between 38 to 47 generates the highest profits for this business. Additionally, the mass customer wealth segment outperforms any other wealth segment. So, if we aim to target new or high-value customers, it is advisable to focus more on the mass customer wealth segment and concentrate on the age group between 38 to 47, as these individuals have a higher buying power.

<img width="1413" alt="Screenshot 2023-07-30 at 1 00 58 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/2a8c7020-498e-499f-a659-e01967ae89a0">




By grouping the ages, you will have a more organized and meaningful representation of age demographics, which will aid in better understanding the relationships between age, profits, and wealth segments.

By visualizing the data in the form of a graph, we can deduce that customers in the age group of 38 to 47 contribute the highest profits to the business. Additionally, the "Mass Customer" wealth segment performs the best among all wealth segments, indicating a focus on this segment for targeting high-value customers. Considering the age group's higher buying power, it becomes essential to concentrate on customers aged between 38 to 47 years for marketing strategies.


Another area of insight pertains to the types of cars owned in different states. By analyzing this data, we can identify which state has the highest number of cars owned. This information can provide valuable insights into the preferences and vehicle ownership patterns of customers in various regions.

<img width="1416" alt="Screenshot 2023-07-30 at 1 05 22 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/01519f49-7687-4795-ab31-23abd1d8f4d5">

Next, we have successfully created a pivot table to analyze bike-related purchases based on different industries. This data provides us with valuable insights into customer preferences and buying behavior within each industry sector.


<img width="1420" alt="Screenshot 2023-07-30 at 1 14 18 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/4bce2440-5542-4620-afa2-4678270b8a93">

Moving forward, we can perform another form of analysis to determine which industry sector is generating the highest profit. By examining the profit figures associated with each industry, we can gain a deeper understanding of the most lucrative sectors for the business. This information will help us identify key areas for growth and investment opportunities.

<img width="1416" alt="Screenshot 2023-07-30 at 1 16 43 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/b6070aa9-3d50-476a-8db5-ae34422af348">

