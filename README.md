# Forecasting the Price of Silver #
![](https://github.com/titansat74/SLV_Forecasting/blob/main/figs/silver%20bars.jpeg)

**For centuries, silver has been valued for its precious appearance, usage as currency, and utility in technological applications. However, more recently, it has been largely overshadowed as an investment vehicle by more popular products such as stocks from technology companies and cryptocurrencies. As we enter a new realm of elevated levels of inflation and economic uncertainty, silver is given another look. In this study, historical price data are utilized to model the price of silver and forecast its performance over the next 12 months. The complete study can be viewed at the following links:**
> * [Full Report](https://github.com/titansat74/SLV_Forecasting/blob/main/docs/Forecasting%20the%20Price%20of%20Silver.pdf)
> * [Google Sheets Presentation](https://github.com/titansat74/SLV_Forecasting/blob/main/docs/Forecasting%20the%20Price%20of%20Silver%20-%20Slides.pdf)


## 1. Data Processing ##
**Silver price data spanning from 2017 to the end of 2021 were taken from the [Yahoo! Finance](https://finance.yahoo.com) tabulation of the exchange-traded fund [SLV](https://finance.yahoo.com/quote/SLV/history?period1=1483228800&period2=1640995200&interval=1d&filter=history&frequency=1d&includeAdjustedClose=true). The daily closing prices were used as the study dataset.**

## 2. Exploratory Data Analysis ##
**To facilitate the examination of the SLV time series data, the data must be stationarized. This is accomplished by differencing the dataset with the lag-1 values, which yields a p-value for the Augmented Dickey-Fuller test of 3.5x10<sup>-13</sup>, indicating strong stationarity.**
**Autocorrelation and partial autocorrelation function plots demonstrate the following:**
  * Significant autocorrelation at lags 4, 9, 15, and 16, perhaps suggesting weekly seasonality
  * Similar correlation coefficients between the plots, implying mixed autoregressive/moving average behavior
 
![](https://github.com/titansat74/SLV_Forecasting/blob/main/figs/fig4.png)

**Notebook for exploratory data analysis:**
> * [EDA Notebook](https://github.com/titansat74/SLV_Forecasting/blob/main/notebooks/SLV_Time_Series_EDA.ipynb)

## 3. Modeling & Forecast ##
**The data were split into a training set (80%) and a test set (20%), comprising data from 2017-2020 and data from 2021, respectively. These data were fitted to Autoregressive Moving Average (ARIMA) and Seasonal ARIMA (SARIMA) models, using a grid search of AR and MA model orders. The results demonstrate that the SARIMA(0,1,0)(2,0,2)3 model provided the best fit to the evaluation dataset (test set). The metrics used in the analysis are presented [here](https://github.com/titansat74/SLV_Forecasting/blob/main/docs/Silver%20Forecasting%20Metrics.pdf).**
**The coefficients for the model are presented below.**
![](https://github.com/titansat74/SLV_Forecasting/blob/main/figs/Table8.png)

**Compared against the Baseline model, which assumes the next day's price is equal to today's price, only the Base SARIMA model outperforms with respect to the test set. A t-test reveals that this outperformance is not significant, yielding a p-value of 0.57 for the hypothesis that the SARIMA residuals are smaller than those of the Baseline.**
![](https://github.com/titansat74/SLV_Forecasting/blob/main/figs/Table9.png)

**Using the SARIMA model, a forecast of 6.0% appreciation for 2022 is obtained.**
![](https://github.com/titansat74/SLV_Forecasting/blob/main/figs/fig9.png)

**Notebook for modeling analysis:**
> * [Modeling Notebook](https://github.com/titansat74/SLV_Forecasting/blob/main/notebooks/SLV_Time_Series_Modeling.ipynb)

## 4. Summary ##
**The major finding of this study are as follows:**
> * **SLV shows significant autocorrelation at lags 4, 9, 15.**
> * **SLV is best modeled by a Seasonal ARIMA model of period 3 - SARIMA(0,1,0)(2,0,2)3.**
> * **Best model forecasts an SLV appreciation of 6.0% for the year 2022.**
