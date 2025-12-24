### Executive Summary
This study evaluates the efficiency of **25 cloud kitchens** using an input-oriented **CCR DEA model**. Only **3 kitchens (Kitchen_1, Kitchen_15, Kitchen_25)** are fully efficient ($\theta$ = 1.00). The remaining 22 kitchens can reduce inputs by **~31% on average** while maintaining outputs, revealing substantial potential for cost, staffing, and waste optimization. The analysis provides quantitative targets for underperforming kitchens and actionable insights for operational improvement.

### Problem Statement
Curry in a Hurry’s 25 kitchens show varying performance: some use excessive resources without corresponding outputs (revenue, ratings, on-time delivery), while others are lean and efficient. Leadership requires a **data-driven evaluation** to:
- Identify truly efficient kitchens
- Quantify inefficiencies in underperforming locations
- Provide input-reduction targets to improve overall operational efficiency

### Data Overview
**Inputs (Resources Used)**
- **Staff:** 3–12 employees
- **Area:** 250–900 sq ft
- **Operating Expenses:** $850–$3,200 per month
- **Food Waste:** 3.5–22 kg/month
**Outputs (Performance Metrics)**
- **Revenue:** $2,800–$6,200 per month
- **Customer Rating:** 3.5–4.9
- **On-Time Delivery:** 83–99%
**Dataset:** 25 Decision-Making Units (DMUs) × 4 inputs & 3 outputs

### DEA Model
**CCR Input-Oriented Model** - minimizes inputs while maintaining outputs
$$
\text{Minimize}: \theta
$$
$$
\text{Subject to:} \sum_{j=1}^n\lambda_jX_{ij} \le \theta X_{io}, \ i=1,...,m
$$
$$
\sum^n_{j=1}\lambda_jY_{rj} \ge Y_{ro}, \ r = 1,...,s
$$
$$
\lambda_j \ge 0, j = 1,...,n
$$
Where:
* $\theta$ = efficiency score (1.00 = fully efficient)
* $X_{ij}$ = input $i$ of kitchen $j$
* $Y_{rj}$ = output $r$ of kitchen $j$
* $\lambda_j$ = intensity weights
* $n$ = 25 kitchens, $m$ = 4 inputs, $s$ = 3 outputs
**Interpretation:**
* $\theta$ = 1 $\rightarrow$ kitchen is on the efficiency frontier
* $\theta$ < 1 $\rightarrow$ kitchen is inefficient; proportional input reductions required
### Key Results
**Overall Efficiency Statistics**
* Average: 69.0%
* Median: 69.1%
* Minimum: 40.31% (Kitchen 10)
* Maximum: 100%
* Standard Deviation: 21.85%
**Efficient Kitchens ($\theta$ = 1.00)**
* Kitchen 1, Kitchen 15, Kitchen 25
**Notable Near-Efficient**
* Kitchen 11 - 97.39% (still inefficient)
**Bottom 5 Worst-Performing Kitchens**

| **Kitchen** | **Efficiency** | Input Reduction Needed |
| ----------- | -------------- | ---------------------- |
| Kitchen 10  | 40.31%         | 59.7%                  |
| Kitchen 24  | 41.30%         | 58.7%                  |
| Kitchen 5   | 43.45%         | 56.6%                  |
| Kitchen 20  | 45.05%         | 54.9%                  |
| Kitchen 13  | 45.13%         | 54.9%                  |
### Key Insights
* **Efficiency Distribution:** Only 12% of kitchens operate at $\theta$ = 1.00; average kitchen uses ~31% more inputs than required.
* **Traits of Efficient Kitchens:** small-to-medium footprint, lean staffing, low opex, minimal waste, high ratings, excellent on-time delivery.
* **Traits of Inefficient Kitchens:** oversized operations, high costs, excessive waste, lower ratings, suboptimal delivery performance.
* **Savings Potential:** ~107 staff could be optimized across inefficient kitchens; ~$10,500+ monthly opex savings.