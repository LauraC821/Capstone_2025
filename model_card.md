# Model Card

Name: Black Box Optimisation Surrogate Model for Capstone Project

Type: Bayesian Optimisation using Gaussian Process (GP) Surrogates

Version: 1.0

Date: 28/01/2026

## Intended use
This model is designed to maximise eight unknown functions, that range between 2 and 8 dimensions, using a limited query budget. 
The model should not be used outside these eight unknown functions. 
The model should definitely not be used for higher dimensional problems, or in settings where stationarity and homoscedasticity cannot be assumed.

## Strategy
### Early Stages (Rounds 1-4)
Initial submissions prioritised exploration, aiming to build an understanding of the global structure. The primary method was an Sklearn Gaussian Process (GP) surrogate model with:
* An Upper Confidence Bound (UCB) acquisition function, where the beta parameter was high to encourage exploration.
* An acquisition function that maximised standard deviation to explore the region of greatest uncertainty, with a penalty to avoid exploration too far from known points.

For function 5, which was expected to be unimodal, exploitation was used from the start with a probability of improvement acquisition function.

### Mid Stages (Rounds 5-10)
For these five rounds the strategy cycled between exploring new regions or exploiting promising ones based on observed performance. A range of techniques were used, including:
* Sklearn GP surrogate models:
    * With UCB acqusition functions where the beta parameter varied (depending upon exploration or exploitation).
    * Using various kernels and length scales.
    * Where separate GP's were trained on each cluster of inputs identified by k-means.
* A Random Forest surrogate model was tried but rarely used.
* LLM prompting was explored to:
    * Critique methodology.
    * Suggest candidate points.
    * Assit with the clustering and random forest methods.

### Late Stages (Rounds 11-13)
With only three queries remaining, the strategy generally focused on exploiting the most promising regions. Given the limited data availability, queries were created manually by extrapolating observed trends or refining points within high-performing regions.

## Performance
| Function | Best Point Found |
| --- | --- |
|1|1.890527|
|2|0.758062|
|3|-0.002485|
|4|0.472639|
|5|8662.405001|
|6|-0.141199|
|7|2.287950|
|8|9.953930|

## Assumptions and limitations
* GP surrogates assume stationarity and homoscedasticity, which may not hold for all unknown functions.
* Manual decisions in query selection limit transparency and reproducibility.
* The limited query budget restricted exploration, especially in higher dimensional spaces.