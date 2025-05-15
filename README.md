# Health Data Dashboard
## Project Objective
To create an interactive dashboard using the `weight-height-updated` dataset to analyse health metrics.

## Dataset Overview
The dataset contains individual health information, including:
- Height (in inches)
- Weight (in pounds)
- Born_Year
- Gender

The dataset was then imported into Power BI Desktop, cleaned, and transformed to meet the project requirements.

## Methodology
### Part 1: Data Preparation & Cleaning
- The dataset was imported into Power BI Desktop via `Get Data > Text/CSV`.
- Filtering the null values

### Part 2: Create calculated Columns
Calculated columns were created in Power BI using DAX (Data Analysis Expressions) to derive new metrics.
- Body Mass Index(BMI)
Provides the measure that estimates body fat based on height and weight
Formula:
``` Dax

BMI = DIVIDE(
'weight-height-updated'[Weight],('weight-height-updated'[Height]*'weight-height-updated'[Height])
) *(703)

```
> #Note: 
>*The BMI is expressed in kg/m2, resulting from mass in kilograms and height in metres.*
>*Our data is in pounds and inches; a conversion factor of `703` is applied to change `(lb/in2)` to `(kg/m2)`.*

- Age
Provides the current age based on the year of birth.
Formula:
``` Dax
Age = YEAR(TODAY())- ('weight-height-updated'[Born_Year])

```

- BMI Category
Group individuals into health-related categories for visual analysis
Formula:
``` Dax
BMI Group = IF('weight-height-updated'[BMI] < 18.5 ,"Underweight",
            IF('weight-height-updated'[BMI] < 25,"Normal",
            IF('weight-height-updated'[BMI] < 30,"Overweight",
            IF('weight-height-updated'[BMI] >=30 ,"Obese")))
)

```

### Part 3: Data Visualisation

 



