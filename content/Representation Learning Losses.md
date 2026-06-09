# [[Contrastive Loss]]
- Pulls similar pairs together, pushes dissimilar pairs apart by a margin m. Used in Siamese networks, face verification.
# [[Triplet Loss]]
- Anchor + positive + negative. Forces: distance (anchor, positive) < distance (anchor, negative) - margin. Triplet selection strategy matters enormously.
# [[InfoNCE]]
- Used in SimCLR and self-supervised learning. Pulls augmented views of the same sample together against all other samples in the batch as negatives. Performance is highly sensitive to batch size, augmentation, and temperature $\tau$
# [[VAE ELBO]]
- Two-part objective: reconstruction loss (explain the data) + KL term (keep the latent space well-structured). $\beta$-VAE variants add weight to the KL term.