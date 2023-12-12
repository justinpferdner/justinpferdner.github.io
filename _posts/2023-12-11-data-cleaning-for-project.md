---
layout: post
title:  "Retrieving Data for Home Prices in Salt Lake and Utah County"
author: Justin Pferdner
description: My method and processes for retrieving data on 1600+ homes in Salt Lake and Utah county 
image: /assets/images/data_cleaning_background.png
---

## Introduction
Home prices have sky-rocketed within the past 5 years. Even through raises in interest rates, homes have continued to sell and prices continue to rise. Many in the real estate market were anticpating the "bubble" to pop and prices to drop rapidly, but this has not been the case since the crash in 2009. My aim with this data set is to answer the question of, "What drives the prices of homes near Salt Lake and Utah County?"

I retrieved data for 1624 homes for sale near Utah County and Salt Lake County. The data for these homes was scraped from https://homes.ksl.com/. 

## Method for Obtaining Homes Data

### Step 1: Get Website Link
KSL's website is open for web-scraping with some minor rules and regulations. I navigated to the homes section within KSL, and filtered my homes search by zooming in on the map to see mostly only Utah and Salt Lake Counties. In this way I could see all the homes for sale on these areas on the left-hand side of the page. I copied this link to scrape using the selenium package in Python. 

### Step 2: Set Up Selenium
After I had the link with the correct homes, I decided the best way to scrape the website would be using the Selenium package in Python. Diving into the HTML code on the website, I saw that each home and all of its information was located in the class name 'Listings_GridItemWrap__VnOPm'. Using the 'find_elements' command in selenium I was able to obtain every home and all of it's information. 

Now it was time to put all the information into rows and columns. I used a for loop in Python to loop through each home in my list of homes elements. For each house, I used the 'find_element' command in selenium to obtain prices, address, bedrooms, bathrooms, and square feet. If one of these elements wasn't found within KSL, the code replaced the value with N/A.

### Step 3: Running the Driver
When the code was complete, I noticed I was only getting 7 homes to show up in my dataset. I found out this was because you had to scroll to the end of KSL's homes page to load more products for viewing. To counteract this, I included a for loop just after I start the web driver that waits 4 seconds (to load the page) then scroll down to the bottom and wait another 4 seconds. I had the code scroll down 80 times, waiting 4 seconds each time, which got me all the available homes in my areas of interest. This process of waiting for the data to load took about 7-8 minutes.

### Step 4: Cleaning the Data
The first three steps took up the majority of my time. It was a tedious process looking through the HTML and getting selenium set up the right way. After obtaining the data, I had to clean up the columns by changing some data types and breaking the columns up. 

I began by extracing Zip Code, State, and City from the Address column. I did this using regex. Next, I used regex again to break up the bedroom/bathroom column into two seperate columns. I then changed these variables to numeric. Subsequently, I cleaned the square feet column to remove all words from the rows and changed the variable to numeric as well. I then cleaned the price column by removing the '$' and all commas, then changing the variable to numeric. After cleaning both the 'Sqft' and 'Price' columns, I created a new column called 'Price_per_sqft' (price per square foot) which I did by dividing the price column by the square foot column. I then mapped each city in the 'City' column to it's appropriate county to create a 'County' column.

Lastly, I knew I wanted to have geo-spatial visualizations in my EDA, so I used a free API for geocoding to convert the addresses into latitudes and longitudes. This required making a loop to call the API for each address, appending the lat and long to previously created empty arrays, and finally adding the filled lat and long arrays to the dataset. That process took about 30 minutes to run, due to rate restrictions.  

## Ethical Considerations

### Adherence to robots.txt
I carefully reviewed and adhered to the rules and regulations set forth in the robots.txt file for KSL's website. Fortunately, web scraping is allowed for scraping homes data from the website. I stuck to just this section of the website, minimizing any potential impact on the website's performance. This focused data extraction ensured that my activities were purposeful and considerate.

### Limited Frequency and Volume
The geocoding API I used had rate limiting restrictions for free users to 1 second per request. I adhered to these rules by including time.sleep(1) to my code to make sure I only requested the API once per second. Also, to prevent any strain on KSL.com's servers, I controlled the frequency and volume of the data requests. Implementing reasonable delays between requests and limiting the number of simultaneous connections reflects my commitment to responsible data collection and helps maintain the overall integrity of the website.

### Publicly Available Information
I only sought out data that was publicly available. I did not attempt to access any restricted areas, private databases, or any other information that was not intentionally made accessible through KSL's website.

In conclusion, the data I have collected via selenium look accurate and I have minimal null values meaning the dataset is fairly complete. The process was not overly complicated and I made sure to follow ethical guidlines for scraping data from the web.