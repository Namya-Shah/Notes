---
Location:
  - YouTube
Channel:
  - "[[Coding with Lewis]]"
Date: 2025-07-03 23:01
Topics:
  - "[[Netflix]]"
---
# Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/T5gTIFhPDaY?si=zHvq1AS6ljAC_yUo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# Notes
- [[Match-cut Transition]]
- [[Viola Jones Framework]]
- [[Fully Convolutional Neural Network for Semantic Segmentation]]
- Optical Flow
- 5 Step Match-cut process
	- Shot segmentation
	- Shot de-duplication
	- Compute representation
	- Compute pair scores
	- Extract top results
- [[Embeddings]]
	- Netflix had pre-trained image text models that created an embedding space between the two that way we can see relationship and similarity.
- Netflix uses **Raytrain** to train the model at scale while using decord to decode videos much faster.
- Netflix then used these segmented videos with text pairings and embeddings
- Search -> [[Cosine Similarity]] -> Database
- Dynamic Time Warping
- [[Gated Recurrent Unit (GRU)]]
- 


# Resources
[# Match Cutting: Finding Cuts with Smooth Visual Transitions Using Machine Learning](https://netflixtechblog.com/match-cutting-at-netflix-finding-cuts-with-smooth-visual-transitions-31c3fc14ae59)
[# Detecting Scene Changes in Audiovisual Content](https://netflixtechblog.com/detecting-scene-changes-in-audiovisual-content-77a61d3eaad6)
[# Building In-Video Search](https://netflixtechblog.com/building-in-video-search-936766f0017c)
