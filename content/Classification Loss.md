# [[Binary Cross-Entropy (BCE)]]
- Standard for binary/multi-label tasks. Always use BCEWithLogitsLoss passing probabilities separately before the log is numerically unstable.
# [[Softmax Cross-Entropy]]
- Standard for multiclass. In PyTorch, pass logits as input. Targets are usually integer class indices, but class-probability targets are also supported for soft labels such as label smoothing.
# [[Label Smoothing]]
- Softens one-hot targets by distributing a small probability mass across all classes. Reduces overconfidence and improves calibration.
# [[Hinge Loss]]
- Margin-based, from SVM. Zero loss for correctly classified examples with a sufficient margin. No calibrated probabilities.
# [[KL Divergence]]
- Compares two distributions. Use reduction="batchmean" in PyTorch "mean" doesn't match the mathematical definition.