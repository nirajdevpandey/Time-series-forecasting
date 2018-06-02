# Time-series-forecasting
This repository is dedicated for time-series forecasting 

### Content
```
    1. checking stationarity in the time-series
    2. if it doesn't have stationarity property, make it stationary by using rolling mean
    3. Arima forcasting by using AIC to find best parameter 
    4. MSE and MAPE loss analization
    
```    
## checking stationarity

A common assumption in many time series techniques is that the data are stationary.
A stationary process has the property that the mean, variance and autocorrelation structure do not change over time. Stationarity can be defined in precise mathematical terms, but for our purpose we mean a flat looking series, without trend, constant variance over time, a constant autocorrelation structure over time and no periodic fluctuations (seasonality).

For practical purposes, stationarity can usually be determined from a run sequence plot.

```python
def TestStationaryAdfuller(ts, cutoff = 0.01):
    ts_test = adfuller(ts, autolag = 'AIC')
    ts_test_output = pd.Series(ts_test[0:4], index=['Test Statistic','p-value','#Lags Used','Number of Observations Used'])
    
    for key,value in ts_test[4].items():
        ts_test_output['Critical Value (%s)'%key] = value
    print(ts_test_output)
    
    if ts_test[1] <= cutoff:
        print("Strong evidence against the null hypothesis, reject the null hypothesis. Data has no unit root, hence it is stationary")
    else:
        print("Weak evidence against null hypothesis, time series has a unit root, indicating it is non-stationary ")
```
![Alt text](C:/Users/Dell/Documents/DDA Lab/Exercise-05/Arima1.jpg,raw=true "Title")
