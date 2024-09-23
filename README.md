# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
NAME : YOHESH KUMAR R.M
REG NO : 212222240118
```
```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Load the Microsoft Stock dataset
data = pd.read_csv('Microsoft_Stock.csv')

# Extract the 'Close' prices and ensure they are numeric
time_series = data['Close']
time_series = pd.to_numeric(time_series, errors='coerce').dropna()

# Calculate the number of data points and lags
n_data_points = len(time_series)
n_lags = min(35, n_data_points - 1)
acf_values = np.zeros(n_lags)

# Calculate the mean and variance of the time series data
mean = np.mean(time_series)
variance = np.var(time_series)
normalized_data = time_series - mean

# Compute the ACF manually
for lag in range(n_lags):
    lagged_data = np.roll(normalized_data, -lag)
    acf_values[lag] = np.sum(normalized_data[:n_data_points-lag] * lagged_data[:n_data_points-lag]) / (variance * (n_data_points - lag))

# Plot the ACF results with blue stems and red markers
plt.figure(figsize=(10, 6))
plt.stem(range(n_lags), acf_values, linefmt='b-', markerfmt='ro', basefmt='k-', use_line_collection=True)
plt.title('ACF Plot for Microsoft Stock Close Prices')
plt.xlabel('Lag')
plt.ylabel('ACF')
plt.grid(True)
plt.show()

```

### OUTPUT:
![image](https://github.com/user-attachments/assets/6c69db79-b573-4fd3-b7ef-14a1711e759f)


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
