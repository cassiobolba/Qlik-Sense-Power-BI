# DATE ISLAND
## Dealing with multiple dates from multiples tables
Recently, I faced a situation of having to build a star schema where there were 5 tables containing dates, and I needed to be able to make a selection by date for whole model.
Usually for one or 2 calendars, you can use the famous **MASTER CALENDAR**. But if you create 5  master calendars:  
* it will not allow you to cross data check,  
* The code will be very confusing for others,  
* You will have a worse performance on script loading.  
  
HOW TO SOLVE: **DATA ISLAND**    
  
### CREATE YOUR DATA SCHEMA  
I created a nearly star schema:  
<p align="center">
  <img width="600" height="450" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Date%20Island/Data%20Model%20-%20Car%20Web.JPG">
</p>  

### STANDARIZE THE DATA FORMAT   
You need to make sure all dates are in the same format:  
``` sql
    Date(DataCompra, 'D/M/YYYY') as DataCompra,
```  
``` sql
    Date(DataMeta, 'D/M/YYYY') as DataMeta,
```  
``` sql
	Date(DataVenda, 'D/M/YYYY') as DataVenda,
```  
``` sql
    Date(VideoData, 'D/M/YYYY') as VideoData,
``` 
``` sql
    Date(FBData, 'D/M/YYYY') as FBData,
```    
  
### CREATE THE CALENDAR FOR THE DATE ISLAND  
The calendar for Date Island can be pretty much the same you are used to use for your single master calendar. The only diference is that your date field from the final calendar should have **NO RELATIONSHIP** with any table. Like the name suggest, the calendar table will be an island isolated.  
``` sql
/* CALENDARIO ISOLADO - USAR EXPRESSAO DE COMPARACAO */
Temp:  
Load  
min(Date(DataVenda,'D/M/YYYY')) as minDate,  
max(Date(DataVenda,'D/M/YYYY')) as maxDate  
Resident Fato_Vendas;  
      
Let varMinDate = Num(Peek('minDate', 0, 'Temp'));  
Let varMaxDate = Num(Peek('maxDate', 0, 'Temp'));  
DROP Table Temp;  

      
TempCalendar:  
LOAD  
$(varMinDate) + Iterno()-1 As Num,  
Date($(varMinDate) + IterNo() - 1) as TempDate  
AutoGenerate 1 While $(varMinDate) + IterNo() -1 <= $(varMaxDate);  
      
Data_Island:  
Load  
  Date(TempDate, 'D/M/YYYY') AS Data,  
  week(TempDate) As WeekN, 
  WeekDay(TempDate) as WeekDay,
  date(today()-7) as pastweek,
  Year(TempDate) As Year,  
  Month(TempDate) As Month, 
  MonthName(TempDate) as MonthName, 
  Day(TempDate) As Day,    
  Week(weekstart(TempDate)) & '-' & WeekYear(TempDate) as WeekYear    
Resident TempCalendar  
Order By TempDate ASC;  
Drop Table TempCalendar;  
```   
You see that my field 'Data' on the final calendar is deferent from the others date field names. So, no relation.  

### FRONT END EXPRESSION  
Now, to use your date calendar in any of the 5 tables, you need just to add an IF condition to the calculations if you want to use the same date filter for the tables.    
Let's say you want to calculate sum of something and then filter it in a filter panel later, you should use the following expression:
```sql
(Sum(if(DataVenda=Data,Total_Vendas))
```  
This is needed to compare the data from the table with the data from data island.
