
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
<img width="700" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Link%20table.JPG">
</p>    

EXAMPLE
```sql
//* load dimension tables *//
Orders:
LOAD
	OrderID & OrderDate as Key_orders,
    //OrderID,
    //OrderDate,
    OrderSalesAmount,
    CustomerID
FROM [lib://LinkTableData/LinkTableDates-data.xlsx]
(ooxml, embedded labels, table is Orders);

Invoices:
LOAD
	InvoiceID &'-'& InvoiceDate as Key_invoice,
    InvoiceID,
    //OrderID,
    //InvoiceDate,
    InvoiceAmount
FROM [lib://LinkTableData/LinkTableDates-data.xlsx]
(ooxml, embedded labels, table is Invoices);

Shipments:
LOAD
	ShipmentID &'-'& ShipmentDate as Key_shipment,
    ShipmentID,
    //OrderID,
    //ShipmentDate,
    CustomerID
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
<img width="700" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Date%20Island.JPG">
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
<img width="700" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Canonical%20Calendar.JPG">
</p>

* Fist step is to create the DateBridge table:  
```sql
//* start mapping tables only mapping the date field and the ID field of each table,   
using resident load from original table *//
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
//* loading OrderDetails data *//
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

//* loading Orders data *//
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

* Finally, to use canonical calendar, on the front end you have to use set analisys expressions that will compare with the table flag created on the bridge table. If you want to sum quantity of material in order table, you have to use the expression:   
```sql
sum({$<DateType={'Order'}>}quantity)
```  

**DATA ISLAND X CANONICAL CALENDAR**    
* Canonical calendar is always a better option;  
* Data Island has no conection with the model, which create the need of going throught all dates;  
* Canonical Calendar has conection, which reduce the impact in the model;  
* Both need expressions on front end, which may slow down vizualization selections;  
* Avoind front end expressions as most as possible;  

**LOAD SCRIPT FLAGS**   
* To calculate YTD sales, you could create the following expression on the vizualization:  
```sql
SUM({<Year={Year(Max(date))}, Date={'<=Date(Max(Date), 'DD MMM YYYY')', Month=>}Sales)
```    
* But every time user makes a selection, the expression need to be validated, which can slow down the process in a large dataset;   
* Instead, flags can be created in the load script, and the output of it will be 1 or 0. 1 if it is part of the last year date, 0 if not:  
```sql   
YearToDate(OrderDate,) *-1 as CYTDFlag,  
...
```    
* Then in the front end, the expression is goin to be simpler:  
```sql
Money(sum({<CYTDFlag={1}>} Sales))
```  

**DATA FUNCTIONS (FOUND ON QLIK COMMUNITY)**  
* Data Offset & Fiscal Years;     
Used when companies have fiscal years different from standard (Jan 1st to Dec. 31st) 

```sql
/* loading Orders data */
Orders:
LOAD
    OrderRecordCounter,
    OrderID,
    Date(OrderDate) as OrderDate, /*Make sure order date in date format*/
    CustomerID,
    EmployeeID,
    ShipperID,
    FreightWeight,
    OrderStatus,
    LastUpdated
FROM [lib://FiscalCalendarData/Orders.qvd]
(qvd);

/* vFiscalYearStartMonth - Tells the starting month of the Fiscal Year
vStartDate - Starting date of the Calendar generation
vEndDate - Ending date of the Calendar generation */
 
LET vToday = Num('20-Mar-2015');

SET vFiscalYearStartMonth = 7;
LET vStartDate = Num(YearStart($(vToday), -1));
LET vEndDate = Num(YearEnd($(vToday)));
 
FiscalCalendar:
LOAD
    *,
    Dual('Q' & Ceil(FiscalMonth/3), Ceil(FiscalMonth/3)) as FiscalQuarter,        // Fiscal Calendar Quarter
    Dual(Text(Date(MonthEnd(OrderDate), 'MMM')), FiscalMonth) as FiscalMonthName; // Fiscal Calendar Month Name

LOAD
    *,
    Year(OrderDate) 
      as Year, /* Standard Calendar Year */  
    Month(OrderDate) 
      as Month, /* Standard Calendar Month */  
    Date(MonthEnd(OrderDate), 'MMM') 
      as MonthName, /* Standard Calendar Month Name */  
    Dual('Q' & Ceil(Month(OrderDate)/3), Ceil(Month(OrderDate)/3)) as Quarter, /* Standard Calendar Quarter */  
    Mod(Month(OrderDate) - $(vFiscalYearStartMonth), 12) + 1 as FiscalMonth, /* Fiscal Calendar Month */  
    YearName(OrderDate, 0, $(vFiscalYearStartMonth) as FiscalYear;/* Fiscal Calendar Year */  

LOAD
    Date($(vStartDate) + RangeSum(Peek('RowNum'), 1) - 1, 'DD-MMM-YYYY') 
      as OrderDate,
    RangeSum(Peek('RowNum'), 1) 
      as RowNum
AutoGenerate vEndDate - vStartDate + 1;  
```

**4-4-5 CALENDAR**  
* Frequently used in logistic and planning activities;    
  
**REVIEW** 
 <p align="center">
<img width="750" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Working%20with%20Dates%20Review.JPG">
</p>

### 2. Managing Security with Section Access   
**SECURITY:** 
* Authentication: Who is trying to get access (not covered in this module). I it handled by Qlik proxy features.   
* Authorization: What they are trying to do? what they are trying to see?    
* All section access script must be placed in the first app section, before the load script;  
* After Section Access script, you need to place **SECTION APPLICATION** before the load statement to start applying the section access control;  

**SECTION ACCESS: APP AUTHORIZATION**  
* Create tables to manage access to specific data;  
* Create a new section to add section access privileges:  
```sql
SECTION ACCESS;
Authorization:
LOAD * INLINE [
    ACCESS, USER ID
    ADMIN, ABC\CASSIO
    USER, ABC\MILAN
];

SECTION APPLICATION;  
...   
```
* Section access must be UPPER CASE;  
* This script would authorize cassio from domain ABC the admin access, and Milan with user access only;    

**SECTION ACCESS: ROW AUTHORIZATION**   
* You can make a user see only specific sections os data from the data set. Ex: A user can only see SALES data:  
```sql
SECTION ACCESS;
Authorization:
LOAD * INLINE [
    ACCESS, USER ID, REDUCTION 
    ADMIN, ABC\CASSIO,  
    USER, ABC\MILAN, SALES
    USER, ABC\KUNAL, PHARMA
    USER, ABC\KUNAL, 
];

SECTION APPLICATION;  
...
```
* All reduction fields must be upper case in both dataset and section access script;      

**SECTION ACCESS: COLUMN AUTHORIZATION**    
* You can omit a full coluumn from a user using the omit function;  
```sql
SECTION ACCESS;
Authorization:
LOAD * INLINE [
    ACCESS, USER ID, OMIT 
    ADMIN, ABC\CASSIO,  
    USER, ABC\MILAN, JobTitle
    USER, ABC\KUNAL, JobTitle
    USER, ABC\KUNAL, Pharma
];

SECTION APPLICATION;  
...
``` 

**SECTION ACCESS: OMIT GROUP OF COLUMNS AUTHORIZATION**   
* In this case you create an omit table pointing to each group access permition. Ex: EMP omit_group has no access to JobTitle, Salary and Experience.   
* Further, the user  MILAN was assigned access to the EMP group, and she will not have access to that.  
```sql
SECTION ACCESS;
Authorization:
LOAD * INLINE [
    ACCESS, USER ID, OMIT_GROUP 
    ADMIN, ABC\CASSIO,  
    USER, ABC\MILAN, EMP
    USER, ABC\KUNAL, EMP
    USER, ABC\KUNAL, CUST
];

OmitGroups:
LOAD * INLINE [
    OMIT_GROUP, OMIT 
    EMP, JobTitle  
    EMP, Salary
    EMP, Experience
    CUST, Address
    CUST, City
];

SECTION APPLICATION;  
...
```
  
**BINARY LOAD**  
* Enables us to copy data from one app to another, with all data, section data and security;  

STEPS:      
* First create a connection with the folder that contain your shared apps. It was created during qlik enterprise installation; Usually: C: > Qlik Share > Apps.  
* Then, get the app ID of the app you desire to copy data;    
* Create the connection statement:  
```sql
BINARY LIB://Connection_folder_name (pc user name_user Id)/app_id_joio898t723bi9h8a98;  
```    
* Used to for example when you want to cross a new data table with an axisting app, but dont want to mess with it;  

**REVIEW**
 <p align="center">
<img width="750" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Review%20Managing%20Security%20with%20Section%20Access.JPG">
</p>


### 3. Classifying Data  
**INTERVAL TYPES**  
* < or > = Lower or greater than (exclude the ending values). EX: Values > 3 = 4,5,6    
* ≤ or ≥ = Lower or equal and greater of equal (include the ending value). Ex: ≥ 3 = 3,4,5,6  


**CLASS ()**   
* You use class function to group values in buckets by intervals of values;    
* Syntax:  
```sql
Class(Expression,Interval[,label[,offset]])
```   
* Let`s say you have a table with artist and its respective sales and you want to classify it by buckets of sales with intervals of 100millions:  
```sql
...
Class(sales, 100, 'sales') AS Ranking,  
...
```
It will create a column with the values of "0 < sales < 100", other values of "100 < sales < 200" and so on.    
* Class function can only divide data in symetric buckets: 50 by 50, or 100 by 100 and so one. No flexibility choosing the size of buckets;     
* In case it happens to the data soucer add a new bucket in a load, class function automatically creates the new bucket;  

**IF ()**    
* Syntax  
```sql
IF(condition, then, else)  
```    
* Nested if functions are used to have cutomized interval buckets. EX: grade < 50 = F, grade > 50 and < 60 = E, grade > 60 and < 70 = D...   
```sql
[Student Grades]:
LOAD
    Student,
    IF (score >=0 and score < 60, 'F',
     IF (score >=60 and score < 70, 'D',
      IF (score >=70 and score < 80, 'C', 
       IF (score >=80 and score < 90, 'B',
       'A')))) as Grade
RESIDENT [Student Scores];
```  

* negative side is that you need to define all buckets manually. In case a new bucket class is added, user need to add to the code;  


**INTERVALMATCH ()**  
* Used to compare the data interval from one table to a predefined table which contain the interval bucket table;  
* You can have the predefined table on your data base or create a INLINE table on the fly;  
* Syntax:  
```sql
Table_name:
IntervalMatch (Match_Field1, Match_Field2)
LOAD 
    load_statement,  
    Fields_from_Interval_Table
RESIDENT [Data_Table]
```     
* You can have as many interval matching fields as you need; Let's say you have 2 different grade criteria for stundents in lower school and high school;  
* You have to create your interval match table like this:  
 <p align="center">
<img width="300" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Interval%20Match%20Table%20with%20Multiple%20Criteria.JPG">
</p>   

**REVIEW**
 <p align="center">
<img width="750" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Classifying%20Data%20Review.JPG">
</p>     

### 4. Generating Missing Date    
**TABLE GENERATION**  
* RESIDENT = Copy table from memory, transform, rename, drop...     
* AUTOGENERATE = Build from scratch, unlimited # of rows.  

**RECORD GENERATION**  

```sql  
Fill in dates gaps:  
/* Table only shows dates where conversion rates changed */ 
Temp_Rates:
LOAD * INLINE [
  Date, Rate
  10/1/2017, 1.01
  10/4/2017, 1.08
  10/8/2017, 1.07
];

/* Capture oldest and newest dates */
Temp_MinMaxDate:
LOAD 
	Min(Date) AS MinDate, 
    Max(Date) AS MaxDate 
RESIDENT Temp_Rates;

LET vMinDate = Peek('MinDate',-1,'MinMaxDate');
LET vMaxDate = Peek('MaxDate',-1,'MinMaxDate');

 DROP TABLE Temp_MinMaxDate;

/* Generate missing dates */
Dates:
LOAD 
	Date($(vMinDate) + RowNo() - 1) AS Date 
AUTOGENERATE vMaxDate - vMinDate + 1;

/* Sort by date, propagate rates down, clean up */
Rates:
NOCONCATENATE LOAD Date, 
  If( IsNull( Rate ), Peek( Rate ), Rate ) AS Rate
RESIDENT Temp_Rates
ORDER BY Date ;

DROP TABLE Temp_Rates;
```  
The result is a table with all dates, and also filling the rates where there is no rate with the previous rate (because the rate is te same).  

**LOOP**    
```SQL
// Policies:
LOAD * INLINE [
    PolicyID, BirthDate, FromDate, ToDate, Type
    10001, 5/21/1980, 5/1/2017, 7/1/2017, Whole Life
    10004, 6/2/1969, 6/1/2017, 8/1/2017, Term
    10002, 7/2/1976, 7/1/2017, 9/1/2017, Whole Life
    10000, 10/7/1952, 10/1/2017, 12/1/2017, Term
    10003, 12/22/1998, 12/1/2017, 2/1/2018, Term
];

// Policies_x_Dates:
LOAD PolicyID,
  Age(FromDate + IterNo() - 1, BirthDate) AS Age,
  Date(FromDate + IterNo() - 1) AS ReferenceDate
RESIDENT Policies
WHILE IterNo() <= ToDate - FromDate + 1;
```  
The records only contain the beggining and end date.  
This script creates a record for each day from the fromdate to the to date, for the age and for a new date field.  
Now, if you select any date, it will show you the insurance active in that day.    

**ACCUMULATION**  
As example, a bank transactions list with deposits and withdraw in the same column and acc and savings.  
* PEEK = if no argument, retrieve value of previous row  
* RangeSum = add values and Evaluate null or  not numerical values as 0,  

```sql
/* Table shows transaction amounts per account - no balances */ 
Temp_Transactions:
LOAD * INLINE [
  Account, Date, Amount
  Checking, 10/7/2017, 100
  Checking, 10/8/2017, 300
  Checking, 10/9/2017, -25
  Savings, 10/7/2017, 1000
  Savings, 10/8/2017, 50
  Savings, 10/9/2017, -500
];

/* Sort data then accumulate amounts */
TransWithBalances:
LOAD Account, Date, Amount,
	IF(Account = Peek(Account),RangeSum(Amount, Peek(Balance)),RangeSum(Amount)) AS Balance
RESIDENT Temp_Transactions
ORDER BY Account, Date;

DROP TABLE Temp_Transactions;
```  
The order by is very important to separate the type of account and organize per day, in order to have the right value.  
The if statement says: If the account is equal to last account (peek functionality), rangesum amount with the last balance value, else just sum with amount.
If it is the first value for one type of account, it will just sum the value itself.
THAT IS WHY IT IS VERY IMPORTANT TO ORDER THE TYPE OF ACCOUNT.  

**SUB FIELD**  
Example, list of skills of employees with skills in the same field. ex:   
name, skill   
cassio, java - css
vic, java  
The skill dimensions is not the same. To solve:  
* SubField =  

```sql
// Employees:
LOAD * INLINE [
	Emp No, Skills
    159, HTML | CSS
	163, JavaScript | jQuery
    174, C# | Ruby
    210, HTML | JavaScript
    215, HTML | PHP | JavaScript
    279, PHP | JavaScript
    286, SQL | JavaScript
    300, C# | SQL
];

Employees_x_Skills:
LOAD [Emp No],
	Trim(SubField(Skills, '|')) AS Skill
RESIDENT Employees;
```  

In the table there are lots of skills listed one after each other.   
The function to separate it is use a subfield, where the first argument is the field 'Skills', the second is the delimiter, where it will break each skill and create a new row for that employee. Use a Trim to eliminate any extra space.  
Example: emp. 159 will have 2 rows, one with HTML and other wiht CSS.   

**CARTESIAN PRODUCT**  
* Raw data contains monthly physical invetory counts;  
* Need to copy inventory counts to all days in between;  

```sql
/* --- Load all existing product Counts  and create a unique key of productID and date to overwrite it later when combining the tables*/
TempInventory:
LOAD
  ProductID,
  "Date",
  Count,
  ProductID & '|' & Num( "Date" ) AS Product_x_DateID
FROM [lib://Data/Cartesian.xlsx]
(ooxml, embedded labels, table is Sheet1);

/* --- Retrieve Min and Max dates and save to variables.
The autogenerate with fieldValueCount generate as many dates as loaded in the previous load. In this case, only 2. Then the fieldValue retrieve each value of the date field and then max and min captures the oldest and newest values. the RecNo() will act as pointer to each row data has been generated.
After, it is stored as a variable using Peek() function to retrieve the min and max.
*/
TempMinMax: 
LOAD
  Min(FieldValue('Date', RecNo())) AS MinDate,
  Max(FieldValue('Date', RecNo())) AS MaxDate
AUTOGENERATE FieldValueCount('Date'); 

LET vMinDate = Peek('MinDate',-1,'MinMaxDate');
LET vMaxDate = Peek('MaxDate',-1,'MinMaxDate');

DROP TABLE TempMinMax;

/* --- Create all combinations of product and date 
1- load distinct all products, in this case only 2 in a separate table TempProduct_x_Dates     
2- Autogenerate all dates missing between the vMinDate and vMaxDate and join to products table. It will generate a cartesian product. you have 31 days x 2 products = 62 rows.
*/
TempProduct_x_Dates:
LOAD DISTINCT ProductID RESIDENT TempInventory;

JOIN (TempProduct_x_Dates)
LOAD Date(RecNo()+$(vMinDate) - 1) AS Date 
AUTOGENERATE vMaxDate - vMinDate + 1;

/* --- Append missing records onto the TempInventory table
1- Load the previous table, create the same Product_x_DateID combination ID;  
2- On a Preceding load, compare and concatenate the keys to don't overwrite the initial values keys  (min and max dates) created previously using where not exists the loaded Product_x_DateID keys.
 */
CONCATENATE (TempInventory)
LOAD * WHERE NOT EXISTS( Product_x_DateID );
LOAD ProductID, Date,
  ProductID & '|' & Num( Date ) AS Product_x_DateID
RESIDENT TempProduct_x_Dates ;

DROP TABLE TempProduct_x_Dates;

/* --- Create final product Count table. Propagate value from above record   
Load the TempInventory and ORDER BY PRODUCT AND DATE. Because we use the same comparison with the previous row with PEEK.  
Load Product and date fields and create a If count:  
if the product ID is equal to the previous ProductID and the count field is null, show the previous count, if false, rangesum with the previous value. 
*/
ProductCounts:
LOAD ProductID, Date,
  If( ProductID=Peek( ProductID ) and IsNull( Count ),
  Peek( Count ),
  RangeSum( Count )) AS Count
RESIDENT TempInventory
ORDER BY ProductID, Date; 

DROP TABLE TempInventory;
```  

**MONTE CARLO SIMULATION**  
* AUTOGENERATE = generate numbers up to a condition  
* Rand () = Generate a randon number  
* Ceil () = round up  
* RecNo () = Show the number of the current row  

```sql 
DiceThrowing:
LOAD *,
  Dice1 + Dice2 AS SumOfDice;
LOAD
  RecNo( ) AS ThrowNo,
  Ceil( Rand( ) * 6 ) AS Dice1,
  Ceil( Rand( ) * 6 ) AS Dice2
AUTOGENERATE 100000;
```
Rand generate a random number and muplied by 6 (number of chances), round up with ceil. Every pair of dice geenerated will be recorder as a unique row number.  

**MONTE CARLO SIMULATION**
The steps are:  
1 - Create a Deck of Cards;  
2 - Shuffle and deal the cards;  
3 - Indetify Flush;  
4 - Indentify Combos;  
5 - Evaluate Combos;  
6 - Creates outcome tables;   

```sql
/* --- Create a Deck of cards   
 the Autogenerate create 4 rows for each iteration  of the while functions WHILE IterNo() <= 13. It means, we will have 52 combinations.  
Pick function select one of the values in the list for each iteration.  
In first iteration,   
 firtst line is interno() 1 and RecNo() 1, it means '2' and 'spades'.  
  Second row is iterno() 1 and RecNo() 2, it meand '2' and 'Hearts' and like this until Recno() is 4 being equal to autogenerate.   
thus, you have card 2 of all 4 suits.  
After recno() 4 it finishes firts iteration. Then start second iterno() and start recno() again. Second iterno() is card number '3', and thus create card 3 for the for recno(), or the 4 suits. finishes the all 4 iterno() for card 3, then move to other iterno() until 13. Thus you create all 52 cards.  
After, load all filed and concatenate the cardvalue with the suits to have the card name. Deck is created
*/
DeckOfCards:
LOAD *,
	CardValue & ' of ' & Suit AS CardName;
LOAD
    Pick(IterNo(),'2','3','4','5','6','7','8','9','10','Jack',
    	'Queen','King','Ace') AS CardValue,
    Pick(RecNo(),'Spades','Hearts','Diamonds','Clubs') AS Suit
AUTOGENERATE 4
WHILE IterNo() <= 13; 

-----------------------------------

/* --- Shuffle deck and deal cards many times with the for loop until 10k hands*/
FOR vHandNo = 1 to 10000
  /* --- Assign a random number to each card */
  LoadDeck:
  LOAD *,
    Rand() AS ShuffleSeed
  RESIDENT DeckOfCards;

  /* --- Order randomly by the random number shuffleseed and deal hands of 5 first cards in the load. drop the table to dont repeat it and concatenate. Next iteration of the variable HandNo. Also, each hand will be registered as the number of the for loop accordin to the variable vHandNo */
  PokerHands:
  LOAD
    CardName,
    CardValue,
    Suit,
    $(vHandNo) AS HandNo
  RESIDENT LoadDeck
  WHERE RecNo() <= 5
  ORDER BY ShuffleSeed;

  DROP TABLE LoadDeck;
NEXT vHandNo

DROP TABLE DeckOfCards;

/* --- Check each hand for Flush  
A flush is when all cards are the same. to indetify, a count of distinct values is used. If the count distinct is equal one, it means all cards are equal.
 */
IdentifyFlush:
LOAD
	HandNo,
	If(Count(DISTINCT Suit)=1,1,0) AS HandHasAFlush
RESIDENT PokerHands
GROUP BY HandNo;

/* --- Group each hand by CardValue 
	   then count the cards to check for pair, 
	   three of a kind, and four of a kind   */
IdentifyCombos:
LOAD
    HandNo,
    CardValue AS CardInCombo,
    If(Count(CardName)=2,1,0) AS ComboIsPair,
    If(Count(CardName)=3,1,0) AS ComboIsThreeOfAKind,
    If(Count(CardName)=4,1,0) AS ComboIsFourOfAKind
RESIDENT PokerHands
GROUP BY HandNo, CardValue;
  
/* --- Evaluate identified combinations in each hand 
	   for two pairs and a full house */
EvaluateCombos:
LOAD *,
	If(HandHasAPair and HandHasThreeOfAKind, 1,0) AS HandHasAFullHouse;
LOAD
    HandNo,
    If(Sum(ComboIsPair)=1,1,0) AS HandHasAPair,
    If(Sum(ComboIsPair)=2,1,0) AS HandHasTwoPairs,
    Sum(ComboIsThreeOfAKind) AS HandHasThreeOfAKind,
    Sum(ComboIsFourOfAKind) AS HandHasFourOfAKind
RESIDENT IdentifyCombos
GROUP BY HandNo;   

/* --- Build table to store a single dimension with simulation outcomes */
Outcomes:
LOAD 
	'Pair' AS Outcome,
    Sum(HandHasAPair) AS Count
RESIDENT EvaluateCombos;

LOAD 
	'Two Pairs' AS Outcome,
    Sum(HandHasTwoPairs) AS Count
RESIDENT EvaluateCombos;

LOAD 
	'Three of a Kind' AS Outcome,
    Sum(HandHasThreeOfAKind) AS Count
RESIDENT EvaluateCombos;

LOAD 
	'Flush' AS Outcome,
    Sum(HandHasAFlush) AS Count
RESIDENT IdentifyFlush;

LOAD 
	'Full House' AS Outcome,
    Sum(HandHasAFullHouse) AS Count
RESIDENT EvaluateCombos;

LOAD 
	'Four of a Kind' AS Outcome,
    Sum(HandHasFourOfAKind) AS Count
RESIDENT EvaluateCombos;

```    


**SAMPLE DATA**  
crtl + 0 + 0  
3 TABLES WILL APPEAR: Characters, ASCII and Transactions

```sql
/*
Generate 26 rows with 2 columns. 
RecNo and autogenerate will create the 26 letters of alphabet with ord, that brings the char number of a string.
ord() =  retorna o número de ponto do código Unicode do primeiro caractere da string de entrada
*/
Characters:
Load Chr(RecNo()+Ord('A')-1) as Alpha, RecNo() as Num autogenerate 26;
 
ASCII:
Load 
 if(RecNo()>=65 and RecNo()<=90,RecNo()-64) as Num,
 Chr(RecNo()) as AsciiAlpha, 
 RecNo() as AsciiNum
autogenerate 255
 Where (RecNo()>=32 and RecNo()<=126) or RecNo()>=160 ;

/*
In the first load, it creates lines with autogenarate until the while conditions meet.
In the preceeding load, it will use tha field to create new calculations.  
mod = modular  
dim1 = multiply field rand 1 by 3, round up with ceil, then use pick to match the number with a character in the list.  
The number that multiplies rand must be the same as number or character in the list
*/ 
Transactions:
Load
 TransLineID, 
 TransID,
 mod(TransID,26)+1 as Num,
 Pick(Ceil(3*Rand1),'A','B','C') as Dim1,
 Pick(Ceil(6*Rand1),'a','b','c','d','e','f') as Dim2,
 Pick(Ceil(3*Rand()),'X','Y','Z') as Dim3,
 Round(1000*Rand()*Rand()*Rand1) as Expression1,
 Round(  10*Rand()*Rand()*Rand1) as Expression2,
 Round(Rand()*Rand1,0.00001) as Expression3;
Load 
 Rand() as Rand1,
 IterNo() as TransLineID,
 RecNo() as TransID
Autogenerate 1000
 While Rand()<=0.5 or IterNo()=1;

 Comment Field Dim1 With "This is a field comment";
 ```  

 **REPLACING NULLS**  
 It is the - that appears in the front end or tables;  
 it is not the same as zero or blank. Nulls cannot be selected.  
 * you can set NullDisplay as a value and replace the dashes if data comes from ODBC;   
 ```sql
 SET NullDisplay = 'Null';   
```

 * isNull = for non ODBC, you can use an IF statement  
 ```sql
 IF(IsNull(age), 'Null', age) as Age; 
```  

* NullAsValue  
Can also be used to set a field where nulls will be replaced:  
 ```sql
 NullAsValue Age;  
 SET NullValue = 'Null';   
 ....  
 NullAsNull *; 
```      

### 5. CrossTable and Generic Loads  
**CROSS TABLE**   

CrossTable (attribute field name, datafield name, qualifier number)    
* Attibute field name = name of the columns that were header and will turn into a single column  
* Data field name = name of the column for the data of the many columns header that will also turn into a single column  
* qualifier number = number of columns that will be kept. in this case, only the artist column;  

```sql
CrossTable (Decade, #sold, 1)
sql select *
FROM tablename;
```

 <p align="center">
<img width="450" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/CrossTable.PNG">
</p>   

**FOR EACH NEXT**  

For each x in the list, it will get subfield by getting from '$(x)' values (the list), looking for the separator ' ' (space) and selecting the second string (tie, sweater and pants), will transform into var y.
```SQL
FOR EACH x IN 'red sweater', 'green tie', 'white pants'  
LET y = SubField('$(x)', ' ', 2);   
TRACE $(y);  
NEXT     
```  

**GENERIC DATABASE**    

Generic load is used whe you have a table with information or attributes from different type of objects, that not necessarily share the same attributes.  
We would need to make a select disctint of every object and its attributes, then concatenate it into a single table.  
But qlik offers the generic load.  

```sql
MyTable:  
Generic  
LOAD   
    Object,  
    "Attribute", 
    Value  
FROM <data source>;
```  

 <p align="center">
<img width="400" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Generic%20Load.JPG">
</p>  

## PART 7  
### 1 - Introduction to Big Data   

<p align="center">
<img width="750" height="400"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Introduction%20to%20big%20data%201.JPG">
</p>

**Pitfalls and Challenges:**    
What to look for?  
Do you have all relevant data?  
What is the quality of the data?  
Does correlation equal casuality?  
Is the sample representing reality?  
Does more data equal more value?    

**Technical Chanllenges**  
Capacity of precessing is a big deal in big amounts of data due to memory process limitations. In order to handle it, there are few methods used. a Split - Apply - Combine Strategy to process is used. but joining them adds a complexity.  

**DataBase Storage**   
Structured data. Usually cannot handle unstructured data. Difficult to keep up with many cocurrent transactions. SQL joins create a lot of overhead and memory use.    
to handle bigdata amount, NoSQL were created.  

**Qlik Big Data Methodologies**  
Qlik uses many technologies to handle big data, but this may not fit all purposes due to complexity, many method can be combined to fit a solution.     
A few methods are: in-memory processing, data segmentation, Chaining, ODAG on demand app generation,  Direct Discovery.  

<p align="center">
<img width="750" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Introduction%20to%20big%20data%202.JPG">
</p>    

### 2 - Access MongoDB Using the Qlik Web Connector  
**CONNECTING TO RELATIONAL DATABASE**  
* In order to connect Qlik with relational database, it is needed a OLE DB or ODBC driver in order to comunicate the Query Language Processor from DBMS Engine DataBase to Qlik Engine.      

<p align="center">
<img width="750" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Connecting%20to%20Relational%20DataBase.JPG">
</p>    

* To connect to a NoSQL DB or MongoDB, the interface is a JSON connector which connect to the Qlik Web Connectors packages, to handle the communications with Mongo  

<p align="center">
<img width="750" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Connecting%20to%20NoSQL%20DataBase.JPG">
</p>        

**DATA ORGANIZATION IS NoSQL**  
* Collections: Are sort of tables in Relational DB ;
* Documents: Are sort of records or rows in Relational DB  ;
* Similarly to a Relational DB, you go to your DB (same icon), press right and create you collection (like a table); 
* After, clik in your collection and add a document. Copy and paste a json file content;    
* Then, create the qlik web connector (need to buy), then add the collection, and then copy the load script generated by converting no sql to qlik script language;  
* Go to qlik, paste the script generated, create the mongo db connection: go add connection, web connector, paste the url generated in the qlik script;  
* Delete the URL on qlik script, and replace for [lib://ConnectionName];  

**REVIEW**  

<p align="center">
<img width="500" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Connecting%20to%20NoSQL%20DataBase%20Review.JPG">
</p>    

### 3 - Direct Discovery   

**WHAT IS IT?**  
Direct Discovery is a hybrid method that combines IN-MEMORY DATA and DIRECT QUERIES to DB and it is part of the Big Data Strategy adopted by qlik to handle big data;  
Can also be used to retrieve real time or nearly real time data with direct discovery; 

**HOW IT WORKS**   
Instead of loading all data to qlik server in memory service, only the dimensions are loaded fully, and the measures, expressions and other fields have only metada data loaded;  
When user open the app or make a selection, the in-memory data is loaded to RAM and a query is sent to the data source and the retrieve the data that was only a metada and also brings to RAM;    
The standard SQL query language used is ANSI SQL, but can also be used terada,MySql and other types os SQL;   

**USE CASES**  
* Data cannot fit in-memory methods;  
* Data would take too long to load in memory;  
* Only interested in aggregated results;  
* Near-real_time analysis needed;  
* Dimension data is limited and relative static:  
    Ex: want to know the avg call duration of 3 regions in a call center. only 3 dimensions of regions will b loaded to in-memory. But milions of lines of call durations will be in DB, only retrieved when needed.  

**SYNTAX COMPARISON**  
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/Direct%20Discovery%20Syntax%20comparison.JPG">
</p>  

* Dimension: Under dimension you place all dimensions you want to be loaded in the app qvd;  
* NATIVE: you can use the native keyword to load that field directly from datasource;  
* Measure: Under keasure you place the field you will retrieve from data source. fields on measure can only be seen in aggregated functions in charts (sum, count, min...), only the metada will be loaded to datamodel;      
* Detail:  Only metadata will be loaded. this data will appear only when user make a selection;  
* You can change the limit of rows in a table at a time by seting it:  

```sql  
SET DirectTableBoxListThreshold = 100000;  
```  
  
**CONSIDERATIONS**  
* The less is the values in the threshold, faster is the load;  
* ` back quote is not allowed;  
* Section access is suported;  
* Joins can be used if the cardinality of the key is low;  
* In memory is usually faster,   
* Can recalculate records without reloading;    

### 4 - ODAG - on demand app genaration    
**WHAT?**  
* App with only aggregate data triggers creation of another app with detail data;  
* Selection in the aggregate data filter deatail data in generated app;  
* Used when all data don't fit in memory, or it would too slow to near real time data;    
* Can ensure optimized user experience;  
* Can combine to meet different use cases;  
* Vary in deployment complexity;    

**HOW?**  
* Two apps are created: one with the template you want to generate with filtered data, and the overview app with aggr data where you will make a selection to decrease number of data and geenrate the ODAG app;  
* You can set a goal to be able to genetate an ODAG app. ex: selection made on overview app must not have more than 50 products;  
* After making the selction on overview app, you enable the ODAG button and can the generate a new ODAG app based on the template app;    
* This works basically by dynamic filtering the source data with where clauses coming from selection; 

**STEPS**  
1. Configure QMC with ODAG service;  
2. Develop traditional load script and UI = TEMPLATE APP;   
3. Add dynamic scrip to capture filters from selction app;  
4. Develop Traditional load script and UI for the Selection app;  
5. Add and configure the on-demand app navigation link;  

**EXAMPLE**  
1. QMC > Enable on Demand > set number of apps, purge time...
2. Create a new app > sales detaisl > create data model normally;  
3. Example: you have InterSales table, and this one will be the selection app, when you add the other tables, you can filter with where clause according to the keyfiled of the table that will make the selection. Thus, when you make a selection in the internetSales table, on the other tables (ODAG) it will show only the fields assossieted with the selection.    
4. Create the selection app as usual;  
5. on the templae app, create the dynamic data where will be the ODAG script;    
6. Paste the generic script in the app section;  

```sql   
// DO NOT ALTER THIS SUBROUTINE  
/*
this is extend QVD where sub routine which receive the values list from ODAG from app navigation object and contain the selections made on the selection app. 
doesn't need modification
*/
SUB ExtendQVDWhere(Name, ValVarName)
  LET T = Name & '_COLNAME';
  LET ColName = $(T);
  LET Values = $(ValVarName);
  IF Len(Values) > 0 THEN
        IF Len(WHERE_PART) > 0 THEN
        LET WHERE_PART = '$(WHERE_PART) AND Mixmatch([$(ColName)],$(Values) )';
    ELSE
        LET WHERE_PART = ' WHERE Mixmatch([$(ColName)],$(Values))';
    ENDIF
  ENDIF
END SUB;

//---------------------------------------------------
/*
Same as before, but for sql subroutine. Because IN cannot be used in QVD.
*/
// // DO NOT ALTER THIS SUBROUTINE
// SUB ExtendSQLWhere(Name, ValVarName)
//   LET T = Name & '_COLNAME';
//   LET ColName = $(T);
//   LET Values = $(ValVarName);
//   IF Len(Values) > 0 THEN
//   	IF Len(WHERE_PART) > 0 THEN
//     	LET WHERE_PART = '$(WHERE_PART) AND $(ColName) IN ( $(Values) )';
//     ELSE
//     	LET WHERE_PART = ' WHERE $(ColName) IN ( $(Values) )';
//     ENDIF
//   ENDIF
// END SUB;

//---------------------------------------------------
/*
This create the set of values that will be inserted in the dynamic where clauses. This will concatene necessáry field and place it into a inline table that will be loaded, for passing the dynamic values. 
DONT NEED MODIFICATION
*/
// DO NOT ALTER THIS SUBROUTINE
SUB BuildValueList(VarName, TableName, ColName, QuoteChrNum)
  IF ($(QuoteChrNum) = 0) THEN
    LET LOADEXPR = 'Concat($(ColName),' & Chr(39) & ',' & Chr(39) & ') AS CombinedData';
  ELSE
    LET CHREXPR = ' Chr(' & '$(QuoteChrNum)' & ') ';
    LET LOADEXPR = 'Concat( $(CHREXPR) & $(ColName) & $(CHREXPR)' & ',' & Chr(39) & ',' & Chr(39) & ') AS CombinedData';
  ENDIF
  _TempTable:
  LOAD $(LOADEXPR) Resident $(TableName);
  LET vNoOfRows = NoOfRows('_TempTable');
  IF $(vNoOfRows)> 0 THEN
    LET $(VarName) = Peek('CombinedData',0,'_TempTable');
  ENDIF
  DROP TABLE _TempTable;
  DROP TABLE '$(TableName)';
END SUB;

/*
// CHANGE #1: Update these blocks of INLINE table loads to correspond to the names of the fields from your
//           selections app.  The contents inside the $() in the record body of the INLINE load statements
//           must match the names of the fields from your selections app that the user makes selections on.
//           If the database column name (or QVD field name) for any of the selection fields has a different
//           name, you need to alter the right hand side of the SET xxxx_COLNAME statement to reflect that
//		     field's corresponding database column (or QVD field) name;
//   
//            All fields for On Demand are prefixed with od and the following to indicate selected or associated
//            values
//              ods = Selected values
//              odo  = Associated values
//              odso = Selected/associated values
//
//
*/


//---------------------------------------------------
/*
HERE THERE MODIFICATIONS  
<YourField> = keyfield used in the where clause in from the fact table, the one used in the select app  
<AnotherField> = change for the second value used in the where clause in a table
*/
SET <YourField> ='';
OdagBinding:
LOAD * INLINE [
VAL
$(odo_<YourField>){"quote": "", "delimiter": ""}
];
SET <YourField>_COLNAME='<YourField>';
CALL BuildValueList('<YourField>', 'OdagBinding', 'VAL', 39);		// 39 is for single quote wrapping values

// Assuming there are two fields for selections, the section above is repeated below for the second field 

SET <AnotherField> ='';
OdagBinding:
LOAD * INLINE [
VAL
$(odo_<AnotherField>){"quote": "", "delimiter": ""}
];
SET <AnotherField>_COLNAME='<AnotherField>';
CALL BuildValueList('<AnotherField>', 'OdagBinding', 'VAL', 39);		// 39 is for single quote wrapping values ='';  

//---------------------------------------------------

/*// CHANGE #2:  Alter this with a leading 'WHERE <condition>' if you want your SQL statement (below)
//             to have a non-changing WHERE clause in addition to the clauses that will be inserted
//             by the selection app (it is fine to leave it as is).
*/  

SET WHERE_PART = '';

//---------------------------------------------------
/*
// CHANGE #3: Update the list of field names here to reflect each of the field names variables you have on the
//           left hand side (assignment target) of the first SET statement of the SET statement pairs in change
//           1 above. Note that in this case we're using ExtendQVDWhere which uses Qlik's Mixmatch to build a 
//           WHERE clause to test whether the inbound records match the conditions.  If your LOAD statement
//           in which WHERE_PART is applied is querying a SQL database, use the 'ExtendSQLWhere' subroutine
//           instead (and, of course, don't forget to include your database CONNECT statement).

// Assumes there are two fields for selections
*/  
  
/*
HERE THERE MODIFICATIONS   
Fill same for '<YourField>', '<AnotherField>'  
<NameOfFolderDataConnection> = folder created and admin  
<NameQVDFile> = qvd needed for this 
*/

FOR EACH fldname IN '<YourField>', '<AnotherField>'
  LET vallist = $(fldname);
  WHEN (IsNull(vallist)) LET vallist = '';
  IF Len(vallist) > 0 THEN
    CALL ExtendQVDWhere('$(fldname)','vallist');
  ENDIF
NEXT fldname

TRACE Generated WHERE clause: ;
TRACE $(WHERE_PART);

LET FOLDER='lib://<NameOfFolderDataConnection>';
LET FACT_QVD='[$(FOLDER)/<NameQVDFile>.qvd] (qvd)';
  

//---------------------------------------------------
  /*

// CHANGE #4: Modify the list of columns (or QVD fields) you wish to load from your database table (or QVD)
//             but leave the the $(WHERE_PART) portion of SQL (or LOAD) statement alone at the end.
//             
//             Note that you can have more than one of these dynamiclly alterered SELECT (or LOAD) statements
//             by replicating the sections from CHANGE #2 thru this change #4 and customize which WHERE clauses
//             will be inserted by altering the list of fields in the FOR EACH statement in Change #3.
  

Go to your template app and change the from statement in the fact table (the one you choose to have the key field used in other where filter) to: 
*/ 

FROM $(FACT_QVD)  
$(WHERE_PART);

```    

7. Create the selection app with only the aggregated fields. comment out all fields not important to have the necessary fields to reduce memory used and increse perfrmance;  
8. In the fact table, create the aggregated sums, count,  year, month, day.... and the fields used in the where exist clauses, use to group by the aggregations and the other date fields created.;    
9. Create the UI of the selection app;  
10. Go to "App Navigation Link" > Create a new > NAme > select template app > Place the expression to be calculated the threshild values > set the threshold max values ex: max o 50 distinct products > set max number of ODAG apps > set retention time > default view select > select where the generated apps will be stored or not;  
11. Drga the link navigation to the bottom of the select app;  
  
**REVIEW**
<p align="center">
<img width="480" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/ODAG%20Review.JPG">
</p> 











































