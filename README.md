# Multi-Channel-Marketing-MLR# Multi-Channel Marketing Analysis using Multiple Linear Regression

## Project Overview
This project upgrades our single-channel analysis by evaluating the combined structural impact of concurrent advertising investments across **TV**, **Radio**, and **Social Media** on continuous corporate **Sales**. By employing Multiple Linear Regression (MLR) via Ordinary Least Squares (OLS), we evaluate independent channel contributions while controlling for other variables and diagnosing potential multicollinearity vulnerabilities using Variance Inflation Factors (VIF).

## Target Goals
* Detect and evaluate potential multicollinearity issues among media predictors.
* Fit a robust multivariate Ordinary Least Squares (OLS) regression model.
* Formally justify feature value inclusions or exclusions based on structural p-values.
* Deliver an optimized, data-driven budget allocation recommendation to maximize marketing ROI.

## Environment & Library Setup
To replicate the environment and run this analysis notebook locally, install the following required dependencies:
```bash
pip install pandas numpy matplotlib seaborn statsmodels scipy


Key Evaluation Findings
1. Multicollinearity Assessment (VIF)
Before model execution, cross-correlations were verified via a Pearson correlation matrix and Variance Inflation Factors (VIF):
TV VIF:2.82
Radio VIF: 3.45
Social Media VIF:1.66
Interpretation: All VIF metrics fall comfortably under the conservative threshold of 5.0. Although a strong baseline correlation exists between TV and Radio ($r = 0.803$), it is not severe enough to destabilize our model's coefficient estimates or artificially inflate standard errors. We can safely retain all features for simultaneous modeling.
2. Overall Model Quality & Variance Explanation
R-squared ($R^2$): 0.904Adjusted
 R-squared ($R^2_{adj}$): 0.0903 (90.3%)
Model Significance (Prob F-statistic): $2.10 \times 10^{-288}$ (Highly Significant
Interpretation: Our multivariate model explains 90.3% of the total variance observed in corporate Sales. The extremely low F-statistic p-value proves that the combination of these three features forms a highly reliable predictive system.
3. Structural Coefficient Breakdown
By examining the weights of our fitted OLS model equation ($Sales = 65.0337 + 77.3227 \cdot TV + 2.9792 \cdot Radio - 0.1577 \cdot Social\ Media$)
:Intercept ($\beta_0$ / const): 65.0337 | p-value: 0.000Interpretation: Baseline sales are expected to be approximately 65.03 units if marketing spend across all three channels is reduced to zero.
TV Coefficient ($\beta_1$): 77.3227 | p-value: 0.000Interpretation: Highly Significant. Holding Radio and Social Media budgets constant, each additional unit spent on TV advertising yields an average increase of 77.32 units in Sales. This is the model's strongest performer
Radio Coefficient ($\beta_2$): 2.9792 | p-value: 0.000Interpretation: Significant. Holding TV and Social Media budgets constant, each additional unit spent on Radio advertising yields an average increase of 2.98 units in Sales
.Social Media Coefficient ($\beta_3$): -0.1577 | p-value: 0.815Interpretation: Statistically Insignificant ($p > 0.05$). Despite showing a moderate initial correlation with sales in isolation, Social Media has a negative coefficient with a massive p-value of 0.815. This proves that Social Media provides zero independent structural value to Sales once TV and Radio spend are accounted for
.Strategic Business RecommendationBased on empirical statistical evidence, corporate marketing capital should be allocated according to the following strict priority framework:

Aggressively Scale TV Advertising: TV is the ultimate growth driver for this business, returning a staggering 77.32 sales units per unit spend. It should receive the largest share of the budget
.Maintain Steady Radio Allocation: Radio provides a reliable, statistically validated positive return (2.98 sales units per unit spend) and serves as a solid supporting channel

.Defund Social Media Marketing: The company is currently wasting resources on Social Media. Because its impact drops to statistically zero ($p = 0.815$) when controlling for other channels, we recommend completely freezing or reallocating the Social Media budget directly into TV advertising to maximize aggregate corporate ROI.
