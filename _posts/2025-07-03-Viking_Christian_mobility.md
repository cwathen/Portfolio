---
title:  "Christian Viking Pioneers"
mathjax: true
layout: post
categories: media
excerpt_separator: <!--more-->
---

![Project_Poster]({{site.baseurl}}/assets/Images/ISBA poster.pdf")

<!--more-->

Python, Photoshop, and ArcGIS were used to create figures.
---

Figure 1 was made with ArcGIS. 

Figure 2-4 used Photoshop to improve the resolution and to create the ranges needed to show the variations in geology of the site.

Figures 5-6 were made using VScode and Python

Several questions were asked in the course of this project. Previous radiocarbon dates placed the site period during an overlap of the Late Viking Age and the Early Medievel Period. Around the site there is evidence of paganism and Christianity during the same timeframe, meaning this was one of the earliest sites where Christianity arrived. 

There were two main questions, that were interesting from a mobility standpoint:

1. Were people moving for Christianity or did they become Christians when Christianity arrived. 
2. Was this a meeting place for the greater area region? For this reason 5 and 30 km ranges were chosen.

A technique called Laser Ablation was used and this ablates shallow lines into enamel and you can create a mobility profile as you will use several different strontium values to determine how an individual moved. 


### Dataflow and tool selection
---

- **Data collection**: Strontium values came from Laser Ablation but ranges were calculated using current geological data that has been published
- **Data transformation**: Excel
- **Data analysis and **visualization****: Transformed data into .csv files so they could be analysed using Python. This allowed for models based on classification of locality, as well as creating graphs.

**Figure 5: Permanent teeth with amendments for Deciduous teeth**

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
from matplotlib.lines import Line2D

df = pd.read_csv('e:\phd.3\Varnehem\TrainingMLwithallteethdata.csv')

plt.rcParams['font.family'] = 'Arial' 

selected_sex = ['Subadult', 'Female', 'Male']
selected_tooth_type = ['M1', 'PM', 'M2', 'M3']  # Replace with the specific tooth type/sex you want to display 

filtered_df =  df[(df['Sex'].isin(selected_sex)) & (df['Tooth type'].isin(selected_tooth_type))]

# Create a copy of the filtered DataFrame to avoid SettingWithCopyWarning
filtered_df = filtered_df.copy()

# Add the 'Different_Tooth' column
filtered_df['Different_Tooth'] = filtered_df['Sex'] == 'Unique_Sex'  
# Replace 'Sex' with 'Individual' and 'Unique_Individual' if wanting to show individuals rather than sex

tooth_markers = {
    'M1': 'o',  # Circle
    'PM': 's', # Square
    'M2': 'v',   # Inverted triangle 
    'M3': 'D' #Diamond
}

plt.figure(figsize=(12,8))

# Create scatterplot for each tooth type separately
#shared_palette = sns.color_palette("colorblind", n_colors=filtered_df['Individual'].nunique())
#Use the above if you want to have colors based on Individual rather than on Sex

scatter = sns.scatterplot(
    x='Distance from ERJ (mm)',
    y='87Sr/86Sr',
    hue='Sex',      # Use 'Individual' column if based on Individual
    style='Tooth type',  
    style_order=['M1', 'PM', 'M2', 'M3'],
    markers=tooth_markers,  # Use different markers for teeth
    data=filtered_df[~filtered_df['Different_Tooth']],
    #palette=shared_palette, #Use this for Individual
    s=100,
    alpha=0.7
    )



sns.lineplot(
        x='Distance from ERJ (mm)',
        y='87Sr/86Sr',
        hue='Sex',      # Color by individual for Figure 6
        units='Individual',
        estimator=None,
        data=filtered_df,
        #palette=shared_palette,
        legend=False,  # Show legend for lines
    )

plt.xlim(6, 0) # x-axis to show distance from cervix
plt.ylim(0.70900, 0.73350)  #Y-axis to show strontium isotopes
y_ticks = np.arange(0.70900, 0.73350, 0.00200)
plt.yticks(y_ticks, [f'{y:.4f}' for y in y_ticks])


# Add labels and title
plt.xlabel('Distance from ERJ (mm)', fontsize=14)
plt.ylabel(r'$^{87}\mathrm{Sr}/^{86}\mathrm{Sr}$', fontsize=14)
plt.title('Individual permanent enamel values', fontsize=14)


# Add minor ticks
plt.minorticks_on()

# lined region to show bioavailable ranges  
# 5km range
plt.hlines(y=[0.7142, 0.7207], xmin=0, xmax=30, color='#377eb8', linestyles='--')  # Horizontal lines
plt.vlines(x=[0, 30], ymin=0.7146, ymax=0.7207, color='#377eb8', linestyles='--')  # Vertical lines
plt.text(5.5, 0.7150, "<5km", color='#377eb8', ha='center') 
# 30 km range
plt.hlines(y=[0.7119, 0.7280], xmin=0, xmax=30, color='#984ea3', linestyles='--')  # Horizontal lines
plt.vlines(x=[0, 30], ymin=0.7146, ymax=0.7207, color='#984ea3', linestyles='--')  # Vertical lines
plt.text(5.5, 0.7285, "<30km", color='#984ea3', ha='center') 


# Display plot
# Add the legend outside the graph (on the right side)
plt.legend(loc='upper left', bbox_to_anchor=(1, 1), frameon=False)
plt.gcf().set_dpi(1000)
plt.show

#end of code
```

**Figure 6: Piechart for locality categories**

```python 

import matplotlib.pyplot as plt
import pandas as pd

df = pd.read_csv(r'e:/phd.3/Varnehem/TrainingMLwithallteethdata.csv')	

# Function to classify movement for each individual, change local min and max to specific ones you need
def classify_movement(Sr_ratios):
    local_min = 0.7142
    local_max = 0.7207
    inside_local = Sr_ratios.between(local_min, local_max)
    transitions = inside_local.diff().fillna(0).astype(int)
    
    if all(inside_local):  # Always within the local range
        return 'Local'
    elif not any(inside_local):  # Always outside the local range
        return 'Non-local'
    elif transitions.sum() == 1 and not inside_local.iloc[0]:  # Moves into the local range
        return 'Mixed - moves into the local range'
    elif transitions.sum() == 1 and inside_local.iloc[0]:  # Moves out of the local range
        return 'Mixed - moves out of the local range'
    elif transitions.sum() > 1:  # Crosses the local range multiple times
        return 'Mixed - crosses local range multiple times'
    else:
        return 'Unclassified'

# Apply the classification to each individual
categories = []
for ind, group in df.groupby('Individual'):  # Group by individual ID
    sr_ratios = group['87Sr/86Sr'].reset_index(drop=True)
    category = classify_movement(sr_ratios)
    categories.append({'Individual': ind, 'Category': category})

# Create a new DataFrame with the categories
category_df = pd.DataFrame(categories)

# Merge the categories back into the original dataframe for reference
df = df.merge(category_df, on='Individual', how='left')

# Count the occurrences of each category
category_counts = category_df['Category'].value_counts()
# Filter out categories with zero counts (if any)
category_counts = category_counts[category_counts > 0]
category_percentages = (category_counts / len(category_df)) * 100 #calculate percentage

# Define custom colors
colors = {'Non-local':'#377eb8', 'Mixed - crosses local range multiple times': '#ff7f00','Local':'#4daf4a', 'Mixed - moves into the local range': '#f781bf', 'Mixed - moves out of the local range': '#a65628'}
plt.rcParams['font.family'] = 'Arial'

# Get colors in the order of categories to plot
colors_ordered = [colors[cat] for cat in category_percentages.index]

# Plot the pie chart
plt.figure(figsize=(12, 10))
wedges, _, autotexts = plt.pie(
    category_percentages,
    autopct='%1.1f%%',  # Show percentage with 1 decimal
    startangle=90,
    colors=colors_ordered,
    textprops={'color': 'black'}  # Color of percentage labels
)

# Modify percentage font size and color
for autotext in autotexts:
    autotext.set_color('black')  # Set percentage text color to white
    autotext.set_fontsize(18)    # Set percentage font size
    autotext.set_fontfamily('Arial')  # Set font family to Arial

# Add a legend outside the pie chart
plt.legend(
    wedges, 
    category_percentages.index, 
    loc="center left",  # Position the legend outside the pie chart
    bbox_to_anchor=(1, 0.5),
    fontsize=18
)

# Set the title
plt.title(r'Categorization based on $^{87}\mathrm{Sr}/^{86}\mathrm{Sr}$ values', fontsize=16)
plt.gcf().set_dpi(1000) #good resolution
plt.show()
#end of code
```