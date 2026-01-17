# UCS654-2026-Assignment-1-Suresh_Sir-
# Assignment-1
## Learning Probability Density Functions using Roll-Number-Parameterized Non-Linear Model

---

## 1. Introduction

The aim of this assignment is to study probability density functions by applying a nonlinear transformation to real-world air quality data and learning the parameters of the resulting distribution. To ensure uniqueness of the model for each student, the transformation is parameterized using the university roll number.

---

## 2. Dataset Description

The dataset used in this assignment is the *India Air Quality Data* obtained from Kaggle. From this dataset, only the NO₂ (nitrogen dioxide) concentration values were considered. Let the NO₂ values be denoted by the variable `x`. Missing and invalid entries were removed before further analysis.

---

## 3. Methodology

The methodology consists of two main steps as specified in the assignment.

---

### Step-1: Roll-Number-Based Nonlinear Transformation

Each NO₂ value `x` is transformed into a new variable `z` using the nonlinear transformation:
z = x + a_r * sin⁻¹(b_r * x)


The parameters `a_r` and `b_r` depend on the university roll number `r` and are defined as:

a_r = 0.05 × (r mod 7)
b_r = 0.3 × (r mod 5 + 1)


For the roll number **102303526**, the calculated values are:

| Parameter | Value |
|---------|-------|
| a_r | 0.15 |
| b_r | 0.6 |

Since the inverse sine function is defined only for inputs in the range [-1, 1], the transformation was applied only to those NO₂ values for which:
-1 ≤ b_r * x ≤ 1


This restriction is mathematically necessary to ensure valid computation.

---

### Step-2: Learning the Probability Density Function

After transforming the data, the probability density function of the transformed variable `z` is modeled as:

p̂(z) = c · e^(-λ(z − μ)²)


The objective is to learn the parameters `μ`, `λ`, and `c` from the data.

---

### Parameter Estimation

The parameters were estimated using standard statistical formulas:

- Mean of the transformed variable:

μ = (1 / N) Σ zᵢ


- Variance of the transformed variable:

σ² = (1 / N) Σ (zᵢ − μ)²


- Parameter λ:

λ = 1 / (2σ²)


- Normalization constant c:

c = √(λ / π)

These estimates ensure that the probability density function is properly centered and normalized.

---

## 4. Results

The estimated parameters of the learned probability density function are summarized below:

| Parameter | Description | Value |
|---------|------------|-------|
| μ | Mean of transformed variable | 0.16681293756448962 |
| λ | Spread parameter | 3.050742611124999 |
| c | Normalization constant | 0.9854346925713743 |

(The exact numerical values depend on the valid transformed samples obtained after applying the domain restriction.)

---
 

## 5. Observations

- The roll-number-based transformation introduces controlled nonlinearity into the data.
- The learned probability density function closely resembles a Gaussian-like distribution.
- Parameter estimation is performed using classical statistical methods.
- The approach ensures uniqueness across students while maintaining mathematical correctness.

---

## 6. Conclusion

In this assignment, a nonlinear roll-number-parameterized transformation was applied to NO₂ air quality data, and a probability density function was learned from the transformed values. The parameters of the distribution were estimated using sample mean and variance, reinforcing key concepts in probability and statistics.

---

## 7. Tools Used

- Google Colab (for numerical computation only)
- Python (basic mathematical and data-handling libraries)




