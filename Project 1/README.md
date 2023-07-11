# Analysis of Global Temperature vs London

## Extracting Data
SQL was used to extract London’s yearly average temperature data from a database. This data was then joined to a table with global yearly average temperature. Having this data in a single table made analysis easier. The following SQL query was used to achieve this:

```sql
WITH london_data AS (
  	SELECT avg_temp london_avg_temp, year
	FROM city_data 
	WHERE city='London' AND country='United Kingdom')

SELECT *
FROM global_data
JOIN london_data ON
	global_data.year=london_data.year
```

## Calculating the Moving Average
Power BI was used to create the line chart for this project. To calculate the moving average a measure was created for both the global and London moving average, this is a calculated field in Power BI using DAX. A moving average is helpful as it smooths out the temperature to give an overall snapshot of what happened to the temperature through the years without impact from short term fluctuations. The following DAX is how this was achieved for the global moving average, the London moving average used the same method:

![image](https://github.com/Hannahllmm/Data-Analyst-Nanodegree/assets/39679731/5c57e1f8-8310-4e4d-99ed-275a03a9c699)


