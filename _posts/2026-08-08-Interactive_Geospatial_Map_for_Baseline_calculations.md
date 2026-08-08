---
title:  "Interactive Nordic 87^Sr/86^Sr Bioavailable Baseline Explorer using Python"
mathjax: true
layout: post
categories: media
excerpt_separator: <!--more-->
---

![Gif]({{site.baseurl}}/assets/Images/Map Animation.apng)
---
An interactive geospatial application for exploring published bioavailable **87^Sr/86^Sr baseline data** in relation to archaeological sites.

The application allows users to enter an archaeological site's geographic coordinates and explore nearby baseline measurements through an interactive map. Samples can be filtered by type, while geographic proximity is visualized using 10 km, 25 km, and 50 km distance zones.

## Project Overview

Strontium isotope analysis is widely used in archaeological research to investigate geographic mobility and provenance. Interpreting archaeological 87Sr/86Sr measurements requires comparison with appropriate environmental baseline data.

This project transforms a research dataset of published bioavailable strontium isotope measurements into an interactive, user-facing geospatial application.

Instead of manually calculating distances and examining large datasets, users can enter a site's latitude and longitude and immediately explore geographically relevant baseline samples.

## Key Features

* Enter an archaeological site's **latitude and longitude** in WGS84 format
* Calculate geodesic distance between the site and baseline samples
* Display baseline samples within **50 km**
* Visualize **10 km, 25 km, and 50 km** proximity zones
* Filter samples by sample type
* Color-code samples based on their type
* Click individual samples to view:

  * Sample type
  * 87^Sr/86^Sr ratio
  * Distance from the archaeological site
* Toggle map layers on and off
* Explore the dataset through an interactive web interface

## Technologies

| Technology | Purpose                                     |
| ---------- | ------------------------------------------- |
| Python     | Application development and data processing |
| Pandas     | Data loading and transformation             |
| GeoPandas  | Geospatial data handling                    |
| Geopy      | Geodesic distance calculations              |
| Folium     | Interactive map visualization               |
| Streamlit  | User interface and application framework    |
| JSON       | Portable application data layer             |

## Data Pipeline

The application separates data loading, analysis, and visualization into modular Python components.

```text
Baseline data from published peer-reviewed articles
          ↓
     Data preparation
          ↓
       JSON dataset
          ↓
     data_loader.py
          ↓
       GeoDataFrame
          ↓
      analysis.py
          ↓
Geodesic distance calculations
          ↓
      mapping.py
          ↓
    Interactive Folium map
          ↓
      Streamlit interface
```

This modular structure allows the underlying dataset, analysis functions, and visualization components to be maintained independently.

## Geospatial Analysis

The application uses latitude and longitude coordinates in **WGS84**.

For each baseline sample, the application calculates the geodesic distance to the user-defined archaeological site.

Samples are then categorized into proximity ranges:

* **Within 10 km**
* **Within 25 km**
* **Within 50 km**
* **Beyond 50 km**

Only samples within 50 km are displayed on the map.

## Interactive Visualization

The map uses separate layers for:

* Archaeological site
* Distance zones
* Baseline sample types

Sample types are represented using different colors, allowing users to quickly distinguish between water, fauna, soil, plant, and other sample categories.

The map also includes an interactive legend and layer controls.

## Project Structure

```text
strontium-baseline-explorer/
│
├── app.py                  # Streamlit application
├── analysis.py             # Distance and proximity analysis
├── data_loader.py          # Data loading and GeoDataFrame creation
├── mapping.py              # Interactive map generation
├── convert_excel.py        # Converts source data to JSON
├── requirements.txt        # Python dependencies
├── README.md               # Project documentation
├── .gitignore
│
├── data/
│   └── baseline.json       # Application dataset
│
└── tests/
    └── test_loader.py      # Data loading test
```

## Running the Application

Clone the repository and navigate to the project directory.

Install the required Python packages:

```bash
pip install -r requirements.txt
```

Run the Streamlit application:

```bash
streamlit run app.py
```

The application will open in your web browser.

## Why I Built It

This project grew from my archaeological science research, where geographic baseline data is essential for interpreting strontium isotope measurements.

I wanted to move beyond a static research dataset and build a tool that could make the data easier to explore, analyze, and communicate.

The project also allowed me to apply my research experience to a broader data workflow:

**Research data → Data processing → Geospatial analysis → Interactive visualization → User-facing application**

## Skills Demonstrated

* Python programming
* Data cleaning and transformation
* Geospatial data analysis
* Geodesic distance calculations
* Interactive data visualization
* Modular application development
* Data pipeline design
* Streamlit application development
* User-focused data presentation

## Author

**Crista Adelle Wathen**
Archaeological Scientist | Data Analyst | Researcher
[LinkedIn](https://www.linkedin.com/in/crista-wathen/)
