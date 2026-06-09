# [[Dice Loss]]
- Optimizes overlap directly. Handles imbalanced foreground/background. Add smoothing constant $\epsilon$ to the denominator to avoid instability.
# [[IoU Loss]]
- Often harsher than Dice when predictions and targets disagree. Both Dice and IoU use soft predictions for differentiability.
# [[Tversky Loss]]
- Generalizes Dice by weighting false positives and false negatives differently via $\alpha$ and $\beta$. Preferred in medical imaging where missing a lesion costs more than a false alarm.
# [[GIoU]]
- Standard IoU gives zero gradient when boxes don't overlap. GIoU adds the enclosing box area to maintain a training signal even with no overlap.
# [[DIoU]]
- Extends GIoU by penalizing center-point distance. Encourages both overlap and spatial alignment.