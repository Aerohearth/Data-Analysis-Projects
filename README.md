# Google Data Analytics Capstone: Cyclistic Case Study
Course: [Coursera Google Data Analytics](https://www.coursera.org/professional-certificates/google-data-analytics#outcomes)

## Intro
In this case study, I will perform many real-world tasks of a junior data analyst. I will work for a fictional company, Cyclistic. In order to
answer the key business questions, I will follow the steps of the data analysis process: ask, prepare, process, analyze,
share, and act.

## Quick links

Data Source: divvy-tripdata // Add links & any

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

### Data Cleaning

1. Before anything else we install and library our core packages

  install.packages("tidyverse")

  library(tidyverse)

2. Next we import our data sets into Rstudio so we can clean them up

q2_2019 <- read_csv("Divvy_Trips_2019_Q2.csv")

q3_2019 <- read_csv("Divvy_Trips_2019_Q3.csv")

q4_2019 <- read_csv("Divvy_Trips_2019_Q4.csv")

q1_2020 <- read_csv("Divvy_Trips_2020_Q1.csv")

3. Before we start taking any jabs at our data we need to format all the data so we have an easier time navigating it. We will format it the same as the most recent dataset (q1_2020) as this will most likely be the format they will continue with):

q2_2019 <- rename(q2_2019, ride_id = "01 - Rental Details Rental ID", rideable_type = "01 - Rental Details Bike ID", started_at = "01 - Rental Details Local Start Time", ended_at = "01 - Rental Details Local End Time", start_station_name = "03 - Rental Start Station Name", start_station_id = "03 - Rental Start Station ID", end_station_name = "02 - Rental End Station Name", end_station_id = "02 - Rental End Station ID", member_casual = "User Type")

q3_2019 <- rename(q3_2019, ride_id = trip_id, rideable_type = bikeid, started_at = start_time, ended_at = end_time, start_station_name = from_station_name, start_station_id = from_station_id, end_station_name = to_station_name, end_station_id = to_station_id, member_casual = usertype)

q4_2019 <- rename(q4_2019, ride_id = trip_id, rideable_type = bikeid, started_at = start_time, ended_at = end_time, start_station_name = from_station_name, start_station_id = from_station_id, end_station_name = to_station_name, end_station_id = to_station_id, member_casual = usertype)

4. Next we ensure that each datasets column names match up to (q1_2020) and change any that don't:

colnames(q3_2019)

colnames(q4_2019)

colnames(q2_2019) 

colnames(q1_2020)

q2_2019 <- rename(q2_2019, ride_id = "01 - Rental Details Rental ID", rideable_type = "01 - Rental Details Bike ID", started_at = "01 - Rental Details Local Start Time", ended_at = "01 - Rental Details Local End Time", start_station_name = "03 - Rental Start Station Name", start_station_id = "03 - Rental Start Station ID", end_station_name = "02 - Rental End Station Name", end_station_id = "02 - Rental End Station ID", member_casual = "User Type")

q3_2019 <- rename(q3_2019, ride_id = trip_id, rideable_type = bikeid, started_at = start_time, ended_at = end_time, start_station_name = from_station_name, start_station_id = from_station_id, end_station_name = to_station_name, end_station_id = to_station_id, member_casual = usertype)

q4_2019 <- rename(q4_2019, ride_id = trip_id, rideable_type = bikeid, started_at = start_time, ended_at = end_time, start_station_name = from_station_name, start_station_id = from_station_id, end_station_name = to_station_name, end_station_id = to_station_id, member_casual = usertype)

5. After formating we check the data types of our columns to ensure that we can use the data together in our analysis

str(q2_2019)
str(q3_2019)
str(q4_2019)
str(q1_2020)

q4_2019 <-  mutate(q4_2019, ride_id = as.character(ride_id)
,rideable_type = as.character(rideable_type))

q3_2019 <-  mutate(q3_2019, ride_id = as.character(ride_id)
,rideable_type = as.character(rideable_type))

q2_2019 <-  mutate(q2_2019, ride_id = as.character(ride_id)
,rideable_type = as.character(rideable_type))

6. Finally we are able to combine all the data together:

all_trips <- bind_rows(q2_2019, q3_2019,q4_2019,q1_2020)

7. Next we remove and update any columns and align the column values that don't match up with (q1_2020):

all_trips <- all_trips %>%

select(-c(start_lat, start_lng, end_lat, end_lng, birthyear, gender, "01 - Rental Details Duration In Seconds Uncapped", "05 - Member Details Member Birthday Year", "Member Gender", "tripduration"))

all_trips <-  all_trips %>%

mutate(member_casual = recode(member_casual
,"Subscriber" = "member"
,"Customer" = "casual"))
