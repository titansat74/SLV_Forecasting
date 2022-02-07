# Forecasting the Price of Silver #
![](https://github.com/titansat74/SLV_Forecasting/blob/main/figs/silver%20bars.jpeg)

**For centuries, silver has been valued for its precious appearance, usage as currency, and utility in technological applications. However, more recently, it has been largely overshadowed as an investment vehicle by more popular products such as stocks from technology companies and cryptocurrencies. As we enter a new realm of elevated levels of inflation and economic uncertainty, silver is given another look. In this study, historical price data are utilized to model the price of silver and forecast its performance over the next 12 months. The complete study can be viewed at the following links:**
> * [Full Report](https://github.com/titansat74/SLV_Forecasting/blob/main/docs/Forecasting%20the%20Price%20of%20Silver.pdf)
> * [Google Sheets Presentation](https://github.com/titansat74/SLV_Forecasting/blob/main/docs/Forecasting%20the%20Price%20of%20Silver%20-%20Slides.pdf)


## 1. Data Processing ##
**Silver price data spanning from 2017 to the end of 2021 were taken from the [Yahoo! Finance](https://finance.yahoo.com) tabulation of the exchange-traded fund [SLV](https://finance.yahoo.com/quote/SLV/history?period1=1483228800&period2=1640995200&interval=1d&filter=history&frequency=1d&includeAdjustedClose=true). The daily closing prices were used as the study dataset.**

## 2. Exploratory Data Analysis ##
**To facilitate the examination of the SLV time series data, the data must be stationarized. This is accomplished by differencing the dataset with the lag-1 values, which yields a p-value for the Augmented Dickey-Fuller test of 3.5$\times$10<sup>-13</sup>, indicating strong stationarity.**
**Autocorrelation &theta**

![](https://github.com/titansat74/SLV_Forecasting/blob/main/figs/fig4.png)

**The decline in Total Points later in the season, which corresponds to a reduction in Over winning percentage, seems to be directly related to the decline in passing yardage, which accompanies a decrease in temperature as the season progresses.**

**Notebook for exploratory data analysis:**
> * [EDA Notebook](https://github.com/titansat74/NFL_Over_Under/blob/main/notebooks/nfl_eda.ipynb)

## 3. Modeling & Forecast ##
**The data were split into a training set (80%) and a test set (20%), comprising data from 2017-2020 and data from 2021, respectively. A description of the metrics used in the analysis can be found [here](https://github.com/titansat74/NFL_Over_Under/blob/main/docs/NFL_Over_Under%20Metrics.pdf). Random Forest yielded the best results with 37 features. No one feature was dominant in any of the models; however, features involving offensive passing, particularly that of the visiting team, were consistently among the most important features.**
![](https://github.com/titansat74/NFL_Over_Under/blob/main/README_files/Table2.png)

**To further optimize the Random Forest results, threshold tuning was performed to determine which subset of games should be wagered to maximize betting efficiency. A threshold of -1 for the Under and +2 Over was found to be most optimal.**
![](https://github.com/titansat74/NFL_Over_Under/blob/main/README_files/fig20.png)

**Notebook for modeling analysis:**
> * [Modeling Notebook](https://github.com/titansat74/NFL_Over_Under/blob/main/notebooks/nfl_modeling.ipynb)

## 4. Summary ##
**The major finding of this study are as follows:**
> * **There is no one dominant feature guiding the prediction of total score, but passing yards is consistently the most important single statistic**
> * **Passing yardage is significantly affected by temperature, which is not adequately considered in the determination of the Over/Under**
> * **Wind is also a significant factor in total score output**
> * **The most important defensive feature is visiting defense red-zone percentage**
> * **The Random Forest model with 37 features is the most optimal model, yielding a seasonal return of 42% for the test set upon application of threshold tuning**
## 6. Future Work ##
**This study can be improved in the future with the following considerations:**
> * **More recent data are available for implementation into the model**
> * **Evolution of features over time can be considered in a time series treatment of the problem**
> * **Varying the bet size in threshold tuning can provide further model optimization**
