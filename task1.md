# KPMG-VIRTUAL-INTERNSHIP

**TASK 1**

**Identifying Data Quality Issues:**

Throughout this assignment, a thorough evaluation of data quality and completeness was conducted on all three datasets. Based on the findings, comprehensive recommendations were formulated to ensure the data is well-prepared for analysis using an Excel Spreadsheet.

Let us examine the data for potential data quality concerns. To ensure data integrity, we can apply filters to identify any instances of data quality issues. For instance, we can use a filter to detect any discrepancies or anomalies within the dataset. As we analyze the data, we will address each potential concern individually.

When dealing with **transactional_ID**, we can confidently state that it does not require any modifications since it consists of unique values. Similarly, the **product ID** is unique, without any duplications, and can be left unchanged as well.

Now, moving on to the transactional date (set for the year 2017), we observe that there are no null values, and the date and time formats appear to be correct. Therefore, we will not alter the transactional date column.

In the case of **online_orders**, we can identify some blanks, indicating the presence of null values. To maintain data completeness, we will remove these null values from the data set.

As we examine the **brands**, we notice the existence of null values. To ensure data integrity, we will eliminate these null values from the brands column.

On the other hand, the **product_line** consists of four different segments, and we do not find any data quality issues here. Hence, we can proceed without modifications to this column.

Similarly, the **product-class and product_sizes** do not pose any data quality issues and can remain unaltered.

Reviewing the **price_list**, we confirm that there are no blank values, ensuring data integrity in this aspect.

Next, we examine the columns related to **standard_cost**, and we do not find any blank values, validating their data integrity.

Regarding the **product_first_sold** column, we notice that the data format contains numbers rather than dates. To rectify this metadata issue, we will convert these numerical entries into appropriate date and time formats.
For this, right click on the coloumn(product first sold) and click on date, It will convert the corresponding coloumn into date format.

<img width="637" alt="Screenshot 2023-07-27 at 1 07 53 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/97d1a988-45d5-43b9-8a7e-53683e4768ea">

Moving on to the **"new customer list" sheet**, we find no null values in the first name and some blanks in last name columns. To maintain data completeness, we will remove the null values from last name column.

In the **gender** column, we encounter inconsistencies, such as the presence of "u" instead of "f" or "m" for female and male, respectively. Since "u" does not convey meaningful information, we will disregard this entry for consistency.

As we continue with the data, we encounter null values in the **job_title** and **job_industry_category** columns. To maintain data integrity, we will remove these null values from both columns.
All the other coloumns looks fine to me.

Furthermore, in the **"CustomerDemographics Sheet"** section, we also address inconsistencies in the gender column by converting all "female" entries to "f" and all "male" entries to "m."
and some blanks in last name columns.

Additionally, we come across a column labeled "default," which appears irrelevant to the dataset. Hence, we will exclude this column from the data set altogether.

Finally, while analyzing the **"customer address sheet"**, we observe that it serves as a primary key and contains unique values, warranting no changes.

To summarize, we have identified several data quality issues in the dataset, including null values, inconsistencies in the gender column, and irrelevant data in the "default" column. To address these issues, we have removed null values, rectified inconsistencies in the gender column, and excluded the "default" column from the dataset. By taking these measures, we can enhance the data integrity and reliability of the dataset.

<img width="605" alt="Screenshot 2023-07-27 at 1 44 05 PM" src="https://github.com/Nidhiwa/KPMG-VIRTUAL-INTERNSHIP/assets/88158951/f364bc8f-0fdb-449d-be9a-6716bf7355f4">
