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
Power BI was used to create the line chart for this project. To calculate the moving average a measure was created for both the global and London moving average, this is a measure in Power BI using DAX. A moving average is helpful as it smooths out the temperature to give an overall snapshot of what happened to the temperature through the years without impact from short term fluctuations. The following DAX is how this was achieved for the global moving average, the London moving average used the same method:

![image](https://github.com/Hannahllmm/Data-Analyst-Nanodegree/assets/39679731/5c57e1f8-8310-4e4d-99ed-275a03a9c699)

This measure works by specifying the period for the moving average, in this case a 10 year period was used. Then for each data point Power BI calculates the minimum year and maximum year the average should be calculated between. The average temperatures between these years are then summed together to calculate the 10 year average at each data point.

## Graph and Analysis
![image](https://github.com/Hannahllmm/Data-Analyst-Nanodegree/assets/39679731/ff4ddd96-4175-4a11-aadc-da6983ccd356)

The most obvious difference between the temperature in London verses globally, is London’s temperature is consistently higher. Looking at the overall trends in London and globally, they are very similar, with dips in the temperature in 1816, 1845 and 1892. Looking at the dip in 1816 is interesting, this was known as “The Year With no Summer” hence the lower temperature. It’s clear however that this lower temperature was more severe globally than in London. Although the temperature did decrease in London during this period, it was not noticeably lower than other cooler years in London. For a while, globally the temperature has been steadily increasing, with this increase happening faster from 1975. In England however the increase in temperature has been less obvious, but from 1987 it has risen sharply, and faster than globally. 
