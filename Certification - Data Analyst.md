
**BOLD**
*italic*

`codigo inlinne`

```kotlin
````

# ROAD TO QLIK CERTIFICATION
Document referring to my studies regarding a certification exam I'm planning to take as Qlik Sense Business Analyst.
I created these categories according to the Qlik guide provided by the company to make your way through all topics covered by the examination.

**REFER TO MY SAMPLE APP ON THE FOLDER "STUDY TRACKER". THIS QLIK APP I CREATED TO HELP ME CONTROL AND INCREASE QUALITY OF MY STUDY PATH**

# SUMMARY CATEGORIES TO STUDY
The below sections are showing all steps to be studied to get Qlik certifications. After this section, all notes taken will be written in the same order as the summary and not in the order I studied. It is meant to make easier to track a specific topic.

## 1-Interpret Business Requirements
1.1 Identify KPIs, dimensions and measures  
1.2 Explain Qlik Sense features: smart search, responsive design, smart visualizations, etc. and how they impact app design  
1.3 Ask appropriate questions to understand the needs of the potential users of the Qlik Sense application  
1.4 Identify user types and their typical devices to use to access apps  
1.5 Explain the existence of APIs, extensions (such as Qlik GeoAnalytics), web mashups, widgets and where they might be used (i.e., NOT how to code them)    
1.6 Explain green-white-gray-light gray

## 2-Prepare Data for Application
2.1 Create a basic data model using Data Manager (e.g., spreadsheets, CSV, flat files, etc.)  
2.2 Explain synthetic keys and possible methods of resolution  
2.3 Create data connections  
2.4 Use smart data load  
2.5 Create connections to Qlik DataMarket  

## 3-Design the Application User Interface
3.1 Structure the application in Qlik Sense to provide coherent sheets and an overall flow matching the expectations of the user journey (DAR concept)  
3.2 Select object types appropriate for the required data analysis (e.g., a line chart to show a trend over time)  
3.3 Identify the proper expression to create the appropriate visualization to meet the business requirements  

## 4-Build the Application
4.1 Add dimensions, measures, and objects   
4.2 Create and use variables  
4.3 Use custom color in charts (e.g., Colormix, CSS colors, IF statements, etc.)  
4.4 Import extensions (e.g., from Branch)  
4.5 Create a story  
4.6 Create master items  
4.7 Apply filters and create bookmarks  
4.8 Use advanced functions like AGGR and Set Analysis

## 5-Deliver the Application
5.1 Perform basic tasks around making a production standard application (e.g., create a thumbnail image, appropriate title, etc.)  
5.2 Understand content-related QMC tasks (but not necessarily how to perform them): Manage Content Library, Publish and Unpublish apps, Import and Export apps

# -----------------------STUDIES REPORT---------------------- 

# 1-Interpret Business Requirements
## 1.1 Identify KPIs, dimensions and measures
### 1.1.1 

## 1.2 Explain Qlik Sense features: smart search, responsive design, smart visualizations, etc. and how they impact app design

## 1.3 Ask appropriate questions to understand the needs of the potential users of the Qlik Sense application

## 1.4 Identify user types and their typical devices to use to access apps

## 1.5 Explain the existence of APIs, extensions (such as Qlik GeoAnalytics), web mashups, widgets and where they might be used (i.e., NOT how to code them)

## 1.6 Explain green-white-gray-light gray

# 2-Prepare Data for Application
## 2.1 Create a basic data model using Data Manager (e.g., spreadsheets, CSV, flat files, etc.)
## 2.2 Explain synthetic keys and possible methods of resolution
## 2.3 Create data connections
## 2.4 Use smart data load
## 2.5 Create connections to Qlik DataMarket

# 3-Design the Application User Interface

## 3.1 Structure the application in Qlik Sense to provide coherent sheets and an overall flow matching the expectations of the user journey (DAR concept)
## 3.2 Select object types appropriate for the required data analysis (e.g., a line chart to show a trend over time)
### 3.2.1. Foundations of Building Visualizations  
<p align="center">
  <img width="600" height="500" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/goodchart-xlarge-1200x630.jpg">
</p>

**Bar Chart**= compareaggregated measures by the length or heigh of bars. (only supports 2 dimensions)    
**Combo Charts** = Compare 2 measures that occupy differente data ranges using bs, lines or markes  
**Line Chart** = Trends iver time mainly
**Scatter** = Discover Correlation, clusters, outliers based on 2 measures  
**Pie Charts** = PErcentage of contributions for small amount of data
**Geo maps** = Use to create sum of orders by map, and create list of customers, phone list...  
**Gauge/KPI** = Show how is the progress toward the goal
**Histogram** = Use to know the distribution (Only 1 measure and  1 dimension)  
**Tree plot** = Data distributoin divided in categories. EX = Distribution of salary per area,manager and position 
**Waterfall** = Used to know the influence a value in a total ex= influence of costs, shipping on total sales  (just measures)
**Box Plot** = Used manly to get outliers from the main distribution. ex= find out who have a salary much bigger than the mean.


## 3.3 Identify the proper expression to create the appropriate visualization to meet the business requirements

--

# 4-Build the Application
## 4.1 Add dimensions, measures, and objects
### 4.1.1. Understanding Dimensions and Measures
**Dimensions** = Quaifying attribute, qualitative. Group values to define visualization elemtns

**Measure** = Numeric value, quantitative. Values which are griuped by demensions and representes by the magnitude of vosualization elements

Depending on the visualization or analysys, you can mix multiples measures and dimensions in a chart, such as the example below.
<p align="center">
  <img width="600" height="500" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/4.1.1%20multiple%20Measures%20in%20a%20chart.JPG">
</p>
<p align="center">
  <img width="600" height="500" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/4.1.1%20multiple%20dimensions%20in%20a%20chart.JPG">
</p>

**Master Items** = can be a calculated measure, reusable, available even after publishing.  
Can be a drill down dimension.  
Calculations can be stored as a master measure to be used many times without needind to calculate again and again. EX: I can store the profit in a master measure:
```sql
sum(total_sales) - sum(total_cost) 
```
Later, I just need to call the profit master measure in a chart and not the whole calculation.  

**Alternative Dimension/Measures**= You add alternative measures that will be available to be switched and change the chart dimension. It is not like drill down. You have the option to choose the dimensions.  
<p align="center">
  <img width="600" height="450" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/3.2.1%20Alternative%20Dimensions%20and%20Measures.JPG">
</p>

**Dimensions and Measures x Chart Type
<p align="center">     
 <img width="600" height="450" src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/3.2.1%20Dimensions%20and%20Measures%20per%20chart%20type.JPG">
 </p>

## 4.2 Create and use variables
## 4.3 Use custom color in charts (e.g., Colormix, CSS colors, IF statements, etc.)
## 4.4 Import extensions (e.g., from Branch)
## 4.5 Create a story

## 4.6 Create master items
#### Why create master Items:  
-Master dimension or master measure values can be colored to represent custom color schemes.  
-Master dimensions can contain multiple fields organized in a drill-down group. 
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/4.6%20Master%20Items%20-%20Drill%20Down.JPG">
</p> 
-Master measures and dimensions can save expressions  

```sql
sum(total_sales) - sum(total_cost) 
```    
-Build and edit visualizations more efficiently using centralized assets.  
-Create an organized and well-named collection of reusable items for other user.  
-Define alternate states of selections to apply to specific visualizations. 
you can define an alternate selection for a chart.go:  
Mater Items > Alternate States > Just name it > Copy one Chart > drag the state to the copied chart > apply.  
now you can apply different selections for same charts and compare
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/4.6%20Master%20Items%20-%20Alternate%20Selections.JPG">
</p> 
<p align="center">
<img width="600" height="450"  src="https://github.com/cassiobolba/Qlik-Sense/blob/master/Images/4.6%20Master%20Items%20-%20Alternate%20Selections%202.JPG">
</p> 

**Three places to create Master Items:**   
Create master items from the Master items ( ) section in the Assets panel,  
Create master items from the Fields (     ) section in the Assets panel,  
Create master items from the Data model viewer (      ), Preview panel,  



## 4.7 Apply filters and create bookmarks
## 4.8 Use advanced functions like AGGR and Set Analysis

# 5-Deliver the Application
## 5.1 Perform basic tasks around making a production standard application (e.g., create a thumbnail image, appropriate title, etc.)
## 5.2 Understand content-related QMC tasks (but not necessarily how to perform them): Manage Content Library, Publish and Unpublish apps, Import and Export apps
 
 