---
title:  "Two-currency Budget Dashboard"
mathjax: true
layout: post
categories: media
---
<head>
      <!-- other head stuff... -->
    <link rel="stylesheet" href="{{site.baseurl}}/assets/css/flickity.css" media="screen">
    <link rel="stylesheet" href="{{site.baseurl}}/assets/css/fullscreen.css">
</head>
<body>
    <!-- all your great html... -->
    <script src="{{site.baseurl}}/assets/js/flickity.pkgd.js"></script>
    <script src="{{site.baseurl}}/assets/js/fullscreen.js"></script>
</body>

<div class="carousel" data-flickity='{ "imagesLoaded": true, "percentPosition": false,"adaptiveHeight": true,"fullscreen": true }'>
    <div class="carousel-cell">
        <img src="{{site.baseurl}}/assets/Images/BudgetDashboard1.jpg" alt="Dashboard" />
    </div>
    <div class="carousel-cell">
        <img src="{{site.baseurl}}/assets/Images/Dashboard_helper.jpg" alt="Dashboard helper" />
    </div>
    <div class="carousel-cell">
        <img src="{{site.baseurl}}/assets/Images/Actual.jpg" alt="Actual" />
    </div>
    <div class="carousel-cell">
        <img src="{{site.baseurl}}/assets/Images/Dividends.jpg" alt="Dividends" />  
    </div>
    <div class="carousel-cell">
        <img src="{{site.baseurl}}/assets/Images/FIRE%20tracker.jpg" alt="Fire Tracker" />
    </div>
    <div class="carousel-cell">
        <img src="{{site.baseurl}}/assets/Images/Networth.jpg" alt="Networth calculation" />  
    </div>
    <div class="carousel-cell">
        <img src="{{site.baseurl}}/assets/Images/Spending.jpg" alt="Spending" />  
    </div>
</div>

---

The photo carousel is of a dashboard that is the first sheet of an in-depth Excel workbook that is connected to 6 other sheets.

This is an in-depth workbook that tracks 2 currencies and can be applied to more than 2 or even just 1. This dashboard also tracks your FIRE (financial independence retire early) goal by demonstrating your percentage reached. This is connected to three sheets - Dividend, Networth and FIRE tracker. The latter of which calculates your FIRE number and age you can early retire based on the 4% rule.

This sheet was made for those within the FIRE community and numbers are associated with no one's personal numbers. 

Example formulas used within the sheet:
```
=VLOOKUP(Q10,$A$9:$M$19,MATCH($Q$1,$B$9:$M$9,0)+1,0)
```
```
=(SUM('Net Worth'!M20,'Net Worth'!M21,'Net Worth'!M27,'Net Worth'!M28,'Net Worth'!M24))/300000
```


