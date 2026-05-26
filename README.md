# Ex.No: 08     MOVINTG AVERAGE MODEL AND EXPONENTIAL SMOOTHING
### Date: 25/05/2026


### AIM:
To implement Moving Average Model and Exponential smoothing Using Python.
### ALGORITHM:
1. Import necessary libraries
2. Read the electricity time series data from a CSV file,Display the shape and the first 20 rows of
the dataset
3. Set the figure size for plots
4. Suppress warnings
5. Plot the first 50 values of the 'Value' column
6. Perform rolling average transformation with a window size of 5
7. Display the first 10 values of the rolling mean
8. Perform rolling average transformation with a window size of 10
9. Create a new figure for plotting,Plot the original data and fitted value
10. Show the plot
11. Also perform exponential smoothing and plot the graph
### PROGRAM:
```
# 1. Import necessary libraries
import pandas as pd
import matplotlib.pyplot as plt
import warnings
from statsmodels.tsa.holtwinters import SimpleExpSmoothing

# 2. Read the dataset
data = pd.read_csv('timeseries_2year.csv')

# 4. Set figure size
plt.rcParams['figure.figsize'] = (12, 6)

# 5. Suppress warnings
warnings.filterwarnings("ignore")

# -------------------------------
# Choose time series column
# -------------------------------
target = 'sales'   # you can change to 'revenue_usd', 'stock_price', etc.

# 6. Plot first 50 values
plt.plot(data[target].head(50), label='Original Data')
plt.title(f"First 50 Values of {target}")
plt.legend()
plt.show()

# 7. Rolling average (window = 5)
rolling_5 = data[target].rolling(window=5).mean()

# 8. Rolling average (window = 10)
rolling_10 = data[target].rolling(window=10).mean()

# 9. Show first 10 values of rolling mean
print("\nRolling Mean (window=5) first 10 values:\n", rolling_5.head(10))

# 10. Plot original vs rolling averages
plt.figure()
plt.plot(data[target], label='Original')
plt.plot(rolling_5, label='Rolling Mean (5)')
plt.plot(rolling_10, label='Rolling Mean (10)')
plt.title("Moving Average Comparison")
plt.legend()
plt.show()

# 11. Exponential Smoothing
model = SimpleExpSmoothing(data[target])
fit = model.fit(smoothing_level=0.2, optimized=False)

# 12. Plot exponential smoothing
plt.figure()
plt.plot(data[target], label='Original')
plt.plot(fit.fittedvalues, label='Exponential Smoothing')
plt.title("Exponential Smoothing")
plt.legend()
plt.show()
```

### OUTPUT:

<img width="443" height="306" alt="image" src="https://github.com/user-attachments/assets/8c1a2ff3-1097-4928-b8b9-2471510fab86" />

Moving Average:

<img width="1248" height="674" alt="image" src="https://github.com/user-attachments/assets/ca6e6e1c-6d70-40d2-85fe-993997823a3f" />

Plot Transform Dataset:

<img width="1249" height="673" alt="image" src="https://github.com/user-attachments/assets/e79320bb-31eb-46df-9ca0-2b919bc2d1a3" />

Exponential Smoothing:

<img width="1241" height="673" alt="image" src="https://github.com/user-attachments/assets/61adee16-2c17-49d8-93fa-4d2029d0b399" />

### RESULT:
Thus we have successfully implemented the Moving Average Model and Exponential smoothing using python.
