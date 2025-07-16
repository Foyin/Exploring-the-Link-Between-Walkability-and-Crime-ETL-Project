# 🚶‍♂️📊 Exploring the Link Between Walkability and Crime

I’ve always been interested in creating projects that explore how a person can improve their standard of living through simple decisions—without necessarily needing to earn more money. Higher income often leads to a better quality of life, but so can living in a convenient location with easy access to essential amenities and low crime rates.

This led me to ask:

> **Is there a relationship between a neighbourhood’s walkability and crime rates?**

Given the well-established link between poverty and crime—and considering that walkable areas may reduce a person’s costs and increase their access to services (thereby reducing poverty)—I began to wonder:

> **Could walkability reduce crime, or does it lead to more crime due to higher population density?**

---

## 🔬 Hypotheses

- **Assaults** will be higher in walkable / densely populated areas  
- **Thefts** will be more common in less walkable areas due to reduced access to necessities  
- **Break and enters** will be less common in more walkable areas  
- **Robberies** will be higher in walkable / densely populated areas  
- These patterns will likely differ across cities  

---

## 🔍 Data Source

- **Toronto Police Crime Database For 2022**  
  _(Includes coordinates, crime type, occurrence date, neighborhood info, etc.)_

---

## 🧠 Project Approach

1. Retrieved public crime data from the Toronto Police Crime Database, including coordinates, crime categories, neighborhoods, and occurrence dates.  
2. Developed a Python script to calculate a walk score based on the location of each crime.  
3. Computed walk scores for every data point in the dataset.  
4. Built an ETL pipeline using **AWS Glue** to clean and structure the data.  
5. Stored the processed data in an **AWS S3 bucket**.  
6. Queried the data using **AWS Athena**.  
7. Visualized findings with **Amazon QuickSight**.

