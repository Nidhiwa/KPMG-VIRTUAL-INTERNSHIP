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

Age is calculated using formula below:

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









These scores will be used to derive an RFM value by assigning weights and adding them together.





Additionally, we have conducted an analysis on age clusters and profitability, which provides insights into which age groups contribute the most to profit. Moreover, we have examined car ownership and bike-related purchases across different states and industries.

The next steps involve creating charts to compare old and new customer lists, followed by developing a PowerPoint presentation to showcase our data insights. Task Three will entail creating dynamic dashboards using Google Studios.

I hope this video has been helpful, and I encourage you to watch the next one where we delve into creating powerful dashboards. Thank you for staying till the end, and I look forward to sharing more valuable content in my upcoming videos. Keep learning and sharing knowledge. Thank you and goodbye.
