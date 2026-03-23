---
Link:
tags:
  - Interview
---
1. What is Agentic AI and how does it differ from traditional AI?
	- Agentic AI refers to systems that demonstrate autonomy. Unlike traditional AI (like a classifier or a basic chatbot) which follows a strict input-output pipeline, an AI Agent operates in a loop: it perceives the environment, reasons about what to do, acts, and then observes the result of that action.
	

| Traditional AI (Passive)                         | Agentic AI (Active)                                        |
| ------------------------------------------------ | ---------------------------------------------------------- |
| Gets a single input and produces a single output | Receives a goal and runs a loop to achieve it              |
| “Here is an image, is this a cat?”               | “Book me a flight to London under $600”                    |
| No actions are taken                             | Takes real actions like searching, booking or calling APIs |
| Does not change strategy                         | Adjusts strategy based on results                          |
| Stops after responding                           | Keeps going until the goal is reached                      |
| No awareness of success or failure               | Observes outcomes and reacts                               |
| Cannot interact with the world                   | Searches airline sites, compares prices, retries           |
2. What are the core components of an AI agent?
	- A robust agent typically consists of four pillars:
		- **The Brain (LLM):** The core controller that handles reasoning, planning, and decision-making
		- **Memory:**
			- Short-term: The context window (chat history)
			- Long-term: Vector databases or SQL
		- **Tools:** Interfaces that allow the agent to interact with the world (e.g., Calculators, APIs, Web Browsers, File Systems)
		- **Planning:** The capability to decompose a complex user goal into smaller, manageable sub-steps (e.g., using ReAct or Plan-and-Solve patterns)
	- ![[Pasted image 20260213191400.png]]
3. Which libraries and frameworks are essential for Agentic AI right now?
	- While the landscape moves fast, the industry standards in 2026 are:
		- **LangGraph:** The go-to for building stateful, production-grade agents with loops and conditional logic.
		- **LlamaIndex:** Essential for "Data Agents", specifically for ingesting, indexing, and retrieving structured and unstructured data.
		- **CrewAI/AutoGen:** Popular for multi-agent orchestration, where different "roles" (Researcher, Writer, Editor) collaborate.
		- **DSPy:** For optimizing prompts programatically rather than manually tweaking strings.
4. Explain the difference between a Base Model and an Assistant Model.	

| Aspect                 | Base Model                                                                           | Assistant (Instruct/Chat) Model                                                                                                |
| ---------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Training method        | Trained only with unsupervised next-token prediction on large internet text datasets | Starts from a base model, then refined with supervised fine-tuning (SFT) and reinforcement learning with human feedback (RLHF) |
| Goal                   | Learn statistical patterns in text and continue sequences                            | Follow instructions, be helpful, safe and conversational                                                                       |
| Behavior               | Raw and unaligned; may produce irrelevant or list-style completions                  | Aligned to user intent; gives direct, task-focused answers and refuses unsafe requests                                         |
| Example response style | Might continue a pattern instead of answering the question                           | Directly answers the question in a clear, helpful way                                                                          |
5. What is the "Context Window" and why is it limited?
	- The context window is the "working memory" of the LLM, which is the maximum amount of text (tokens) it can process at one time. It is limited primarily due to the Self-Attention Mechanism in Transformers and storage constraints.
	- The computational cost and memory usage of attention grow quadratically with the sequence length. Doubling the context length requires roughly 4x the compute. While techniques like "Ring Attention" and "Mamba" (State Space Models) are alleviating this, physical VRAM limits on GPUs remain a hard constraint.
	- ![[Pasted image 20260214113647.png]]
6. Have you worked with Reasoning Models like OpenAI o3, DeepSeek-R1? How are they different?
	- Yes. Reasoning models differ because they utilize inference-time computation. Instead of answering immediately, they generate a "Chain of Thought" (often hidden or visible as "thought tokens") to talk through the problem, explore different paths, and self-correct errors before producing the final output.
	- This makes them significantly better at math, coding, and complex logic, but they introduce higher latency compared to standard "fast" models like GPT-4o-mini or Llama 3.
7. How do you stay updated with the fast-moving AI landscape?
	- *"I follow a mix of academic and practical sources. For research, I check arXiv Sanity and papers highlighted by Hugging Face Daily Papers. For engineering patterns, I follow the blogs of LangChain and OpenAI. I also actively experiment by running quantized models locally (using Ollama or LM Studio) to test their capabilities hands-on."*
8. What is specific about using LLMs via API vs. Chat interfaces?
	- Building with APIs (like Anthropic, OpenAI, or Vertex AI) is a fundamentally different from using
		- **Statelessness:** APIs are stateless; you must send the entire conversation history (context) with every new request.
		- **Parameters:** You control hyper-parameters like temperature (randomness), `top_p` (nucleus sampling), and `max_tokens`. This can be tweaked to get a better response or longer response or longer responses than what's on offer on chat interfaces.
		- **Structured Output:** APIs allow you to enforce JSON schemas or use "function calling" modes, which is essential for agents to reliably parse data, whereas chat interfaces output unstructured text.
9. Can you give a concrete example of an Agentic AI application architecture?
	- Consider a **Customer Support Agent**
		1. **User Query:** *"Where is my order #123?"*
		2. **Router:** The LLM analyzes the intent. It seems this is an "Order Status" query, not a "General FAQ" query.
		3. **Tool Call:** The agent constructs a JSON payload `{"order_id": "123"}` and calls the Shopify API.
		4. **Observation:** The API returns "Shipped - Arriving Tuesday."
		5. **Response:** The agent synthesizes this data into natural language. "Hi! Good news, order #123 is shipped and will arrive this Tuesday."
	- ![[Pasted image 20260214114823.png]]
10. What is "Next Token Prediction"?
	- 