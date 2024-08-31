# Heston-Nandi GARCH Model

This Python module implements the Heston-Nandi GARCH (HN-GARCH) model, which is a popular model in financial econometrics for modeling volatility dynamics and option pricing.

## Overview

The module provides the following functions:

- **hngarch_sim**: Simulates data using the Heston-Nandi GARCH model.
- **hngarch_fit**: Estimates the parameters of the Heston-Nandi GARCH model using maximum likelihood estimation.
- **hngarch_stats**: Computes various statistics related to the Heston-Nandi GARCH model.
- **HNGOption**: Calculates the price of a Heston-Nandi GARCH option.

## Functions

### `hngarch_sim(model=None, n=1000, innov=None, n_start=100, start_innov=None, rand_gen=np.random.normal)`

Simulates time series data using the Heston-Nandi GARCH model.

**Parameters:**
- `model`: A dictionary containing model parameters (`lambda`, `omega`, `alpha`, `beta`, `gamma`, `rf`).
- `n`: The number of time steps to simulate.
- `innov`: Optional; an array of innovations.
- `n_start`: Optional; the number of starting innovations.
- `start_innov`: Optional; an array of starting innovations.
- `rand_gen`: Optional; a random generator function.

**Returns:**
- A simulated time series.

### `hngarch_fit(x, model=None, symmetric=True, trace=False, title=None, description=None)`

Fits the Heston-Nandi GARCH model to a given time series using maximum likelihood estimation.

**Parameters:**
- `x`: The time series data.
- `model`: A dictionary containing initial guesses for model parameters.
- `symmetric`: Optional; whether the model should be symmetric.
- `trace`: Optional; whether to print trace information during optimization.
- `title`: Optional; a title for the output.
- `description`: Optional; a description of the output.

**Returns:**
- A dictionary containing the estimated parameters and other model statistics.

### `hngarch_stats(model)`

Calculates various statistics related to the Heston-Nandi GARCH model, including mean, variance, skewness, kurtosis, persistence, and leverage effects.

**Parameters:**
- `model`: A dictionary containing the model parameters.

**Returns:**
- A dictionary containing calculated statistics.

### `HNGOption(TypeFlag, model, S, X, Time_inDays, r_daily)`

Calculates the price of an option using the Heston-Nandi GARCH model.

**Parameters:**
- `TypeFlag`: Option type (e.g., "call" or "put").
- `model`: A dictionary containing the model parameters.
- `S`: The current stock price.
- `X`: The strike price.
- `Time_inDays`: The time to maturity in days.
- `r_daily`: The daily risk-free rate.

**Returns:**
- The option price.

## Dependencies

- `numpy`
- `scipy`

## Usage

To use the module, simply import the functions you need and call them with the appropriate parameters. For example:

```python
from hngarch import hngarch_sim, hngarch_fit, hngarch_stats, HNGOption

# Simulate time series data
sim_data = hngarch_sim()

# Fit the model
fit_results = hngarch_fit(sim_data)

# Calculate model statistics
stats = hngarch_stats(fit_results['model'])

# Calculate option price
option_price = HNGOption('call', fit_results['model'], S=100, X=95, Time_inDays=30, r_daily=0.01)
