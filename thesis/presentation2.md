#Presentation plan (20 minutes)
- 3 mins for what MSTS is (with examples)
- 2 mins on models (practice timing, avoid too many equations too quickly)
- 1 minute explaining what the new model aims to achieve
- 4 minutes discussing the theory of FASSTER
- 2 minutes discussing heuristic estimation
- 3 mins on key research outputs (fasster package)
- 4 mins results (?)
- 2 mins future research

# Brief overview of MSTS
- Patterns of MSTS are common in areas including utilities, consumer electronics, transportation, online services, and health systems.
- In fact, all series which involve humans will be multiple seasonal, due to daily routines which differ between weekdays and weekends (particular research focus, show graph weekday/weekend ped graph)
- accurate MSTS modelling is essential for understanding and predicting these complex systems
- MSTS is becoming more common as the more temporally fine grained data is collected via sensors (show granularity ped graph)
- Such as... pedestrian counts!
- Many additional features of MSTS need to be considered in a model, including holiday effects (point out in granularity ped graph), and covariates (change to electricity demand graph)
- What makes a good model - Flexible, accurate, fast, robust
- Very few models are available for forecasting these series

# Models
## Regression based models
- Overview of how they work
- Considered models (MLR, GAM, Prophet)
- Preliminary results: performance of these models, key issues

## State space models
- Overview of how they work
- Considered models (DSHW, BATS/TBATS, MS ARIMA)
- Preliminary results: performance of these models, key issues

## Benchmark models
A multiple seasonal equivelant of seasonal naive is included as a minimum performance indicator. This model simply uses the last observed value from the same multi-seasonal period as the forecasted value.

# The research goal
To extend the capabilities of state space models to allow for more flexible specification and exogenous inputs. Ideally, this model would also be accurate, fast, and robust.

# The proposed model
FASSTER

- Key extension is switching terms in the model
- Allows user-specified flexible model specification
- Built on top of a DLM to leverage the relative speed of the Kalman Filter
- Key components of the model - poly, seas/trig, arma, xreg

# Heuristic estimation
A problem in estimating this model is that many terms need to be estimated very quickly.
To overcome this, heuristics can be applied.

The most important parameters to estimate are the variance of the observation noise and state noise.

The successful heuristic method involved filtering through the dataset, and then smoothing to give an estimate of the underlying states. From this, the appropriate state variance and observation variance can be estimated.

# Key research outcomes
In addition to developing a new model to capture switching seasonal patterns, a key outcome from this research is the implementation of the model in an R package (include link to repo)

Particular care was taken to ensure that the user interface for the model was intuitive to R users. This involved designing the model function to work well with the tidyverse of packages, and ensuring that the model specification is consistent with standard formula conventions. Unlike many packages, FASSTER doesn't destroy the functionality of formula tools such as the `OR` operator, and instead introduces a new infix operator `%G%`.

To specify common key components of the model, special convenience functions have been defined.

# Model performance and applications

# Extensions
- Automatic detection of groups
- Streaming data
- Improved heuristic estimation
