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
 
In order to avoid data mismatch, boths tables were joined based on orderID.    

Expression used to calculate total sales not suming returned itens (Considering returned the money to costumer who returned itens )

``` sql
sum(Sales) - sum({$<Returned={"yes"}>}Sales)
```

**A) Year/Month/Day Filters:**  
 
