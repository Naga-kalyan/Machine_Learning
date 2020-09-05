# TIME SERIES ANALYSIS
# INTRODUCTION
* Time series analysis is a statistical technique that deals with time series data, or trend analysis.  Time series data means that data is in a series of  particular time periods or intervals.
* Most of business houses work on time series data to analyze sales number for the next year, website traffic, competition position etc.
# WHAT IS TIME SERIES DATA?
* A time series is a series of data points indexed (or listed or graphed) in time order. Thus it is a sequence of discrete-time data.
* A time is a sequence taken at successive equally spaced points in time.
# WHAT IS TIME SERIES FORECASTING ?
* Time Series Forecasting is the use of statistical models to predict future values based on past results.
* What kind of variables can we forecast? : Any variable that can be tracked and collected over the time.
# COMPONENTS OF TIME SERIES DATA?
* Time Series data collected over a period of time is influenced by a variety of factors.
* Classified mainly four types 
  - Trend 
  - Seasonality
  - Cycling 
  - Irregularity
* First three components - deterministic — also known as “signals”.
* Last component - random variable — also called “noise” - ‘in-deterministic’ component.
* For proper forecast — one must know to what extent each component is present— remove / analyze the component
### 1. ***TRENDS***
  * Trend is a gradual shift or movement to relatively high and low values over a long period of time.
  * Higher lows to higher highs in the plot signify uptrend.
  * Lower highs to lower lows in the plot signify downtrend.
  * If there is no trend it is called horizontal or stationary trend.
### 2. ***SEASONALITY***
  * Seasonality refers to periodic fluctuations. 
  * For example, electricity consumption is high during the day and low during night, or online sales increase during Christmas before slowing down again.
### 3. ***CYCLING***
  * Patterns in data that do not fall in the same calendar year.
  * Cyclical patterns exist when data exhibits rises and falls that are not of a fixed period.
  * Examples are business like cycles, lasting several years, length of the current cycle is unknown before hand.

<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/Reinforcement%20Learning/TimeSeriesAnalysis/IMG/1.png"/></p>

# TIME SERIES FORECASTING METHODS
### 1. ***Average Method***:
* The forecast of all future values are equal to the average of all past vales.
* In essence, what will happen tomorrow is the average of everything that has happened till now.
### 2. ***Moving Average Method***:
* The forecast of all future values are equal to the average of the time series for a defined number of time periods.
* In essence, what will happen tomorrow is the average of everything that has happened in last 3 months.
*  We can decide the duration of time period for averaging.
### 3. ***Naive Method***:
* The forecast of all future values are equal to the value of the last observation.
* In essence, what will happen tomorrow is what happened yesterday.
### 4. ***Seasonal Naive Method***:
* The forecast of all future values are equal to the value of the last year’s observation in the same month.
* In essence, what will happen tomorrow is what happened same day last year.
* Assumes magnitude of the seasonal pattern will remain constant.
### 5. ***Simple Linear Model***:
* Similar to linear regression
* Does not take trend into account.
* Does not take Variance into account.
* Does not take Seasonality into account.
### 6. ***Weighted Moving Average***:
* A Moving average where some time periods are weighted differently than others is called as weighted moving average.
* Sometimes (especially when the trend is too high or too low), we may need to give extra weightage for a particular time period data.
* It will be more meaningful if the weights for older time period is smaller than the weights for recent time period.

<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/Reinforcement%20Learning/TimeSeriesAnalysis/IMG/2.png"/></p>

### 7. *Exponential smoothing*:
* Exponential smoothing method compares past data from previous time periods with exponentially decreasing importance in the forecast so that the most recent data carries more weight in the moving average.
* Simple exponential smoothing method is helpful in forecasting the value for the present time period X, using an exponential smoothing constant a (falling between 0 and 1).

<p align="center">
  <img src="https://github.com/Naga-kalyan/Machine_Learning/blob/master/Reinforcement%20Learning/TimeSeriesAnalysis/IMG/3.png"/></p>

# ACCURACY OF FORECAST
If <img src="https://render.githubusercontent.com/render/math?math={F_t}">, represents the forecast and <img src="https://render.githubusercontent.com/render/math?math={D_t}">, represents demand for a period <img src="https://render.githubusercontent.com/render/math?math={t}">, then following measures are used to check accuracy of the forecast.
* The forecast error for the period <img src="https://render.githubusercontent.com/render/math?math={t}"> is given as : <img src="https://render.githubusercontent.com/render/math?math={E_t}={F_t - D_t}">

* Average error over n period is given as : <img src="https://render.githubusercontent.com/render/math?math={AE_n}={\frac{1}{n}{\sum_{i=1}^n E_i}}">

* Another terminology bias is used show the sum of errors :  <img src="https://render.githubusercontent.com/render/math?math={bias_n}={\sum_{i=1}^n E_i}">

* As the average error cancels positive and negative errors, in most of the situations, mean absolute deviation error is used:<img src="https://render.githubusercontent.com/render/math?math={MAD_n}={\sum_{i=1}^n |E_i|}">

* A measure which is closely related to the MAD, but which expresses the magnitude of the error relative to the magnitude of the demand is known as the mean absolute percentage error, or MAPE.<img src="https://render.githubusercontent.com/render/math?math={MAPE_n}={\sum_{i=1}^n |\frac{E_i}{D_i}|}">

* Another measure of average error is known as the mean squared error, or MSE.<img src="https://render.githubusercontent.com/render/math?math={MSE_n}={\sum_{i=1}^n {E_i}^2}">

* The square-root of MSE is called as RMSE, and least RMSE is always expected for a better accuracy in forecasting.
* To automatically detect when a forecast model is no longer producing good forecasts, a measure known as a ***tracking signal*** is often used.<img src="https://render.githubusercontent.com/render/math?math={Tracking Signal}={\frac{bias}{MAD}}">

* This tracking signal is a measure that can be used in a control-chart-like manner so that when an out-of-control state is reached, the forecasting model can be revised to get things back in control.
* By dividing the bias by the MAD, the control limits for this “unit-less” measure are the same for every product being forecast and therefore separate control limits need not be kept for each product.
* Instead, a common rule of thumb is **when the tracking signal reaches a value of positive or negative “6”, it is time to investigate the forecasting model**.

# ARIMA MODEL
* ARIMA, short for ***‘Auto Regressive Integrated Moving Average’*** is actually a class of models that ‘explains’ a given time series based on its own past values, that is, its own lags and the lagged forecast errors, so that equation can be used to forecast future values
### Step 1 : Checking the data for Stationarity
* One way is looking the plot of the data - check whether it looks like a white noise
* Second method is - a statstical test called as Augmented Dickey -Fuller test
* **Augmented Dickey -Fuller test**
  - We will take Null Hypothesis as : The time series data is stationary.
  - Alternative Hypothesis is : The Time series data is non-stationary.
  - If the test-statistic value of Dickey Fuller test is lesser than the critical value (at 1% or 5% or 10% confidence interval),then we can say that null hypothesis is accepted at a particular confidence level.
  - If the test-statistic is greater, we have to reject null hypothesis
### Step-2 : Making the data for Stationarity
* One of the tricks to reduce trend can be transformation. For example, in the current example, we can clearly see that the there is a significant positive trend. So we can apply log-transformation which penalize higher values more than smaller values.
* Then we can go for differencing the time-series data.
### *Step 3*: Plot PACF and ACF
* **ACF** 
  - It is an (complete) auto-correlation function which gives us values of auto-correlation of any series with its lagged values.
  - In simple terms, it describes how well the present value of the series is related with its past values.
  - A time series can have components like trend, seasonality, cyclic and residual.
  - ACF considers all these components while finding correlations hence it’s a ‘complete auto-correlation plot’.
* **PACF**
  - PACF is a partial auto-correlation function.
  - Basically instead of finding correlations of present with lags like ACF, it finds correlation of the residuals (which remains after removing the effects which are already explained by the earlier lag(s)) with the next lag value hence ‘partial’ and not ‘complete’ as we remove already found variations before we find the next correlation.
  - So if there is any hidden information in the residual which can be modeled by the next lag, we might get a good correlation and we will keep that next
### STEP 4 : Build ARIMA Model
* An ARIMA model is characterized by 3 terms: p, d, q
<br>where,
<br>&emsp;&emsp;p is the order of the AR(Auto Regressive) term
<br>&emsp;&emsp;q is the order of the MA(Moving Average) term
<br>&emsp;&emsp;d is the number of differencing required to make the time series stationary
### Step 5 :Forecasting for future time period
