# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 90/03/2026

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
import matplotlib.pyplot as plt
import numpy as np

# Data provided in the prompt
data = [3, 16, 156, 47, 246, 176, 233, 140, 130, 101, 166, 201, 200, 116, 118, 247, 209, 52, 153, 232, 128, 27, 192, 168, 208, 187, 228, 86, 30, 151, 18, 254, 76, 112, 67, 244, 179, 150, 89, 49, 83, 147, 90, 33, 6, 158, 80, 35, 186, 127]
lags = range(35)

# 1. Mean
mean_val = np.mean(data)

# 2. Variance
var_val = np.var(data)

# 3. Normalized data (Zero-centered)
norm_data = [x - mean_val for x in data]

# 4. Pre-allocate autocorrelation table
acorr = []

# 5. Go through lag components one-by-one
n = len(data)
for l in lags:
    # Autocorrelation calculation logic:
    # Sum of (x_i - mean) * (x_{i+lag} - mean) divided by (n * variance)
    # This gives the correlation coefficient at each lag
    c = 0
    for i in range(n - l):
        c += norm_data[i] * norm_data[i + l]
    acorr.append(c / (n * var_val))

# Store results in an array
acorr_array = np.array(acorr)

# 6. Display the graph
plt.figure(figsize=(10, 6))
plt.stem(lags, acorr_array)
plt.title('Autocorrelation Plot')
plt.xlabel('Lags')
plt.ylabel('Autocorrelation')
plt.grid(True)
plt.savefig('autocorrelation_plot.png')

print(f"Mean: {mean_val}")
print(f"Variance: {var_val}")
print(f"Autocorrelation array (first 5): {acorr_array[:5]}")
```
### OUTPUT:
<img width="857" height="547" alt="tex3" src="https://github.com/user-attachments/assets/e4fe7ba3-e94a-4604-9e7b-5d952bdee8f5" />

### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
