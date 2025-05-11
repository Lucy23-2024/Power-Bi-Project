# Power-Bi-Project - Health Data Dashboard
## Project Objective
To Create an interactive dashboard using `weight-height-updated` dataset to analyze health metrics.

# Project Overview
This project aims to analyze individual health metrics by calculating Body Mass Index (BMI) using given weight and height data. 
The goal is to:

- Clean and prepare raw data

- Calculate BMI for each person

- Calculate the age for each person

- Categorize BMI according to health standards

- Provide interactive visuals to support insights into health trends across different groups (e.g., age or gender, if applicable)


1. Importing Data
Importing our `csv.file` to Power BI

2. Data Cleaning
- Filtering the null values
- Close and Apply

3. Creating New Columns
- Body Mass Index(BMI)

```Dax
BMI = DIVIDE(
'weight-height-updated'[Weight],('weight-height-updated'[Height]*'weight-height-updated'[Height])
) *(703) 

```
#Note: 
*The BMI is expressed in kg/m2, resulting from mass in kilograms and height in metres.*
*Our data is in pounds and inches, a conversion factor of 703 to change (lb/in2) to (kg/m2) is applied.*
