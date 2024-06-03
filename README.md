# README

## Disclaimer: 
Due to the large number of arrests that occur in the USA, I had to separate out the arrest data into several csv files. To reproduce my work, you will have to recombine these files (or add a loop to loop through the files).

## Project Overview

The purpose of this project is to analyze the disparity between arrest data and demographic data within a state. By comparing the number of people arrested by race to the population of that race residing in a state, the project aims to highlight potential disparities that may exist in law enforcement practices. While differences in arrests may be due to multiple reasons (income disparities, law enforement disparities, crime disparities, etc.), I believe it is still important to look at this data from just the perspective of race as a starting point.

## Script 1: `Data Preprocessing (DataPreprocessing.ipynb)`

This script combines downloaded arrest data from multiple sources into a single dataframe and conducts basic data analysis on the combined dataset. 

### Combining Downloaded Data
- The script imports necessary libraries such as `os`, `pandas`, and `sqlite3`.
- It iterates through folders in the root directory, reading CSV files containing arrest data.
- The data is combined using SQL JOIN operations and saved as `arrest_data_USA.csv`.

### Basic Data Analysis
- Descriptive statistics are calculated on the joined DataFrame using Pandas.

### Loading State Demographic Data
- Demographic data for each state in the analyzed year (2022) is loaded and processed to obtain statistics for each state, saved as `demogaphic_data.csv`.

## Script 2: `Analysis and Display (USA_Arrest_Data_Analysis.ipynb)`

This script conducts deeper analysis on arrest data at both a national and state level, focusing on disparity between different racial groups.

### Country-Wide Data Analysis
- Disparity metrics are calculated between demographic data and arrest data for each state. The description for how this is calculated can be found below.
- Disparity values are visualized on a choropleth map of the USA, illustrating disparities between states.

### State-Specific Data Analysis
- Users input a state abbreviation for analysis.
- Demographic and arrest data for the selected state are retrieved.
- A bar chart is generated to visualize the demographics of the selected state compared to their arrest statistics.

## Disparity Calculation Method

The disparity between arrest data and demographic data is calculated using a simple but informative method. The disparity metric is computed as the Euclidean distance between the percentage of arrests for each racial group and the percentage of the population represented by that racial group in a given state.

### Formula:
The disparity D for a particular racial group i in a state is calculated as follows:


$$D_i = \sqrt{\sum_{i=1}^{n} (A_i - P_i)^2}$$


Where:
- $D_i$ is the disparity for racial group i.
- $A_i$ is the percentage of arrests for racial group i.
- $P_i$ is the percentage of the population represented by racial group i.
- $n$ is the total number of racial groups.

### Explanation of the Method:

#### 1. Euclidean Distance:
The Euclidean distance formula is utilized because it provides a straightforward measure of the difference between two sets of data points. In this case, it quantifies the difference between the percentages of arrests and the percentages of the population for each racial group.

#### 2. Interpretability:
The resulting disparity values are intuitive to interpret: the larger the value, the greater the disparity between the racial composition of arrests and the racial composition of the population. This allows for easy comparison across different states and racial groups.

#### 3. Sensitivity to Differences:
The method captures the sensitivity to differences in both the relative sizes of racial groups and the disparities in their arrest rates. By squaring the differences before summing them, larger disparities are given proportionally more weight in the overall disparity calculation.

#### 4. Simplicity and Transparency:
The calculation method is simple and transparent, making it accessible for stakeholders and policymakers to understand. It doesn't rely on complex statistical models, ensuring its applicability across various contexts.

This method offers a clear and interpretable way to quantify the disparities between arrest data and demographic data, providing valuable insights for understanding and addressing potential biases in law enforcement practices.


