# [[MSE]]
- Squares errors, so large residuals dominate. Best when big mistakes are unacceptable. Sensitive to outliers.
# [[MAE]]
- Linear penalty. More robust to outliers, but not differentiable at zero (uses subgradients)
# [[Huber]]
- Quadratic for small errors, linear for large ones. Best for both: smooth optimization + outlier resistance. Controlled by threshold $\delta$
# [[Log-Cosh]]
- Smooth everywhere, similiar behavior to Huber. Fully differentiable.
# [[Quantile (Pinball)]]
- Penalizes over/underestimation asymmetrically. Use when you need a specific percentile forecast, not just the mean.
# [[MAPE]]
- Relative error. Useful when scale varies; breaks when targets are near zero.
# [[MSLE]]
- Penalizes relative differences on log scale. Good for skewed, non-negative targets.