**np.random.normal** is a function in NumPy that generates random numbers from a normal (or Gaussian) distribution.  

### What is a Normal Distribution?

A normal distribution is a probability distribution that is symmetrical around its mean. It is often referred to as the "bell curve" due to its shape. Many natural phenomena follow a normal distribution, such as heights, weights, and IQ scores.  

### Parameters of np.random.normal

The function takes three parameters:

- **loc:** The mean of the distribution.  
- **scale:** The standard deviation of the distribution.  
- **size:** The shape of the output array.  

### Example

Python

```python
import numpy as np

# Generate 1000 random numbers from a normal distribution with mean 50 and standard deviation 10
data = np.random.normal(loc=50, scale=10, size=1000)
```

This code will create an array `data` containing 1000 random numbers drawn from a normal distribution with a mean of 50 and a standard deviation of 10.

### Visualization

To visualize a normal distribution, you can use libraries like Matplotlib:

Python

```python
import matplotlib.pyplot as plt

plt.hist(data, bins=30, density=True)
plt.show()
```

This code will create a histogram of the generated data, showing the bell-shaped curve of the normal distribution.

# Example
## Simulating Stock Prices with np.random.normal

**Problem:** Let's say you want to simulate the price of a stock over time. A common assumption in finance is that stock prices follow a log-normal distribution. While the returns on a stock might be normally distributed, the prices themselves are log-normally distributed.

**Solution:** We can use `np.random.normal` to simulate the daily returns of a stock, and then calculate the stock prices based on these returns.

Python

```python
import numpy as np

# Parameters
initial_price = 100
num_days = 252  # Typical number of trading days in a year
daily_volatility = 0.02  # Assuming 2% daily volatility

# Generate random daily returns
daily_returns = np.random.normal(0, daily_volatility, num_days)

# Calculate prices
prices = np.empty(num_days + 1)
prices[0] = initial_price
for i in range(1, num_days + 1):
    prices[i] = prices[i - 1] * (1 + daily_returns[i - 1])

# Plot the simulated stock prices
import matplotlib.pyplot as plt
plt.plot(prices)
plt.xlabel('Days')
plt.ylabel('Price')
plt.title('Simulated Stock Price')
plt.show()
```

**Explanation:**

1. We start with an initial stock price and specify the number of days to simulate and the daily volatility.
2. We generate random daily returns using `np.random.normal` with a mean of 0 (no expected return) and the specified standard deviation (volatility).
3. We calculate the stock prices for each day by multiplying the previous day's price by (1 + daily return).
4. Finally, we plot the simulated stock prices to visualize the results.

**Note:**

- This is a simplified model. Real-world stock prices are influenced by many other factors.
- For more accurate simulations, you might consider using more complex models like the Black-Scholes model.

# Example 2
## Simulating Measurement Error with np.random.normal

**Problem:** Let's say you're collecting data on a physical quantity, like length or weight. Measurements are never perfectly accurate; there's always some error.

**Solution:** We can use `np.random.normal` to simulate measurement error.

Python

```python
import numpy as np

# True value of the quantity
true_value = 10

# Number of measurements
num_measurements = 100

# Measurement error standard deviation
error_sd = 0.2

# Simulate measurements
measurements = np.random.normal(true_value, error_sd, num_measurements)

# Calculate mean and standard deviation of measurements
mean_measurement = np.mean(measurements)
sd_measurement = np.std(measurements)

print("True value:", true_value)
print("Mean measurement:", mean_measurement)
print("Standard deviation of measurements:", sd_measurement)
```

**Explanation:**

1. We define the true value of the quantity and the number of measurements.
2. We specify the standard deviation of the measurement error.
3. We generate random measurements using `np.random.normal` with the true value as the mean and the specified standard deviation.
4. We calculate the mean and standard deviation of the simulated measurements.

**Note:**

- The mean of the measurements should be close to the true value, especially for a large number of measurements due to the Central Limit Theorem.
- The standard deviation of the measurements should be close to the specified error standard deviation.