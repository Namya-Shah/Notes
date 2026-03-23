---
Location:
  - YouTube
Channel:
  - Aishwarya Srinivasan
Date: 2026-03-04 00:27
Topics:
  - Projects
tags:
  - YouTube
---
# Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/9WIsvEswZTk?si=UUf6J3LOvZtS_Y1f" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
# Projects
## Production Grade RAG
  - Phase 1: Get the fundamentals working
  - Phase 2: Graduating from demo to production quality (BM25 and similarity search), also adding re-ranker, citation enforcement
    - Store all of the prompts in versioned config files, because prompts are the part of architecture
  - Phase 3: Measurement of Faithfulness
  ### Tech Stack
  - LangChain
  - LangGraph
  ### Vector Store
  - ChromaDB
  - Weaviate
  ### Reranking
  - cohere reranker
  - sbert.net
  ### Evaluation Framework
  - Ragas
## Developing an offline local AI assistant using a small language model
- Why this project works?
	- Privacy regulations to consider
	- Latency requirements that rule out network round trips
	- Cost constraints at scale
	- Edge deployments situations where internet connectivity isn't guaranteed.
- Phase 1: Measurement
	- I want you to rigorously benchmark your model's inference performance:
		- Tokens per second
		- Time to first token
		- Total response latency
	- Write down all this and include it in your documentation.
- Phase 2: Add structure and determinism
	- Enforce JSON output schema on your model's responses
	- Validate them with Pydantic
	- Implement a retry mechanism that catches invalid outputs
	- Re-prompts once before failing gracefully
	- Run same set of prompts at different temperatures
- Phase 3: Model Comparison Study
	- Pick 3 models at random
      - Compare memory usage
      - Tokens per second
      - Output quality on a standardized set of 30 to 50 test prompts
    - Write it all up as a concise technical report with actual number and analysis
    - **OPTIONAL:** Try quantized model
## Add comprehensive monitoring and observability to your RAG
- Phase 1: Instrument every step of your RAG pipeline with tracing
	- You can see exactly:
		- which chunks were retrieved?
		- how the reranker reordered them?
		- what prompt was sent to the language model?
		- what the response was?
		- how many tokens were consumed?
	- Tools
		- LangSmith
		- LangFuse (Open-Source/Self-Host)
		- BrainTrust
- Phase 2: Tracking quality metrics over time
	- Measure latency at P50 and P95 percentiles and not just the average.
	- Track cost per request
	- Measure the citation coverage, which is the percentage of your answers that are properly grounded in retrieved evidence.
	- Monitor your failure rate, which means how often does the system errors out or produces a response that it cannot support
- Phase 3: This connects everything with regression gating
	- Evaluation dataset from project 1 now runs automatically as part of your continuous integration pipeline.
	- If the faithfulness or any other key metric drops below a defined threshold, the build fails and the change doesn't get merged.
	- Versioning the prompts and configuring files right alongside your code because a prompt change can affect the system behavior just as dramatically as a code change.
## Fine-Tuning
### Supervised Fine-Tuning
### Preference Tuning


