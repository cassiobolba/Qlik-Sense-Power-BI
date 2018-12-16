# DESCRIPTIVE
## 1) Analizing the data: What questions we want  to answer?
### Finance Questions:  
1-  Total sales per year/month  
2-	Total sales per category per year/month  
3-	Total sales by region per year/month  
4-	Total profit  
### Geographic Questions:
1-	Best seller region  
2-	Best Seller state  
3-	Best Seller city  
### Product Questions:
1-	Best Seller Category Product  
2-	Best Seller Product  
3-	Most profitable product  
### Vendor/Costumer Questions:
1-	Best Vendor  
2-	Most profitable vendor  
3-	Costumer who bought the most  
### Delivery Questions:
1-	Most used delivery method  
2-	Avg time between Order Date and Ship Date  
3-	Total products returned   
4-	Most returned products   
5-	Sales Lost with returned products  
6-	Profit Lost with returned products  

## 2) Analizing the data: How to answer the questions with the available data? Challenges

**A) Total sales:** Analizing the main table "Orders", you see sales value is there. But if you compare the data with the table "Returns", the returned product is also on "Orders" table.  
Qlik Sense associative engine can handle  it by itself.

Below, expression used to calculate total sales not suming returned itens (Considering business returned the money to costumer who returned itens, and further named **vTotal_Sales_No_Returned** )

``` sql
sum(Sales) - sum({$<Returned={'Yes'}>}Sales)
```
**B) Profit:**  
The profit also had to be calculated by ignoring the returned products by the following expression (further named as **vTotal_Profit_No_Returned** ):
```sql
=(sum(Profit) - Sum({$<Returned={'Yes'}>}Profit))
```
The secondary KPI, which is a percentage of total profit over total sales, was created based the two past expressions. The expressions were saved as variables to be reused later
``` sql
'%'&round(((vTotal_Profit_No_Returned)*100)/(vTotal_Sales_No_Returned), 0.01)
```
To color the total profit KPI, we used the below expression. Profit percentage limit calculation (target is 10%)
``` sql
=(sum(Sales) - Sum({$<Returned={'Yes'}>}Sales)) * 0.1
```

When sales is below the 10% margin:
<p align="center">
  <img width="600" height="100" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Below_Target_Profit.JPG">
</p>
When sales is above the 10% margin:
<p align="center">
  <img width="600" height="100" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Above_Target_Profit.JPG">
</p>

**C) Sales by Category:**  
It was created a master dimension with specific RGB colors for each category, to make sure the colors will be the same on other visualizations.
<p align="center">
  <img width="410
  " height="500" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Category_MasterDimension.JPG">
</p>


**D) Selection Header:**  
A selection header was created to assure the user will know what kind of selection he is looking at:  
```sql
(if(GetSelectedCount(Region)>0,' Region: '&GetFieldSelections(Region)))&' '&
(if(GetSelectedCount(State)>0, '| State: '&GetFieldSelections(State)))&' '&
(if(GetSelectedCount(City)>0, '| City: '&GetFieldSelections(City)))&' '&
(if(GetSelectedCount(Category)>0, '| Category: '&GetFieldSelections(Category))) &' '&
(if(GetSelectedCount([Sub-Category])>0, '| Sub-Category: '&GetFieldSelections([Sub-Category]))) &' '&
(if(GetSelectedCount([Product Name])>0, '| Product: '&GetFieldSelections([Product Name]))) &' '&
(if(GetSelectedCount(Person)>0, '| Sales Person: '&GetFieldSelections(Person)))
```
The result is the image below:
<p align="center">
<img width="500"
     height="100"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Selection%20Header.JPG">
</p>

**C) Year/Month/Day Filters:**  

      
