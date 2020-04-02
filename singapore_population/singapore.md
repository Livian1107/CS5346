---
layout: default
title: Singapore Population 2018 Analytics
description: 2018 Singapore population pyramid over gender and distribution flow over various ethnic groups.
---

_March 29, 2020_

**Student Name:** Lai Liwen
**Matriculation Number:** A0162537A

This dataset is about the annual population of Singapore residents (citizens and permanent residents) by age groups, ethnic group and gender from 1957-2018, manageed by MInistry of Trade and Industry - Department of Statistics. From this dataset, we could visualize the trend of Singapore total population since the last half decade through a simple bar chart. As the population by age, ethnic and gender groups are also included, we could leverage population pyramid and fow chart to visualize the weightage of various groups in the total population, which will be shown as following. 

[Dataset](https://data.gov.sg/dataset/resident-population-by-ethnicity-gender-and-age-group)

## Singapore Populaion Increasement Bar Chart 1957-2018
This chart is a simple bar chart of Singapore population over 1957-2018. The x-axis represents the time - which year, while the y-axis represents the corresponding population of that year. We can see the population is in an incresing trend for the last hald decade.
<iframe src="https://livian1107.github.io/CS5346/singapore_population/year" width="100%" height="500"></iframe>

##### Data used in this bar chart

| Data         | Data Type     | Encoding  | Note                                                 |
|:-------------|:--------------|:----------|:-----------------------------------------------------|
| Year         | Ordinal       | Position  | The x-axis shows every year                          |
| Population   | Quantitative  | Length    | The length of the bar shows the number of population |


## Singapore Populaion Pyramid Over Genders
This chart is 2018 Singapore population pyramid over genders. Each row represents an age group and listed in descending order. Each row is a bar with the length representing the number of population of the related age and gender group, and also the weightage of each groups in the total population in percentage. From this chart we can see the great distribution over age 20-64. The gender is generally equal in each age group.For the age group over 65 years old, the female group tends to have greater weightage than the male group.
<iframe src="https://livian1107.github.io/CS5346/singapore_population/gender" width="100%" height="500"></iframe>

##### Data used in this bar chart

| Data          | Data Type     | Encoding  | Note                                                 |
|:--------------|:--------------|:----------|:-----------------------------------------------------|
| Population    | Quantitative  | Length    | The length of the bar shows the number of population |
| Age Groups    | Categorical   | Position  | Each age groups is on its own row (sorted in descending order) |
| Gender Groups | Categorical   | Position  | Each gender group is on its own discrete column |


## Singapore Populaion Sankey Diagram - Flow Over Various Ethnic Groups
This chart is 2018 Singapore population flow over various ethnic groups and also related gender groups. Each group would be reprented by a node and the nodes are linked together accordingly if this node is the sub group of the parent node. For examplem, the _'Total Residents'_ is made up of _'Total Chinses'_, _'Total Malays'_, _'Total Indians'_, and _'Other Ethnic Groups'_, the flow arrows are directed from the parent node _'Total Residents'_ to the all other four sub group nodes. The same for the related age group nodes for each ethnic group nodes.

From this sankey diagram, we can see how Singapore residents are made up of various ethnic groups and corresponding weitage of each groups in the total population. The flow shows how the population distribute into various groups clearly.
<iframe src="https://livian1107.github.io/CS5346/singapore_population/flow" width="100%" height="500"></iframe>

##### Data used in this bar chart

| Data          | Data Type     | Encoding  | Note                                                 |
|:--------------|:--------------|:----------|:-----------------------------------------------------|
| Population    | Quantitative  | Width     | The width of each flow arrows represents the number of population |
| Groups | Categorical   | Position | Each ethnic groups is on its own section row on the second column |
| Link | Relational   | Connection  | Each groups has been connected to its parent/child groups accordingly |

[back](./)
