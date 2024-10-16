# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
## DEVELOPED BY : Kishore S
## REG NO : 212222240050
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
## DEVELOPED BY : Kishore S
## REG NO : 212222240050
```python
import numpy as np
import pandas as pd
import statsmodels.api as sm
import matplotlib.pyplot as plt

# Load the data from the CSV file

df = pd.read_csv('Google_Stock_Price_Train.csv')

# Extract the 'Open' column (you can replace this with another column if needed)
data = df['Open'].values

# Calculate mean and variance
data_mean = np.mean(data)
data_var = np.var(data)

# Normalize the data
normalized_data = (data - data_mean) / np.sqrt(data_var)

# Compute the autocorrelation function (ACF)
acf_result = np.correlate(normalized_data, normalized_data, mode='full')
acf_result = acf_result[len(acf_result)//2:]  # Keep only positive lags

# Plot the ACF result
plt.figure(figsize=(10, 5))
plt.stem(acf_result[:36], use_line_collection=True)  # Plot only the first 36 lags
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function (ACF) of Google Stock Prices')
plt.show()

```

### OUTPUT:
![image](https://github.com/user-attachments/assets/0682ec78-8d6a-49f3-933c-e7d2d41277a4)

### RESULT:
Implementation of auto correlation function in python was successfully completed .
