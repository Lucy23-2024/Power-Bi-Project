# Power-Bi-Project - Health Data Dashboard
## Project Objective
To Create an interactive dashboard using `weight-height-updated` dataset to analyze health metrics.

# Project Overview

1. Importing Data
Importing our `csv.file` to Power BI

2. Data Cleaning
- Filtering the null values
- Close and Apply

3. Creating New Columns
- Body Mass Index(BMI)

```Dax
BMI = DIVIDE(
'weight-height-updated'[Weight],('weight-height-updated'[Height]*'weight-height-updated'[Height])) *(703) 

```
#Note: 
~The BMI is expressed in kg/m2, resulting from mass in kilograms and height in metres.~
~If pounds and inches are used, a conversion factor of 703 (kg/m2)/(lb/in2) is applied.~

 
