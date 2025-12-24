---
Lecture Date: 2025-02-04
Presentation: 
Links: 
Subject:
  - "[[EM 616 - Time Series Analysis]]"
Refernces: 
tags:
  - EM616
---
```table-of-contents
```
_**PROFESSOR: ARUN K. TANGIRALA**_

# Introduction

- **A time-series simply refers to an ordered collection of data (usually in time)**
- e.g., yearly wages, annual production, daily temperature, hourly satellite images
- Measurements could be a function of other dimensions (e.g., frequency, space)
- Data may be collected at regular or irregular intervals
    - **Regular interval**: Interval between two data points is the same
    - **Irregular interval**: Interval between two data points is not same
- Many variables could be recorded simultaneously (multivariate data)
    - For example if we take temperature, we could be measuring precipitation, pressure and many more. **It is an example of multiple variables that are collected simultaneously**
## Example
Time-series can consist of different components:

- **Deterministic**
> [!NOTE] DEFINITION
> A deterministic signal is something that can be predicted accurately given even small amount of past or infinite past
    
1. Trend (polynomial, spline)
2. Seasonal (periodic) and Cyclic components
- **Stochastic**
> [!NOTE] DEFINITION
> A stochastic signal is something that cannot be predicted accurately given even huge amount of past or infinite past.
    
1. Stationary component
    1. Something is invariant. Some statistical properties are not changing with time.
2. Non-stationary trend (e.g., random walk)
3. Changing mean, variance, temporal correlation, etc.

Time Series could be multivariate, multidimensional and also transformed into another domain


