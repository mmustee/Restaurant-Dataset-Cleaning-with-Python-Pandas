# Restaurant-Dataset-Cleaning-with-Python-Pandas
Cleaning and Preparing a Restaurant Dataset (Zomato) with Python/Pandas

## Project Overview

This dataset contains restaurant listings from Zomato's Bangalore platform. Before any analysis could be performed, the raw data required significant cleaning — inconsistent rating formats, mixed-type cost columns, duplicate listings, and missing values across key fields. This notebook prepares the dataset for exploratory and business analysis, enabling questions around pricing strategy, cuisine performance, and location-based investment decisions.

## Objectives
- Deleting redundant columns
- Renaming the columns
- Dropping duplicates
- Cleaning individual columns
- Remove the NaN values from the dataset
- Check for some more Transformations

## Tools and Libraries
- Python
- Pandas

## Key Steps

### Initial Exploration

Loaded the raw dataset (51,717 rows, 17 columns) and inspected data types, null counts, and column structure using data.info() and data.shape to understand the scope of cleaning required before making any changes.

### Removing Redundant Columns

url, address, phone, location, rest_type, cuisines, reviews_list, menu_item, listed_in(type), listed_in(city)) that were either non-analytical, free-text fields unsuitable for structured analysis, or outside the scope of the business questions being answered. Retained 7 columns focused on restaurant identity, ordering features, ratings, and cost.

### Standardizing Column Names

Renamed all columns using a capitalisation loop to ensure consistent, readable naming conventions across the dataset, replacing the original inconsistent mix of lowercase and snake_case labels.

### Removing Duplicate Records

Identified 29,103 duplicate rows (56% of the dataset) using duplicated().sum(). All duplicates were removed using drop_duplicates(), reducing the dataset to 22,614 unique records.
