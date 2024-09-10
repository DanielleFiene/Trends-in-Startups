# Startups Database Analysis Project

## Project Overview

This project demonstrates the use of SQL queries to analyze a dataset of startups. The dataset contains information such as the name of the startup, its category, valuation, number of employees, and other key metrics. The queries cover fundamental SQL operations like aggregation, filtering, and grouping to extract meaningful insights from the data.

## SQL Queries and Their Purpose

### 1. **Retrieve All Data**
```sql
SELECT * FROM startups;
```
- **Purpose**: Fetches all columns and rows from the `startups` table, giving a complete view of the dataset.

### 2. **Count the Number of Startups**
```sql
SELECT COUNT(*) FROM startups;
```
- **Purpose**: Counts the total number of startups in the dataset.

### 3. **Calculate Total Valuation**
```sql
SELECT SUM(valuation) FROM startups;
```
- **Purpose**: Sums up the valuations of all startups, providing the total valuation in the dataset.

### 4. **Find the Maximum Amount Raised by SEED-Stage Startups**
```sql
SELECT MAX(raised) FROM startups
WHERE stage = 'SEED';
```
- **Purpose**: Finds the highest amount raised by startups at the "SEED" funding stage.

### 5. **Find the Earliest Founded Startup**
```sql
SELECT MIN(founded) FROM startups;
```
- **Purpose**: Identifies the oldest startup by finding the minimum founding year.

### 6. **Calculate the Average Valuation**
```sql
SELECT AVG(valuation) FROM startups;
```
- **Purpose**: Provides the average valuation of all startups in the dataset.

### 7. **Average Valuation by Category**
```sql
SELECT category, AVG(valuation) FROM startups
GROUP BY category;
```
- **Purpose**: Calculates the average valuation for each startup category.

### 8. **Rounded Average Valuation by Category**
```sql
SELECT category, ROUND(AVG(valuation), 2) FROM startups
GROUP BY category;
```
- **Purpose**: Same as the previous query but rounds the average valuation to two decimal places for better readability.

### 9. **Sorted Average Valuation by Category**
```sql
SELECT category, ROUND(AVG(valuation), 2) FROM startups
GROUP BY 1
ORDER BY 2 DESC;
```
- **Purpose**: Groups startups by category and sorts them by their average valuation in descending order.

### 10. **Count Startups by Category**
```sql
SELECT category, COUNT(*) FROM startups
GROUP BY 1;
```
- **Purpose**: Counts how many startups exist in each category.

### 11. **Count Startups by Category with More Than 3 Startups**
```sql
SELECT category, COUNT(*) FROM startups
GROUP BY 1
HAVING COUNT(*) > 3
ORDER BY 2 DESC;
```
- **Purpose**: Filters categories that have more than 3 startups and orders the results by the number of startups in descending order.

### 12. **Average Number of Employees by Location**
```sql
SELECT ROUND(AVG(employees)), location FROM startups
GROUP BY 2
ORDER BY 1 DESC;
```
- **Purpose**: Calculates the average number of employees for startups in each location and orders them by the highest average.

### 13. **Locations with More Than 500 Average Employees**
```sql
SELECT ROUND(AVG(employees)), location FROM startups
GROUP BY 2
HAVING AVG(employees) > 500;
```
- **Purpose**: Lists locations where startups have an average of more than 500 employees.

## Key Concepts Learned

- **Aggregation Functions**: Used functions like `COUNT()`, `SUM()`, `AVG()`, `MAX()`, and `MIN()` to analyze startup data.
- **Grouping**: Utilized `GROUP BY` to segment data by categories or locations for more detailed analysis.
- **Filtering Groups**: Applied the `HAVING` clause to filter groups based on conditions (e.g., categories with more than 3 startups).
- **Sorting Results**: Used `ORDER BY` to sort the results based on different criteria like average valuation and number of employees.
- **Data Formatting**: Applied `ROUND()` to control the precision of numeric data for better readability.

## How to Use This Project

1. **Setup SQLite**:
   - If you're using SQLite, ensure you have it installed. You can install it via the terminal:
     ```sh
     sudo apt-get install sqlite3
     ```

2. **Load the Dataset**:
   - Create a `startups.db` database and import the dataset (which could be in CSV format).
   - Use the following commands to import data:
     ```sql
     .mode csv
     .import 'startups.csv' startups
     ```

3. **Run the Queries**:
   - Execute the provided queries in the SQLite command line or any other SQL environment (like DBeaver, DB Browser for SQLite, etc.) to see the results.

## Conclusion

This project demonstrates fundamental SQL skills in working with a database of startups. It covers essential SQL operations like selecting, grouping, and filtering data, providing insights into the startup ecosystem based on categories, valuations, employee count, and more. These skills are highly transferable and useful for data analysis in any domain that relies on structured data storage.
