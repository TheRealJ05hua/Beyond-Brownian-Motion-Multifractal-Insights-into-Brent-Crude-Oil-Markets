# Multifractal Model of Asset Returns (MMAR) Implementation

This project implements the Multifractal Model of Asset Returns (MMAR) for simulating asset price movements, with a focus on crude oil prices. The MMAR is used to capture complex market dynamics, including volatility clustering and long-range dependence.

## Dependencies

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from tqdm import tqdm
import plotly.graph_objects as go
from fbm import FBM
```

## Key Components

1.	Data Preparation and Parameter Estimation
•	Imports and processes historical crude oil price data.
•	Estimates key parameters: Hurst exponent (H), alpha zero, lambda, and sigma squared.
2.	Lognormal Cascade Generation
•	Implements functions to generate the multifractal time warping.
3.	Trading Time Calculation
•	Computes the trading time (theta_t) based on the lognormal cascade.
4.	MMAR Simulation
•	Calculates the magnitude parameter for fractional Brownian motion.
•	Generates simulated returns and price paths based on the MMAR model.
5.	Visualization
•	Provides functions to plot simulated paths, returns, and prices.
6.	Option Pricing
•	Implements Monte Carlo method for pricing European options based on simulated paths.

## Usage
1.	Prepare the data and estimate initial parameters.
2.	Generate the lognormal cascade and calculate trading time.
3.	Simulate MMAR returns and price paths.
4.	Visualize the results using provided plotting functions.
5.	(Optional) Use the simulated paths for option pricing.

## Key Functions
•	lognormal_cascade() and calculate_lognormal_cascade(): Generate the lognormal cascade.
•	calculate_trading_time(): Compute the trading time.
•	calculate_magnitude_parameter(): Determine the magnitude for fractional Brownian motion.
•	calculate_mmar_returns(): Generate simulated returns and price paths.
•	plot_mmar_paths(), plot_mmar_paths_filla(), plot_mmar_paths_fillb(): Visualize results.
•	price_option() and price_options_for_strikes(): Price options based on simulated paths.

## Note

This implementation assumes familiarity with the MMAR model. Users should adjust parameters based on their specific asset and market conditions.
For more information, refer to:
Mandelbrot, B. B., Fisher, A., & Calvet, L. (1997). A multifractal model of asset returns. Cowles Foundation Discussion Paper.
![image](https://github.com/user-attachments/assets/f014558f-29d5-4966-a832-0378193961f8)
