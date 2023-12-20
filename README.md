## Project 1 - Pricing Exotic Options (Asian Call Option and a European Barrier Put Option) using Monte Carlo Simulation
# Asian Call Option
Asian option is a path dependent option whose payoff (in this example) is dependent on average of the prices the stock has taken over the tenure of option.
Payoff = max(Savg- K,0)
So, I created a function which simulates the 100000 paths (by creating an array ) at discrete time steps using Stock Price GBM Process St = S0 * np.exp(r-0.5*sigma*sigma)*dt + sigma*z*np.sqrt(dt)
Then took the average of stock price at each time step for each simulated path and calculated the final arithmetic average .
Calculated the payoff as max(Savg-K,0)
As price today is calculated as discounted expected payoff. I discounted the expected payoff to today to get the price of an Asian Call Option
# European barrier put option
Barrier options are options where the payoff depends on whether the underlying asset's price reaches a certain level during a certain period of time
So in this implementation ,I have tried one kind of Knock-out options wherein if the value of a stock reaches a certain barrier upside , then the option will become worthless
Then I simulated the path GBM Process(Euler discretization) and checked the condition at each time step if the stock crosses a certain barrier, then payoff for that simulated path becomes zero.
After running 1000 simulations , I calculated the total payoff across all simulated paths and calculated the price today as the expected discounted payoff.

## Project 2 – Pricing European plain vanilla options and Greeks using BSM Model and calculating the Price and Greeks using inbuilt python libraries using mibian and py_vollib and comparing the prices and greeks value from BSM and inbuilt libraries.

## Project 3 :- Pricing a swaption using Black’s Model 
The Black Model is a variant of BSM Option Pricing Model . It is used for pricing options on future contracts, bond options, interest rate cap and floors and swaptions.
P = np.exp(-r*t) *[F*N(d1) – K*N(d2)]

## Project 4 :- Predicting the price of a stock using time series analysis(ARIMA Model)
I downloaded the price of Tesla stock price data using yahoo finance for the time period 1st Jan to 1st Sep 2023 and tried to performed time series analysis on that.
From the plot , stock price was trending upwards and therefore was non-stationary and same can be verified using augmented Dicky-Fuller test(ADF test) .
I performed first order differencing on the data to make it stationary and verified the same using plot and ADF test.
For determining the lags, I used the pacf and acf plots using statsmodels library and observed statistically significant lags at 4 for both tried to fit the ARIMA model on the differenced series with parameters (AR-4, I -1, MA -4).
Compared the model results with actual stock price value.

 ## Project 5 :-  Calculation of Value-at-Risk and Expected Shortfall

Downloaded 5 stocks data from yahoo finance and calculated the mean and standard deviation(using Modern Portfolio theory) and covariance among the 5 stocks.
Calculated the historical 1-day VaR and ES using numpy percentile function at a confidence interval of 95% for a portfolio amount of $500000.
Under the assumption of normality, calculated the VaR and ES at confidence interval of 95%.
Under Monte Carlo Simulation, calculated the portfolio PnL (mu + sigma*z) by sampling 100000 values of z and then taken the required percentile for VaR and ES.
