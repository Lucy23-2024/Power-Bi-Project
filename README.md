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
- Card Insights (KPIs)
Visual Type: Cards
Metrics Displayed: `Average Height`, `Average Weight`, `Average BMI` & `Total Number of Population`
Purpose: Quickly identify the typical physical characteristics of individuals

- Comparative Analysis
Visual Type: Clustered Bar Chart
Metric: `Average BMI` by `Gender`
Purpose: Visualize Gender by Average BMI

- Comparative Analysis
Visual Type: Stacked Bar Chart
Metrics Displayed: `BMI Categories` by `Gender`
Purpose: Visualise gender-based differences in BMI values

- KPI Gauge:
Visual Type: Gauge
Metric: Average BMI
Purpose: Custom BMI gauge to visually represent where a value falls within the health spectrum

4. Age Demographics
Visual Type: Donut Chart
Metric: Distribution of `Age Category` by `Gender`
Purpose: Show the distribution of ages.

5. Filtering for Insights
Visual Type: Slicer
Field: Gender, BMI group
Purpose: Allow users to filter the entire report by `gender` and/or `BMI Group`, updating all visuals dynamically.

6. Detailed Table
Visual Type: Table
Included Columns: Age, Height, Weight, BMI, BMI Group
Enhancements:
Conditional Formatting: `Colour-coded` BMI values (e.g., light green for underweight, dark green for obese)

## Conclusion
The Health Data Dashboard effectively visualises health metrics, providing actionable insights into BMI and age distribution. 
The use of rounded KPIs, interactive filters, and varied visuals ensures a user-friendly experience. 

 
 



