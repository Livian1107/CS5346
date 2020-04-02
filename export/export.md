---
layout: default
title: 2012-2018 Annual Exports Of Services By Major Trading Partner
description: Findings over last Data are compiled solely from the International Trade in Services Survey
---

_April 2, 2020_

##### **Student Name:** Lai Liwen
##### **Matriculation Number:** A0162537A
##### **Link (report page):** [https://livian1107.github.io/CS5346/export/export.html](https://livian1107.github.io/CS5346/export/export.html)
##### **Link (PowerBI: interactive charts report, 3 pages for 3 charts):** [https://bit.ly/2R8CFNU](https://bit.ly/2R8CFNU)

This dataset contains SARS number outbreak confirmed cases, deaths, recovered from March to July 2003 across the world. The dataset could help us to understand how SARS spreads arcoss the world over time and this could be useful for us to forsee the future situation of COVID. 
[Dataset](https://data.gov.sg/dataset/exports-of-services-by-major-trading-partner-annual)

## Cumulative Numer of Cases by Date and Country
This line chart shows the growth of SARS confirmed case over time from March 2003 till July 2003. x-axis represents the timeline over 2003, while y-axis represents the number of confirmed cases. Different colors represents different countries in the chart to form the line chart. Overall, the cases stopped increasing around May as the situation was under controlled.

<img src="rate.png" style="width: 840px; height: 500px" />

##### Data used in this line chart

| Data         | Data Type     | Encoding  | Note                                                 |
|:-------------|:--------------|:----------|:-----------------------------------------------------|
| Year         | Ordinal       | Position  | The x-axis shows each date                        |
| Confirmed Cases  | Quantitative  | Position | The y-axis represents the total confirmed cases on that related date |
| Country   | Categorical | Hue    | The different colors represent different countries |


## Death Rate and Recover Rate by Country
This 100% stacked bar chart shows the the number of death and recodered cases and corresponding weitage converted into deatch rate and recovered rate for each countries. The light blue represents the death rate while the dark blue represents the recover rate. As 100% stacked bar chart, the longer of the dark blue bar at each row represents higher recover rate. The longer the light blue bar represents higher death rate. Here we can see that South Africa had the highest death rate.

<img src="death rate.png" style="width: 840px; height: 500px" />

##### Data used in this 100% stacked bar chart

| Data         | Data Type     | Encoding  | Note                                                 |
|:-------------|:--------------|:----------|:-----------------------------------------------------|
| Case Rate  | Quantitative  | Length | The length of the bar shows the related case rate |
| Case Type | Categorical  | Color | Dark blue represents recover rate while light blue represents death rate |
| Country   | Categorical | Postion | Each country is on its own row |


## Total Confirmed Cases Treemap by Country
This treemap represents the total confirmed cases by country (exclduing China). The greater area represents larger number of total confirmed cases, which will be on the top left corner.

<img src="rank.png" style="width: 840px; height: 500px" />


##### Data used in this treemap

| Data         | Data Type     | Encoding  | Note                                                 |
|:-------------|:--------------|:----------|:-----------------------------------------------------|
| Confirmed Cases  | Quantitative  | Size | The area of the rectangle represents the size of confirmed cases for the related country |
| Country   | Categorical | Hue    | The different colors represent different countries |
| Sorted Confirmed Cases  | Ordinal | Position    | The data with higher rank tend to appaer on top and left |

## SARS Spread Map
This map shows how the SARS spread across the world. The size of the circle represents the total confirmed cases in the related country. As we can see from the chart, SARS widely spread in Asia and Europe, and the major cases were in China.

<img src="map.png" style="width: 840px; height: 500px" />


##### Data used in this map

| Data         | Data Type     | Encoding  | Note                                                 |
|:-------------|:--------------|:----------|:-----------------------------------------------------|
| Confirmed Cases  | Quantitative  | Size | The size of the circle represents the size of confirmed cases for the related country |
| Country   | Categorical | Postion | The map shows the position of each country |


[back](./)

