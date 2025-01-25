## Overview

This project focuses on building a data warehouse for analyzing flight punctuality data. It involves schema design, data population, and creating actionable visualizations using Tableau to extract insights. The aim is to showcase the benefits of data warehousing and advanced analytics in the airline industry.

## Project Goals

1. **Create a centralized data warehouse** for flight punctuality data to facilitate analytics.
2. **Implement a star schema** to enable efficient querying and reporting.
3. **Populate tables with data** processed using Python and Microsoft Excel.
4. **Generate visualizations** in Tableau to extract insights into flight punctuality, delays, and operational efficiency.


## Schema Design

A **star schema** was used with the following entities:
- **Fact Table**: `FLIGHT_PUNCTUALITY_FACT`
- **Dimension Tables**:
  - `AIRPORT_DIM`
  - `AIRLINE_DIM`
  - `DATE_DIM`
  - `ORIGIN_DESTINATION_DIM`
  - `ORIGIN_DESTINATION_COUNTRY_DIM`  
- **Final Schema Design**:  
![Schema-Img](images/schema.jpg)


## Table Definitions

### Example: `FLIGHT_PUNCTUALITY_FACT`
```sql
CREATE TABLE FLIGHT_PUNCTUALITY_FACT (
    FLIGHT_PUNCTUALITY_ID NUMBER PRIMARY KEY,
    NUMBER_FLIGHTS_MATCHED NUMBER,
    FLIGHTS_CANCELLED_PERCENT NUMBER,
    FLIGHT_TYPE VARCHAR2(100),
    ...
    AVERAGE_DELAY_MINS NUMBER,
    REPORTING_AIRPORT_CODE VARCHAR2(3),
    ORIGIN_DESTINATION_ID NUMBER,
    ARLINE_CODE VARCHAR2(5),
    FOREIGN KEY (REPORTING_AIRPORT_CODE) REFERENCES AIRPORT_DIM(REPORTING_AIRPORT_CODE),
    ...
);
```



## Data Processing and Population

1. **Combining Files**: 
   - Used Python's Pandas library to merge monthly CSV files into one dataset.
   - Handled encoding issues and missing columns.

2. **Transformations**:
   - Converted columns into appropriate formats (e.g., percentages, date).
   - Added new columns such as `reporting_airport_code` and `airline_code`.

3. **Database Loading**:
   - Populated tables using Oracle APEX Object Browser by mapping processed CSVs.



## Visualizations

### Created using Tableau:
1. **Punctuality of Top UK Airlines**:
   - Highlights airlines' early or delayed performance.  
    ![visualization1](/images/Punctuality%20of%20Top%20UK%20airlines.jpg)
   
2. **Flights Delay Pattern**:
    - Classifies delays into short and long categories.  
    ![visualization2](/images/Flights%20Delay%20Patterns%20Classifying%20Short%20and%20Long%20Delays.jpg)
   
3. **Average Delay Trends**:
   - Tracks delay trends across reporting periods.  
   ![visualization3](/images/Trend%20Analysis%20of%20Average%20Delay%20Minutes%20Over%20Time.jpg)
4. **Flight Cancellations**:
   - Analyzes airports with the highest cancellations.  
   ![visualization4](/images/Flight%20Cancellations%20Top%205%20Airports%20vs.%20Others.jpg)
5. **Flight Activity Insights**:
   - Identifies top airports based on matched flights.  
    ![visualization5](/images/Flight%20Activity%20Insights.jpg)



## Key Insights

1. **On-Time Performance**:
   - Jet2.com leads in punctuality with 64.1% early/on-time flights.
2. **Delay Trends**:
   - Summer months experience the highest delays.
3. **Top Airports**:
   - Heathrow, Gatwick, and Manchester dominate flight activity and cancellations.



## How to Run

1. **Database Setup**:
   - Load data using processed CSVs.

2. **Visualization**:
   - Import the Tableau workbook (`.twb`) and connect it to the database.

