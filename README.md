# Case-Study-2-Bellabeat
Case study from the Google Data Analytics Certificate program
Data source: https://www.kaggle.com/datasets/arashnic/fitbit

## Data Preparation
Looked at the data within Excel to identify how tables will be connected.

I noticed and confirmed that the merged file appropriately merged the individual activity, step, and calorie files. As a result, I just used the merged file and not the individual ones since it is redundant.

I alter determined max/min values for the appropriate columns and sorted them to determine any outliers. This determination helps with identifying the filters during the data cleaning process. There were some observations in the data that didn't quite make sense such as a high sedentary time but also a high step and calorie count, which is paradoxical. However, the filters applied took out most of these observations, and thus I left the rest in there since it didn't affect my overall results.

The weight log file was pretty straightforward. I noticed it also had an ID column, which was perfect as a key to link my two tables together. While I didn't notice this in my data preparation, going through my analysis, I went back in Excel and confirmed that there was only weight data for 8 of the individuals. This was disappointing since I couldn't identify any weight trends with confidence due to the very low sample size.

All the minute and hourly data couldn't be uploaded into BigQuery and merging them was taking too long for it to even work, so I unfortunately couldn't use these data sets and stuck with the daily ones instead.

Once I understood and had confidence in my data, I went to clean it in SQL.

## Data Cleaning
Since the weight_log file had weights recorded for different users at different times, I took the average weight and used this in my analysis. All users only logged their weight 1-2 times within a month, so an average weight is reasonable here (i.e. no significant change).

SQL code for getting average weight values in a new file: https://console.cloud.google.com/bigquery?sq=426298227585:40dc8db5a5b445eab10708deef3b09ed

Once this information was determined, I combined the data on the user ID and applied filters based on findings in the data preparation process and some obvious outliers (i.e. being sedentary for 24 hours isn't logical).

Additionally, I added a "health" column to identify the health of the individual based off their BMI (i.e. underweight, overweight, normal, etc.).

SQL code for data cleaning and final table: https://console.cloud.google.com/bigquery?sq=426298227585:5ba08ba8fcbe478bb3cc4de0a56f42ed

## Data Analysis and Visualization
All visualization and analysis were done in Tableau and it can be found here: https://public.tableau.com/views/CaseStudy2Bellabeat_16733285091120/Dashboard1?:language=en-US&:display_count=n&:origin=viz_share_link

I first looked at the relationship between calories burned and steps taken. As expected, there was a good correlation, but not as strong as expected, which was something I needed to investigate further.

I also confirmed the relationshpi between steps and distance, and that was very strong, so I had confidence to use either during my analysis, whichever was more applicable. Since many workouts may not cover distance, I focued all my activity analysis absed on time instead of distance (though the resutls didn't vary much).

Since there were different types of activity, I wanted to see how impactful each was in burning calories, so that visualization was made.

I then looked into how many steps were taken each day. This would assist with identifying trends for the marketing team and better understand how users use their devices.

Then, I thought to see how many of the users actually logged data to see how often users are using this product. Turns out, not many use their products very often, which likely resulted in some of my data being less conclusive than excpected. While my initial filters played a part in this, there are still too little inputs from users to get a more wholesome look at the data. Depite this, it did give insight into how users are (or aren't) using the product.

With these analyses and other visualizations I tested, I was able to make my presentation to Bellabeat

## Presenting the Data & Conclusion
With my findings in Tableau, I created the PowerPoint presentation that incldues my visualizations, interpretations, and my recommednations for the company. This summed up the entire process and incldues all the key info from my analysis.
