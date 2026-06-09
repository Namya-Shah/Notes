# [[Class Weights]]
- Upweight minority classes in cross-entropy. Simple and effective, but too large weights destabilize training.
# [[pos_weight in BCE]]
- For binary tasks, scales the positive class contribution directly. Often a strong baseline for class contribution directly. Often a strong baseline for class imbalance, though resampling can still help depending on the problem.
# [[Focal Loss]]
- Down-weights easy examples, focuses on training on hard ones. Controlled by $\gamma$ (focusing) and $\alpha$ (class balance). Standard for dense object detection. When $\gamma = 0$, it reduces to regular cross-entropy.
# [[Class-Balanced Reweighting]]
- Uses effective sample count rather than raw frequency. Smoother than inverse-count weighting, especially at extreme imbalance.