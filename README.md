
# Hotel Revenue Project

Developing end-to-end data dashboards from database development, data extraction via SQL, and dashboard creation via POWER BI.

![hotelrevenue](https://user-images.githubusercontent.com/118931406/208079130-7bf26347-fe73-4e01-aa92-2e910eb4a987.gif)


## OBJECTIVE

- There is a need to know if hotel revenue is growing year over year in both types of hotels, as well as segmenting the revenue by type of hotel.

- Is there a trend in guests driving their own cars, and should our parking lot be expanded?
## Documentation

Raw Data was taken from Kaggle,
click on for- 
[Raw Data](https://www.kaggle.com/datasets/ferranindata/hotel-revenue-data-project)


## Required Skills

Language: SQL

Visualisation: Power BI

## Roadmap

- UPPLOAD DATA IN SQL DATABASE
- DATA ANALYSIS USING SQL
- ANALYSIS IN POWER BI
- DASHBOARD CREATION


## DATA ANALYSIS USING SQL

 Join all year-wise table as one table ---

    with hotels as 

    ( select * from dbo.['2018$'] union select * from dbo.['2019$'] union select * from dbo.['2020$'])

    select*from hotels

 Now Left Join All Hotels table with meal_cost$ and market_segment$ table---

    with hotels as 

    ( select * from dbo.['2018$'] union select * from dbo.['2019$'] union select * from dbo.['2020$'])

    select*from hotels 

    left join dbo.market_segment$ on hotels.market_segment = market_segment$.market_segment 
   
    left join dbo.meal_cost$ on meal_cost$.meal = hotels.meal


## ANALYSIS USING POWER BI

- Connect sql server with power bi


- create a custom coloumn as 

      Revenue = ([stays_in_week_nights] + [stays_in_weekend_nights])*([adr]*[1-Discount])

- Create a custom field in DAX as 

      Total Nights = sum(stays_in_week_nights + stays_in_weekend_nights)

      Parking Percentage = SUM[required_car_parking_spaces]/[Total Nights]
## INTERPRETATION FROM DASHBOARD

- Hotel Revenue is growing year over year in both types of hotels.

- There is no need to Expand the Parking lot.
