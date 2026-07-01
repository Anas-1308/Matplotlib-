# Matplotlib Crash Course 📊

A comprehensive starter guide to data visualization in Python using **Matplotlib**. This repository covers everything from basic line plots to styling customizations, multiple chart types, subplots, and integration with **Pandas**.

---

## 📋 Table of Contents
1. [Installation & Setup](#1-installation--setup)
2. [Basic Plotting](#2-basic-plotting)
3. [Plot Customization (Lines & Markers)](#3-plot-customization-lines--markers)
4. [Labels, Titles, and Ticks](#4-labels-titles-and-ticks)
5. [Grid Lines](#5-grid-lines)
6. [Bar Charts](#6-bar-charts)
7. [Pie Charts](#7-pie-charts)
8. [Scatter Plots](#8-scatter-plots)
9. [Histograms](#9-histograms)
10. [Subplots](#10-subplots)
11. [Integrating Matplotlib with Pandas](#11-integrating-matplotlib-with-pandas)

---

## 1. Installation & Setup
To install Matplotlib, run the following pip command in your terminal:
```bash
pip install matplotlib
```
To verify the installation and check the version:

Python
```import matplotlib
print(matplotlib.__version__)
```
Most plotting actions are done using the pyplot module, typically imported with the alias plt:

Python
```
import matplotlib.pyplot as plt

import numpy as np # Recommended for handling data arrays efficiently
```
2. Basic Plotting
To create a standard line graph, map pairs of X and Y coordinates. Remember to call plt.show() to render the output window.
```
Python
x = np.array([2023, 2024, 2025, 2026])
y = np.array([15, 25, 30, 20])

plt.plot(x, y)
plt.show()
```
3. Plot Customization (Lines & Markers)
You can customize line styles and point markers using arguments inside plt.plot(). Alternatively, bundle configurations into a dictionary and unpack it using .
```
Python
# Customization using a styling dictionary
line_style = {
    "marker": "o",               # 'o' for circle, 'v' for triangle, '*' for star
    "markersize": 10,
    "markerfacecolor": "#00FFCC",
    "markeredgecolor": "#00FFCC",
    "linestyle": "dashed",       # 'solid', 'dashed', 'dotted', 'dashdot', 'None'
    "linewidth": 4
}

plt.plot(x, y, **line_style, color="#003366")
plt.show()
```
4. Labels, Titles, and Ticks
Make graphs readable by giving them context with explicitly styled titles, axis labels, and targeted ticks.
```
Python
plt.plot(x, y)

# Title and Axis styling
font_config = {"family": "Arial", "size": 20, "weight": "bold", "color": "#003366"}
plt.title("Class Size Trend", fontdict=font_config)
plt.xlabel("Year", fontdict=font_config)
plt.ylabel("Students", fontdict=font_config)

# Forcing ticks to match exact data points
plt.xticks(x)
plt.tick_params(axis="both", colors="#003366")

plt.show()
```
5. Grid Lines
Grid lines introduce reference metrics behind data points for improved assessment.
```
Python
plt.plot(x, y)
plt.grid(axis='y', linestyle='--', linewidth=1.5, color='lightgray') # Tracks Y-axis changes
plt.show()
```
6. Bar Charts
Bar charts contrast categorical distributions. Toggle the standard plt.bar() function to plt.barh() for a horizontal chart alternative.
```
Python
categories = np.array(["Grains", "Fruit", "Vegetables", "Protein", "Dairy"])
values = np.array([4, 3, 2, 5, 3])

plt.bar(categories, values, color="skyblue", edgecolor="black")
plt.xlabel("Food Category")
plt.ylabel("Quantity (Servings)")
plt.show()
```
7. Pie Charts
Pie charts map parts-to-a-whole percentage distributions.
```
Python
labels = ["Freshman", "Sophomore", "Junior", "Senior"]
students = [300, 250, 275, 225]
colors = ["red", "yellow", "blue", "green"]
explode = [0, 0, 0, 0.1] # Highlights 'Senior' slice by lifting it out

plt.pie(students, labels=labels, autopct="%1.1f%%", colors=colors, explode=explode, shadow=True, startangle=90)
plt.title("College Student Distribution")
plt.show()
```
8. Scatter Plots
Scatter charts plot correlations between variables. Add a legend to organize multi-class point systems.
```
Python
hours_studied = [1, 2, 3, 5, 6, 7, 8]
exam_grades = [60, 62, 68, 75, 82, 85, 87]

plt.scatter(hours_studied, exam_grades, color="red", s=200, alpha=0.5, label="Class A")
plt.xlabel("Hours Studied")
plt.ylabel("Grade")
plt.legend()
plt.show()

```
9. Histograms
Histograms summarize continuous numeric distributions by bucketing them into range intervals called "bins."
```
Python
# Simulating a normal curve distribution around a median grade of 80
scores = np.random.normal(loc=80, scale=10, size=100)
scores = np.clip(scores, 0, 100) # Prevents values exceeding standard constraints

plt.hist(scores, bins=10, color="lightgreen", edgecolor="black")
plt.xlabel("Scores Range")
plt.ylabel("Number of Students")
plt.show()

```
10. Subplots
Subplots isolate multi-graph grids within a uniform canvas footprint, tracking index parameters unpacked from plt.subplots().
```
Python
# Creates a 2x2 grid layout matrix
fig, axes = plt.subplots(nrows=2, ncols=2)

x_vals = np.array([1, 2, 3, 4])

# Plot top-left subplot
axes[0, 0].plot(x_vals, x_vals * 2, color="red")
axes[0, 0].set_title("x * 2")

# Plot top-right subplot
axes[0, 1].plot(x_vals, x_vals ** 2, color="blue")
axes[0, 1].set_title("x ^ 2")

# Plot bottom-left subplot
axes[1, 0].plot(x_vals, x_vals ** 3, color="green")
axes[1, 0].set_title("x ^ 3")

# Plot bottom-right subplot
axes[1, 1].plot(x_vals, x_vals ** 4, color="purple")
axes[1, 1].set_title("x ^ 4")

plt.tight_layout() # Mitigates axis overlapping collisions
plt.show()
```
11. Integrating Matplotlib with Pandas
You can quickly clean structured database records via pandas and map data counts straight onto a Matplotlib layout.
```
Python
import pandas as pd

# Extract data framework records from a standard CSV
df = pd.read_csv("pokemon_data.csv")

# Extract and count unique column attributes
type_counts = df["Type 1"].value_counts(ascending=True)

# Build a clean horizontal bar layout directly from the dataset counts
plt.barh(type_counts.index, type_counts.values, color="cornflowerblue", edgecolor="black")
plt.title("Count of Pokémon by Primary Type")
plt.xlabel("Count")
plt.ylabel("Type")
plt.tight_layout()
plt.show()
```
