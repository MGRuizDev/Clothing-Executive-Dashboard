## Clothing-Executive-Dashboard
<br>
Clothing Executive is a business that is transitioning an important marketing strategy implementation. There is a concern about their sales because ratings are falling on certain products, finding a reason might not only improve the image of the product to the people but also financial gains. They also require a centralized source of clear and available data to keep informed the stakeholders about performance and different metrics. Having a small amount of data, around 50,000 rows in a spreadsheet file with two sheets: Sales, SalesPerson, and a third sheet: Products, that was created for this specific task, I have decided to use Excel as main tool.
This project incorporates the use of powerful lookup tools for table's transformation, also the use of pivot tables and graphs, to create a dynamic dashboard with straightforward visuals that quickly display vital metrics, which help to describe important insights about the sales performance of this international clothing business.
<br>

### Tasks Of The Development Process.

1.- Gathering data to create the sales table.
<br>

Gather sales person data with XLOOKUP, and insert it into the sales sheet.<br>
  
    =XLOOKUP([@EmployeeKey],Table_Salesperson[[#All],[EmployeeKey]],Table_Salesperson[[#All],[Salesperson]],,0)

<br>

Gather the Products data with INDEX and MATCH, and insert it into the sales sheet.<br>

    =INDEX(Products!$A$2:$G$335,MATCH(Sales!$C2,Products!$A$1:$A$335,0),MATCH(Sales!I$1,Products!$A$1:$G$1,0))

<br>

Note: There are some empty values in the "Email" column. In order to get an empty space instead of a 0, When using the lookup to retrieve this data, I tweak the formula to include a conditional IF statement.<br>
Note: In the first match of the formula, I absolute referenced the column Sales!$C2, In the second match of formula, I absolute referenced the row Sales!I$1. So when drag down or right, it doesn’t populate with the last row or column, respectively.<br>
Note: Sorting mess up with formulas.<br>

<br>

2.- Removed unimportant columns (for this task): The "resellers" key and "sales territory" key columns.

<br>

3.- Create Sales column.<br>
4.- Create Net Revenue column.<br>
5.- Change format date to months as letters. (font > number > date)<br>
6.- Change data type to currency type where appropiate.<br>

<br>

7.- Examine and eliminate duplicates when required.

<br>
<br>

![Sales Table](/images/CED_SalesX.png)
<br>
<br>

8.- Create Pivot tables (alt+N+V+T)<br>
Note: Transform to table if it is not yet done (ctrl + T) to work with pivot tables, sorts and filters.<br>

<br>

PT: Total Sales (Total Sales Over Time Chart)(rows: date, columns: product, values: sales)
Note: remove decimal number using format cells.<br>
Chart: line chart.<br>
Add time line slicer: OrderDate.<br>
Add slicers: Category, Brand, Color, Size.<br>
Note: if a change to the core table has been done, to reflect this change on the pivot table just do > pivotTable > Refresh.<br>

<br>
<br>

![Total_Sales Table](/images/CED_TSalesPT.png)
<br>
The sales trends are showing a small but gradual increment, in most cases, for the majority of the products, except for Jeans and Dress which had a drastic increase of sales trends, both in the mid-year of 2018 for Jeans, and 2019 for Dresses. It will be advisable to go deep into detail about the reason of this unexpected move with more data.

<br>
<br>

PT: Sales By Country.<br>
Chart: Bar Chart.<br>
Chart: sort in descending order.<br>

<br>
<br>

![Country_Sales Table](/images/CED_SCountry_PT.png)
<br>
Only Canada doubled its sales compared to half of the other countries, making it the country with the most sales. It is followed by Cuba. While the rest of the countries are far behind, and Portugal on a concerned condition at the very bottom.

<br>
<br>

PT: Top 5 Salesperson.<br>
Chart: Bar Chart.<br>
Note: Go to > Value filter > top 10.<br>

<br>
<br>

![Pivote Table](/images/CED_T5_PT.png)
<br>
Linda and Jillian are around the 10 million in sales

<br>
<br>
<br>
<br>

9.- Summary Dashboard is a collage of the different visuals in a centralized point.<br>
Dashboard: Start by changing width and height of first column and row to create a margin.<br>
Dashboard: Add shape for title. Cut and paste charts to dashboard. To make all charts work together, with timeline and slicers, update the report connections.<br>

<br>
<br>

![Dashboard](/images/CED_DashboardX.png)
<br>
With a neat and clear interaction of the visuals with the slicers and timeline, this dashboard creates a dynamic observation of the performance in an appealing way.

<br>
<br>
<br>
<br>

10.- Create Summarize Business Data sheet.<br>

<br>
<br>

![Statistics Table](/images/CED_SBData.png)
<br>
This spreadsheet consits of basic statistical information on the sum of sales per day.<br>
Having a mean and median value very close, with a high range assuming an extended distribution with an also high standard deviation.

<br>
<br>
<br>
<br>

11.- Use Power Query to extract, transform, and load customer data.<br>
This powerful tool will allow to retrieve data from a file that contain customer purchase data, that can be used to enrich the analysis.
<br>
<br>

![Power_Query](/images/CED_PowerQuery.png)
<br>

Change: create duplicate columns of annual income and time spent, to modify the their value with the maximum of two decimal digits.<br>
Change: replace gender and product category data type from number to text. (Make change in the source file or query).<br>
We end up with quantitative data, discrete and continuous.<br>
<br>
<br>
<br>
<br>

12.- Loaded data from power query becomes Customer Purchase Data table.<br>
Insert Pivot Tables in the same worksheet. Time spent on the website, Gender, Age, Category. <br>
Note: summarize by counting value to create frequency attribute.<br>
PT: On Category pivot table, add % Cumulative attribute.<br>
Graph: Add Cumulative bar chart linked to PT Category.<br>
Note: To remove the graph format axis, on properties, change number with ;;;<br>
Note: When using formulas to create the stats table, automatic data update becomes easy. On the contrary, if pivot table is used, there is the need to refresh every time a change is made to the source table.<br>
<br>
<br>

![CustomerPurchase Table](/images/CED_CustomerInfo_Stats.png)
<br>

Adults aged 40 to 60 are the most predominant buyers, and men's clothing is purchased the most.

<br>
<br>
<br>
<br>


13.- Integrate functionality to send emails with the statistical information from sales per day table.<br>
The VBA program will go over salesperson table and pick only managerial positions to retrieve the email account.<br>
Note: In order to use VBA functionality the file type has to be macro enabled (.xlsm).<br>
<br>
<br>


![VBA_Email](/images/CED_VBA_Email.png)
<br>
This functionality that will keep Managers up to data on this valuable metrics.

<br>
<br>
<br>
<br>

14.- Add a button and integrate the macro to send emails with statistics.<br>
Note: Small tweak when referencing the range on the sheets. First select the sheet (Sheets("name").Select), then select the Range (Range("A2").Select).<br>

<br>
<br>


![Button Macro](/images/CED_ButtonToMacro.png)
<br>
The ability to promptly provide vital information to decision makers is game changing.


<br>
<br>
<br>
<br>

### Some other observations.
<br>
<br>

Ratings are falling on certain product  finding a reason might not only improve a person's perception but also gains.
Man and woman share a similar number of loyalty program awarded. Despite this, woman, specially middle aged woman stands out in this regard.

Has it been expected, because of the initial concern, we can see on products table that Jeans have the highest rating, specially extra large size product on yellow, white and green. When looking at categories by gender, we can see that woman and man (slightly higher in women) are the most bought categories on colors white, yellow and green for both categories.

Women seems to buy also men's clothing, probably as a gift. Specially jeans have shown a gradual sales increase among men and women. And when looking at T-shirts, we can see a very poor performance that probably can be improved, probably by using the popularity of jeans, these two can be sold together, initially reducing the price on t-shirts, in an attempt to promote and create liking for the product, another option is to completely rebrand the underperforming products, this can greatly increase profits.



<br>
<br>

<br>
<br>



