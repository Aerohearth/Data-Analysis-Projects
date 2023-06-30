# Google Data Analytics Capstone: Cyclistic Case Study
Course: [Coursera Google Data Analytics](https://www.coursera.org/professional-certificates/google-data-analytics#outcomes)

## Intro
In this case study, I will perform many real-world tasks of a junior data analyst. I will work for a fictional company, Cyclistic. In order to
answer the key business questions, I will follow the steps of the data analysis process: ask, prepare, process, analyze,
share, and act.

## Quick links

Data Source: [divvy-tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html)

[Data Cleaning Queries](https://github.com/Aerohearth/Data-Analysis-Projects/blob/main/Data%20Cleaning)

[Data Exploration Queries](https://github.com/Aerohearth/Data-Analysis-Projects/blob/main/Data%20Cleaning)

## Background

In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that
are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and
returned to any other station in the system anytime.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments.
One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes,
and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers
who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the
pricing flexibility helps Cyclistic attract more customers, Moreno (the director of marketing a.k.a my manager) believes that maximizing the number of annual members will
be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a
very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic
program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to
do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why
casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are
interested in analyzing the Cyclistic historical bike trip data to identify trends.

## Ask

### Business task: 
Design marketing strategies aimed at converting casual riders into annual members

### Guiding Questions:

Three questions will guide the future marketing program:
1. How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclistic use digital media to influence casual riders to become members?

Moreno has assigned me the first question to answer: How do annual members and casual riders use Cyclistic bikes
differently?

## Prepare

### Data Source:
I will be using Cyclistic’s most recent historical trip data to analyze and identify trends. The data ranges from the second quarter of 2019 to the first quarter of 2020 as we want to use the most recent data over the timespan of a year available to us. You can view the data at [divvy-tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html), The data has been made available by Motivate International Inc. under this [license](https://ride.divvybikes.com/data-license-agreement).

This is public data that you can use to explore how different customer types are
using Cyclistic bikes. But note that data-privacy issues prohibit you from using riders’ personally identifiable information. This
means that you won’t be able to connect pass purchases to credit card numbers to determine if casual riders live in the
Cyclistic service area or if they have purchased multiple single passes.

### Data Organization:
There are 4 files each named and seperated by year and quarter Divvy_Trips_YYYY_Q# and each file contains rider information for the entire quarter, such as ride id, bike type, start time, end time, start station, end station, start location, end location, and whether the rider is a member or not. The corresponding column names are ride_id, rideable_type, started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng and member_casual.

## Process

### Tools:

R - for cleaning and analysis

Tableau - for visualization

### Data Cleaning:

[Queries](https://github.com/Aerohearth/Data-Analysis-Projects/blob/main/Data%20Cleaning)

I format and combine all the data into one dataset labeling it under all_trips_v2. After, I create columns detailing the date, day, month, year, day of the week, and ride_length to add more keys I can analyze my data by.

### Data Exploration:

I take the data and start to take stabs at the data starting with the summary, trying to find any differences between casual and member riders. Next I aggregated the data between ride length and member status to get a general overview of how the casual and member riders comapre to each other. Next I decided to seperate the data by member status and the day of the week it was to get an accurate representation of the mean ride length between casual and member riders throughout the week.

### Data Analysis


