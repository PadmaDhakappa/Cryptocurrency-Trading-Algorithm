

# Cryptocurrency Trading Algorithm 

## Abstract
This project aims to create a simple and beginner-friendly cryptocurrency trading algorithm using a simple cross over strategy that helps the user buy and sell at the right time. The algorithm uses historical data of the Bitcoin to USD exchange rate from Yahoo Finance  and applies two simple moving averages (SMA) of different lengths to generate buy and sell signals based on the crossover points. The algorithm also performs backtesting to evaluate the performance and profitability of the strategy compared to the benchmark. The project is implemented in Python using the pandas, numpy, and matplotlib.pyplot modules.

## Inspiration
The inspiration for this project came from the growing popularity and interest in cryptocurrencies, especially Bitcoin, which is the most widely used and traded digital currency in the world. Bitcoin is known for its high volatility and unpredictability, which makes it challenging and risky to trade. However, it also offers opportunities for potential profits if the trader can identify the right time to enter and exit the market. Therefore, I wanted to create a simple and easy-to-understand trading algorithm that can help beginners and enthusiasts to learn and apply a basic trading strategy using historical data and simple moving averages.

## Introduction
A simple moving average (SMA) is a way of finding the average price of a stock over a certain period of time. It helps to smooth out the fluctuations in the price and show the overall trend. For example, a 9-day SMA means that you take the closing prices of the last 9 days and add them up, then divide by 9. This gives you the average price for the last 9 days. You can do this for every day and plot the SMA on a chart. The SMA will move up or down as the prices change.  

A simple cross over strategy is a popular trading strategy that uses two or more moving averages to identify potential buy and sell signals based on the crossover points. The basic idea behind this strategy is to compare two moving averages of different lengths and look for a crossover where one moving average crosses above or below the other. For example, you can use a fast SMA (such as 10-day SMA) and a slow SMA (such as 40-day SMA) and plot them on the same chart. When the fast SMA crosses above the slow SMA, it indicates a bullish trend and a buy signal. When the fast SMA crosses below the slow SMA, it indicates a bearish trend and a sell signal.  

## Methodology
The methodology of this project consists of the following steps:

- Data collection: I used the Yahoo Finance API  to download the historical data of the Bitcoin to USD exchange rate from January 1st, 2023 to November 29, 2023. The data contains the date, open, high, low, close, and volume of each day. I stored the data in a pandas dataframe called `BTC_USD`.
- Data processing: I used the pandas module to calculate the daily percent returns of Bitcoin and added it to the dataframe as a new column called `BTC_Return`. The daily percent return is the ratio of the current closing price to the previous closing price, minus one. It shows how much the price has changed from one day to the next.
- Trade signal generation: I used the pandas module to calculate the fast and slow simple moving averages of the closing price and added them to the dataframe as new columns called `Short` and `Long`. I used a window of 10 days for the fast SMA and a window of 40 days for the slow SMA. I also used the numpy module to create a new column called `Signal` that contains the trade signals based on the crossover points. The `Signal` column has three possible values: 1 for buy, -1 for sell, and 0 for no signal. I used the `np.where` function to assign the values based on the following logic: if the fast SMA is greater than the slow SMA, then the signal is 1; if the fast SMA is less than the slow SMA, then the signal is -1; otherwise, the signal is 0.
- Backtesting: I used the pandas and numpy modules to create a new dataframe called `backtest` that contains the backtesting results for the simple cross over strategy. The backtest dataframe has the same index as the trade signal dataframe, which is the date. The backtest dataframe has three columns: `BTC_Return`, `Alg_Return`, and `Balance`. The `BTC_Return` column is the same as the one in the `BTC_USD` dataframe, which is the daily percent return of Bitcoin. The `Alg_Return` column is the daily percent return of the algorithm, which is calculated using the `np.where` function. The logic is: if the signal is 1, then the algorithm return is equal to the Bitcoin return; if the signal is -1 or 0, then the algorithm return is zero. The `Balance` column is the daily value of the portfolio using the algorithm, which is calculated by multiplying the initial balance ($10,000) with the cumulative product of the `Alg_Return` column. The cumulative product is the result of multiplying all the previous returns together, which gives the total return of the algorithm from the start to the current date.
- Performance evaluation: I used the pandas and matplotlib.pyplot modules to measure and compare the performance of the algorithm and the benchmark. The benchmark is the Bitcoin price itself, which represents the passive strategy of holding Bitcoin without trading. I used the following metrics to evaluate the performance: mean, standard deviation, and cumulative return. The mean is the average of the daily percent returns, which measures the expected return of the strategy. The standard deviation is the measure of the variability or volatility of the daily percent returns, which measures the risk of the strategy. The cumulative return is the final value of the portfolio divided by the initial value, which measures the total growth or decline of the strategy. I also used the `plt.plot` function to plot the portfolio value and the Bitcoin price over time on the same chart, which illustrates the performance visually.

## Discussion
The discussion of the results can be divided into two parts: the strengths and the limitations of the project.

The strengths of the project are:

- The project is simple and beginner-friendly, as it uses a basic and easy-to-understand trading strategy and a few Python modules to implement it.
- The project is informative and comprehensive, as it covers the whole process of data collection, data processing, trade signal generation, backtesting, and performance evaluation.
- The project is transparent and reproducible, as it provides the code, the data, and the references for the project.

The limitations of the project are:

- The project is based on historical data, which may not reflect the future performance of the algorithm. The market conditions and the price movements of Bitcoin may change over time, which may affect the validity and reliability of the algorithm.
- The project is based on a simple cross over strategy, which may not capture the complexity and dynamics of the cryptocurrency market. The algorithm may miss some opportunities or generate false signals due to the lag and noise of the moving averages. The algorithm may also be affected by the choice of the window lengths and the frequency of the data.
- The project is based on a few assumptions and simplifications, which may not reflect the reality of the cryptocurrency trading. The algorithm assumes that the user has a fixed initial balance and does not add or withdraw money from the portfolio. The algorithm also assumes that the user can buy and sell Bitcoin at the closing price of each day and does not incur any transaction costs or fees.

## Conclusion
The conclusion of the project is that the cryptocurrency trading algorithm using a simple cross over strategy is a simple and beginner-friendly way of learning and applying a basic trading strategy using historical data and simple moving averages. However, the algorithm is not very effective or profitable, as it underperforms the benchmark in terms of return and risk. Therefore, the algorithm needs to be improved and refined to make it more robust and realistic. Some possible ways of improving the algorithm are:

- Use different types of moving averages, such as exponential moving average (EMA), weighted moving average (WMA), or adaptive moving average (AMA), which may reduce the lag and noise of the SMA.
- Use different lengths and combinations of moving averages, such as 5-day and 20-day, or 20-day and 50-day, which may capture different trends and patterns of the price movements.
- Use different frequencies and sources of data, such as hourly, daily, or weekly data, or data from different exchanges or platforms, which may provide more information and accuracy for the algorithm.
- Use different indicators and signals, such as volume, momentum, or trend lines, which may complement and confirm the moving average crossover signals.
- Use different methods and metrics to evaluate the performance, such as Sharpe ratio, Sortino ratio

