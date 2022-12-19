---
title:  "Two-currency Budget Dashboard"
mathjax: true
layout: post
categories: media
---

![Budget Dashboard]({{site.baseurl}}/assets/Images/BudgetDashboard1.jpg)

### Budgeting Dashboard using 2 currencies
---
The photo is of a dashboard that is the first sheet of an in-depth Excel workbook that is connected to 7 other sheets.

This is an in-depth workbook that tracks 2 currencies and can be applied to more than 2 or even just 1. This dashboard also tracks your FIRE (financial independence retire early) goal by demonstrating your percentage reached. In addition, one sheet also calculates your FIRE number based on the 4% rule and age.

Example Formulas used within the sheet:
```
=VLOOKUP(Q10,$A$9:$M$19,MATCH($Q$1,$B$9:$M$9,0)+1,0)
```
```
=(SUM('Net Worth'!M20,'Net Worth'!M21,'Net Worth'!M27,'Net Worth'!M28,'Net Worth'!M24))/300000
```