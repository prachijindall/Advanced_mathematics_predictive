# **PROBABILITY DENSITY FUNCTIONS**

## **Overview**

This assignment involves applying a personalized non-linear transformation to NO2 data from the India Air Quality dataset, based on your roll number. The transformed data is then used to estimate parameters of a specified probability density function (PDF) using statistical techniques. The goal is to understand data transformation, parameter estimation, and model validation in a probabilistic context.

## **Objectives**

1)Understand and apply a roll-number-dependent non-linear transformation to convert raw NO2 values into a new variable z.

2)Learn the parameters λ, μ, and c for the given PDF formula through estimation methods.

3)Interpret the fitted PDF and validate its appropriateness for the data.

4)Prepare the estimated parameters for submission.

## **Mathematical Formulation**
### *Step 1: Data Transformation*

Each NO2 value x is transformed into z using the function:

z = Tr(x) = x + ar × sin(br × x)


The coefficients ar and br are calculated from your roll number r:

ar = 0.05 × (r mod 7)

br = 0.3 × (r mod 5 + 1)


For r = 102317155:

ar = 0.05 × (102317155 % 7) = 0.05 × 3 = 0.15

br = 0.3 × (102317155 % 5 + 1) = 0.3 × (0 + 1) = 0.3


This transformation introduces non-linearity, making the analysis unique to your roll number and simulating feature engineering.

### *Step 2: PDF Parameter Estimation*

The PDF to fit is:

p̂(z) = c × exp(-λ(z - μ)²)


λ (lambda) controls the spread or variance of the distribution.
μ (mu) represents the central location or mean.
c is a scaling constant that adjusts the height of the PDF.

Estimation is performed using Maximum Likelihood Estimation (MLE), which finds parameters that maximize the likelihood of the observed z values under this model. This involves optimizing the negative log-likelihood function numerically.

## **Quick Start**
### *Prerequisites*

Ensure you have access to libraries like NumPy, Pandas, SciPy, Matplotlib, and Seaborn for data handling, optimization, and visualization.

### *Download Dataset*

Access the dataset at:

https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data


Download the CSV file and save it locally (e.g., as india_air_quality_data.csv).

### *Running the Analysis*

Compute ar and br using your roll number.

Load the NO2 data, clean it and apply the transformation.

Use MLE to estimate λ, μ, and c.

Generate visualizations to check the fit.

## **Implementation Details**
### *Estimation Approach*

Maximum Likelihood Estimation (MLE) is the primary method, where parameters are chosen to maximize the probability of observing the data. This is done by minimizing the negative log-likelihood, using optimization algorithms to handle the non-linear nature of the PDF.

Alternative methods like curve fitting to a histogram or method of moments can be considered for comparison, but MLE is recommended for accuracy.

### *Key Concepts*

Transformation Function: Applies a sine-based adjustment to x, creating z.

PDF Model: A Gaussian-like function with adjustable parameters.

Negative Log-Likelihood: Measures how well the model fits the data; lower values indicate better fits.

Optimization: Iterative process to find optimal parameters within bounds (e.g., positive values for λ and c).

## **Output Interpretation**
### *Visualization Breakdown*

Raw NO2 Distribution: A histogram showing the original data's spread.

Transformation Curve: A plot demonstrating how x values map to z via the non-linear function.

PDF Fit: Overlay of the fitted PDF on the histogram of z to assess alignment.

Q-Q Plot: A quantile-quantile plot to evaluate if the data follows the model's distribution.

## **Parameter Insights**

λ indicates the concentration of data around μ (higher λ means tighter clustering).
μ is the expected value of z.
c ensures the PDF's scale matches the data density.

The PDF's integral over the data range should approximate 1 for a valid density function.

## **Example Output**

For roll number 102317155, after processing the dataset:

ar: 0.150000

br: 0.300000
Estimated λ = 0.000727

Estimated μ = 27.645665

Estimated c = 0.016751


The PDF equation would be:

p(z) = 0.016751 × exp(−0.000727 × (z − 27.645665)²)

## **Learning Outcomes**

By completing this, you'll grasp:

Data transformation techniques for probabilistic modeling.

Parameter estimation in PDFs using likelihood methods.

Model validation through statistical plots.

Application of mathematical concepts in data analysis.
