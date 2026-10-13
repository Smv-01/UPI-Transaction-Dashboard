# UPI-Transaction-Dashboard
Dashboard Link : https://app.powerbi.com/groups/me/reports/your-report-id/ReportSection
Problem Statement

This dashboard helps banks & payment providers understand how their customers use UPI (Unified Payments Interface). It helps them know how much money is moving every month, how the remaining account balance changes over time & which cities, banks, devices & payment methods are driving these transactions. Through different slicers, they get to know their strong & weak areas, & thus they can improve their services by identifying these areas. It also lets them know the monthly trend of transaction amount & remaining balance, thus since by using this dashboard they have identified the months with unusually high or low activity, they can further work on factors responsible for it.

Since, number of transactions is not same for all the age groups (60 % transactions are made by A3 age group, whereas only 25 % are made by A2 age group & 15 % by A1 age group), thus they must focus on those age groups where the usage is low.

Also since transaction amount & remaining balance both vary from month to month, thus they must try to understand the reason behind these changes.

Steps followed
Step 1 : Load data into Power BI Desktop, dataset is an excel file (UPI+Transactions.xlsx, Sheet1).
Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
Step 4 : First row was promoted to headers & correct data type was assigned to every column (text, date, decimal number & whole number).
Step 5 : Column named "TransactionTime" contained date & time together, so it was split by delimiter (space) into two columns, the date part was removed & the time part was renamed back to "TransactionTime".
Step 6 : Columns named "CustomerAccountNumber" & "MerchantAccountNumber" were changed to text data type, as account numbers are identifiers & should not be aggregated.
Step 7 : In the report view, under the view tab, theme was selected.
Step 8 : Visual filters (Slicers) were added for ten fields named "BankNameSent", "BankNameReceived", "City", "Gender", "DeviceType", "PaymentMethod", "MerchantName", "Purpose", "TransactionType" & "Age Groups". All slicers are of dropdown style.
Step 9 : A line chart & a column chart were added to the canvas representing total transaction amount by month. While creating these visuals, field named "TransactionDate" (month level of the date hierarchy) was added to the X-axis & field named "Amount" (sum) was added to the Y-axis.
Step 10 : A line chart & a column chart were also added representing total remaining balance by month. While creating these visuals, field named "TransactionDate" (month level of the date hierarchy) was added to the X-axis & field named "RemainingBalance" (sum) was added to the Y-axis.
Step 11 : All four charts were placed on top of each other & four bookmarks were created, named as below, (a) Line Chart Amount (b) Column Chart Amount (c) Line Chart Balance (d) Column Chart Balance

Using bookmark navigator (insert tab > buttons > navigator > bookmark navigator), user can switch between these four charts by a single click.

Step 12 : Titles were given to all the four charts, for example "Transactions By Month [Column] (Year 2024)" & "Balance By Month [Line] (Year 2024)".
Step 13 : Calculated column was created in which, customers were grouped into various age groups.

for creating new column following DAX expression was written;

    Age Groups = 
    
    IF('UPI Transaction'[CustomerAge]<=25,"A1",
    
    IF('UPI Transaction'[CustomerAge]<=35,"A2","A3"))

    where, A1 = age up to 25 (25 included), A2 = age 26 to 35 (35 included), A3 = age above 35
<img width="1541" height="791" alt="Screenshot 2026-10-13 092029" src="https://github.com/user-attachments/assets/83379425-9999-45df-92a5-7b6ab018a07c" />
Step 14 : A second page was added to the report, containing the same slicers & a matrix visual. In the matrix, field named "TransactionDate" (month level) was added to Rows, fields named "City" & "Currency" were added to Columns & fields named "Amount" & "RemainingBalance" (sum) were added to Values.

<img width="997" height="512" alt="Screenshot 2026-10-13 092420" src="https://github.com/user-attachments/assets/fc933578-6e30-4a19-bced-b5ab200a5d47" />
Step 15 : A report level filter was applied on the field named "Currency", thus it is applicable on all the pages of the report.
Step 16 : The report was then published to Power BI Service.

Report Snapshot (Power BI DESKTOP)

Page 1 :
<img width="1377" height="777" alt="Snapshot Dashboard" src="https://github.com/user-attachments/assets/7861834a-dd5d-492d-95e8-342aed1e9057" />

Page 2 :
<img width="1366" height="768" alt="Screenshot 2026-10-13 092529" src="https://github.com/user-attachments/assets/59604665-f1bb-4533-92a6-6cb3429c7b6e" />

Insights

A two page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

[1] Total Number of Transactions = 20000

Number of transactions (Male) = 10000 (50.00 %)

Number of transactions (Female) = 10000 (50.00 %)

Total transaction amount (Male) = 9,927,901.15

Total transaction amount (Female) = 9,944,372.88

       thus, number of transactions is same for both the genders, although total transaction amount of female customers is slightly higher.
[2] Transaction Amount By Month (2024)
a) Month with highest transaction amount - May (1,706,785.86)
b) Month with lowest transaction amount - August (1,598,708.63)
c) Total transaction amount - 19,872,274.03

Amounts of all currencies (INR, USD, EUR & GBP) are added as they are, without any currency conversion.

Transaction amount can be viewed as a line chart or a column chart using the bookmark navigator.

These values will change if different visual filters will be applied.

[3] Remaining Balance By Month (2024)
a) Month with highest remaining balance - June (8,535,972.29)
b) Month with lowest remaining balance - May (8,222,006.79)
c) Total remaining balance - 100,410,817.42

Remaining balance can be viewed as a line chart or a column chart using the bookmark navigator.

Remaining balance will change if different visual filters will be applied.

[4] Some other insights
Age Group

1.1) 15.00 % transactions belong to 'A1' age group (age up to 25).

1.2) 25.00 % transactions belong to 'A2' age group (age 26 to 35).

1.3) 60.00 % transactions belong to 'A3' age group (age above 35).

     thus, maximum transactions belong to 'A3' age group.
Device Type

2.1) 33.34 % transactions were made using 'Laptop' device.

2.2) 33.34 % transactions were made using 'Tablet' device.

2.3) 33.33 % transactions were made using 'Mobile' device.

   thus, transactions are almost equally distributed among all the three devices.
Payment Method

3.1) 33.34 % transactions were made using 'Phone Number'.

3.2) 33.34 % transactions were made using 'QR Code'.

3.3) 33.33 % transactions were made using 'UPI ID'.

    thus, transactions are almost equally distributed among all the three payment methods.
City

4.1) 25.00 % transactions were made in 'Bangalore' city.

4.2) 25.00 % transactions were made in 'Delhi' city.

4.3) 25.00 % transactions were made in 'Hyderabad' city.

4.4) 25.00 % transactions were made in 'Mumbai' city.

    thus, transactions are equally distributed among all the four cities, but total transaction amount is highest in 'Mumbai' (5,052,564.92) & lowest in 'Bangalore' (4,875,336.23).

