---
title:  "Loan data model case study"
mathjax: true
layout: post
categories: media
excerpt_separator: <!--more-->
---
![Loan Case Study flow]({{site.baseurl}}/assets/Images/Loancasestudy.jpg)

<!--more-->
#Case
---

You are the data architect for a loan brokering company. The company has customers that apply for loans. Banks are then invited to make bids on the loans matching or partially matching the requested loan amount. The bids will have different amounts, interest rates and repayment times and are largely based on the information provided by the customer and by the credit report. The credit report is made at the time of the application. It will give us a credit score as well as other indicators such as number of credit remarks. Once the customer has gotten bids from banks, he or she can accept a bid. The loan is then, in most cases, signed and paid out. Your task is to design a logical data model that can support the following requirement:
- Store customer information like name, email and address info
- Store credit report info
- Store information about the application (amounts and dates)
- Store information about the bids (amounts, interest rates, repayment time)
- Store information about the banks
Furthermore, it should be possible to analyze how many applications that were created, received bids, where accepted and paid out. The data model can be done in many ways and there is not one correct answer. It’s up to you to describe why you chose this model.
Deliverables:
- A diagram of the logical model including entities, attributes and relationships
- A description of the model and why you chose it.
- A description of the dataflow design proposal and tools selection rationale
- A short description of how this model could fit into a data warehouse landscape with multiple sources and users of data.
- A description of important aspects you see in relation to data governance and security.
Assumptions:
- You are free to make any assumptions in addition to the above information.
- Assume that the data sources of the loans are two different databases with data in different formats.
- Assume that users of the data are report creators and users knowledgeable in SQL.

###Model chosen
---
**Logical Data Model** because it shows the elements and their relationships, and it serves as a blueprint. 
- This model is flexible and can be amended in the future and attempts to reduce data duplication. For instance, keeping customer information as a separate entity from the application data ensures that we don’t have to update this information as it can be referenced by using foreign keys that reference a primary key.

![Loan Case Study flow]({{site.baseurl}}/assets/Images/Loancasestudy.jpg)

![Loan Case Study table]({{site.baseurl}}/assets/Images/Loancasestudy1.jpg)

###Dataflow and tool selection
---

**Data collection**: Various data sources (loan apps, credit reports, bank bids, etc.) can be collected and integrated into BigQuery.
**Data transformation**: DBT (open-source modelling tool) can transform raw data into a useable format.
**Data analysis and **visualization****: Transformed data can be queried using SQL and visualized using PowerBI. PowerBI allows interactive dashboards to be created so we can know how many loan bids per application were made and other important questions can be answered.

###Data warehouse - BigQuery 
---

- GCP’s BigQuery is affordable and has ML capabilities. It has the benefit of allowing all information to be in one location. 
- Model can be used a basis for building a warehouse integrating data from different sources (customer information, credit reporting, bank information), allowing us to have a central location for data access. 
- Users can extract and transform data using ETL processes and (Analysts, BI teams) access the data using SQL for analysis and reporting. ML engineers and Data Scientists can create predictive models using the data.

###Data governance and security
---
- Ensure the establishment of policies and procedures that protect customer and bank data. 
- Secure access to data warehouse and encrypt sensitive data.
- Establish policies that ensure compliance with regulations such as GDPR.

###Future Expansion of Model
---
- Joint applications
- Different application types -
e.g., Personal Loan vs Debt Consolidation Loan.
- Multiple applications
- Insert region in consideration to governance and security.
