# Portfolio evaluation and visualization

# Project description
The Portfolio evaluation and visualization program is a Python-based application that enables users to optimize investment portfolios using different strategies and visualize the results. The program helps investment analysts to evaluate portfolio strategies for their clients to decide on optimal hyperparameters. The program utilizes historical stock data to estimate portfolio weights and evaluate portfolio performance based on various metrics. 

# Key features
**Data retrieval:** The program includes a data retrieval module that allows users to fetch historical stock data using predefined or custom stock tickers from yahoo finance. 

**Portfolio optimization:** Users can select from two portfolio optimization strategies: "Minimum Variance" and "Maximum Sharpe Ratio". The program applies these strategies to calculate optimal portfolio weights based on historical stock data.

**Hyperparameter tuning:** The program allows users to specify different hyperparameters for covariance estimation, mean estimation, and penalty values. It performs a comprehensive hyperparameter search to find the optimal combination of parameters for portfolio optimization.

**Out of sample performance evaluation:** The program optimizes portfolio weights and tests the performance on the data from next period. Framework enables monthly portfolio rebalancing (each month portfolio is reoptimized to satisfy strategy goal)

**Visualization:** The program provides visualizations to analyze the performance of optimized portfolios. It generates scatter plots comparing the optimal portfolio with individual constituents and displays the performance of tuned portfolios based on expected returns and volatility.

**Analysis and insights:** The program provides insights into key portfolio metrics such as expected returns, volatility, and Sharpe ratio. These metrics help users evaluate and compare different portfolios.

# How to use it:
Programs requires two functions to run. Below are input responses required from the user:

`stock_data = ask_full_stock_data_retrieval()`

Guide: 
1.	Does user want to use default tickers?
* yes – provide own list of yahooo finance tickers separated by comma
*	no – program uses default ones (DAX constituents)
2.	Does user want use default date range?
* yes – default range is between "2013-01-01" and "2023-01-01"
*	no – provide default date in format YYYY-MM-DD
  
In case for a specified date range there is no data for a list of tickers, a user can decide on proceeding without some stocks or to provide tickers and data range again
Finally functions retrieves monthly stock returns.

`portfolio_optimization_and_visualisation(data = stock_data)`

Guide:
1.	Decide on portfolio strategy. 
  *	1 – Minimum variance portfolio (portfolio with lowest fluctuation of returns)
  *	2 – Maximum sharpe ratio portfolio (portfolio with best relation between yield and risk)
2.	Does the user want to search for optimal covariance estimate?
  *	Yes – provide list of integers from 1 to 8 corresponding to displayed covariance estimates. These are the candidates to be searched from to get optimal portfolio.  Values need to be separated by comma. When a list contains at least 2 values, a program performs hyperparameter tunning of covariance.
  *	No – default value is sample covariance. No tunning for this parameter.
3.	Does the user want to search for optimal mean estimate?
  *	Yes – provide list of integers from 1 to 3 corresponding to displayed mean estimates. Details same as in point 2.
  *	No – default value is mean historical return. No tunning for this parameter.
4.	Does the user want to search for optimal shrinkage value?
  *	Yes – provide list of doubles, separated by comma. It is recommended to use values between 0 and 2, e.g. 0.1, 0.5 . Details same as in point 2.
  *	No – default value is 0. No tunning for this parameter.
    
  The results are two visualizations.
  * Performance of tuned portfolios: Shows all tuned portfolios in expected returns-volatility scatterplot. The color of points corresponds to selected strategy criterion. Star shows optimal portfolio.
  * Performance of optimal portfolio vs 100% investing in any of constituents: Compares the optimal portfolio with strategy of investing 100% in any of stock which is part of this portfolio. 

# Authors
Dagmara Jaśkowiak and Mateusz Konarczyk
