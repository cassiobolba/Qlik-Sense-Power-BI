
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
**WHY COMBINE TABLES?**  
* Join data from different tables;  
* Combine tables with matching values to reduce number of tables and enhance performance;  
* Mapping tables work similar as joins, but for another specif cases;  

**CONCATENATING TABLES**  
2 Types of concatenation: Forced (when the number of columns and field names between tables are different) and automatic (when tables fully macth);   

**JOINS**  
Same logic as SQL 
* Right  
* Left  
* Inner  
* Outer   

**MAPPING TABLES**   
Mappings are used:  
* When one table has only two fields (key and a value);  
* First you need to express which table is being mapped:  

```sql
Table_name_map:
MAPPING LOAD  
    Key_field,  
    Values_field;  
<source>
```  
Mapped tables are droped automatically after loading data.  
Secondly, you need to apply the map in the desired table:  

```sql
Table_name:
LOAD
    Key_field,  
    APPLY MAP ('Table_name_map', Key_field, 'Not Found')as Map_Field,    
    Field_2;  
<source>  
```  

'Table_name_map' = Table name to be mapped  
Key_field = Field to match both tables  
'Not Found' = What to fill in case there is no match

#### REVIEW  
<p align="center">     
<img width="800" height="470" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Combining%20Tables.JPG">
</p> 


### 6 - Create Master Items
#### Why create master Items:  
* Master dimension or master measure values can be colored to represent custom color schemes.  
* Master dimensions can contain multiple fields organized in a drill-down group. 
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/4.6%20Master%20Items%20-%20Drill%20Down.JPG">
</p> 

* Master measures and dimensions can save expressions  

```sql
sum(total_sales) - sum(total_cost) 
```    
* Build and edit visualizations more efficiently using centralized assets.  
* Create an organized and well-named collection of reusable items for other user.  
* Define alternate states of selections to apply to specific visualizations. 

you can define an alternate selection for a chart, go:  
Mater Items > Alternate States > Just name it > Copy one Chart > drag the state to the copied chart > apply.  
now you can apply different selections for same charts and compare
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/4.6%20Master%20Items%20-%20Alternate%20Selections.JPG">
</p>

<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/4.6%20Master%20Items%20-%20Alternate%20Selections%202.JPG">
</p> 

**Three places to create Master Items:**   
* Create master items from the Master items (  ) section in the Assets panel;  
* Create master items from the Fields (  ) section in the Assets panel;  
* Create master items from the Data model viewer (  ), Preview panel;  

### 7 - Creating Master Items from the Data Model Viewer  

#### REVIEW
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Master%20Items%20Review.JPG">
</p>   

## Part 5 - Validating and Troubleshooting
### 1. Resolving Data Model Issues    
**SYNTHETIC KEYS**  
When two  tables has more than one field in common;  
To resolve, just leave 1 field with common name or create a compound key concatenating the comon fields:  
```sql
Table_name:  
LOAD  
Key_1ID & Key_2ID as New_key,  
...
```   
**CIRCULAR REFERENCE** 
Solution is similar to solving synthetic keys: Removing or renaming the fields.  

**QUALIFY / UNQUALIFY**
Used to solved Synthetic keys and Circular references.  
When using it, it will rename the field wit same name using the table perfix before the field name.  

```sql
QUALIFY *;
UNQUALIFY Key_field;
TABLE_NAME:
LOAD
    Field1,
    Field2,
    Field3
FROM <...>
UNQUALIFY *;
```  

* Add on the top of load statement the qualify, which will add a table prefix in all field "tablename.fieldname";    
* Below, use the unqualify to not use the prefix in the key field;  
* Then load table script;  
* At the end, add the unqualify to finish the qualifying function;    

#### REVIEW   
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Resolving%20Association%20Issues.JPG">
</p>    

### 2. Debugging the Script    
**common errors:**    
* Lack of connection or connection error name;  
* Lack of colon or semi-colon;  
* Lack of colon after table name;  
* Different table names;  

**Error Mode:**  
You can set the error mode to continue trying to load the script even with errors:  
```sql
SET ErrorMode=1; (default, it stops the load when find error)  
or  
SET ErrorMode=0; (Try to continue the load)
```  

**Debbuger**  
* Use to check errors;    
* Run the code chunks by chunks;    
* Check log of loading;    
* You can favourite on the debugger the most checked expression for errors;  

#### REVIEW   
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Debugging%20the%20script.JPG">
</p> 

### 3. Validating the Model  
**VALIDATION TABLE**  
* A table is created joining data from the Qlik Data Model and the Source Data Model, to compare if the fields match;  
* Also it is possible to create calculations field to check if there is any variance in values, making easier to spot values differece;   
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Validation%20Table.JPG">
</p>    

**COUNTER FIELDS**  
* Count fields to check if the number match with the real one;  
* Create flags to separate fields to calculate;  
```sql
TableName:  
LOAD  
    IF (gender='Male', 1, 0) as MalesFlag,  
    IF (gender='Female', 1, 0) as FemalesFlag,  
...
```  
Now is easy to count the number of each gender:  
```sql
SUM(MalesFlag)
```  
* Could be dangerous to create counts of key fields values, so it is better to create a new field as flag for counting:  
```sql  
...
1 as ProductsFLag,  
...
```   
It will create a a value 1 for each row. Now you can sum(ProductsFLag) to see all orders;  

#### REVIEW     
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Validating%20the%20Data%20Review.JPG">
</p>   

# ADVANCED  
## Part 6 - Advanced Scripting  
### 1. Working with Dates in the Data Load Script  
**MASTER CALENDAR**   
* we create master calendar to usually have a continuous date ranges, avoiding gaps:  
1st create the max and min variables > Autogenerate all missing dates in a temp calendar table > Resident load the auto-generated field to a master calendar table > drop the temporary tables. (check the master calendar section); 
* Master calendar works fine when there is a single **date field**;    
* You can create multiple master calendars, but it slows down data model, and is confusing for business analyst since you will have many date tables.    

**LINK TABLES**  
* Good solution when you have more than a date field;  
* It is a table that contain common fields from two or more tables;  
* Used to solve Circular references and Synthetic Keys;  
 <p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Link%20table.JPG">
</p>    

EXAMPLE
```sql
//* load dimension tables *//
Orders:
LOAD
	OrderID & OrderDate as Key_orders,
    //OrderID,
    OrderDate//,
    //OrderSalesAmount,
    //CustomerID
FROM [lib://LinkTableData/LinkTableDates-data.xlsx]
(ooxml, embedded labels, table is Orders);

Invoices:
LOAD
	InvoiceID &'-'& InvoiceDate as Key_invoice,
    InvoiceID,
    //OrderID,
    InvoiceDate//,
    //InvoiceAmount
FROM [lib://LinkTableData/LinkTableDates-data.xlsx]
(ooxml, embedded labels, table is Invoices);

Shipments:
LOAD
	ShipmentID &'-'& ShipmentDate as Key_shipment,
    ShipmentID,
    //OrderID,
    ShipmentDate//,
    //CustomerID
FROM [lib://LinkTableData/LinkTableDates-data.xlsx]
(ooxml, embedded labels, table is Shipments);

//* build temporary link table *//
LinkTable_Temp:
LOAD *,
     OrderDate as DATE,
     'OrderDate' as DateType
FROM [lib://LinkTableData/LinkTableDates-data.xlsx]
(ooxml, embedded labels, table is Orders);

Invoices:
Concatenate LOAD 
	 *,
     InvoiceDate as DATE, 
     'InvoiceDate' as DateType
FROM [lib://LinkTableData/LinkTableDates-data.xlsx]
(ooxml, embedded labels, table is Invoices);

Shipments:
Concatenate LOAD 
	 *,
     ShipmentDate as DATE,
     'ShipmentDate' as DateType
FROM [lib://LinkTableData/LinkTableDates-data.xlsx]
(ooxml, embedded labels, table is Shipments);
//* end of temporary link table *//


//* create final LinkTable *//
LinkTable:
LOAD
     DateType, 
     DATE,
     Day(DATE) as Day,
     Month(DATE) as Month,
     Year(DATE) as Year,
     InvoiceAmount,
     OrderSalesAmount,
     CustomerID,
     OrderID,
     OrderID &'-'& OrderDate as Key_orders,
     InvoiceID &'-'& InvoiceDate as Key_invoice,
     ShipmentID &'-'& ShipmentDate as Key_shipment
Resident LinkTable_Temp;
//* end of final linktable *//

//* drop the temporary LinkTable *//
DROP Table LinkTable_Temp;
```
* It works up to a few tables, more than 3 or 4 tables make the script to complex and overwhelming;  

**DATE ISLAND**  
* Like a stand alone master calendar loose in the data model;  
* Easier to do than link tables;    

 <p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Date%20Island.JPG">
</p> 

EXAMPLE:  
```sql
//* Generating the quarters automatically to map to calendar later *//
QuartersMap:  
MAPPING LOAD   
            RowNo() as Month,  
            'Q' & Ceil (RowNo()/3) as Quarter  
AutoGenerate (12);  

//* Temp table to create the max and min date *//  
Temp:  
LOAD  
            Min(OrderDate) as minDate,  
            Max(OrderDate) as maxDate  
Resident Orders;  
  
LET varMinDate = Num(Peek('minDate', 0, 'Temp'));  
LET varMaxDate = Num(Peek('maxDate', 0, 'Temp'));  
DROP Table Temp;  

//* Temp calendar table to generate continuous date series values (fill the gaps) *//   
TempCalendar:  
LOAD  
            $(varMinDate) + IterNo()-1 as Num,  
            Date($(varMinDate) + IterNo() - 1) as TempDate  
            AutoGenerate 1 While $(varMinDate) + IterNo() -1 <= $(varMaxDate); 

//* Date Island is created from resident load from TempCalendar table. The TempDate field is aliased to loose relationship with other tables *//    
DateIsland:  
LOAD  
            TempDate as Date,  
            Week(TempDate) as Week,  
            Year(TempDate) as Year,  
            Month(TempDate) as Month,  
            Day(TempDate) as Day,  
            YearToDate(TempDate)*-1 as CurYTDFlag,  
            YearToDate(TempDate,-1)*-1 as LastYTDFlag,  
            InYear(TempDate, MonthStart($(varMaxDate)),-1) as RC12,  
            Date(MonthStart(TempDate), 'MMM-YYYY') as MonthYear,  
            ApplyMap('QuartersMap', Month(TempDate), Null()) as Quarter,  
            Week(WeekStart(TempDate)) & '-' & WeekYear(TempDate) as WeekYear,  
            WeekDay(TempDate) as WeekDay  
Resident TempCalendar  
Order By TempDate ASC; 
//* Drop the temp tables *//  
DROP Table TempCalendar; 
```  
* Since there is no association between tables and date island, you have to create a comparison if statement on the frontend to show results. For example, sum of sales:  
```sql
sum(if(OrderDate=Date,sales))
```
* The model will have to compare every single date to check the if condition, what can slow down the visualization on the front end.    

**CANNONICAL DATE FIELD**  
* A bridge table is created in the table with the finest granularity and then is connected to the canonical table;  
* Finest granularity is a table where each record has only one values of each type associated;  
* It is not centrilized as a link table, is easy to create beacause does not require the concatenated fields as link table;  

 <p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Canonical%20Calendar.JPG">
</p>

* Fist step is to create the DateBridge table:  
```sql
//* start mapping tables only mapping the date field and the ID field of each table, using resident load from original table *//
OrderID2OrderDate:
Mapping 
LOAD
    OrderID, 
    OrderDate 
Resident Orders;

OrderLineKey2ShipmentDate:
Mapping 
LOAD
    OrderLineKey, 
    ShipmentDate 
Resident Shipments;

CustomerID2RelationshipEndDate:
Mapping 
LOAD
    CustomerID, 
    RelationshipEndDate 
Resident Customers;

//* end of mapping tables *//
//* apply the map using resident from the table with finest granularity *//

DateBridge:
LOAD FinestGranularity, 
    ApplyMap('OrderID2OrderDate',OrderID,Null()) as CanonicalDate, 
    'Order' as DateType
Resident OrderDetails;

LOAD FinestGranularity, 
    ApplyMap('OrderLineKey2ShipmentDate',OrderLineKey,Null()) as CanonicalDate, 
    'Shipment' as DateType
Resident OrderDetails;
    
LOAD FinestGranularity, 
    ApplyMap('CustomerID2RelationshipEndDate',OrderID,Null()) as CanonicalDate, 
    'CustomerEndDate' as DateType
Resident OrderDetails;

```
* While loading the data in the actual tables, create the  FinestGranularity field with alias from the field that has no repeated values:  
```sql
//* loading OrderDetails data */
OrderDetails:
LOAD
    KEY_OrderDetails,
    OrderLineKey,
    OrderLineKey as FinestGranularity,
    OrderID,
    LineNo,
    ProductID,
    Quantity,
    UnitPrice,
    LineSalesAmount,
    Discount
FROM [lib://CanonicalDateData/OrderDetails.qvd]
(qvd);

//* loading Orders data */
```

* Last step, create the canonical calendar:  
```sql
CanonicalCalendar:
LOAD CanonicalDate,
    Day(CanonicalDate) as Day,
    Month(CanonicalDate) as Month,
    Year(CanonicalDate) as Year,
    Date(MonthStart(CanonicalDate),'MMM-YYYY') as MonthYear
Resident DateBridge;
```

PAREI NA PARTE 2. CONITUNAR NO VIDEO 3





