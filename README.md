---
title: "Cyclistic Bike Share Case Study"
author: "Touch Hun"
date: '2022-06-20'
output: html_document
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

![](cyclistic_brand.jpg)

# Introduction

Cyclictic is a company located in Chicago. It provides bike transportation to customers as a rider. At the present, its bike-share program that features more than 5,800 bicycles and 600 docking stations. It is offering three kinds of bikes, reclining bikes, hand tricycles, and cargo bikes, which are inclusive to people with disabilities and riders who cannot use a standard two-wheeled bike. The bikes can be unlocked from one station and returned to any other station in the system at anytime.


There are diversified customer preferences. The majority of riders prefer traditional bikes and only 8% of riders use the assistive options. Cyclistic customers are more likely ride for their leisure and only about 30% use them to commute to work each day.

Keeping a long term service strategy, the markeing director leads the data analyst team of six and starts the development of campaigns and initiates to promote the bike-share program.These include email, social media, and other channels. 

After discussing with the Cyclitic's finance analyst, the marketing director understands that maximizing the number of annual members, called subscribers is the key success for the future growth. However, rather than targeting the new customers, the marketing director, Lily Moreno believes that there is a good chance to convert casual riders into members because they are already aware of the Cyclistic program and have chosen Cyclitic for their mobility needs.

However, before this promotion campaign is accepted by the Cyclistic executive team, the data analyst team of six lead by the marketing director, Lily Moreno needs to provide the guides with data driven strategy. 

As a data anlayst, my work is to find the insights from the dataset and present them to the stakeholders, who are my marketing supervisor, Moreno, and Cyclistic executive team. The business problem is to search for the differences that annual members and casual riders use Cyclistic bikes.


## Stage 1. Ask

The question to the business problem is "how do annual members and casual riders use Cyclistic bikes differently?". To answer this question, the six stages of the data analysis are needed to support the findings and presented to the team members and the stakeholders.

## State 2. Prepare
The historical data for bike trips can be publicly accessed at [the company's website](https://divvy-tripdata.s3.amazonaws.com/index.html). The data is in zip files and organized by years from 2014 to 2022. Only 12 most recently monthly datasets that are relevant to the business problem are considered, downloaded and housed locally in a sub-folder for further stages of the analysis.

The data integrity is well mananged because the data is originally collected and owned by Cyclistic, and only relevant variables are included to secure the privacy, security and accessibility of the datasets. The trip data by the staff serice and system inspection is deleted to guarantee the accuracy. Generally speaking, the data is ROCCC because it is regularly updated to the current availabe data. However, it needs some data cleaning because of some false starts of bike trips and users to secure the bike docks.

## Stage 3: Process
To ensure the data integrity and accesiblity, the origal and cleaned data are stored locally and separately in different sub-folders. The csv and excel files are stored in the subfolders "data_csv" and "data_xlxs". The excel files are converted from the origal csv files, and they are cleaned using the sorting and filtering tools to observe any inaccuracy, inconsitancy, and incompleteness. Some records with the ride length less than 60 seconds are deleled from the excel files because they are potially false starts and user's relocks. Since the base time for pricing the charge on bikeride in minutes, a varialbe "ride_length_minutes" is added to the excel files. After that, some data aggregation is done for the purpose of accuracy check.

Also, using R programming, the data is sorted and filtered to look for any inconsistency, inaccuracy and inadequacy, and they are stored locally in a sub-folder. And finally, all the 12 monthly datasets are combined into a dataset for a whole year analysis. Checking the consistency among the results from the spreadsheets and R programming is very helpful in data cleaning so that it guarantees the data integrity.


Since each of the data file is in the csv format, it is converted to the excel format so that the data can be more effectively converted and transformed using the excel rich functionality. For example, using date and time format allows to calculate the ride length of each trip so that it can show some differences between the members and casual riders.

After the ride length is added to the sheet, some inconsistency of the data is observed between the start time and end time of the trips, so those are deleted rowwise.

## Stage 4: Analyze
 Firstly, geolocations of the start stations for each of the rider types are shown in the following maps.
 ![](./images/casual.png) 
 ![](members.png)
For these two types of riders, there is no significant difference for using the bikes in terms of geolocatons of the stations.

### Analysis on the diffences between members and casual riders
#### Exploratory data analysis
After looking into the ride lengths in details, the data needs more cleaning in statistical terms for the outliers. After removing the outliers using the IQR method, the ride length distributios by types of riders and by days of week are shown here.
![](./images/ride_length_by_riders.jpeg)

![](./images/ride_length_by_days.jpeg) 
### Descriptive measures on ride lengths

#### Descritpive measures on ride length (minutes)
<table style="width:100%" border = 1>
<tr><th> Ride Length </th> <th> Min.</th> <th>Median</th> <th> 1Qu.</th> <th>Mean</th> <th> 3rd Qu.</th> <th> Max.</th> </tr>
<tr><th></th><th> 1 </th> <th> 6.267 </th> <th> 10.667</th> <th>13.234 </th> <th> 17.983</th> <th> 42.217</th> </tr>
</table>
#### Descriptive measures on ride lengths (minutes) by type of riders
<table style="width:70%" border=1>
<tr> <th> member_casual </th> <th> mean of ride length in minutes </th>  </tr>
  <tr>  <td align = "center"> casual </td> <td align ="center"> 15.67 </td> </tr>
  <tr>  </td> <td align = "center"> member </td> <td align = "center"> 11.57 </td> </tr>
   </table>
#### Descriptive measures on ride lengths (minutes) by days of the week
<table style="width:80%" border = 1>
<tr> <th>  </th> <th> day_of_week </th> <th> ride_length_minutes </th>  </tr>
  <tr>  <th> 1 </th> <td align = "center"> Sun </td> <td align="center"> 14.76 </td> </tr>
  <tr> <th> 2 </th> <td align = "center"> Mon </td> <td align="center"> 12.80 </td> </tr>
  <tr> <th> 3 </th> <td align = "center"> Tue </td> <td align="center"> 12.26 </td> </tr>
  <tr> <th> 4 </th> <td align = "center"> Wed </td> <td align="center"> 12.35 </td> </tr>
  <tr> <th> 5 </th><td align = "center"> Thu </td> <td align="center"> 12.45 </td> </tr>
  <tr> <th> 6 </th> <td align = "center"> Fri </td> <td align="center"> 12.98 </td> </tr>
  <tr> <th> 7 </th> <td align = "center"> Sat </td> <td align="center"> 14.77 </td> </tr>
   </table>


The trend line of memberhip by month has shown that the percentage of members is decreasing, so it is a negative sign that Cyclistic should consider attacting more causal riders to be an annual member.

![](./images/monthly_percent.jpeg)


![](./images/monthly_mean_length.jpeg)

Even by day or month, the difference between the members and casual riders is about four minutes per trip as the bar plot and the line chart have shown.

![](./images/daily_mean_length.jpeg)

## Stage 5: Share
With the task assigned by the markeing supervisor, Lily Moreno, as a data story teller, after cruching all the data, and using all the methods and tools, I can show the insights clearly to the stakeholders including the executive team and my manager
with [this power presentaton ](https://touhu11.github.io/capstone_cyclistic/cyclistic_presentation.pptx) with some recommenations.

## Stage 6: Act
Based on my findings, I would like to give three recommendations.

(1). Annual promotion is likely successful based on the casual rider trend line of increasing percentages of riders.

(2). Their geo-location background is similar to that of the members based on their starting points of trips. There are there is no problem for the casual riders to use the bikes at the current stations.

(3). Their usage patterns are similar to those of the members by considering the ride lengths by days of the week. Their trip lengths are even longer, so they can save more if they subcribe their annual membership.









