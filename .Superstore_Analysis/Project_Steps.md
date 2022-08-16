
# Supersote Data Analysis
Stores keep records of their data in databases to keep track of things such as inventory, sales, profits and losses. Flip Beans is a fictual company which speacilizes in the sale of goods and products in three categories, Tech devices, furniture and office supplies. 
The marketing department wants to find insights from their orders dataset for the past four years to base their upcoming advertising campigns on. 

## Data and License

The data used in the analysis was downloaded from [Kaggle](https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting) under the license [GPL 2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.en.html)



## Data Cleaning 
The data was loaded to Google Sheets,  https://docs.google.com/spreadsheets/d/1mZWCBlB2zQ4JMgs_MLd8GmOlM-I9_gDVyvLsqJfl8S4/edit?usp=sharing  
The following steps were followed in data cleaning:  
### Overall Study of the data
The data had 18 columns. On closer inspection, I only needed about 10 columns so I hid the unneccessary columns. Secondly, I removed the one duplicate row that was in the dataset to remain with 9799 unique rows.  
### Fixing Data Formats  
Since the data was in CSV format on download, on uploading to Sheets, the format was greatly affected. I adjusted column data types to the right data types such as dates to DMY from MDY
### Data Manipulation for Use in the Analysis
#### Data Validation
##### First Validation
I validated the orders by year to ensure they matched the number of orders per category  
```Furniture Orders per Year
=COUNTIFS(sales_clean!$D:$D,"2015",sales_clean!$R:$R,"furniture")
=COUNTIFS(sales_clean!$D:$D,"2016",sales_clean!$R:$R,"furniture")
=COUNTIFS(sales_clean!$D:$D,2017,sales_clean!$R:$R,"furniture")
=COUNTIFS(sales_clean!$D:$D,"2018",sales_clean!$R:$R,"furniture")
=SUM(E4,F4,G4,H4)
```
```Office Supplies Orders per Year
=COUNTIFS(sales_clean!$D:$D,"2015",sales_clean!$R:$R,"office supplies")
=COUNTIFS(sales_clean!$D:$D,"2016",sales_clean!$R:$R,"office supplies")
=COUNTIFS(sales_clean!$D:$D,"2017",sales_clean!$R:$R,"office supplies")
=COUNTIFS(sales_clean!$D:$D,"2018",sales_clean!$R:$R,"office supplies")
=SUM(E5,F5,G5,H5)
```
```Tech Devices Orders per Year
=COUNTIFS(sales_clean!$D:$D,"2015",sales_clean!$R:$R,"technology")
=COUNTIFS(sales_clean!$D:$D,"2016",sales_clean!$R:$R,"technology")
=COUNTIFS(sales_clean!$D:$D,"2017",sales_clean!$R:$R,"technology")
=COUNTIFS(sales_clean!$D:$D,"2018",sales_clean!$R:$R,"technology")
=SUM(E6,F6,G6,H6)
```
##### Second Validation
I validated the data by matching the number of orders by category to orders by product ID as follows:  
```Rule One
=COUNTIF(sales_clean!R:R,"furniture")
=COUNTIF(sales_clean!R:R,"office supplies")
=COUNTIF(sales_clean!R:R,"technology")
```
```Rule Two
=COUNTIF(sales_clean!Q:Q,"*fur*")
=COUNTIF(sales_clean!Q:Q,"*off*")
=COUNTIF(sales_clean!Q:Q,"*tec*")
```



## Data Analysis
Most of the analysis was conducted by the use of pivot tables to aggregate the data as follows:  
### Pivot Tables
#### Orders per Segment 
https://docs.google.com/spreadsheets/d/1mZWCBlB2zQ4JMgs_MLd8GmOlM-I9_gDVyvLsqJfl8S4/edit#gid=187506054&range=A3:B7

#### Orders per Category
https://docs.google.com/spreadsheets/d/1mZWCBlB2zQ4JMgs_MLd8GmOlM-I9_gDVyvLsqJfl8S4/edit#gid=187506054&range=A10:B14
#### Orders per Shipment Mode
https://docs.google.com/spreadsheets/d/1mZWCBlB2zQ4JMgs_MLd8GmOlM-I9_gDVyvLsqJfl8S4/edit#gid=187506054&range=A17:B22
#### Orders per Region 
https://docs.google.com/spreadsheets/d/1mZWCBlB2zQ4JMgs_MLd8GmOlM-I9_gDVyvLsqJfl8S4/edit#gid=187506054&range=A25:B30  
#### Orders in Different States per Year
https://docs.google.com/spreadsheets/d/1mZWCBlB2zQ4JMgs_MLd8GmOlM-I9_gDVyvLsqJfl8S4/edit#gid=187506054&range=A32:F83
#### Sub-Category Orders
https://docs.google.com/spreadsheets/d/1mZWCBlB2zQ4JMgs_MLd8GmOlM-I9_gDVyvLsqJfl8S4/edit#gid=187506054&range=H45:I63  
### Key formulas used
#### Sorting Monthly Data
The monthly data in pivot tables was not aggregated from January to December. I used the following array formula to sort the issue for better visualization  
```
 =SORT(D18:H29,MONTH(D18:D29&1),1)
 // The formula sorts the range using the month column using January as the first month
```
#### Finding key data in pivot tables
To find the number of top orders from 2015 to 2018 I used the following formula:
```
=ArrayFormula(LARGE($B$34:$B$82,{1,2,3,4,5}))
// It returns the top five values in the specified column
//I then used the following formula to find the states with the values above
=INDEX($A$33:$A$82, MATCH(G33, $B$33:$B$82, 0))
```
## Data Visualization
After data analysis, I used the data in the sheet **"pivot_tables"** to create various visualization as shown in the sheet, https://docs.google.com/spreadsheets/d/1mZWCBlB2zQ4JMgs_MLd8GmOlM-I9_gDVyvLsqJfl8S4/edit#gid=847368584&range=1:1000



## Findings
After data analysis, I created a the following powerpoint to report my findings, https://docs.google.com/presentation/d/1pCnS5-xpF1z0NXSLlNwdSrlyL4-b6Jzwda-i5CVceus/edit?usp=sharing  
