# hotel_revenue_project

#Indentify The Stakeholders Query---

1).There is a need to know if hotel revenue is growing year over year in both types of hotels, as well as segmenting the revenue by type of hotel.

2).Is there a trend in guests driving their own cars, and should our parking lot be expanded?

#COLLECT RAW DATA SET---

Data was downloaded from Kaggle for this project.

#UPPLOAD DATA IN SQL DATABASE

#DATA ANALYSIS USING SQL---

First we need to join all year-wise table as one ---

with hotels as (
select * from dbo.['2018$']
union
select * from dbo.['2019$']
union
select * from dbo.['2020$'])

select*from hotels


Now Left Join All Hotels table with meal_cost$ and market_segment$ table---

with hotels as (
select * from dbo.['2018$']
union
select * from dbo.['2019$']
union
select * from dbo.['2020$'])

select*from hotels
left join dbo.market_segment$
on hotels.market_segment = market_segment$.market_segment 
left join dbo.meal_cost$
on meal_cost$.meal = hotels.meal


#NOW ANALYSIS IN POWER BI

First connect sql server with power bi 
then write above sql query in power bi during connecting sql server 

#HOTEL REVENUE TREND-----
Now create a custom coloumn as Revenue---
Custom Column formula = ([stays_in_week_nights] + [stays_in_weekend_nights])*([adr]*[1-Discount]) 

Create a custom field for total nights---
Total Nights = sum(stays_in_week_nights + stays_in_weekend_nights)

#TREND IN GUEST WITH PERSONAL CARS---
For this we need parking percentage with total nights

NOW WRITE A QUERY IN POWER BI DAX FOR ANALYSING PARKING TREND--
Parking Percentage = SUM[required_car_parking_spaces]/[Total Nights]


#RESULT FROM INTERPRETATING ABOVE TREND-----

1).Hotel Revenue is growing year over year in both types of hotels.

2).There is no need to Expand the Parking lot.

