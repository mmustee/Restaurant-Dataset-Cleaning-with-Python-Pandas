# Restaurant-Dataset-Cleaning-with-Python-Pandas
Cleaning and Preparing a Restaurant Dataset (Zomato) with Python/Pandas

## Dataset
The raw dataset used in this project is the Zomato Bangalore Restaurants dataset, 
available on Kaggle:
https://www.kaggle.com/datasets/rishikeshkonapure/zomato/data

Download `zomato.csv` and place it in the root of the project folder before running the notebook.

## Project Overview

This dataset contains restaurant listings from Zomato's Bangalore platform. Before any analysis could be performed, the raw data required significant cleaning — inconsistent rating formats, mixed-type cost columns, duplicate listings, and missing values across key fields. This notebook prepares the dataset for exploratory and business analysis, enabling questions around pricing strategy, cuisine performance, and location-based investment decisions.

## Before & After Summary

| Metric | Before | After |
|--------|--------|-------|
| Total rows | 51,717 | 11,193 |
| Duplicate rows | 29,103 | 0 |
| Null values | 13,909 | 0 |
| Columns | 17 | 7 |

## Objectives
The raw Zomato dataset contained several data quality issues that made it 
unsuitable for analysis in its original form. The goal of this project was 
to resolve these issues systematically and produce a clean, analysis-ready 
dataset. Specifically, this involved:

- Removing 10 non-analytical columns (including urls, phone numbers, and 
  free-text fields) that were outside the scope of the business questions
- Standardising inconsistent column naming conventions across all 7 retained columns
- Identifying and eliminating 29,103 duplicate records (56% of the dataset)
- Resolving 13,909 null values across the Rate, Dish_liked, and Approx_cost columns
- Cleaning the Rate column which contained irregularly formatted strings 
  such as "4.1/5" and "3.8 /5" with inconsistent spacing
- Encoding the Online_order column from Yes/No strings to binary integers 
  (1/0) to prepare the data for numerical analysis and potential modelling

## Tools and Libraries
- Python
- Pandas

## Key Steps

### Initial Exploration

Loaded the raw dataset (51,717 rows, 17 columns) and inspected data types, null counts, and column structure using data.info() and data.shape to understand the scope of cleaning required before making any changes.

![](images/Step1a.png)
### Removing Redundant Columns

url, address, phone, location, rest_type, cuisines, reviews_list, menu_item, listed_in(type), listed_in(city)) that were either non-analytical, free-text fields unsuitable for structured analysis, or outside the scope of the business questions being answered. Retained 7 columns focused on restaurant identity, ordering features, ratings, and cost.
![](images/Step2a.png)
![](images/Step2b.png)
### Standardizing Column Names

Renamed all columns using a capitalisation loop to ensure consistent, readable naming conventions across the dataset, replacing the original inconsistent mix of lowercase and snake_case labels.
![](images/Step3.png)
### Removing Duplicate Records

Identified 29,103 duplicate rows (56% of the dataset) using duplicated().sum(). All duplicates were removed using drop_duplicates(), reducing the dataset to 22,614 unique records.
![](images/Step4.png)
### Handling Null Values

After removing duplicates, identified remaining nulls: 2,420 in Rate, 11,348 in Dish_liked, and 141 in Approx_cost. All rows containing null values were dropped, resulting in a final clean dataset of 11,193 records. This approach was chosen to ensure complete, reliable records for downstream analysis.
![](images/Step5.png)
### Cleaning the Rate Column

The Rate column contained inconsistently formatted strings such as "4.1/5" and "3.8 /5" (with irregular spacing). Removed whitespace and replaced the / separator with " out of " to produce a human-readable, standardised format (e.g., "4.1 out of 5").
![](images/Step6.png)
###  Encoding the Online_order Column

Converted the Online_order column from Yes/No string values to binary integers (1 = Yes, 0 = No) using a map function, making the column ready for numerical analysis and potential modelling.
![](images/Step7.png)
### Exporting the Cleaned Dataset

Exported the final cleaned dataset to CSV using index=False to avoid writing the DataFrame index as an unwanted column — an important detail that was identified and corrected during the process.

![](images/Step8.png)

## Next Steps
Now that the dataset has been cleaned and prepared, it enables the following 
analytical work:

- **Rating Analysis** — Explore correlations between restaurant ratings, 
  pricing, and online ordering availability to identify what drives higher 
  customer scores
- **Pricing Segmentation** — Group restaurants by approximate cost for two 
  people to understand how price bands relate to customer satisfaction and 
  votes
- **Online Ordering Impact** — Analyse whether restaurants offering online 
  ordering consistently outperform those that don't in terms of ratings and 
  engagement
- **Dashboard Development** — Load the cleaned dataset into Power BI to 
  build an interactive dashboard surfacing key restaurant performance insights
