# A complete analysis project using SQL (PostgreSQL) Tesla company
## Project Overview:
  #### In this project we aim to analysis the prices of Tesla, to check is the year 2025 is best year to invest in Tesla, or the company towards the edge.

### Data source:
    The data comes from yahoo finace from 2010 to 2025
    Downloaded as CSV file
    Contains information about the date, open price, close price, volume
  
## Tools:
- Python (Jupyter notebook)
- SQL (postgreSQL)
## Python:
  - installing yfinance package for yahoo finance website
  - download data of tesla as csv from yahoo finance
### SQL:
  - creating database
  - Create table in database 
  - copy the content from CSV to the table in the database
### Analysis:
  - Starting Analysis
### Final Story: 
## Data Extraction ( Using Python ):
1- installing yfinance package for yahoo finance website
in jupyter notebook

    - !pip install yfinance

2- download data of tesla as csv from yahoo finance

  - import yfinance as yf

3- Download TSLA data for  specified period

  - data = yf.download("TSLA", start="2010-06-26", end="2025-03-23")

4- Save to CSV
  - data.to_csv("TSLA_historical.csv")
## Data Transformation and Data Loading ( using SQL ):
 1- creating database
 
  - CREATE DATABASE tsla;
    
2- Create table in database

in query tool:
 - CREATE TABLE Tsla_prices
(
stock_date date,
close_price numeric(20,6),
high_price numeric(20,6),
low_price numeric(20,6),
open_price numeric(20,6),
volume bigint
);
  
## Data Exploration and analysis:
  1- List the  dates where the close price was greater than the average of close price
  - SELECT stock_date, close_price, open_price
FROM Tsla_prices
WHERE close_price >= 
(
SELECT AVG(close_price)
FROM Tsla_prices)
ORDER BY date, close_price DESC
;
  
  2- List the dates where the volume was greater than the average
  - SELECT stock_date, volume
FROM Tsla_prices
WHERE volume >=
(
SELECT AVG(volume)
FROM Tsla_prices
)
ORDER BY stock_date, volume DESC;
  
  3- List the dates for top 10 close prices
  - SELECT stock_date, MAX(close_price)
FROM Tsla_prices
GROUP BY stock_date
ORDER BY stock_date DESC;

- SELECT stock_date, MAX(close_price)
FROM Tsla_prices
GROUP BY stock_date
ORDER BY stock_date DESC
LIMIT 10;

  4- List the dates for least 10 close price
  
  - ELECT stock_date, MIN(close_price)
FROM Tsla_prices
GROUP BY stock_date
ORDER BY  MAX(close_price) DESC
LIMIT 10;



  
