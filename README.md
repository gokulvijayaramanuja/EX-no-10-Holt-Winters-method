# EX-no-10-Holt-Winters-method
## AIM:
   To implement the holt winters method using python program
## Procedure:
  1.Import necessary libraries , Matplotlib for plotting, and Pandas for data handling.
  
  2.Create an Exponential Smoothing model (Holt-Winters) using statsmodels. Configure the model with trend and seasonal components.
  
  3.Creating a time series plot with a specified time range that includes the forecast.
  
  4.Generate a long-term forecast by forecasting future values for the entire time series.
  
## Program:
```python
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
```

## Output:
### airline.index
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/3e9d4d66-2676-4273-aed5-ecbe3f83e5f0)
### airline.tail()
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/675107e1-e371-44a1-8329-569626bfce72)
### len(airline)
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/25fa7ece-823a-42dc-b5fb-6f8f457f560a)

### len(test_airline)
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/62b9448f-fc9c-4536-9f05-e97186b25cd7)
### test_predictions[:10]
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/0b36516f-11df-42f3-8a0d-b7e420b435eb)
### Train and Test Data Graph
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/6443beb2-577c-4773-a677-40e5efdc92cc)
### Train, Test and Predicted Test using Holt Winters graph
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/9b28465b-ea03-42f9-b0d9-ba0f2f9d2e6a)

### Prediction Graph
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/188cea63-4669-468f-999d-c5fa46096680)
### Mean Absolute Error
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/148075be-7024-4cb0-936d-8314acf2d2c5)
### Mean Squared Error
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/7a9c6ca2-4040-4af9-a3fd-97b68c5d3aca)
### test_airline.describe()

![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/e2f2932e-ce13-45c6-81eb-3e55bf6d2f46)

### Airline Passenger Forecast Graph
![image](https://github.com/praveenst13/EX-no-10-Holt-Winters-method/assets/118787793/558067cc-1480-4b33-b31b-8f7a42f211ad)


## Result:

Thus the program to implement holt winters method is written and verified using python programming.
