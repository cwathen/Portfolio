---
title:  "Figure from a Case study to understand how Christianity was brought to two different part of Sweden using a chronological Timeline from R"
mathjax: true
layout: post
categories: media
excerpt_separator: <!--more-->
---

![Timeline of two Viking age sites]({{site.baseurl}}/assets/Images/Rplot01n1.jpg)
---
This schedule was used to understand how Christianity was brought to different parts of the country. Here we compared the timelines of two sites from two different dioceses. At this time Västerhus was part of Norway and Varnhem was part of Sweden but had closer relations for Denmark. 

Using this timeline, along with other data, we were able to see that Västerhus was a site where Christianity was part of the community so there was less variation in diet and mobility. Varnhem, on the other head, shows how Christianity was brought to the area and it welcomed more people who traveled further distances to partake. The high amount of non-local burials from outside a 30 km radius shows that people were traveling far distances to take part whereas in Västerhus the population was largely local and did not have to travel far. 

<!--more-->
Use the R vistime package to start off.

Using the text of event, etc. will let you edit it to your specific dates. This library requires a month and date so if you are like me and care only about years, then you can use 01-01. 

- Event = Chronological age 
- Group = how you want to group the years together, for instance, by site, by geographical area, etc.
- Start = the start date (YEAR-MONTH-DATE), use 01-01 if month-date are unknown or unspecified
- End = the end date (YEAR-MONTH-DATE), use 01-01 if month-date are unknown or unspecified
install

```r
library(vistime) 

data <- read.csv(text="event,group,start,end
 Viking Age,Chronology,0800-01-01,1050-01-01
 Early Medieval Period,Chronology,1050-01-01,1350-01-01
 Wooden Church built,Varnhem,1000-01-01,1000-01-01
 Stone Church built,Varnhem,1030-01-01,1050-01-01
 Fru Sigrid donates estate to Cistercians,Varnhem,1150-01-01,1150-01-01
 Period of cemetery Use,Varnhem,0900-01-01,1150-01-01
 Maximum period of cemetery use,Västerhus,1125-01-01,1500-01-01
 Erection of Frösö runic stone,Västerhus,1050-01-01,1080-01-01
 Pagan burial ceases,Västerhus,1025-01-01,1050-01-01")
```
>If you want it to aligned with no event labels use this one

```r
gg_vistime(data, optimize_y = TRUE, show_labels = FALSE) 
```
>If you want the event labels but it won't be aligned

```r
gg_vistime(data, optimize_y = FALSE)
```