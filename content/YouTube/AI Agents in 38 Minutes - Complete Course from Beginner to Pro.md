---
Location:
  - YouTube
Channel:
  - Marina Wyss
Date: 2025-12-21 20:34
Topics:
  - AI Agents
tags:
  - YouTube
  - "#AI-Agents"
---
# Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/sNvuH-iTi4c?si=a_DhrzZKoDIhzhMI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# Notes
- Extracting key fields from invoices and storing them in the databases
- Full customer service agent that handles questions
## Use Case Matrix
![[Pasted image 20251221203645.png]]
![[Pasted image 20251221203916.png]]
## Context Engineering
- System prompts
- Instructions
- Role
- Memory
- Tools
- and more!
## Task Decomposition
- **Outline** using an LLM
- **Generate search terms** using an LLM, then call a search API
- **Fetch pages** using a tool
- **Write draft** with an LLM using those sources
- **Self-critique** the draft using an LLM to reflect and list gaps
- **Revise** using an LLM

> *Memory* is what lets an agent remember what worked, what failed, and what it needs to do differently next time, so it actually improves on each run.

![[Pasted image 20251221204833.png]]
## Guardrails
- Quality gate between what the agent says is done and the task that actually is being finalized.
- 3 main approaches to guardrails
	- For deterministic stuff like output format and length, we can just use standard code snippets.
	- Checking if the response is factually consistent with the sources or is the tone positive and professional (LLM Judge)
	- Need human to check the work (Human Feedback)
## Design Patterns
- **Reflection** basically just means we don't stop at the first draft.
	- When using reflection, the model produces something, critiques it, then rewrites it if needed.
- **Tool Use**
	- Calendar appointments, getting current time and more...
	- ![[Pasted image 20251221210050.png]]
- **Planning**
	- Give the agent access to tools
	- Prompt it to create a plan: "List the step-by-step actions to answer this question"
	- Execute the plan step-by-step
	- Repeat until you're done
- **Multi-Agent Collaboration**
	- Specialization at each step
	- Limits individual agents' context windows
	- Mix different LLMs
	- Easily parallelizable
	- Split up long operations
- **Roles**
	- *Researcher*
		- Tasks
			- Analyze market trends
			- Research competitors
		- Tools
			- Web search
	- *Designer*
		- Tasks
			- Create visualizations and graphics
		- Tools
			- Image generation
			- Code for making plots
	- *Writer*
		- Tasks
			- Transform research into final copy
		- Tools
			- None (just the LLM)
- **Sequential**
	- ![[Pasted image 20251222125713.png]]
- Parallel
	- ![[Pasted image 20251222125742.png]]
- **Single Manager Hierarchy**
	- ![[Pasted image 20251222125814.png]]
- **Deeper Hierarchy**
	- ![[Pasted image 20251222125853.png]]
- **All-to-All**
	- ![[Pasted image 20251222125919.png]]
- **Coordination Pitfalls**
	- *Redundant Work*
		- Multiple agents may redo the same searches or call the same tools
	- *Unnecessary serialization*
		- Chaining steps that could run concurrently slows everything down
	- *Define interfaces, not vibes*
		- Each agent needs a clear schema for inputs and outputs
	- *Scope tools per agent*
		- Give each agent only the tools it actually needs with least privilege
	- *Log the trace*
		- Keep per step artifacts
			- What did each agent plan?
			- What prompts did it use?
			- What tool calls did it make?
			- What results came back?
	- *Evaluate components and end-to-end*
		- Component level
			- Is this research relevant?
			- Are the images high quality?
			- Is the copy tone appropriate?
		- End-to-end
			- Is the final brochure good?
			- Did it meet requirements?
- **Functional Decomposition**
	- Split the tasks by technical domain or expertise
- **Spatial Decomposition**
	- Split by file directory or structure
- **Temporal Decomposition**
	- Split tasks into sequential stages where the later stages depend on the earlier ones being complete.
- **Data-driven decomposition**
	- Split by data partitions
	- Useful for large datasets to process it into chunks
	- *Example:*
		- Agent 1 processes Week 1 logs
		- Agent 2 processes Week 2 logs
		- Agent 3 processes Week 3 logs
		- Agent 4 processes Week 4 logs
## Improving non-LLM components
- **Tune the knobs.** Fiddle with things like web search date ranges, top-k results, RAG chunk size, similarity thresholds, and so on.
- **Swap providers.** Try alternative web search APIs. Different OCR or vision models, and so on.
## Improving LLM components
- Prompt better
- Few shot input-output pairs
- Try another model
- Decompose hard tasks into smaller pieces
- Fine-tune (only as a last resort)
> [!NOTE]
> Nailing the output quality should be the first step.
## Reducing Latency
- **Get a baseline**
	- Time each step in the workflow
- **Parallelize**
	- Run anything in parallel that you can
- **Right-size the model**
	- Use smaller, faster LLM where tasks are simple, like keyword generation
	- Reserve the heavy weight models for synthesis and reasoning
- **Try faster providers**
	- Throughput and token streaming speeds vary a lot
	- A provider with optimized serving can cut seconds without any prompt changes.
- **Trim Context**
	- Shorter prompts and contexts means faster decoding.
## Cost Sources
- **LLM calls:** Determined by input tokens and output tokens.
	- Input tokens are cheaper but output tokens cost more.
- **API calls:** Web search, PDF conversion, image generation, speech-to-text. These often have per-call or per-unit pricing.
- **Infrastructure:** If you're running your own retrieval systems, vector databases, or compute for code execution.
## Optimizing Cost
- Attack the big buckets first
- Tier your models
- Cache aggressively
- Constrain outputs
- Use batch when possible
## Observability & Monitoring
- Observability covers debugging, quality monitoring, and hallucination tracking.
- The outputs from AI model are un-deterministic
- **Two kinds of metrics**
	- "*Zoom-in*" metrics help you debug single runs.
		- This is your full trace: prompts, tool calls, token usage, retry attempts, and every decision point. Basically everything required to reproduce an error and see exactly where it went wrong.
	- "*Zoom-out*" metrics tell you how the whole system is doing over many runs.
		- This includes automated quality checks (often with an LLM-as-judge), hallucination rates, success/ROI measures, and trend lines that show whether changes are helping or hurting.
## Security Threats
- Prompt injection
	- Malicious content and user input or external data that hijacks your agents instruction.
- Unsafe code generation
	- Agents writing code that accesses sensitive data or executes dangerous operations
- Data leakage
	- PII or proprietary information could be exposed through agent outputs or tool calls.
- Resource exhaustion
	- Agents could spin up expensive operations or infinite loops
## Safe Code Execution
- Sandbox execution
	- Isolate code execution completely from your main application
- Resource limits
	- Set timeouts, memory caps, CPU limits
	- Block dangerous imports & network access unless explicitly needed
	- File system rights outside of a designated temp directory
- Whitelist libraries only
	- Don't allow arbitrary installs
- Validation plus reflection loop
	- If code execution errors, capture the trace back and let the model fix the code.
- Deterministic I/O
	- Have code return a small structured result like a number, a list, or a JSON object.
	- Don't let the code directly output to the user or write to files they can access
- Input and output sanitation
	- All inputs are validated before they reach the agent and all the outputs are scanned for sensitive data like API keys or PII.
