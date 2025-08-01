# 🚴‍♂️ MongoDB Data Engineering Project: Bike Rentals Analysis

This project is part of my **Data Engineer formation** and focuses on working with a dataset of bike-sharing trips using **MongoDB**, **Python**, and **data cleaning and analysis pipelines**.

We use real-world trip data (`trips_.json`) and apply data quality checks, anomaly detection, and aggregation queries to extract valuable insights.

---

## 📂 Project Structure

- `trips_.json`: Original dataset
- `cleaned_trips.json`: Cleaned and validated data
- `cas_pratique_mongodb_2.ipynb`: Jupyter notebook with all analysis steps
- `README.md`: This file 🙂

---

## 🧹 Data Cleaning & Anomaly Detection

We first cleaned the dataset and saved it to `cleaned_trips.json`. Then we loaded it into MongoDB and applied a series of checks using PyMongo to detect common data issues:

### ✅ Anomaly Detection Functions

| Check | Description |
|-------|-------------|
| `detect_overlapping_bike_rentals()` | Flags cases where the same bike is rented by two users at overlapping times |
| `detect_underage_users()` | Flags users under 13 years old (based on `birth_year`) |
| `detect_missing_birth_year()` | Flags users with missing `birth_year` |
| `detect_very_short_rentals()` | Flags trips with a duration of 1 second or less |
| `detect_duration_mismatches()` | Flags records where the calculated time difference doesn’t match `tripduration` |

Each detection function adds an `"anomaly"` field to the affected documents for easy tracking.

---

## Aggregation Queries

Using MongoDB aggregation operators (`$match`, `$group`, `$sort`, `$limit`, `$expr`, `$hour`, etc.), we answered the following business questions:

### 1. Top 5 Most Frequent Trips by Female Users
### 2. Number of Trips by Usertype on January 1
### 3. Average Trip Duration (7 AM – 9 AM) by Start Station
### 4. Top 3 Most Frequent Start Stations (6 AM – 8 AM)
### 5. Replace all gender 0 to gender 1

## Technologies Used
- Python (Jupyter Notebook)
- MongoDB (via Docker container)
- PyMongo (MongoDB connector for Python)
- VS Code
- JSON files for input/output
