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

## 2) Analizing the data: Some expressions used

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
'%'&
	round(
    	  (((sum(Profit) - Sum({$<Returned={'Yes'}>}Profit)))*100)/(sum(Sales) - Sum({$<Returned={'Yes'}>}Sales)),
      0.01)
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
(if(GetSelectedCount(Person)>0, '| Sales Person: '&GetFieldSelections(Person)))&' '&
(if(GetSelectedCount(year)>0, '| Year: '&GetFieldSelections(year)))&' '&
(if(GetSelectedCount(month)>0, '| Month: '&GetFieldSelections(month)))&' '&
(if(GetSelectedCount(day)>0, '| Day: '&GetFieldSelections(day)))
```
The result is the image below:
<p align="center">
<img width="500"
     height="100"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Selection%20Header.JPG">
</p>

**E) Year/Month/Day Filters:**  
To make the report more dynamic, a  drill down dimension was created to make a faster selections in some charts, regarding  the dates: year / month / day.    
<p align="center">
<img width="475"
     height="550"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Drill%20Down%20Dimension.JPG">
</p>

**F) Count of Orders:**  
The same thought used to calculate the sales was used to count the number of orders: does not count returned orders. Also, analysing the data, was possibel to see that if an order has more than one item, it get repeated for each item. Thus, was added the DISTINCT function to count unique orders:
```sql
count(distinct [Order ID]) - count(distinct {$<Returned={'Yes'}>}[Order ID])
```

**G) Cell color for products with low margin:**  
In the pivot table displaying sales and profit margin by location, it was added an expression to highlight in red locations with lower margin of sales:
```sql
if(
	(((sum(Profit) - Sum({$<Returned={'Yes'}>}Profit))*100)/(sum(Sales) - sum({$<Returned={'Yes'}>}Sales)))<= 9.99 ,
    red(255),
    Green(255)
   )
```
It was also added an expression to highligh in green the profitable regions:
```sql
if((sum(Profit) - Sum({$<Returned={'Yes'}>}Profit))<= 0 ,red(255),Green(255))
```
<p align="center">
<img width="475"
     height="550"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Pivot%20Table%20sales%20location%20color.JPG">
</p>

**H) Top Vendor by Value and order:**  
In order to highlight who is the best vendor, it was created a caption to show it with the following expression
```sql
FirstSortedValue
			(distinct Person, 
                		(-aggr
                        	(Sum(Sales) - sum({$<Returned={'Yes'}>}Sales),
                        Person)) 
             )
                         &' = '&
             num
                 (max
                      (aggr
                            (sum(Sales) - sum({$<Returned={'Yes'}>}Sales),
                       Person)),
                  '$#.###.###,#0'
                  )
```
<p align="center">
<img width="475"
     height="150"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Top%20vendor%20by%20value.JPG">
</p>

Also, to sow the best vendor by order number, it was created the following expression:
```sql
FirstSortedValue
		(distinct Person,
        			(-aggr
                    	(count(Sales) - count({$<Returned={'Yes'}>}Sales),
                     Person)) 
         )
                     &' = '&
         max
         	(aggr
            	(count(Sales) - Count({$<Returned={'Yes'}>}Sales)
            ,Person)
            )
            
```
<p align="center">
<img width="475"
     height="150"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/top%20vendor%20by%20order.JPG">
</p>

**I) Top 5 products sold and top 5 margin:**  
On sales page, it is shown the top 5 bigger value produtcs sold. In order to acomplish that, it was used the following expression and result:
```sql
=aggr
	(if
    	(rank
        	(sum(Sales) - sum({$<Returned={'Yes'}>}Sales))<=5,
        [Product Name]),
[Product Name])
```
<p align="center">
<img width="475"
     height="150"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Top%205%20products%20sold%20by%20value.JPG">
</p>

Similarly, a table was created to show the top 5 biggest profit margin with the following expression:
```sql
=aggr
	(if
    	(rank
        	(sum(Profit) - sum({$<Returned={'Yes'}>}Profit))<=5,
         [Product Name]),
[Product Name])
```
<p align="center">
<img width="475"
     height="150"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Top%205%20products%20sold%20by%20margin.JPG">
</p>
Color expression was also added to the table as seen before, with very similar expressions.

**J) Number or order Returned and % from total orders:**  
Set modifiers were used to count the total number of orders retuned and the represetavite % over the total orders, with the following expressions:
```sql
count(distinct {$<Returned={'Yes'}>}[Order ID])
```
for percentagem over the total, the expression used was:
```sql
((count(distinct {$<Returned={'Yes'}>}[Order ID]))*100 ) / ((count(distinct [Order ID])) - (count(distinct {$<Returned={'Yes'}>}[Order ID])))
```
<p align="center">
<img width="475"
     height="150"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Orders%20Returned.JPG">
</p>

**K) Value of sales returned and % from total sales:**
To display the amount of money returned to costumer and the % it represents over the total, set modifier were also used:
```sql
Sum({$<Returned={'Yes'}>}Sales)
```
For the % o money returned over the total:
```sql
((Sum({$<Returned={'Yes'}>}Sales))*100) / (sum(Sales) - Sum({$<Returned={'Yes'}>}Sales))
```
<p align="center">
<img width="475"
     height="150"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/orders%20returner%20in%20value.JPG">
</p>

**L) Value of profit loss and % from total sales:**
Similar set expressions were used:
```sql
 Sum({$<Returned={'Yes'}>}Profit)
```
and:
```sql
 ((Sum({$<Returned={'Yes'}>}Profit)) *100) / (SUM(Sales) -  Sum({$<Returned={'Yes'}>}Profit))
 ```
 <p align="center">
<img width="475"
     height="150"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/orders%20returned%20profit%20loss.JPG">
</p>

## 3) Final Result:
* The app was designed to be very easy fo user to interact. That's why all pages have all filter on the left panel;
* Also, the main is to check influence of selection of each page on the totals ;
* According to the first section, on page was created for each area of analysis;
* To make even more flexible to check influence of a selection, there are navigation buttons for each page on the top of all pages. Ex: User make a product selection on the product page and want to check if that product was ever returned, he/she just need to navigate to Returned Products Page throught the navigation button and then come back. 

**GENERAL SALES PAGE**
 <p align="center">
<img width="700"
     height="400"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/page%201%20-%20General%20Sales%20Page.JPG">
</p>

**SALES BY REGION PAGE**
 <p align="center">
<img width="700"
     height="400"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/page%202%20-%20Sales%20By%20region.JPG">
</p>

**SALES BY VENDOR PAGE**
 <p align="center">
<img width="700"
     height="400"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/part%203%20-%20sales%20by%20vendor.JPG">
</p>

**SALES BY PRODUCT PAGE**
 <p align="center">
<img width="700"
     height="400"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/Page%204%20-%20Sales%20by%20product.JPG">
</p>

**PRODUCTS RETURNED PAGE**
 <p align="center">
<img width="700"
     height="400"
     src="https://github.com/cassiobolba/Qlik-Sense/blob/master/APP%20-%20Super%20Store%20Sales%20Report/Images/page%205%20-%20Products%20returned.JPG">
</p>


