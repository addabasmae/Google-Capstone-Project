# Cyclistic Bike-Share Analysis

## Project Brief
- Company activity: Cyclistic is a bike-sharing company that has a fleet of 5,824 bicycles geotracked and locked into a network of 692 stations across Chicago. These bikes can be unlocked from one station and returned to any other station in the system anytime. 
The company offers three flexibility pricing plans: Single-ride passes, full-day passes and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.
- Problem: Annual members are much more profitable than casual riders.
- Strategic goal: Maximizing the number of annual memberships by designing marketing strategies aimed at converting casual riders into annual members. 
- Key Stakeholders: Cyclistic executives, Marketing Director (Lily Moreno) and marketing analytics team.

## Business Task
- Business Task Statement: Understand how annual members and casual riders use Cyclistic bikes differently so targeted marketing strategies can be recommended for conversion.
- Guiding questions:
  -	How do casual riders and annual members differ in their usage patterns?
  -	What are the key differences in ride duration, time of day, and day of the week usage?
  -	Are there any preferences in bike types used by each group?
  -	What are the most popular locations for each group?

## Prepare Phase - Data Sources Description
-	The data is first-party collected directly from Cyclistic’s historical trip data, it is updated regularly, and the data source/license are available.
-	The data we will be working with is a public (open) data that is respecting privacy measures considering that we don’t have access to riders’ personally identifiable information. The company is making the data available under a license that allows us to access, reproduce, analyze, copy, modify and distribute the data.
-	For our analysis we are using 12 csv files, each of them includes monthly bike rides starting from December 2023 to November 2024.

## Process Phase – Cleaning and Manipulation of Data
We will be using R to clean and analyze the data as the datasets are too large and it will help us organize, modify and clean dataframes. The detailed processing and analysis code is documented in the attached R Markdown file “Cyclistic Bike-Share Analysis.Rmd”. 
Nevertheless, the main steps we followed are summarized below: 
-	Installing and loading required packages such as tidyverse, lubridate, janitor, etc.
-	Importing csv files by using read_csv and changing their names to make them more understandable. These files contain data regarding the monthly trips from 12-2023 to 11-2024.
-	Examining individual datasets using str() to display their structure and rowtotal() to identify the total rows of all tables combined.
-	Merging all 12 datasets into one dataframe called “Full_Year_df”
-	Examining the combined dataframe and checking for missing values, duplicates and invalid data types.
-	Examining patterns by rideable_type (classic bike, electric bike, electric scooter) and member_casual (casual, member).
-	Cleaning the dataframe by following these steps:
  -	Dropping station data columns as they are unreliable for station-based analysis.
  -	Excluding rows where "end_lat" or "end_lng" are NA to ensure accurate geospatial mapping.
  -	Removing duplicated rows based on ride_id to ensure each trip is unique and prevent skewed counts.
  -	Cleaning column names using clean_names() function to ensure consistency and compatibility.
-	Manipulating the dataframe by following these steps:
  -	Adding columns for: Date, Weekday, Day, Month, Year, Time, Hour and Ride Duration.
  -	Rounding `start_lat`, `start_lng`, `end_lat`, and `end_lng` to 4 decimal places for consistent mapping.
  -	Renaming the columns of “rideable_type” and “member_casual” to “bike_type” and “user_type” to improve clarity.
  -	Saving the cleaned dataset.

## Analyze Phase - Analysis Summary
After processing and cleaning the dataset, we will keep using R to calculate key metrics and identify patterns differentiating casual riders and annual members. This supports our business task of enhancing membership conversion strategies. The main steps in our analysis are outlined below: 
-	Calculating the total rides and user type breakdown including rides count and percentage.
-	Calculating the overall average ride duration as well duration statistics by user type. These include average, median, minimum and maximum durations. 
-	Investigating outliers and anomalies: To ensure our duration findings accurately reflect typical behavior, an analysis of ride duration outliers (rides > 120 minutes & rides < 1 minute) was conducted.
-	Analyzing time-based trends in bike usage by calculating the ride count per user type by month, weekday and hour.
-	Comparing bike type preferences across user types by calculating total rides and the average ride duration per bike type and user type. 
-	Conducting a geospatial analysis to identify usage patterns:
  -	Identifying activity hotspots (Start & End Points).
  -	Identifying temporal trends within geospatial hotspots by defining peak weekdays and hours in top hotspots and determining the major hotspots during peak days and hours.
  -	Exporting key analysis outputs as CSV files for Tableau visualizations.

## Share Phase - Supporting Visualizations
Based on our data analysis, we will use Tableau for our visualizations to create interactive maps, charts, and dashboards that highlight usage patterns and support membership conversion strategies.

The final dashboard is published in Tableau public (Link: “https://public.tableau.com/app/profile/asmae.addab/viz/GoogleCapstoneProject_CyclisticBike-ShareAnalysis/Dashboard3")


## Project Recommendations
-	Boost Member Conversion: Target casual riders in weekend/leisure hotspots with promotions and trial memberships to encourage annual subscriptions.
-	Optimize Bike Allocation:  Prioritize electric bike availability at casual hotspots on weekends and member hotspots on weekdays.
-	Seasonal & Location-Based Campaigns: Run promotions during spring/summer and near high-traffic recreational areas to maximize casual rider engagement.
-	Enhance System Reliability: Strengthen docking station maintenance to prevent short and long rides and ensure reliability at high-traffic hotspots for both user types.
-	Tailor Engagement by User Behavior: Send personalized offers to members for weekday commutes and to casual riders for weekend leisure trips, aligned with peak hours.
-	Plan for Growth & Maintenance: Use hotspot and duration trends to guide station placement, bike type distribution, and maintenance scheduling.




  
  


