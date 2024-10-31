# cyclistic_bike-share-case-study-
A Case Study Project 

## Table of Content 
- [Project Overview](#project-overview)
- [Data Source](#data-source)
- [Tools](#tools)
- [Project Structure](#project-structure)
- [Data Analysis](#data-analysis)
- - [Data Visualiation](#data-visualization)
- [Results](#results)
- [Recommendations](#recommendations)
- [Limitations](#limitations)
## Project Overview 
  You are a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, your team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, your team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve your recommendations, so they must be backed up with compelling data insights and professional data visualizations.
## Data Source
  divy-tripdata
  https://divvy-tripdata.s3.amazonaws.com/index.html
## Tools
  jupyter notebook | Ms Excel 
## Project Structure
  Data
  - Data Collection
      ![image](https://github.com/user-attachments/assets/1af92dbf-bb7e-4eb5-98ab-59d422dfdcef)

  - Data Overview
    excel spread sheets was used in data overview to get he general understanding of the dataset
    ![image](https://github.com/user-attachments/assets/57e44063-04da-4111-a306-aab84269026e)
 
  - Data Transfromation
    
    jupyter note book is used to perform the data transformation because we are using python to analyse this dataset 
    python gives us a lot of flexibility when handling data
    ![image](https://github.com/user-attachments/assets/90460f10-0d6b-412a-a79c-08149a6e742e)
## Data Analysis 
  jupyter note book is used to perform the data anlysis because we are using python to analyse this dataset 
  python gives us a lot of flexibility when handling data.
  
  ![image](https://github.com/user-attachments/assets/e98754df-9f83-4059-9489-fb035209d470)
  
  in the image we can see how we can use jupyter notebook and python can perform analysis. the image shows     us   the calculation of the ride lenght in minutes.

  here we convert the started at column and the ended at column to datetime format
  ![image](https://github.com/user-attachments/assets/426e2e7b-8e36-4c7b-85a4-ef2991a201f8)

## Data Visualization
   - python can alaso be used to carry out data visualization    
      ![output_20_0](https://github.com/user-attachments/assets/67a589cf-6277-4ce5-ac91-dc308ab6f87f)
     the above image showing rides by hour stats between the casual riders and members

  - Number of rides days of the week stats between the casual and member
    ![output_21_0](https://github.com/user-attachments/assets/96a9c694-269e-4f2c-ba52-29ab254980d3)

  - ride length distribution between casuals and member customers
    ![output_21_0](https://github.com/user-attachments/assets/cbcc8428-fe25-47d7-9969-d9837d83b73e)
  
## Results 
  the reults of the analysis  shows 
  - the members have a higher activity rate from the 7am to 9pm 
  - but in the case of rides more causals riders makes trips on everyday of the weeek than the members
  -  wednesdays and thursdays are the days with the most bike trips by casuals
  -  saturdays and sunday is the time when members make the most bike trips
## Recommendations 
  - Target casual riders with promotions for weekday rides: Incentivize weekday usage to increase casual         rider engagement.
  - Offer trial memberships: A limited-time offer for casual riders to experience member benefits may             encourage them to convert to annual members.
  - Digital media campaigns: Use social media and targeted ads focusing on convenience, flexibility, and cost savings to appeal to casual riders.
## Limitations
  i was not able to use sql for this project because my Sql won't let me import multiple data, big query won't let me unless i suncribe to google cloud services and big query sub.
