---
Location:
  - YouTube
Channel:
  - "[[IBM]]"
Date: 2025-07-16 09:34
Topics:
  - "[[Retrieval Augmented Generation]]"
  - "[[Multi-Agent]]"
  - "[[Internet of Things]]"
tags:
  - "#YouTube"
---
# Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/Ts42JTye-AI?si=53VJboii-OsxrioI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# Notes
## Internet of Things (IOT)
### Agriculture
- Agricultural AI Agents interfacing with IoT controllers
- **Goal**
	- Maximize crop yield
- **Planner**
	- **Tool 1** -> Weather API
	- **Tool 2** -> Soil Sensor API
- **Memory**
	- Stores history + context
- **Executor**
	- Generates action plan
- **Action**
	- IoT Controllers
> Process is iterative and self-improving
## Retrieval Augmented Generation (RAG)
### Content Creation
- Can write a blog post for any topic we like
- **Goal**
	- Write blog post on solar energy for students
- **Planner**
	- **Tool** -> Web Search
- **Memory**
	- The tool looks for relevant documents and then the agent (RAG) splits these documents into chunks. These chunks are then stored into *vector database*
- **Executor**
	- We use LLMs to write the blogpost. It doesn't use its past memory to write but it uses the new memory stored in the vector database.
- **Action**
	- The action is to populate the outline incorporating those recalled facts, and adjust the tone for the target audience.

## Multi-Agent
### Disaster Response
- **Goal**
	- Coordinate emergency response after major earthquake
- **Planner**
	- Coordination Agent
	- **Tool 1** -> Vision AI
	- **Tool 2** -> NLP Analyzer
	- **Tool 3** -> Simulation model
- **Memory**
	- Shared Situational Map
- **Executor**
	- Recommends Action
- **Action**
	- Coordinates the response

### Banking/Finance
- Agents demonstrate real-time stream processing, continuously ingesting transaction data and using anamoly detection to flag fraud transaction
### Customer Experience
- Agents use sentiment analysis.
- Analyzing customer tone to adjust their responses
### Healthcare
- We use multi-agent coordination, specialized sub agents handle different tasks like analyzing lab results and managing prescriptions.
### Human Resources
- Workflow Automation
	- They execute multi step processes, like onboarding new employees, automatically integrating with systems like workday or SAP.
### IT Operations
- It automates remediation checking out the faults and then executing scripts to fix issues.
### Supply Chain
- It uses predictive analytics forecasting demands on market needs.
### Transportation
- Dynamic replanning
- Continuously recalculating optimal routes