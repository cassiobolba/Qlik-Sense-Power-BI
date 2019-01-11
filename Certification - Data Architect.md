
**BOLD**
*italic*

`codigo inlinne`

```kotlin
```
#
##
###
####


# Basic
## Part 1 - Intro to Qlik Sense
## Part 2 - Understanding The Data Modeling User Interfaces

### Data Model Viewer  

* While loading data from a data source, you can use the Data Profiling or not to help you to build the model;  
*  Using Data profiling does not create table connections instantly but offers the option of doing it on data manager, as well as allow bulk division and other edititings;  
<p align="center">     
 <img width="600" height="180" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20model%201.JPG">
 </p> 

* If not using data profiling, the table connections are created automaticaly, and you have to edit on the data load editor changing field names  
* You can check the table relationship connected through lines  
<p align="center">     
 <img width="800" height="500" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20model%202.JPG">
 </p> 

* Click in a table header and on preview button to check data quality specs for the table:
Table Metadata: # of rows and # of fields
Field Metadata: Density od field filled , Total distinct values, Present Distinct Values, Non-Null Values, Subset Ratio  
* Data manager is where you can connect tables trought recomended association 

### Data Model Issues
**Circular Reference**
* When data is associated in a closed loop. Lead to data mishmatch.  
* You can solve by renaming the field you don't want as a key field, or braking association in  Data Manager    

**Synthetic Key**
* This is when there are more then one field as key field creating a composite key;   
* You can brake it on data manager by breaking the synthetic key;    
* you can also rename the field or concatenate them on data load editor;   
 <p align="center">     
 <img width="800" height="500" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20model%203.JPG">
 </p>

## Part 3 - Data Manager
To use data manager with all functions, while loading data, you must anable the DATA PROFILING option.  
There are 2 main tabs on Data manager: Association and tables tab
**Association TAB**
* Generate data grouping  
* Generate Geo data from the geo analytics   
* Association bubble view  
* Evaluate, consider, configura break and preview associations  
* Concatenate, Synchronize, delete, reload, view detaisl and edit tables  

**Tables TAB**
* Determine # of fields  
* View data source  
* Identify concatenated tables split or concatenate it 
* Delete and edit tables   

**Edit Tables TAB**   
While in table tab, you can go to editing a table and:  
* Edit table or field names,   
* format date fields,  
* edit or break associations,  
* calculate fields,  
* unpivot tables,   
* use cards: Summary, bucket, set nulls,order, split, replace data.

### Loading data in the Data Manager
* After starting the load process and enabled the data manager, you can create the associations by dragging and droping the bubbles (tables) on the top of each other or use recommended association automatically. Consider the colors to see if the association is recommended or not (green, yellow and red). 
 <p align="center">     
 <img width="800" height="500" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Manager%201.JPG">
 </p>

* After creating the association, load the data;  
* In the tables tab you check you data, use cards, edit data format, create calculated fields;  
* In select data from source, you go back to the loading screen and can exlude columns, edit and as you were adding the table from the first time; c  
* In tables you can concatenate table manually 

**Summary**
 <p align="center">     
 <img width="800" height="500" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Manager%202.JPG">
 </p>

## Part 4 - Data Manager Calculations and Transformations
### CARDS  
It is available unde the edit table 
**Summary Card:**  
check the data type (dim or mea), Distinct vs. total values, frequency cont chart, null values, mixed values, summary metrics  
**Bucket Card:**  
divide data in buckets of values ranges. It creates a new column field. Ex: measure with ages from 0 to 100, if you apply 5 buckets, you can then classify first bucket 0-20 as young, 21-40 as adult, 41-60 middle age and so on. You can also personilize the ranges values and names as you wish.  
**Split Card:**   
It allows you to split your data in a field, as you wish. EX: you have a field car plate number = IHB-7701. You can split it into 2 fields, one for numbers and other for letters. Similiar to the example below:
 <p align="center">     
 <img width="400" height="300" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Manager%20-%20Split%20Card.JPG">
 </p>
 
**Replace and Set Null Card:**     
Used to replace disparate values. EX: In you table there are USA, U.S.A and United Stated. You can select theses values to become one of them to make it standard.  
In null card you can select the distinct values you want to be treated as nulls (kind of exclude the values from field)  

**Order Card:**  
If the order function in the chart does not match your requirements, you can use order card to customize the order. EX: Sort Gold, Silver and Bronze (which cannot be achieved by ascendig or descending. Just by expression)  

### CALCULATED FIELDS  
You can access in the add field button.  
EX: you can calculate the profit of a field by subtracting cost by selling price.
```sql
round(selling_price - cost_price, 0.01)
```
 <p align="center">     
 <img width="400" height="300" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Manager%20-%20Calculated%20Fields.JPG">
 </p>

Another example is to standarize a field that has multiple different asnwers: y, Yes, YES, n, NO, NO by calculating a new field:  
```sql
upper(left(Agree_or_not))
```  
The result is only, Y or N

### UNPIVOT  
Turn a wide table to a tall table
 <p align="center">     
 <img width="400" height="300" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Manager%20-%20Unpivot.JPG">
 </p>

### Review
 <p align="center">     
 <img width="800" height="500" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Manager%20calc-%20review.JPG">
 </p>













