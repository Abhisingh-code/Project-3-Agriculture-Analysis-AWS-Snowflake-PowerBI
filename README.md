## Agriculture-Data-Analysis Dashboard

Dashboard Link : https://app.powerbi.com/groups/me/reports/7a0adb39-c058-48b8-b54a-99ff9c7abc5d/c49c816013112c9abec0?redirectedFromSignup=1&experience=power-bi


## Problem Statement

This dashboard helps to analyze agricultural conditions and crop performance using environmental factors such as rainfall, temperature, and humidity. It provides insights into how these factors impact crop yield across different years, seasons, crops, and locations.

Since, environmental conditions vary over time, thus analysis is required to understand their impact on agricultural productivity.

Also since crop yield fluctuates based on climate factors, thus it is important to monitor trends for better farming decisions.


### Steps followed

Step 1 : Open AWS, create 'S3' bucket and upload the data file into the bucket.  

Step 2 : Create role in AWS, under permission policies Select AmazaonS3FullAcesss, provide a role name and click create.

Step 3 : open Snowflake create integration object for establishing connection between 'Snowflake' and 'Amazon S3 bucket' by updating (ARN) from AWS Roles.

Step 4 : open AWS go to the created role, Under Trust relationships, Edit trust policy, update (ARN/Property Value) and (External ID/Property Value) from Snowflake and click update policy.

Step 5 : open Snowflake, (create: database, schema, blank table, stage by mentioning integration object(Holds the location of the data that need to be uploaded in Snowflake), copy data into a new dataset by mentioning stage and give file format as 'csv').

Step 6 : Data Profiling in Snowflake Using [Result view and chart view].

Step 7 : Data Transformation in Snowflake

       (1) Created new table named: "agriculture" to copy the original data.
       (2) Increased the 'RAINFALL' column values by 10%(1.1) by writing an update statement
       (3) Reduced the 'AREA' Column values by 10%(0.9) by writing update statement.
       (4) Added new column 'YEAR_GROUP' into the "agriculture" table (this column tells up about year groups and year values and the category they fall into) and update statements were   written to fill data into this column.

           //Year 2004 to 2009 - Y1                            
           
                Update agriculture
                set year_group = 'Y1'
                Where year >= 2004 and year <= 2009
   
           //Year 2010 to 2015 - Y2                            
           
                Update agriculture
                set year_group = 'Y2'
                Where year >= 2010 and year <= 2015

           //Year 2016 to 2019 - Y3                            
           
                Update agriculture
                set year_group = 'Y3'
                Where year >= 2016 and year <= 2019

        (5) Added new column 'RAINFALL_GROUPS' into the "agriculture" table (in this column depending on rainfall values categories the records in three categories)
            
           //values in rainfall_groups MIN: 255 and MAX: 4103 
             
           //Rainfall 255 & 1200 - Low                            
           
                Update agriculture
                set rainfall_groups = 'Low'
                Where rainfall >= 255 and rainfall < 1200
   
           //Rainfall  1200 & 2800 - Medium                           
           
                Update agriculture
                set rainfall_groups = 'Medium '
                Where rainfall >= 1200 and rainfall < 2800

           //Rainfall 2800 & 4103 - High                           
           
                Update agriculture
                set rainfall_groups = 'High '
                Where rainfall >= 2800 

Step 8 : Load data into Power BI Desktop from Snowflake.  

Step 9 : Open power query editor & check "column distribution", "column quality" & "column profile".

Step 10 : Select "column profiling based on entire dataset".

Step 11 : Adding Stacked bar charts on page 1(Rainfall Analysis)

         (1) Average Rainfall by Year

         (2) Average Rainfall by Season
         
         (3) Average Rainfall by Crops
    
         (4) Average Rainfall by Location
          

under Build visual, under X-axis[Rainfall(Average)] remains same and Y-axis() changes for each KPIs in order(YEARS, SEASON, CROPS, LOCATION) 


Step 12 : Adding Stacked bar charts on page 1(Temperature Analysis)

         (1) Average Temperature by Year

         (2) Average Temperature by Season
         
         (3) Average Temperature by Crops
    
         (4) Average Temperature by Location
          

under Build visual, under X-axis[Temperature(Average)] remains same and Y-axis() changes for each KPIs in order(YEARS, SEASON, CROPS, LOCATION) 


Step 13 : Adding Stacked bar charts on page 1(Humidity Analysis)

         (1) Average Humidity by Year

         (2) Average Humidity by Season
         
         (3) Average Humidity by Crops
    
         (4) Average Humidity by Location
          

under Build visual, under X-axis[Humidity(Average)] remains same and Y-axis() changes for each KPIs in order(YEARS, SEASON, CROPS, LOCATION)


Step 14 : Adding Stacked bar charts on page 1(Yield Analysis)

         (1) Average Yield by Year

         (2) Average Yield by Season
         
         (3) Average Yield by Crops
    
         (4) Average Yield by Location
          

under Build visual, under X-axis[Yields(Average)] remains same and Y-axis() changes for each KPIs in order(YEARS, SEASON, CROPS, LOCATION)

   

Step 12 : Report published to Power BI Service.

Snapshot of Dashboard (Power BI Service)

(Dashboard snapshot)

Report Snapshot (Power BI DESKTOP)

(Report snapshot)



## Insights

A multi-page report was created on Power BI Desktop & published to Power BI Service.

Following inferences can be drawn:

[1] Rainfall Analysis

Rainfall remains relatively consistent with slight fluctuations across years.

    thus, rainfall is stable but varies slightly over time.  

[2] Temperature Analysis

Temperature varies significantly across years and crops.

    thus, temperature plays a key role in crop conditions.  

[3] Humidity Analysis

Humidity remains almost constant across years, seasons, and locations.

    thus, humidity has minimal variation.  
[4] Crop Yield Analysis

Crops like Cotton and Coconut show higher yield compared to others.

    thus, certain crops are more productive.  
[5] Seasonal Impact

Yield is highest in Rabi season compared to others.

    thus, season strongly impacts agricultural output.  
[6] Location-wise Insight

Locations like Kodagu and Mysuru show higher yield performance.

    thus, geography influences productivity.  
