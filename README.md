## COMP6940 Assignment 1 – Part 1  
### NYC Yellow Taxi (January 2023): Demand, Pricing, and Temporal Patterns

This repository contains the implementation for **COMP6940: Big Data and Data Visualization – Assignment 1 (Part 1)**.

The objective of this project is to analyze **NYC Yellow Taxi trip data for January 2023** to understand taxi demand patterns, pricing behavior, and temporal trends. The analysis includes data ingestion, cleaning, feature engineering, statistical aggregation, window-based metrics, and exploratory visualizations.

---

## Repository Structure

project/
├── README.md  
├── requirements.txt  
├── data/  
│   ├── raw/  
│   │   ├── tlc/  
│   │   └── lookup/  
│   └── curated/  
│       └── part1_taxi_curated.parquet  
└── part1_taxi/  
&nbsp;&nbsp;&nbsp;&nbsp;├── 01_ingest.ipynb  
&nbsp;&nbsp;&nbsp;&nbsp;├── 02_clean_features.ipynb  
&nbsp;&nbsp;&nbsp;&nbsp;├── 03_stats_eda_viz.ipynb  
&nbsp;&nbsp;&nbsp;&nbsp;├── report.pdf  
&nbsp;&nbsp;&nbsp;&nbsp;└── data_dictionary.pdf  

---

## Dataset Sources

The datasets used in this project come from the **NYC Taxi & Limousine Commission (TLC)**.

Taxi Trip Data (January 2023)  
https://d37ci6vzurychx.cloudfront.net/trip-data/yellow_tripdata_2023-01.parquet

Taxi Zone Lookup Table  
https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv

Official Documentation  
https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

---

## How to Run the Project

Clone the repository:
```
git clone https://github.com/zuhrahmoh/COMP6940__A1.git  
cd COMP6940__A1  
```
Install required Python packages:
```
pip install -r requirements.txt  
```
Run the notebooks **in the following order**.

---

## 1. Data Ingestion

Notebook:  
`part1_taxi/01_ingest.ipynb`

This notebook performs the following tasks:

- Downloads the NYC taxi dataset and taxi zone lookup table
- Saves the raw files into the following directories:

data/raw/tlc/  
data/raw/lookup/

- Loads both datasets using Pandas
- Prints dataset metadata including:
  - Row counts
  - Column names
  - Data types
  - Null counts

---

## 2. Data Cleaning and Feature Engineering

Notebook:  
`part1_taxi/02_clean_features.ipynb`

This notebook:

- Merges taxi zone lookup data with trip records
- Creates time-based features such as pickup date, hour, weekday, and week of year
- Constructs engineered metrics including trip duration, speed, fare per mile, and tip rate
- Applies required cleaning rules
- Reports the number of rows removed by each rule
- Saves the curated dataset to:

`data/curated/part1_taxi_curated.parquet`

---

## 3. Statistics, EDA, and Visualizations

Notebook:  
`part1_taxi/03_stats_eda_viz.ipynb`

This notebook performs statistical analysis and exploratory data analysis.

### Groupby Metrics

- Daily trip counts grouped by pickup borough and date
- Mean and median fare amount and trip distance by borough and weekday
- Proportion of trips by payment type for each pickup hour
- Mean tip rate grouped by distance bucket

### Window Metrics

- 7-day rolling mean of daily trip counts by borough
- Day-over-day difference in trip counts
- Day-over-day percent change in trip counts

### EDA Questions

1. Which borough has the strongest weekday effect  
2. Identification of anomalous daily trip volumes using z-scores  
3. Determining whether tip rate is more strongly associated with pickup hour or distance bucket  

### Visualizations

1. Daily trip time series by borough with a 7-day rolling average  
2. Before/after cleaning distribution of trip duration  
3. Relationship between trip distance and fare amount  
4. Heatmap of average trips by weekday and pickup hour  

---

## Curated Dataset

The curated dataset contains cleaned and engineered features including:

### Geography
- PULocationID
- DOLocationID
- PU_borough
- PU_zone
- DO_borough
- DO_zone

### Time
- tpep_pickup_datetime
- tpep_dropoff_datetime
- pickup_date
- pickup_hour
- weekday
- week_of_year

### Core Numeric Fields
- passenger_count
- trip_distance
- fare_amount
- tip_amount
- total_amount
- payment_type

### Engineered Fields
- trip_duration_min
- speed_mph
- fare_per_mile
- tip_rate
- distance_bucket

Detailed descriptions of each field are available in:

`part1_taxi/data_dictionary.pdf`

---

## Reproducibility

To reproduce the entire analysis pipeline:

1. Install dependencies using requirements.txt
2. Run the notebooks sequentially:
   - 01_ingest.ipynb
   - 02_clean_features.ipynb
   - 03_stats_eda_viz.ipynb

The notebooks will automatically download raw data, generate the curated dataset, and reproduce all analysis outputs.

---

## Authors

COMP6940 Assignment 1 – Group Submission

Group Members:

- Dillon Carl - 816029891
- Elena Panchoo - 816034966
- Eysah Ali - 816030849
- Zuhrah Mohammed - 816036112
  

---

### Academic Use

This repository was created for academic coursework at **The University of the West Indies** as part of the COMP6940 Big Data and Data Visualization course.
