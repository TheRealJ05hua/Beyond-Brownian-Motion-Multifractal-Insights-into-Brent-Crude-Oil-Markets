# The Variance Gamma (VG) Model

This project implements the Variance Gamma (VG) model for option pricing using a numerical solution of the Variance Gamma Partial Integro-Differential Equation (PIDE). The implementation also includes a Monte Carlo simulation for comparison purposes.

## Highlights
- [The VG PIDE](#the-vg-pide)
- [Numerical solution of the PIDE](#numerical-solution-of-the-pide)
- [Comparison with Monte Carlo, closed formula, and Fourier inversion](#comparison-with-monte-carlo-closed-formula-and-fourier-inversion)
- [Comparison with the Black Scholes PDE](#comparison-with-the-black-scholes-pde)

<a id="the-vg-pide"></a>
## The VG PIDE
The VG PIDE can be solved using the Finite Difference Method, a numerical approach introduced by Cont and Voltchkova. The VG model is similar to the Merton PIDE but includes a truncation in the integral, leading to the following approximated form:

$$
\frac{\partial V(t,x)}{\partial t} +
\left( r-\frac{1}{2}\sigma_{\epsilon}^2 - w_{\epsilon} \right) \frac{\partial V(t,x)}{\partial x} 
+ \frac{1}{2}\sigma_{\epsilon}^2 \frac{\partial^2 V(t,x)}{\partial x^2}
+ \int_{|z| \geq \epsilon} V(t,x+z) \nu(dz) = (\lambda_{\epsilon} + r) V(t,x)
$$

### Parameters:
- **$\sigma_{\epsilon}^2$**: Small jumps variance
- **$w_{\epsilon}$**: Martingale correction
- **$\lambda_{\epsilon}$**: Intensity of large jumps

### Lévy Measure:
$$
\nu(dz) = \frac{e^{\frac{\theta z}{\sigma^2}}}{\kappa |z|} \exp 
\left( - \frac{\sqrt{\frac{2}{\kappa} + \frac{\theta^2}{\sigma^2}}}{\sigma} |z| \right) dz
$$

Where $\theta$, $\sigma$, and $\kappa$ are the model parameters.

<a id="numerical-solution-of-the-pide"></a>
## Numerical Solution of the PIDE
This section provides the implementation of the VG PIDE using a numerical method. The code fetches Brent crude oil data, calculates the necessary parameters, and then solves the VG PIDE using finite difference methods. The process involves setting up boundary conditions, calculating Lévy measures, and iterating backward through time to find the option price.

### Libraries Used:
- `numpy`
- `scipy`
- `matplotlib`
- `pandas`
- `pandas_datareader`
- `datetime`
- `sympy`
- `IPython.display`

### Key Steps:
1. **Data Fetching**: Brent crude oil data is fetched from the FRED API.
2. **Parameter Calculation**: Volatility and other VG parameters ($\theta$, $\sigma$, $\kappa$, etc.) are calculated.
3. **Discretization**: Space and time domains are discretized, and boundary conditions are set.
4. **Lévy Measure**: The Lévy measure for the VG process is calculated.
5. **PIDE Solution**: The VG PIDE is solved numerically, and the option price is determined.

### Results:
- The final option price is plotted against the underlying Brent Crude Oil prices.

<a id="comparison-with-monte-carlo-closed-formula-and-fourier-inversion"></a>
## Comparison with Monte Carlo, Closed Formula, and Fourier Inversion
After solving the VG PIDE numerically, comparisons are made with other methods such as Monte Carlo simulation, closed-form solutions, and Fourier inversion techniques. These methods provide different perspectives and validations for the accuracy of the VG model implementation.

<a id="comparison-with-the-black-scholes-pde"></a>
## Comparison with the Black Scholes PDE
Finally, the VG PIDE solution is compared with the classical Black-Scholes PDE to highlight the differences in option pricing under these two models, particularly under the presence of jumps and skewed distributions in the VG model.



## References
1. Cont, R., & Voltchkova, E. (2005). A finite difference scheme for option pricing in jump diffusion and exponential Lévy models. *SIAM Journal on Numerical Analysis*, 43(4), 1596-1626.

<a id="sec5"></a>
**[1]** Cont & Voltchkova: A finite difference scheme for option pricing in jump diffusion and exponential Lévy models, SIAM J. Numer. Anal., 2005.
