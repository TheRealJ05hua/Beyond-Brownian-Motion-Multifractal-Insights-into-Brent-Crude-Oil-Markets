Variance Gamma Model for Option Pricing
This repository contains the implementation of the Variance Gamma (VG) model for pricing options, particularly on Brent crude oil. The VG process introduces more realistic modeling of asset returns by incorporating skewness and kurtosis, allowing for a better fit to real-world financial data. The model is solved using numerical techniques for the Variance Gamma Partial Integro-Differential Equation (PIDE), Monte Carlo simulations, and other methods.

Overview
This implementation includes:

Numerical solution of the VG PIDE
Monte Carlo simulation
Comparison with closed-form solutions and Fourier inversion
Comparison with the Black-Scholes PDE
Table of Contents
The VG PIDE
Numerical Solution of the PIDE
Comparison with Monte Carlo, Closed Formula, and Fourier Inversion
Comparison with Black-Scholes PDE
Installation
Clone this repository:

bash
Copy code
git clone https://github.com/your-repo/variance-gamma-option-pricing.git
Install the necessary dependencies:

bash
Copy code
pip install -r requirements.txt
Usage
VG PIDE Numerical Solution:

The VG PIDE is solved using finite difference methods, and Brent crude oil option prices are calculated.
The model takes into account the infinite activity of the VG process by truncating the Lévy measure integral.
Monte Carlo Simulation:

A Monte Carlo simulation is implemented to generate price paths using the VG process and compare results against PIDE solutions.
Closed-form Solutions & Fourier Inversion:

Semi-closed formulas derived by Cont & Voltchkova are compared to numerical solutions, alongside Fourier inversion techniques.
The VG PIDE <a id='sec1'></a>
The Variance Gamma PIDE for option pricing is approximated as follows:

∂
𝑉
(
𝑡
,
𝑥
)
∂
𝑡
+
(
𝑟
−
1
2
𝜎
𝜖
2
−
𝑤
𝜖
)
∂
𝑉
(
𝑡
,
𝑥
)
∂
𝑥
+
1
2
𝜎
𝜖
2
∂
2
𝑉
(
𝑡
,
𝑥
)
∂
𝑥
2
+
∫
∣
𝑧
∣
≥
𝜖
𝑉
(
𝑡
,
𝑥
+
𝑧
)
𝜈
(
𝑑
𝑧
)
=
(
𝜆
𝜖
+
𝑟
)
𝑉
(
𝑡
,
𝑥
)
∂t
∂V(t,x)
​
 +(r− 
2
1
​
 σ 
ϵ
2
​
 −w 
ϵ
​
 ) 
∂x
∂V(t,x)
​
 + 
2
1
​
 σ 
ϵ
2
​
  
∂x 
2
 
∂ 
2
 V(t,x)
​
 +∫ 
∣z∣≥ϵ
​
 V(t,x+z)ν(dz)=(λ 
ϵ
​
 +r)V(t,x)
Where $\sigma_\epsilon$, $w_\epsilon$, and $\lambda_\epsilon$ are parameters derived from the Lévy measure.

Numerical Solution of the PIDE <a id='sec2'></a>
The PIDE is solved using a finite difference approach. The discretization of the integral term is handled by truncating the Lévy measure. The grid is set up to simulate oil price movements, and option prices are calculated over this grid.

Run the VG PIDE solution:

python
Copy code
# Create VG process and pricer objects
VG = VG_pricer(opt_param, VG_param)

# Solve using PIDE
VG.PIDE_price((30000, 30000), Time=True)
Monte Carlo Simulation <a id='sec3'></a>
The Monte Carlo simulation generates VG paths to estimate option prices. The following command runs a Monte Carlo simulation with $N = 20,000,000$ samples.

python
Copy code
# Run Monte Carlo simulation
VG.MC(20000000, Err=True, Time=True)
Comparison with Black-Scholes PDE <a id='sec4'></a>
This implementation also provides a comparison with the Black-Scholes PDE to illustrate the differences between the models, particularly in handling volatility.

Dependencies
Python 3.x
numpy, scipy, pandas, pandas_datareader, matplotlib
Additional packages for advanced numerical methods like cython, sympy
To install the required packages:

bash
Copy code
pip install numpy scipy pandas pandas_datareader matplotlib cython sympy
Example Results
Here is a sample plot of the option price curve for Brent Crude Oil using the VG model:


References
[1] Cont, R., & Voltchkova, E. "Finite Difference Methods for Option Pricing in Jump-Diffusion and Exponential Lévy Models."
