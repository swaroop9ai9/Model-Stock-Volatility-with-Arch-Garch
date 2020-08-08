# Model-Stock-Volatility-with-Arch-Garch
Modelling Stock Volatility with Arch and Garch for time series forecasting in python

A change in the variance or volatility over time can cause problems when modeling time series with classical methods like ARIMA.
The ARCH or Autoregressive Conditional Heteroskedasticity method provides a way to model a change in variance in a time series that is time dependent, such as increasing or decreasing volatility. An extension of this approach named GARCH or Generalized Autoregressive Conditional Heteroskedasticity allows the method to support changes in the time dependent volatility, such as increasing and decreasing volatility in the same series.

* Problem with Variance:
- Autoregressive models can be developed for univariate time series data that is stationary (AR), has a trend (ARIMA), and has a seasonal component (SARIMA).
- One aspect of a univariate time series that these autoregressive models do not model is a change in the variance over time.Classically, a time series with modest changes in variance can sometimes be adjusted using a power transform, such as by taking the Log or using a Box-Cox transform.
(Box-Cox transform: A Box Cox transformation is a way to transform non-normal dependent variables into a normal shape. Normality is an important assumption for many statistical techniques; if your data isn't normal, applying a Box-Cox means that you are able to run a broader number of tests.)

# Finance domain problem:
 - There are some time series where the variance changes consistently over time. In the context of a time series in the financial domain, this would be called increasing and decreasing volatility.
- In time series where the variance is increasing in a systematic way, such as an increasing trend, this property of the series is called heteroskedasticity. It’s a fancy word from statistics that means changing or unequal variance across the series.
- If the change in variance can be correlated over time, then it can be modeled using an autoregressive process, such as ARCH.

# ARCH Model:

- Autoregressive Conditional Heteroskedasticity, or ARCH, is a method that explicitly models the change in variance over time in a time series.

- Specifically, an ARCH method models the variance at a time step as a function of the residual errors from a mean process (e.g. a zero mean).
- A lag parameter must be specified to define the number of prior residual errors to include in the model.(q: The number of lag squared residual errors to include in the ARCH model.)
- A generally accepted notation for an ARCH model is to specify the ARCH() function with the q parameter ARCH(q); for example, ARCH(1) would be a first order ARCH model.
- The approach expects the series is stationary, other than the change in variance, meaning it does not have a trend or seasonal component. An ARCH model is used to predict the variance at future time steps.

- In practice, this can be used to model the expected variance on the residuals after another autoregressive model has been used, such as an ARMA or similar.

# GARCH Model:

- Generalized Autoregressive Conditional Heteroskedasticity, or GARCH, is an extension of the ARCH model that incorporates a moving average component together with the autoregressive component.
- Specifically, the model includes lag variance terms (e.g. the observations if modeling the white noise residual errors of another process), together with lag residual errors from a mean process.
- The introduction of a moving average component allows the model to both model the conditional change in variance over time as well as changes in the time-dependent variance. Examples include conditional increases and decreases in variance.
- As such, the model introduces a new parameter “p” that describes the number of lag variance terms:

  p: The number of lag variances to include in the GARCH model.
  q: The number of lag residual errors to include in the GARCH model.
  
A generally accepted notation for a GARCH model is to specify the GARCH() function with the p and q parameters GARCH(p, q); for example GARCH(1, 1) would be a first order GARCH model.
- For p = 0 the process reduces to the ARCH(q) process, and for p = q = 0 E(t) is simply white noise. In the ARCH(q) process the conditional variance is specified as a linear function of past sample variances only, whereas the GARCH(p, q) process allows lagged conditional variances to enter as well. This corresponds to some sort of adaptive learning mechanism.
- As with ARCH, GARCH predicts the future variance and expects that the series is stationary, other than the change in variance, meaning it does not have a trend or seasonal component.

* The configuration for an ARCH model is best understood in the context of ACF and PACF plots of the variance of the time series.

* This can be achieved by subtracting the mean from each observation in the series and squaring the result, or just squaring the observation if you’re already working with white noise residuals from another model.
- If a correlogram appears to be white noise […], then volatility ca be detected by looking at the correlogram of the squared values since the squared values are equivalent to the variance (provided the series is adjusted to have a mean of zero).

# ARCH and GARCH models in Python:
