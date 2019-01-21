
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

### 2. Data Model Viewer  

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

#### Data Model Issues
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

### 2.Data Manager
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

#### Loading data in the Data Manager
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

### 4.Data Manager Calculations and Transformations
#### CARDS  
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

#### CALCULATED FIELDS  
You can access in the add field button.  
EX: you can calculate the profit of a field by subtracting cost by selling price.
```sql
round(selling_price - cost_price, 0.01)
```
 <p align="center">     
 <img width="400" height="275" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Manager%20-%20Calculated%20Fields.JPG">
 </p>

Another example is to standarize a field that has multiple different asnwers: y, Yes, YES, n, NO, NO by calculating a new field:  
```sql
upper(left(Agree_or_not))
```  
The result is only, Y or N

#### UNPIVOT  
Turn a wide table to a tall table
 <p align="center">     
 <img width="400" height="275" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Manager%20-%20Unpivot.JPG">
 </p>

#### REVIEW
 <p align="center">     
 <img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Manager%20calc-%20review.JPG">
 </p>

### 5.Data Manager Associations and Concatenations  
**CHECKING DATA ASSOCIATIONS**  
Even though you can automatically generate associations through data manager, it is always a good practice to check the association quality (check color showing).   

**CONCATENATE TABLES**   
One example of concatenating tables is when you have an order table, and a NEW ORDER TABLE.  
* when you load a table with exact same fields name and # of fields, it automatically concated the tables on data manager, showing a bubble with Overlaped circles:     
 <p align="center">     
 <img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20manager%20-%20Concatenating%20tables.JPG">
 </p>  

**FORCE CONCATENATION**   
Is used when you want to concatenate tables with different number of fields and different fields names, or even diffent field data:  
* Go to data manager > click on triple dots > Select both tables;   
* The manager will auto concatenate field with similar values;  
* Remaining fields must be concatenated manually;  
* Click on Edit Mappings > Edit Fields;  
* It will open both tables on right with all fields. the field not yet mapped are going to have a question mark beside (?);  
* Drag and the field from one table to another, from right column side to the manager;  
 <p align="center">     
 <img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20manager%20-%20forcing%20Concatenating%20tables.JPG">
 </p>    

* You can also split the tables after concatenating;

#### REVIEW
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20manager%20-%20Concatenating%20tables%20review.JPG">
</p>  

### 6.Introduction to the Data Load Editor 
Data Load Editor has 4 main functions:  
* **Connect to data source:** Connect to DB, file, API...  
* **Extract data:** Pull the data from the source;  
* **Transform data:**  You can edit data, change field names, change field format (eihter in main tab or in the load editor);  
* **Load dat into app:** Load and store data into a QVD;

#### OVERVIEW
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Data%20Load%20Script%20-%20Introduction%20Overview.JPG">
</p>

# Intermediate
## Part 3 - Loading Data
### 1. Loading Data from a Database
Data can come from many different sources:   
* Physical table structures;  
* Logical Views from tabular dataset;  
* Programing structures as Stored Procedures and user defined functions.      

**Connection storage Location**    
* Qlik Sense Desktop: In the QVF file (stay with the report file)  
* Qlik Sense Enterprise: Created on the QMC and is not saved on QVF  

#### Connection Syntax
```sql
LIB CONNECT TO 'connection_name';
```
* The syntax must be right before the tables to be loaded;  
* Organize the tables in groups according to different connections, or create a different tab to each different connection;    
* When a LIB syntax is placed, it disconect from previous LIB connection;  

#### **Loading from DATABASE**  
**OLE DB**   
Frequently used to access MDB files (access DB). Requires selection of a provider.    
* Select a provider (for .mdb is "microsoft jet 4.0 OLE DB...") > Find the file or server name > Check security if needed > Test > Name it > Create.

<p align="center">     
<img width="300" height="400" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/OLE%20DB%20connection.jpg">
</p>  

* After creating the connection, clik on insert data on the connection;  
* Select tables available, fields from tables and on and insert the script;



**ODBC (Open DB Configuration)**   
Used to connect to SQL servers DataBases. Requires set-up of the DSN in Advance:    
* When you open ODBC connection option, it looks for any DSN in the system automatically;  
* enter the User and Paswword > Rename it > Create;  

<p align="center">     
<img width="300" height="400" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/ODBC%20Connection.jpg">
</p>

* Qlik in add data > Select the database > Select the tables > Insert Script

**Loading from Stored Procedures:**  
Create the table with the fields as it was from a normal table and add the 'EXEC' command followed by the address of the procedure:  
```SQL
[Table_name]:
LOAD
Cust,
Product,
price;
SQL EXEC SP_NAME.dbo.SPgetDivision
```
### 2. Considerations when loading Data from Excel  
* You can either choose loading data from Script Editor or Data Manager;  
* In case loaded by script editor, you can still go to data manager and "Synchronize data" , to make available the data manager capabilities available;  
* You can ignore first rows on the "header size" option, in case you have more lines of header in your spreadsheet;  
* In case there is no header ojn you table, choose "no Field Names" on the "field names" panel;  

#### REVIEW
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Considerations%20when%20loading%20data%20from%20excel.JPG">
</p>  

### 3. Incorporating Data from Qlik DataMarket  
* Qlik data service, already cleaned, to be used in your models;  
* Finacial data, exchange rates, populations, countries and so on...    
* When usgng a resident load from a DM table, you need to use the noconcatenate function to avoid data concatenation:  
```sql
[New_table_name]:
NoConcatenate
LOAD
field1,
field2
RESIDENT DM_table_name;
DROP DM_table_name;
```

#### REVIEW
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Incorporating%20data%20from%20qlik%20data%20market.JPG">
</p>    

### 4. Working with QVD files  
* QVD: Table compressed in a phisical form in a disc.  
* QVD is much faster compared to a data connection; because it compress the data as 1 entity in the QVD file, while data conections load data row by row;   
* To create a QVD> Load data from a source (xls, DB, API, DM) > Model it and store into a qvd using:  
```sql
STORE  <table name> INTO[lib://<dataconnection>/<filename>.qvd];
```  
* Add this in the end of the data model: 
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/QVD%20creation%20syntax%20example.JPG">
</p>    

* QVD archtechture usualy is composed by a extraction layer from the data connection (after extracting, the connection is closed) and storing in a first layer QVD. After, others layers of QVD can be created according to data manipulation needed and also stored in QVD to the be available to be usied in multiple applications:  
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/QVD%20application%20architecture%20and%20modeling.JPG">
</p>   

* When storing, you select the path, and can create a structured folder repository to store the QVD according to the organization needed;    

#### INCREMENTAL LOAD  
* Used when data load takes a long time, also users and qlik need to extract data from DB, overwhelming the connection likely leading to slowness issues;    
* Incremental load is function in the script that make the load happens only for the most recent modifications, reducing the connection time to database;  
* There are 3 types of incremental load strategies: Insert, Update and Delete;  

```sql
LET vLastExecTime = ReloadTime();
LET vBeginningThisExecTime = Now ();
DataTable:
SQL SELECT PrimKey, X, Y 
FROM DB_Table
WHERE LastUpdate >= #$(vLastExecTime)#
AND LastUpdate < #$(vBeginningThisExecTime)#;
```   
* ReloadTime function and now functions are required to create the where condition and select the time frame AFTER LAST RELOAD and NOW;  
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Incremental%20load%20example.JPG">
</p> 

#### REVIEW  
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Working%20with%20QVD%20review%201.JPG">
</p>   

<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Working%20with%20QVD%20review%202.JPG">
</p> 

## Part 4: Model Architecting
### 1 - Associating Tables and Transforming Data 
**ASSOCIATING**  
To Associate tables with the correct field in the load script you can alias the field:  
```sql
Field_name as Key_field_name
```  
**PRECEDING LOAD**  
* Used to make transformation in qlik script after loading from DB;  
* Can have multiple stacked tranformations (load on top of load, on top of load...);  
* The reading on a preceding load is from bottom (DB selections) to top (modification loads);  

```sql
LOAD
Field_a + Field_b as Field_C;
SQL SELECT  
Field_a,
Field_b  
FROM Database_name;
``` 
* Try to make as most calculation as possible on load script to make the visualizations faster;  
* You cannot refer a new field aliased in the same load statement, you need to create a new load on the top (stacked preceding load).  

### 2 - Reload Data for Analysis     
**IN MEMORY DATA PROCESS**    
Since data in QVD are in memory data, they need to be reloaded every time the data is aletered on data source.  
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Reloading%20data.JPG">
</p> 

**TRIGGERS**  
In Qlik Enterprise you can create triggers to automatically reload, in QMC.    

**CHECKING LAST LOAD**  
Either a funtion on app page or on the app options (3 dots).  

### 3 - Creating Data During Reload   
**INCLUDE**  
Bring External reference from a source text file. EX: SET variables, LET...  
```sql
$(Include=[lib://<connector/<filename>])
```    
Application:  
* Easier migration of apps from one country to another
* Support for multiple developers contributing to the same data load script  

**AUTOGENERATE**     
Used for:  
* Rapid generation of large, unique datasets, for performance testing;  
* Generation of master caledar; 

```sql
TableName:  
LOAD  
    ROWNO() AS ID,  
    RAND() AS RandomNuM,  
    1 AS OneEveryTime  
AUTOGENERATE  
    5  
;
```  
This script is going to generate 5 rows for each of the 3 columns created on the load script. RowNo is incremental, random is random and 1 will always be 1.  

**INLINE**  
* Sused when small volume in infrently changing hard-coded data;  
* Custom sort orders;  
* Data which only architecs should change;   
* Also used to create tables for section access;  
```sql
TableName:  
LOAD 
    *
INLINE [
    Field1, field2, field3  
    value1, value2, value3  
    value4, value5, value6  
];  
```   
**RESIDENT**   
* Create table copies and apply data manipulation throught row filtering;  
* Always drop the temporary tables;    

```sql
TableName:
LOAD
    *
RESIDENT 
    <Table_Name>
WHERE <Criteria needed>
ORDER BY <Field>
;
```  

### 4 - Generating a Master Calendar   
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Master%20Calendar%20Review.JPG">
</p> 


**ANOTHER EXAMPLE**
```sql
Temp:  
Load  
min(OrderDate) as minDate,  
max(OrderDate) as maxDate  
Resident Orders;  
      
Let varMinDate = Num(Peek('minDate', 0, 'Temp'));  
Let varMaxDate = Num(Peek('maxDate', 0, 'Temp'));  
DROP Table Temp;  
      
TempCalendar:  
LOAD  
$(varMinDate) + Iterno()-1 As Num,  
Date($(varMinDate) + IterNo() - 1) as TempDate  
AutoGenerate 1 While $(varMinDate) + IterNo() -1 <= $(varMaxDate);  
      
MasterCalendar:  
Load  
  TempDate AS OrderDate,  
  week(TempDate) As Week,  
  Year(TempDate) As Year,  
  Month(TempDate) As Month,  
  Day(TempDate) As Day,  
  ApplyMap('QuartersMap', month(TempDate), Null()) as Quarter,  
  Week(weekstart(TempDate)) & '-' & WeekYear(TempDate) as WeekYear,  
  WeekDay(TempDate) as WeekDay  
Resident TempCalendar  
Order By TempDate ASC;  
Drop Table TempCalendar;  
```

### 5 - Combining Tables 
### 6 - Create Master Items
### 7 - Creating Master Items from the Data Model Viewer