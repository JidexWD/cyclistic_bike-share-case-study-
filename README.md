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
     
      # Convert 'started_at' and 'ended_at' columns to datetime format
      df['started_at'] = pd.to_datetime(df['started_at'])
      df['ended_at'] = pd.to_datetime(df['ended_at'])


      # Calculate ride length in minutes
      df['ride_length'] = (df['ended_at'] - df['started_at']).dt.total_seconds() / 60

      # Create day_of_week column based on started_at
      df['day_of_week'] = df['started_at'].dt.day_name()


      # Separate casual riders and annual members
      casual_riders = df[df['member_casual'] == 'casual']
      annual_members = df[df['member_casual'] == 'member']



      # Calculate the average ride length for both groups
      avg_ride_length_casual = casual_riders['ride_length'].mean()
      avg_ride_length_member = annual_members['ride_length'].mean()


      # Count rides by day of the week for both groups
      rides_by_day_casual = casual_riders['day_of_week'].value_counts()
      rides_by_day_member = annual_members['day_of_week'].value_counts()

      print("Casual riders by day of the week:\n", rides_by_day_casual)
      print("Members by day of the week:\n", rides_by_day_member)


      print(f"Average ride length (Casual riders): {avg_ride_length_casual} minutes")
      print(f"Average ride length (Annual members): {avg_ride_length_member} minutes")


      
## Data Visualization
  - python can alaso be used to carry out data visualization

        # Extract the hour from 'started_at' to analyze peak times
        df['hour'] = df['started_at'].dt.hour

        # Group by hour for casual riders and members
        rides_by_hour = df.groupby(['hour', 'member_casual']).size().unstack()

        # Plot the number of rides by hour of the day
        rides_by_hour.plot(kind='bar', stacked=True, figsize=(10,6))
        plt.title("Rides by Hour of Day (Casual vs Member)")
        plt.xlabel("Hour of the Day")
        plt.ylabel("Number of Rides")
        plt.show()
    ![output_20_0](https://github.com/user-attachments/assets/67a589cf-6277-4ce5-ac91-dc308ab6f87f)
    the above image showing rides by hour stats between the casual riders and members

  - Number of rides days of# Create day_of_week column based on started_at
    df['day_of_week'] = df['started_at'].dt.day_name() the week stats between the casual and member

          # Number of Rides by Day of the Week
          plt.figure(figsize=(10, 6))
          sns.countplot(data=df, x='day_of_week', hue='member_casual', order=['Monday', 'Tuesday',         'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'])
          plt.title('Number of Rides by Day of the Week (Casual vs Member)')
          plt.show()
    ![output_21_0](https://github.com/user-attachments/assets/96a9c694-269e-4f2c-ba52-29ab254980d3)

  - ride length distribution between casuals and member customers

        # Ride Length Distribution
        plt.figure(figsize=(10, 6))
        sns.histplot(data=df, x='ride_length', hue='member_casual', bins=50, kde=True)
        plt.xlim(0, 60)  # Focus on rides less than 1 hour
        plt.title('Ride Length Distribution (Casual vs Member)')
        plt.show()
          
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
