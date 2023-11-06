EX-no-10-Holt-Winters-method
AIM:
To implement the holt winters method using python program

Procedure:
1.Import necessary libraries , Matplotlib for plotting, and Pandas for data handling.

2.Create an Exponential Smoothing model (Holt-Winters) using statsmodels. Configure the model with trend and seasonal components.

3.Creating a time series plot with a specified time range that includes the forecast.

4.Generate a long-term forecast by forecasting future values for the entire time series.

Program:
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.api import ExponentialSmoothing, SimpleExpSmoothing, Holt
airline  = pd.read_csv('/content/AirPassengers.csv',index_col='Month',parse_dates=True)
airline.index.freq = 'MS'
airline.index
airline.tail()
len(airline)
train_airline = airline[:108]
test_airline = airline[108:]
len(test_airline)
fitted_model = ExponentialSmoothing(train_airline['#Passengers'],trend='mul',seasonal='mul',seasonal_periods=12).fit()
test_predictions = fitted_model.forecast(36).rename('HW Test Forecast')
test_predictions[:10]
train_airline['#Passengers'].plot(legend=True,label='TRAIN')
test_airline['#Passengers'].plot(legend=True,label='TEST',figsize=(12,8))
plt.title('Train and Test Data');
train_airline['#Passengers'].plot(legend=True,label='TRAIN')
test_airline['#Passengers'].plot(legend=True,label='TEST',figsize=(12,8))
test_predictions.plot(legend=True,label='PREDICTION')
plt.title('Train, Test and Predicted Test using Holt Winters');
train_airline['#Passengers'].plot(legend=True,label='TRAIN')
test_airline['#Passengers'].plot(legend=True,label='TEST',figsize=(12,8))
test_predictions.plot(legend=True,label='PREDICTION',xlim=['1958-01-01','1961-01-01']);
from sklearn.metrics import mean_absolute_error,mean_squared_error
print(f'Mean Absolute Error = {mean_absolute_error(test_airline,test_predictions)}')
print(f'Mean Squared Error = {mean_squared_error(test_airline,test_predictions)}')
test_airline.describe()
final_model = ExponentialSmoothing(airline['#Passengers'],trend='mul',seasonal='mul',seasonal_periods=12).fit()

forecast_predictions = final_model.forecast(steps=36)
airline['#Passengers'].plot(figsize=(12,8),legend=True,label='Current Airline Passengers')
forecast_predictions.plot(legend=True,label='Forecasted Airline Passengers')
plt.title('Airline Passenger Forecast');
Output:
airline.index
image

airline.tail()
image

len(airline)
image

len(test_airline)
image

test_predictions[:10]
image

Train and Test Data Graph
image

Train, Test and Predicted Test using Holt Winters graph
image

Prediction Graph
image

Mean Absolute Error
image

Mean Squared Error
image

test_airline.describe()
image

Airline Passenger Forecast Graph
image

Result:
Thus the program to implement holt winters method is written and verified using python programming.
