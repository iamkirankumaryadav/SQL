# `Time Series`

### `Characteristics`

1. Sequene of data points
2. Timestamp
3. Regular intervals ( Frequency: Fixed interval between measurements )
4. Measurements

Measurements | Time Unit | Unit of Measure
:--- | :--- | :---
CPU Utilization | Microseconds | Percentage
Newtwork I/O | Seconds | MB
Units Produced | Minutes | Count
Customers Served | Hours | Count
Packages Delivered | Days | Count
Auto Accidents | Months | Count
Company Profit | Quarterly | Money
Births and Deaths | Annualy | Count

### `Metric types`

1. `Counter` :  Monotonically increases ( Number of cars passing through toll booth )
2. `Gauge` : Numerical measure that goes up and down ( Temperature )
3. `Summary` : Calculate values over time window, groups, such as count or amount.
4. `Histograms` : Counts of items ( Frequency ) over buckets.

### `Examples`

1. Stock market data ( Price of stock at a particular instance of time )
2. Time tide tables ( High and low tides time )
3. Performance monitoring ( Monitoring sofware, servers, industrial usage )
4. Health monitoring ( Measuring heart rate, ECG,  )
5. Population statics ( Rise in population after decades )
6. Business performance ( Profit over quarters or last year )

### Data Ingestion

- Time series data is collected in `continuous series` ( Each second or minute creates a new row in relational database )
- Split large tables by rows into range partitions ( Partition by Year, Quarter, Month or Week )
- `date`, `datetime` and `timestamp` are used for creating partitions without overlapping.
- Latest data are on the top of relational data.
- Helps in comparing performance, sale or profit same time last year.
- Drop or summarize data after a period of time.

### `Query Patterns`

- We often query the latest data.
- Comparing time periods ( Average revenue this quarter and previous quarter )
- Summarize time window by aggregating data of larger time intervals.
