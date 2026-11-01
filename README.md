# Ex.No: 03 COMPUTE THE AUTO FUNCTION(ACF)

# Date: 01/11/2026

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.

# Dataset Used: canteen_shop_data
# Software Required:
- Jupyter Notebook

### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
data = pd.read_csv("canteen_shop_data.csv")

data['Date'] = pd.to_datetime(data['Date'])

x = data['Date']
y = data['Price'].values
N = len(y)

lags = range(35)

mean_data = np.mean(y)
variance_data = np.var(y)

autocorr_values = []

N = len(y)

lags = range(35)

autocorr_values = []

mean_data = np.mean(y)
variance_data = np.var(y)

for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum(
            (y[:-lag] - mean_data) *
            (y[lag:] - mean_data)
        ) / N

        autocorr_values.append(auto_cov / variance_data)
plt.figure(figsize=(10, 6))

plt.stem(lags, autocorr_values)

plt.title("Autocorrelation Function of Canteen_shop_data_set")
plt.xlabel("Lag")
plt.ylabel("Autocorrelation")

plt.grid(True)
plt.show()

```
### OUTPUT

<img width="910" height="508" alt="image" src="https://github.com/user-attachments/assets/aacd60a9-af91-4c42-b5cb-100a259c537e" />

### RESULT

 Thus we have successfully implemented the auto correlation function in python.
