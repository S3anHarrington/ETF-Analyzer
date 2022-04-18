# ETF-Analyzer
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

![Screen Shot 2022-01-22 at 16 17 10](https://user-images.githubusercontent.com/91238235/150659698-0e00c5d8-ec90-4095-af61-b5096c74a3e8.png)

Analyze a single asset in the FinTech ETF

For this part of the assignment, you’ll use SQL queries with Python, Pandas, and hvPlot to analyze the performance of a single asset from the ETF.

Complete the following steps:

Write a SQL SELECT statement by using an f-string that reads all the PYPL data from the database. Using the SQL SELECT statement, execute a query that reads the PYPL data from the database into a Pandas DataFrame.

Use the head and tail functions to review the first five and the last five rows of the DataFrame. Make a note of the beginning and end dates that are available from this dataset. You’ll use this information to complete your analysis.

Using hvPlot, create an interactive visualization for the PYPL daily returns. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.

Using hvPlot, create an interactive visualization for the PYPL cumulative returns. Reflect the “time” column of the DataFrame on the x-axis. Make sure that you professionally style and format your visualization to enhance its readability.

![Screen Shot 2022-01-22 at 16 18 12](https://user-images.githubusercontent.com/91238235/150659724-de1ccbd1-9d7f-4866-b329-c8a6148e90f2.png)

![Screen Shot 2022-01-22 at 16 18 52](https://user-images.githubusercontent.com/91238235/150659744-5d45f22f-e631-4d72-baeb-bc55bfe23e06.png)

![Screen Shot 2022-01-22 at 16 19 24](https://user-images.githubusercontent.com/91238235/150659752-537268ae-c882-4106-bf07-16c97a741fa6.png)

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

![Screen Shot 2022-01-22 at 16 20 43](https://user-images.githubusercontent.com/91238235/150659773-deed2a8a-80fe-4fd5-9083-465d68e55e00.png)

![Screen Shot 2022-01-22 at 16 22 02](https://user-images.githubusercontent.com/91238235/150659798-299c59b4-5696-4b1f-b1c8-e35e51253042.png)

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

![Screen Shot 2022-01-22 at 16 24 57](https://user-images.githubusercontent.com/91238235/150659841-baf0e231-6d6f-4863-ab9e-68d979c2e247.png)

![Screen Shot 2022-01-22 at 16 25 32](https://user-images.githubusercontent.com/91238235/150659849-11d3c522-8cdf-47e0-a58f-843713156680.png)

![Screen Shot 2022-01-22 at 16 26 23](https://user-images.githubusercontent.com/91238235/150659867-b8236303-47e2-42c3-bdc4-cc987e0ecdfb.png)

![Screen Shot 2022-01-22 at 16 26 54](https://user-images.githubusercontent.com/91238235/150659876-b9f17b3c-93c5-441d-9444-118fdbbc10bf.png)

Happy coding!

-----------------------------------------------------------------------

## Contributors

Sean Harrington: www.linkedin.com/in/sean-harrington16

-----------------------------------------------------------------------

## License
