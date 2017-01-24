---
layout: post
title: NYC Subway Data Analysis
---

This is the first project for the Metis Data Science bootcamp. Our client, WomenTechWomenYes (WTWY), an organization that aims at building an inclusive community and increasing participation for women in technology related industries, is seeking help to promote their annual gala event.

Even though we were given a fairly short timeline (1 week), we managed to capture the essence of data science projects from start to end. Below is an overview of the steps we took:

1. Understand the Problem and Objectives
2. Scrap the Data
3. Wrangle the Data
4. Analyze the Data
5. Visualize and Present Findings


## Understand the Problem and Objectives

Since WTWY has a limited amount of free tickets to hand out for their annual gala, we decided to set the goal to be maximizing attendance at the gala with individuals who are most likely to make donations and contribute the cause. 

## Data Scraping & Data Wrangling

We collected our data sets through the Metropolitan Transportation Authority website. Since the data sets are weekly, we create a python function using to download these txt files instead of scrapping many files individually (efficiency, woohoo!). Nevertheless, the raw data is still far from being in a nice and clean format that we can easily work with, so we took steps to clean the data, such as converting dates into date objects, adding day of the week and dropping unnecessary columns. In the end, we obtained a set of clean data from April to June in 2016.

![png](https://github.com/tlids/tlids.github.io/blob/master/images/data%20example.png)


## Analyze the Data

Using the MTA data, we were able to calculate the number of entries for a specific station and time, which give us an idea of which stations and dates generate the most traffic. In addition, we used the list of top 10 zip codes with the most venture capital funding raised by technology companies (between Jan 1st to July 31st in 2016) in NYC as a proxy for where individuals who are passionate about technology are likely to be. It became clear that we wanted to target the overlapping section of these criteria, which are stations with heavy foot traffic that are also in the top 10 zip codes by venture capital funding on the busiest day and month.



## Visualize and Present Findings

Our data showed that compared to April and May, June had 4000 more ridership on average. Days in the middle of the week, especially Wednesday, generate a higher traffic. This is pretty intuitive since people are more likely to take day off from work toward the beginning or ending of Monday - Friday. Weekend’s subway riderships are a lot lower, indicating that people are not utilizing public transportation as much on weekends.







Next, through mapping the stations with their corresponding zip codes using a reverse geocoding process and analyzing the number of entries for each station, we found the following stations to be in the target zip codes and top 50 stations in terms of foot traffic. The number in the parentheses represent the station’s ranking in terms of average foot traffic in June.

1. GRD CNTRL-42 ST (2)
2. 34 ST-HERALD SQ (3)
3. TIMES SQ-42 ST (7)
4. 42 ST-PORT AUTH (8)
5. 14 ST (17)
6. 42 ST-BRYANT PK (27)
7. CHURCH AV (34)
8. BEDFORD AV (35)
9. BOROUGH HALL (36)
10. 33 ST (40)

The graph below shows that, compared to the top 50 stations, the average traffic is much higher for our 10 target stations, meaning that we can reach out to more potential attendees by stationing marketing folks there.




We also compared the number of riderships throughout the week for the 10 target stations in the graph below. Consistent with previous finding, these stations are also more popular on Wednesday.
