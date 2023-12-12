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

![boxplot of price by county](/assets/images/eda/home_price_by_county.png)

### Scatterplot Price by Square Feet

![price by sqft scatter](/assets/images/eda/price_by_sqft_by_county.png)

### Median Home Price by City

![median home price](/assets/images/eda/median_home_price.png)

### Average Price per Square Foot by City

![avg price/sqft by city](/assets/images/eda/avg_price_per_sqft.png)

### Home Price by Number of Bedrooms

![price/bedrooms](/assets/images/eda/price_by_bedroom.png)

### Correlation Heatmap of Quantitive Variables

![heatmap](/assets/images/eda/corr_heatmap.png)