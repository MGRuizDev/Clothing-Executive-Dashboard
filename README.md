## Clothing-Executive-Dashboard
<br>
An excel file with two sheets: Orders, SalesPerson, and a third sheet: Products that was created for this specific task. 

<br>

### Tasks

<br>

Gather sales person data with XLOOKUP, and insert it into the orders sheet.<br>
=XLOOKUP([@EmployeeKey],Table_Salesperson[[#All],[EmployeeKey]],Table_Salesperson[[#All],[Salesperson]],,0)
<br>
Gather the Products data with INDEX and MATCH, and insert it into the orders sheet.<br>
=INDEX(Products!$A$2:$G$335,MATCH(Sales!$C2,Products!$A$1:$A$335,0),MATCH(Sales!I$1,Products!$A$1:$G$1,0))
<br>
Note: When getting email there are some empty values in order to get an empty space instead of a 0 I tweak the formula to include a conditional IF.<br>
Note: First match look column Sales!$C2, Second match look row  Sales!I$1. So when drag down or right, it doesn’t populate with the last row or column, respectively.<br>
Note: Sorting mess up with formulas.<br>

<br>

Removed unimportant columns for these task: resellers key and sales territory key columns.

<br>

Create Sales column.<br>
Create Net Revenue column. (sales - cost)<br>
Change format date to months as letters. (cntr+shift+down, font > number > date)<br>
Change data type to currency type where appropiate.<br>

<br>

Check and remove duplicates,(select all data and , data remove duplicates)

<br>

Transform to table if it is not (contrl + T) to work with pivot tables, sorts and filters.<br>
Create Pivot table (insert, pivot table (alt+N+V+T)<br>
<br>
PT: Total Sales (Total Sales Over Time Chart)(date on rows, product on columns, sales on values)(removr decimal number using format cells)<br>
Chart: line chart.<br>
Problem: ungroup date.<br>
Add time line slicer.<br>
Add slicers: Category, Brand, Color, Size.<br>
Note: if change core table to reflect any change to pivot table just go to pivotTable > Refresh.<br>
<br>
PT: Sales By Country.<br>
Chart: Bar Chart. (copy paste previous pivot tabel: cntr+left click move)<br>
Chart: sort in descending order.<br>
<br>
PT: Top 5 Salesperson.<br>
Chart: Bar Chart. (Value filter > top 10)<br>
<br>
Create Dashboard: start by changing wide and height of first column and row to create margin.<br>
Dashboard: add shape for title. Cut and paste charts to dashboard. To make all charts work together, with time line and slicers update report connections.<br>
