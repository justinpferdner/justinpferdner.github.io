---
layout: post
title:  "Exploratory Data Analysis on Homes near Salt Lake and Utah County"
author: Justin Pferdner
description: My method and processes for analyzing and exploring data on 1600+ homes near Salt Lake and Utah county 
image: /assets/images/eda_background.png
---

## Introduction
In my previous post, I explained my process in obtaining data for home prices in and around Salt Lake and Utah county. I aim at answering the question of what the difference in home prices is between the different counties. In this post, I would like to highlight some of my exploratory techniques that I used to analyze the data retrieved. If you would like to learn more about the project, please visit my previous post where I outline my methods on the data collection of home prices.

## Visualizations
Here are some of the most informative visualizations I made for understanding the data. The dataset contains the following columns: Price ($), Address, Bathrooms, Bedrooms, Square Feet, Price per Square foot, Zip Code, State, City, Latitude, Longitude, and County.

### Distribution of Home Prices

![dist of home prices](/assets/images/eda/dist_of_home_prices.png)

The histogram of home prices is a solid visual in understanding the most typical price ranges. The distribution is extremely right-skewed (due to a few million dollar homes) but most homes range around $400,000 to $600,000. After seeing the price distribution, I was curious about the distribution by county, so I created side-by-side boxplots:

![boxplot of price by county](/assets/images/eda/home_price_by_county.png)

This visual is informative in that it helps us clearly see the differences in home prices between counties. Summit County and Wasatch County have higher medians, whereas Salt Lake and Utah County have lower median home prices.

### Scatterplot Price by Square Feet

![price by sqft scatter](/assets/images/eda/price_by_sqft_by_county.png)

The next visual I wanted to look at was how price and square feet correlated. I created the scatterplot above which displays square feet on the x axis and price on the y axis. There appears to be a positive correlation between price and square feet, with a few outliers. It is mostly linear.

### Median Home Price by City

![median home price](/assets/images/eda/median_home_price.png)

To begin looking at differences between cities, I first looked at the median home price. This visualization was informative in seeing the distinction between the expensive areas, the moderately priced areas, and the cheaper areas in Utah. Cities like Sundance, Wanship, Hideout and Brighton are clearly the most expensive cities to live in. 

### Average Price per Square Foot by City

![avg price/sqft by city](/assets/images/eda/avg_price_per_sqft.png)

The next visual I created for differences between cities was average price per square foot. Cities in Wasatch County like Park City and Midway have the highest price per square foot, whereas in cities like Cedar Valley and Salem you can get a larger house for a smaller price tag.

### Home Price by Number of Bedrooms

![price/bedrooms](/assets/images/eda/price_by_bedroom.png)

Often the number of bedrooms in a house makes the house more expensive. I decided to explore this through side-by-side boxplots. Sure enough, as the number of bedrooms increases the median price increases as well. The variability in price also seems to increase as the number of bedrooms goes up.

### Correlation Heatmap of Quantitive Variables

![heatmap](/assets/images/eda/corr_heatmap.png)

Lastly, I used a heatmap to see the correlation between all of the quantitative variables in the dataset. This inlcuded number of bedrooms, number of bathrooms, price, and square feet. The two variables that are most closely correlated are price and square feet at 0.74. Bedrooms and bathrooms have a somewhat strong correlation as well of 0.68.

### Summary
The most intriguing findings from my data were those that involved differences between cities and counties. Seeing price per square foot was also an informative statistic to look at because it shows the areas where you can get the best bang for your buck when buying a house. It was interesting to see how some of the most expensive areas compared to the cheaper areas.

#### Link to Data, Code, and Streamlit App
[Data and Code](https://github.com/justinpferdner/semester_project)
[Streamlit App](https://semesterproject-ulqytaqsqwudqzqxekd2mc.streamlit.app/)