# Time Series Forecasting and Linear Regression Modeling

## Predicting Future Movements in the Value of Japanese yen verse the U.S. dollar

#### Time-Series Forecasting

In this assignment, historical Dollar-Yen exchange rate futures data was used to apply time series analysis and modeling to determine whether there was any predictable behavior.

Summary of Analysis: 

1. Decomposition using a Hodrick-Prescott Filter (Decompose the Settle price into trend and noise)
2. Forecasting Returns using an ARMA Model
3. Forecasting the Settle Price using an ARIMA Model
4. Forecasting Volatility with GARCH


A historical plot of Yen-USD futures settle price, it indicates a long-term trend of the Yen strengthening against the Dollar and therefore, a potential long-term investment opportunity. 

![yen](yen.png)

The plot of the Settle price verse the Trend line found using the Hodrick-Prescott Filter indicates the actual Yen settle price significantly fluctuates from the trend line. These flunctuations could represent short term buying opportunities when the Yen settle price falls below the trend line.  

![trendline](Trendline.png)

Looking more closely at the most recent data as of 10/15/2019, the Yen sits below the trend line indicating a potential near-term buying opportunity.

![recentdata](recenttrendline.png)

### Forecasting Returns using an ARMA Model

The ARMA model was run on the futures Settle Returns, the AR and MA parameters were set to order=(2, 1). Based on the results, the model forecasts returns to decline over the next 5-day period. 

![ARMAplot](ARMAgraph.png)

But the summary of the model's results show coefficients with p-values greater than 0.05 and therefore, not statistically significant. I would not be confident using this model. The prior days' returns do not appear to be good predictors of future returns. 

![ARMA](ARMA.png)

### Forecasting the Settle Price using an ARIMA Model

The ARIMA model was run on the raw Yen Settle Price with 5 auto-regressive lags and 1 moving average lag; order=(5,1,1). The model forecasts the Japanese Yen Settle Price will move higher in the near term. 

![ARIMAplot](ARIMAgraph.png)

But the summary of results show p-values of the lag coefficients to be greater than 0.05, therefore, not statistically significant. I would not be confident using this model.   

![ARIMA](ARIMA.png) 


### Volatility Forecasting with GARCH

The GARCH model was used to forecast near-term volatility of Japanese Yen futures returns. The parameters were set to order=(2,1). The model predicted risk to increase over the next five days. 

![GARCHplot](GARCHgraph.png)

Based on the model's summary of results, I would be confident using this model. Although, the model shows mixed p-values results, the one day lag is less than 0.05 and the two day lag is greater than 0.05. The one-day lag of volatility is statistically significant indicating a relationship between yesterday's volatility to today's volatility in the Settle price. The two-day lag does not show statistical significance. I would reduce the parameter p to a value of 1.   

![GARCH](GARCH.png)


In summary, the Yen price chart indicates a long-term trend of strengthening against the Dollar and would potentially make a great long term investment. Based on recent data analysis, the Yen currently sits below the trend line and may also be a short term buying opportunity. Unfortantely, the ARMA and ARIMA model did not show statistical signficance and therefore do not provide additional insight into the direction of future returns or settle price. But the GARCH model does appear to be helpful in the analysis and predicts higher risk in the near term to monitor. 



1. Based on your time series analysis, would you buy the yen now?
2. Is the risk of the yen expected to increase or decrease?
3. Based on the model evaluation, would you feel confident in using these models for trading?


#### Linear Regression Forecasting

In this notebook, you will build a Scikit-Learn linear regression model to predict Yen futures ("settle") returns with *lagged* Yen futures returns and categorical calendar seasonal effects (e.g., day-of-week or week-of-year seasonal effects).

Follow the steps outlined in the regression_analysis starter notebook to complete the following:

1. Data Preparation (Creating Returns and Lagged Returns and splitting the data into training and testing data)
2. Fitting a Linear Regression Model.
3. Making predictions using the testing data.
4. Out-of-sample performance.
5. In-sample performance.

Use the results of the linear regression analysis and modeling to answer the following question:

* Does this model perform better or worse on out-of-sample data compared to in-sample data?

The linear regression model does a poor job of predicting Yen futures settle returns with lagged Yen futures returns. This is evident by the high deviation between predicted returns verse actual returns from the plot and high root mean squared errors.

The model does perform better on out-of-sample data compared to in-sample data given the lower root mean squared error. This could be due to the smaller data set used in testing and therefore, a lower level of noise. If this test is performed several more times with different time series data selected for training and testing, I would expect the out-of-sample error to be larger than the in-sample error.

Include a Markdown that summarizes your models and findings and include this report in your GitHub repo
