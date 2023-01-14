---
title:  "Spotify Week 1 SQL querys"
mathjax: true
layout: post
categories: media
excerpt_separator: <!--more-->
---
This is short project completed to ask 3 questions from the global spotify weekly charts. Several steps need to be completed, including creating a database, inserting a csv file and creating queries to answer questions.

Before conducting any of these steps the data must be looked at for clarity and make a plan for cleaning if needed. 

Step 1:
Create a database, I called mine Spotify charts

Step 2:
Create a table to insert a CSV file

```
create table spotify (Pos numeric,
			 Pos_movement VARCHAR(50),
			 Artist varchar(50),
			 Title VARCHAR(100),
			 Weeks integer,
			 Peak integer,
			 Peakx integer,
			 Streams bigint,
			 Streams_movement bigint,
			 Total bigint)
```

![Spotify Global Weekly Chart CSV]({{site.baseurl}}\assets\Images\spotify_weekly_chart1.csv) 

Step 3: Begin querys

Question 1: Top 3 songs that spent the most amount of time in the charts and how many weeks each?

```
select title, weeks from spotify
order by weeks desc 
limit 3

```
Answer:
||Title |Weeks|
|-------|:----:|:-------:|
|1|Believer|309|
|2|Perfect|303|
|3|Shape of you| 298|

Question 2: How times is Ed Sheeran on this list?
```
select count (artist)
from spotify
where artist like 'Ed Sheeran%'

```


Answer: 
|Count |
|-------|
|4|

Question 3: Which 3 songs dropped in the most amount of streams from previous week (include artist for clarity)?

```
select artist, title, 
100*(streams - (streams - streams_movement))/(streams - streams_movement)
as Percent_Change
from spotify
order by percent_change ASC 
limit 3

```
Answer
The above SQL query calculated the percentage change from two columns, the original value of streams is not included, only the movement. So I calcuated the change by subtracting the streams-movement from the streams. 

Adding the 'as Percent_Change' created a new column to see the values, however, this column was not added into the original table. 

||Artist |Title|Percent_Change|
|-------|:----:|:----:|:-------:|
|1|Mert Demir |Antidepresan|-19|
|2|Ñengo Flow |Gato de Noche|-16|
|3|Jung Kook |Dreamers [Music from the FIFA World Cup Qatar 2022 Official Soundtrack]|-11|


--------
