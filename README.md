# Assignment
## Learning Probability Density Functions using Roll-Number-Parameterized Non-Linear Model

--------------------------------------------

Objective

The objective of this assignment is to:
1. Apply a roll-number-based nonlinear transformation to a dataset feature.
2. Learn the parameters of a probability density function (PDF) for the transformed variable.
3. Estimate Gaussian distribution parameters using Maximum Likelihood Estimation (MLE).

--------------------------------------------

Dataset

Dataset Used: India Air Quality Data  
Feature Considered: NO2

The dataset contains air quality measurements across various locations in India.
For this assignment, only the NO2 column is used as the feature variable x.

--------------------------------------------

Step 1: Non-Linear Transformation

Each value of x is transformed into a new variable z using:

z = x + a_r * sin(b_r * x)

Where:
a_r = 0.05 * (r mod 7)
b_r = 0.3 * (r mod 5 + 1)
r = 102303463

For roll number 102303463:
r mod 7 = 3
r mod 5 = 3

Therefore:
a_r = 0.15
b_r = 1.2

Final transformation:
z = x + 0.15 * sin(1.2x)

--------------------------------------------

Step 2: Learning the Probability Density Function

The transformed variable z is modeled using the Gaussian probability density function:

p(z) = c * exp(-lambda * (z - mu)^2)

Using Maximum Likelihood Estimation:

mu = mean(z)
sigma^2 = variance(z)

lambda = 1 / (2 * sigma^2)
c = 1 / sqrt(2 * pi * sigma^2)

--------------------------------------------

Estimated Parameters

lambda = 0.0014599899081690277
mu     = 25.80638519611327
c      = 0.021557579212396885

--------------------------------------------

Conclusion

The NO2 feature was transformed using a roll-number-based nonlinear function.
A Gaussian distribution was fitted to the transformed variable using Maximum
Likelihood Estimation. The estimated parameters define the learned probability
density function for the transformed data.
