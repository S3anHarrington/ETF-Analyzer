# ETF-Analyzer
Create a Web Application for an ETF Analyzer

In this Challenge assignment, you’ll build a financial database and web application by using SQL, Python, and the Voilà library to analyze the performance of a hypothetical fintech ETF.

Instructions:

Use this notebook to complete your analysis of a fintech ETF that consists of four stocks: GOST, GS, PYPL, and SQ. Each stock has its own table in the etf.db database, which the Starter_Code folder also contains.

Analyze the daily returns of the ETF stocks both individually and as a whole. Then deploy the visualizations to a web application by using the Voilà library.

The detailed instructions are divided into the following parts:

Analyze a single asset in the ETF

Optimize data access with Advanced SQL queries

Analyze the ETF portfolio

Deploy the notebook as a web application

Analyze a Single Asset in the ETF

For this part of the assignment, you’ll use SQL queries with Python, Pandas, and hvPlot to analyze the performance of a single asset from the ETF.

Complete the following steps:

Write a SQL SELECT statement by using an f-string that reads all the PYPL data from the database. Using the SQL SELECT statement, execute a query that reads the PYPL data from the database into a Pandas DataFrame.

Use the head and tail functions to review the first five and the last five rows of the DataFrame. Make a note of the beginning and end dates that are available from this dataset. You’ll use this information to complete your analysis.

Using hvPlot, create an interactive visualization for the PYPL daily returns. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.

Using hvPlot, create an interactive visualization for the PYPL cumulative returns. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.

Optimize Data Access with Advanced SQL Queries

For this part of the assignment, you’ll continue to analyze a single asset (PYPL) from the ETF. You’ll use advanced SQL queries to optimize the efficiency of accessing data from the database.

Complete the following steps:

Access the closing prices for PYPL that are greater than 200 by completing the following steps:

Write a SQL SELECT statement to select the dates where the PYPL closing price was higher than 200.0.

Using the SQL statement, read the data from the database into a Pandas DataFrame, and then review the resulting DataFrame.

Select the “time” and “close” columns for those dates where the closing price was higher than 200.0.

Find the top 10 daily returns for PYPL by completing the following steps:

Write a SQL statement to find the top 10 PYPL daily returns. Make sure to do the following:

Use SELECT to select only the “time” and “daily_returns” columns.

Use ORDER to sort the results in descending order by the “daily_returns” column.

Use LIMIT to limit the results to the top 10 daily return values.

Using the SQL statement, read the data from the database into a Pandas DataFrame, and then review the resulting DataFrame.

Analyze the ETF Portfolio

For this part of the assignment, you’ll build the entire ETF portfolio and then evaluate its performance. To do so, you’ll build the ETF portfolio by using SQL joins to combine all the data for each asset.

Complete the following steps:

Write a SQL query to join each table in the portfolio into a single DataFrame. To do so, complete the following steps:

Use a SQL inner join to join each table on the “time” column. Access the “time” column in the GDOT table via the GDOT.time syntax. Access the “time” columns from the other tables via similar syntax.

Using the SQL query, read the data from the database into a Pandas DataFrame. Review the resulting DataFrame.

Create a DataFrame that averages the “daily_returns” columns for all four assets. Review the resulting DataFrame.

Hint Assuming that this ETF contains equally weighted returns, you can average the returns for each asset to get the average returns of the portfolio. You can then use the average returns of the portfolio to calculate the annualized returns and the cumulative returns. For the calculation to get the average daily returns for the portfolio, use the following code:

etf_portfolio_returns = etf_portfolio['daily_returns'].mean(axis=1)
You can use the average daily returns of the portfolio the same way that you used the daily returns of a single asset.

Use the average daily returns in the etf_portfolio_returns DataFrame to calculate the annualized returns for the portfolio. Display the annualized return value of the ETF portfolio.

Hint To calculate the annualized returns, multiply the mean of the etf_portfolio_returns values by 252.

To convert the decimal values to percentages, multiply the results by 100.

Use the average daily returns in the etf_portfolio_returns DataFrame to calculate the cumulative returns of the ETF portfolio.

Using hvPlot, create an interactive line plot that visualizes the cumulative return values of the ETF portfolio. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.

Deploy the Notebook as a Web Application

For this part of the assignment, complete the following steps:

Use the Voilà library to deploy your notebook as a web application. You can deploy the web application locally on your computer.

Take a screen recording or screenshots to show how the web application appears when using Voilà. Include the recording or screenshots in the README.md file for your GitHub repository.

Review the following code which imports the required libraries, initiates your SQLite database, popluates the database with records from the etf.db seed file that was included in your Starter_Code folder, creates the database engine, and confirms that data tables that it now contains.
[1]:

# Importing the required libraries and dependencies
import numpy as np
import pandas as pd
import hvplot.pandas
import sqlalchemy
​
# Create a temporary SQLite database and populate the database with content from the etf.db seed file
database_connection_string = 'sqlite:///etf.db'
​
# Create an engine to interact with the SQLite database
engine = sqlalchemy.create_engine(database_connection_string)
​
# Confirm that table names contained in the SQLite database.
engine.table_names()
/var/folders/hn/z9s0kkts3nq44rn55_b365r40000gn/T/ipykernel_1682/3092246052.py:14: SADeprecationWarning: The Engine.table_names() method is deprecated and will be removed in a future release.  Please refer to Inspector.get_table_names(). (deprecated since: 1.4)
  engine.table_names()
[1]:
['GDOT', 'GS', 'PYPL', 'SQ']
Analyze a single asset in the FinTech ETF

For this part of the assignment, you’ll use SQL queries with Python, Pandas, and hvPlot to analyze the performance of a single asset from the ETF.

Complete the following steps:

Write a SQL SELECT statement by using an f-string that reads all the PYPL data from the database. Using the SQL SELECT statement, execute a query that reads the PYPL data from the database into a Pandas DataFrame.

Use the head and tail functions to review the first five and the last five rows of the DataFrame. Make a note of the beginning and end dates that are available from this dataset. You’ll use this information to complete your analysis.

Using hvPlot, create an interactive visualization for the PYPL daily returns. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.

Using hvPlot, create an interactive visualization for the PYPL cumulative returns. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.

Step 1: Write a SQL SELECT statement by using an f-string that reads all the PYPL data from the database. Using the SQL SELECT statement, execute a query that reads the PYPL data from the database into a Pandas DataFrame.
[8]:

# Write a SQL query to SELECT all of the data from the PYPL table
query = f'SELECT * FROM pypl' 
​
# Use the query to read the PYPL data into a Pandas DataFrame
pypl_dataframe = pd.read_sql_query(query, con=engine)
​
Step 2: Use the head and tail functions to review the first five and the last five rows of the DataFrame. Make a note of the beginning and end dates that are available from this dataset. You’ll use this information to complete your analysis.
[9]:

# View the first 5 rows of the DataFrame.
pypl_dataframe.head()
[9]:
time	open	high	low	close	volume	daily_returns
0	2016-12-16 00:00:00.000000	39.90	39.90	39.12	39.32	7298861	-0.005564
1	2016-12-19 00:00:00.000000	39.40	39.80	39.11	39.45	3436478	0.003306
2	2016-12-20 00:00:00.000000	39.61	39.74	39.26	39.74	2940991	0.007351
3	2016-12-21 00:00:00.000000	39.84	40.74	39.82	40.09	5826704	0.008807
4	2016-12-22 00:00:00.000000	40.04	40.09	39.54	39.68	4338385	-0.010227
[10]:

# View the last 5 rows of the DataFrame.
pypl_dataframe.tail()
[10]:
time	open	high	low	close	volume	daily_returns
994	2020-11-30 00:00:00.000000	212.51	215.83	207.0900	214.200	8992681	0.013629
995	2020-12-01 00:00:00.000000	217.15	220.57	214.3401	216.520	9148174	0.010831
996	2020-12-02 00:00:00.000000	215.60	215.75	210.5000	212.660	6414746	-0.017827
997	2020-12-03 00:00:00.000000	213.33	216.93	213.1100	214.680	6463339	0.009499
998	2020-12-04 00:00:00.000000	214.88	217.28	213.0100	217.235	2118319	0.011901
Step 3: Using hvPlot, create an interactive visualization for the PYPL daily returns. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.
[24]:

# Create an interactive visualization with hvplot to plot the daily returns for PYPL.
pypl_dataframe.hvplot.line(figsize=(15,10), x='time',y=['daily_returns'],title="PYPL Daily Returns")
[24]:
Step 4: Using hvPlot, create an interactive visualization for the PYPL cumulative returns. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.
[25]:

# Create an interactive visaulization with hvplot to plot the cumulative returns for PYPL.
((pypl_dataframe['daily_returns'] + 1).cumprod() - 1).hvplot.line(figsize=(15,10), x='Time',title="PYPL Cumulative Returns")
[25]:
Optimize the SQL Queries

For this part of the assignment, you’ll continue to analyze a single asset (PYPL) from the ETF. You’ll use advanced SQL queries to optimize the efficiency of accessing data from the database.

Complete the following steps:

Access the closing prices for PYPL that are greater than 200 by completing the following steps:

Access the closing prices for PYPL that are greater than 200 by completing the following steps:

Write a SQL SELECT statement to select the dates where the PYPL closing price was higher than 200.0.

Select the “time” and “close” columns for those dates where the closing price was higher than 200.0.

Using the SQL statement, read the data from the database into a Pandas DataFrame, and then review the resulting DataFrame.

Find the top 10 daily returns for PYPL by completing the following steps:

Write a SQL statement to find the top 10 PYPL daily returns. Make sure to do the following:

Use SELECT to select only the “time” and “daily_returns” columns.

Use ORDER to sort the results in descending order by the “daily_returns” column.

Use LIMIT to limit the results to the top 10 daily return values.

Using the SQL statement, read the data from the database into a Pandas DataFrame, and then review the resulting DataFrame.

Step 1: Access the closing prices for PYPL that are greater than 200 by completing the following steps:

- Write a SQL `SELECT` statement to select the dates where the PYPL closing price was higher than 200.0.

- Select the “time” and “close” columns for those dates where the closing price was higher than 200.0.

- Using the SQL statement, read the data from the database into a Pandas DataFrame, and then review the resulting DataFrame.
[15]:

# Write a SQL SELECT statement to select the time and close columns 
# where the PYPL closing price was higher than 200.0.
second_query = f"SELECT close, time FROM pypl WHERE close > 200"
​
# Using the query, read the data from the database into a Pandas DataFrame
pypl_higher_than_200 = pd.read_sql_query(second_query, con=engine)
​
# Review the resulting DataFrame
pypl_higher_than_200.head()
[15]:
close	time
0	202.92	2020-08-05 00:00:00.000000
1	204.09	2020-08-06 00:00:00.000000
2	201.71	2020-08-25 00:00:00.000000
3	203.53	2020-08-26 00:00:00.000000
4	204.34	2020-08-27 00:00:00.000000
Step 2: Find the top 10 daily returns for PYPL by completing the following steps:

-  Write a SQL statement to find the top 10 PYPL daily returns. Make sure to do the following:

    * Use `SELECT` to select only the “time” and “daily_returns” columns.

    * Use `ORDER` to sort the results in descending order by the “daily_returns” column.

    * Use `LIMIT` to limit the results to the top 10 daily return values.

- Using the SQL statement, read the data from the database into a Pandas DataFrame, and then review the resulting DataFrame.
[16]:

# Write a SQL SELECT statement to select the time and daily_returns columns
# Sort the results in descending order and return only the top 10 return values
third_query = """
SELECT time, daily_returns 
FROM pypl
ORDER BY daily_returns DESC
LIMIT 10;
"""
​
# Using the query, read the data from the database into a Pandas DataFrame
pypl_top_10_returns = pd.read_sql_query(third_query, con=engine)
​
​
# Review the resulting DataFrame
pypl_top_10_returns
[16]:
time	daily_returns
0	2020-03-24 00:00:00.000000	0.140981
1	2020-05-07 00:00:00.000000	0.140318
2	2020-03-13 00:00:00.000000	0.138700
3	2020-04-06 00:00:00.000000	0.100877
4	2018-10-19 00:00:00.000000	0.093371
5	2019-10-24 00:00:00.000000	0.085912
6	2020-11-04 00:00:00.000000	0.080986
7	2020-03-10 00:00:00.000000	0.080863
8	2020-04-22 00:00:00.000000	0.075321
9	2018-12-26 00:00:00.000000	0.074656
Analyze the Fintech ETF Portfolio

For this part of the assignment, you’ll build the entire ETF portfolio and then evaluate its performance. To do so, you’ll build the ETF portfolio by using SQL joins to combine all the data for each asset.

Complete the following steps:

Write a SQL query to join each table in the portfolio into a single DataFrame. To do so, complete the following steps:

Use a SQL inner join to join each table on the “time” column. Access the “time” column in the GDOT table via the GDOT.time syntax. Access the “time” columns from the other tables via similar syntax.

Using the SQL query, read the data from the database into a Pandas DataFrame. Review the resulting DataFrame.

Create a DataFrame that averages the “daily_returns” columns for all four assets. Review the resulting DataFrame.

Hint Assuming that this ETF contains equally weighted returns, you can average the returns for each asset to get the average returns of the portfolio. You can then use the average returns of the portfolio to calculate the annualized returns and the cumulative returns. For the calculation to get the average daily returns for the portfolio, use the following code:

etf_portfolio_returns = etf_portfolio['daily_returns'].mean(axis=1)
You can use the average daily returns of the portfolio the same way that you used the daily returns of a single asset.

Use the average daily returns in the etf_portfolio_returns DataFrame to calculate the annualized returns for the portfolio. Display the annualized return value of the ETF portfolio.

Hint To calculate the annualized returns, multiply the mean of the etf_portfolio_returns values by 252.

To convert the decimal values to percentages, multiply the results by 100.

Use the average daily returns in the etf_portfolio_returns DataFrame to calculate the cumulative returns of the ETF portfolio.

Using hvPlot, create an interactive line plot that visualizes the cumulative return values of the ETF portfolio. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.

Step 1: Write a SQL query to join each table in the portfolio into a single DataFrame. To do so, complete the following steps:

- Use a SQL inner join to join each table on the “time” column. Access the “time” column in the `GDOT` table via the `GDOT.time` syntax. Access the “time” columns from the other tables via similar syntax.

- Using the SQL query, read the data from the database into a Pandas DataFrame. Review the resulting DataFrame.
[17]:

# Wreate a SQL query to join each table in the portfolio into a single DataFrame 
# Use the time column from each table as the basis for the join
query = """
SELECT gdot.time, gdot.daily_returns, gs.daily_returns, pypl.daily_returns, sq.daily_returns, gdot.close, gs.close, pypl.close, sq.close, gdot.high, gs.high, pypl.high, sq.high, gdot.volume, gs.volume, pypl.volume, sq.volume 
FROM (((gdot
INNER JOIN gs ON gdot.time= gs.time)
INNER JOIN pypl ON gdot.time = pypl.time)
INNER JOIN sq ON gdot.time = sq.time);
"""
​
# Using the query, read the data from the database into a Pandas DataFrame
etf_portfolio = pd.read_sql_query(query, con=engine)
​
# Review the resulting DataFrame
etf_portfolio.head()
[17]:
time	daily_returns	daily_returns	daily_returns	daily_returns	close	close	close	close	high	high	high	high	volume	volume	volume	volume
0	2016-12-16 00:00:00.000000	-0.023218	-0.016708	-0.005564	0.017339	23.980	238.94	39.32	14.375	24.73	243.19	39.90	14.47	483544	5017963	7298861	4516341
1	2016-12-19 00:00:00.000000	-0.007923	0.000795	0.003306	-0.001043	23.790	239.13	39.45	14.360	24.01	239.74	39.80	14.60	288149	2970314	3436478	3944657
2	2016-12-20 00:00:00.000000	0.001261	0.016602	0.007351	0.009053	23.820	243.10	39.74	14.490	23.94	243.65	39.74	14.82	220341	3268700	2940991	5207412
3	2016-12-21 00:00:00.000000	0.001679	-0.006911	0.008807	-0.007591	23.860	241.42	40.09	14.380	23.97	242.40	40.74	14.54	249189	2604678	5826704	3901738
4	2016-12-22 00:00:00.000000	0.006077	-0.005178	-0.010227	-0.023644	24.005	240.17	39.68	14.040	24.01	242.86	40.09	14.34	383139	2026506	4338385	3874004
Step 2: Create a DataFrame that averages the “daily_returns” columns for all four assets. Review the resulting DataFrame.
[18]:

# Create a DataFrame that displays the mean value of the “daily_returns” columns for all four assets.
etf_portfolio_returns = etf_portfolio['daily_returns'].mean(axis=1)
​
# Review the resulting DataFrame
etf_portfolio_returns.head()
[18]:
0   -0.007038
1   -0.001216
2    0.008567
3   -0.001004
4   -0.008243
dtype: float64
Step 3: Use the average daily returns in the etf_portfolio_returns DataFrame to calculate the annualized returns for the portfolio. Display the annualized return value of the ETF portfolio.
[19]:

# Use the average daily returns provided by the etf_portfolio_returns DataFrame 
# to calculate the annualized return for the portfolio. 
trading_days = 252
annualized_etf_portfolio_returns = etf_portfolio_returns * trading_days
​
# Display the annualized return value of the ETF portfolio.
annualized_etf_portfolio_returns.head()
[19]:
0   -1.773496
1   -0.306518
2    2.158814
3   -0.252987
4   -2.077206
dtype: float64
Step 4: Use the average daily returns in the etf_portfolio_returns DataFrame to calculate the cumulative returns of the ETF portfolio.
[20]:

# Use the average daily returns provided by the etf_portfolio_returns DataFrame 
# to calculate the cumulative returns
etf_cumulative_returns = (1 + etf_portfolio_returns).cumprod()
​
# Display the final cumulative return value
etf_cumulative_returns.tail()
[20]:
994    4.374534
995    4.357078
996    4.329679
997    4.378371
998    4.418250
dtype: float64
Step 5: Using hvPlot, create an interactive line plot that visualizes the cumulative return values of the ETF portfolio. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.
[23]:

# Using hvplot, create an interactive line plot that visualizes the ETF portfolios cumulative return values.
etf_cumulative_returns.hvplot.line(figsize=(15,10), x='time', title="ETF Portfolio Cumulative Returns")
[23]:
