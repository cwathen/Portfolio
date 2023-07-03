---
title:  "HR Dashboard and SQL"
mathjax: true
layout: post
categories: media
excerpt_separator: <!--more-->
---
This is short project using Power BI and SQL analyzed HR data to help the department to monitor and manage different aspects of employee data to maintain a healthy workforce.

<!--more-->

Power BI
---
![HR Dashboard]({{site.baseurl}}/assets/Images/HR_dashboard.jpg)




Several KPIs are used to address different points

1. Employee count: How many employee are in the workforce? If this number is not clear then it is difficult to assess the size of the workforce to determine future growth or downsizing.
2. Attrition count: Currently the data does not show how many employees have left the organization so this needs to be standardized
3. Attrition Rate: Without a clear measure of rate or attrition count, we cannot assess the overall turnover rate and compare it with other similar companies in the industry
4. Active employees: Need a way to measure the active and inactive employees so that productivity can be measured.
5. Average Age: This would evaluate the workforce demographics and the company's ability to attract and retain talent of different ages.


You can visit the PowerBI file with the data and the dashboard here, by visiting [this repository](https://github.com/cwathen/PowerBi)

SQL 
---
Create a table to insert a CSV file

```
create table HR_data
(
	emp_no integer PRIMARY KEY,
	gender varchar(50) NOT NULL,
	marital_status varchar(50),
	age_band varchar(50),
	age integer,
	department varchar(50),
	education varchar(50),
	education_field varchar(50),
	job_role varchar(50),
	business_travel varchar(50),
	employee_count integer,
	attrition varchar(50),
	attrition_label varchar(50),
	job_satisfaction integer,
	active_employee integer
)
```

Question 1: KPI- Employee Count

```
select sum(employee_count) as Employee_Count from hrdata;
```

Question 2: KPI- Attrition Count

```
select count(attrition) from hrdata where attrition='Yes';
```
--------
