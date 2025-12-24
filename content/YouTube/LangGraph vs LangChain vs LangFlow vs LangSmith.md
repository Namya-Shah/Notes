---
Location:
  - YouTube
Channel:
  - "[[FuturMinds]]"
Date: 2025-07-16 23:52
Topics:
  - "[[LangGraph]]"
  - "[[LangChain]]"
  - "[[LangFlow]]"
  - "[[LangSmith]]"
tags:
  - "#YouTube"
---
# Video
<iframe width="560" height="315" src="https://www.youtube.com/embed/ldBsvhjEREc?si=lsJwYeEdPM2seOoV" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# Notes
## LangChain
- Abstractions
	- Pre-built steps and concepts that you can chain together
- LLM Support
- Prompts
	- Prompt templates so we don't require to hardcode any query
	- Customizing prompts dynamically for different tasks
- Chains
	- Heart of langchain
	- we can chain different tasks together like calling an LLM, retrieving data, processing responses
- Indexes
	- Document loaders and vector databases to pull in external data so our model isn't limited to what it is train on
- Memory
	- Langchain enables the application to remember past interactions adding long-term memory to your workflows
- Agents
	- These components use the LLM as a reasoning engine to decide the next step in the workflow that makes our workflow dynamic
## LangGraph
- It excels at handling multiple agents where one wants to solve complex problems
![[Pasted image 20250718104635.png]]
- **State** is a shared data structure that represents the current snapshot of the application. It maintains information that can be updated and accessed by different parts of the graph.
	- A typical state might include user inputs, agent outcomes and a list of actions taken throughout the workflow
- **Nodes** represent the individual components or actions within the graph.
	- Each node can perform specific task such as executing an LLM, running a function or interacting with external tools
- **Edges** connects nodes and define the flow of execution within the graph.
	- They determine how data moves from one node to another
	- This is not a directed graph which means nodes can make decision about which node they want to call next and they can talk to each other back and forth.
> [!IMPORTANT] NOTE
> We use LangGraph when we require cyclical interactions and decision making processes. It is also ideal for scenarios where multiple agents need to collaborate and work together.
## LangFlow
- No-code workflow to create chatbots or data preprocessing tools
- Drag-and-drop interface
- Langflow is built on top of LangChain and provides visual interface to build and experiment with LangChain flows
- Perfect for prototyping LLM applications
- *Not to be used in production but intended to be used in prototyping*
## LangSmith
- Designed to assist at all stages of the LLM application's lifecycle
	- Includes prototyping, beta testing, and production
- Designed to be independent so we can use it with any LLM framework and using LangChain is not mandatory
- We should not use it if our application is straight forward

