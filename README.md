# Monte Carlo Option Pricing Model
This project implements a Monte Carlo simulation to price European call and put options using the Geometric Brownian Motion model. The simulation allows you to estimate the option prices by generating multiple paths for the underlying stock price and calculating the average payoff at maturity.

## Table of Contents
- [Introduction](#introduction)
- [Model Parameters](#model-parameters)
- [Geometric Brownian Motion](#geometric-brownian-motion)
- [Monte Carlo Simulation](#monte-carlo-simulation)
- [Usage](#usage)
- [Potential Improvements](#potential-improvements)
- [License](#license)

## Introduction
Options are financial derivatives that provide the right, but not the obligation, to buy or sell an underlying asset at a specified strike price on or before a specified date. Monte Carlo simulation is a technique used to understand the impact of risk and uncertainty in financial, project management, cost, and other forecasting models.

This project focuses on using Monte Carlo simulation to price European options. European options can only be exercised at expiration, unlike American options, which can be exercised at any time before expiration.

## Model Parameters
The following parameters are used in the Monte Carlo simulation:

- **Initial Stock Price (S0)**: The current price of the underlying stock.
- **Strike Price (K)**: The price at which the option can be exercised. For a call option, this is the price at which the holder can buy the stock. For a put option, it's the price at which the holder can sell the stock.
- **Time to Maturity (T)**: The time remaining until the option's expiration, expressed in years.
- **Risk-free Interest Rate (r)**: The annualized risk-free interest rate.
- **Volatility (sigma)**: The annualized volatility of the stock's returns.
- **Number of Simulations (n_simulations)**: The number of simulated paths to generate.
- **Number of Time Steps (num_steps)**: The number of discrete time steps in each simulated path.

## Geometric Brownian Motion
The Geometric Brownian Motion (GBM) model is used to simulate the paths of the stock prices. It is described by the stochastic differential equation:

$$
dS_t = \mu S_t dt + \sigma S_t dW_t
$$

where:
- \( S_t \) is the stock price at time \( t \).
- \( \mu \) is the drift rate of the stock.
- \( \sigma \) is the volatility of the stock.
- \( W_t \) is a Wiener process (also called Brownian motion).

The discrete approximation of this model is:

$$
S_{t+\Delta t} = S_t \exp \left( \left( r - \frac{\sigma^2}{2} \right) \Delta t + \sigma \sqrt{\Delta t} Z \right)
$$

where \( Z \) is a standard normal random variable.

### Variance Reduction
To improve the accuracy of the simulation and reduce variance, antithetic variates have been implemented. This technique involves generating pairs of negatively correlated random variables, which can help to reduce the variance of the simulation estimates.

## Monte Carlo Simulation
The Monte Carlo simulation process involves:
1. Generating multiple random paths for the stock price using the GBM model.
2. Calculating the payoff for each path at maturity.
3. Discounting the payoffs to their present value.
4. Averaging the discounted payoffs to estimate the option price.

## Potential Improvements
- **Increase Accuracy**: Use more simulations and time steps.
- **Variance Reduction Techniques**: Implement methods like antithetic variates, control variates, and importance sampling.
- **Different Models**: Explore models like the Heston model (stochastic volatility) or jump diffusion models.
- **Early Exercise**: For American options, use methods like Least-Squares Monte Carlo (LSM) to account for early exercise.
- **Parallel Computing**: Use parallel computing to speed up simulations.
