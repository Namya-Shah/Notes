---
tags:
  - article
URL: https://blog.cloudflare.com/code-mode/
---
1. Convert the MCP tools into a TypeScript API, and then ask an LLM to write code that calls that API.
2. Agents are able to handle many more tools, and more complex tools, when those tools are presented as a Typescript API rather than directly.
	- Perhaps, this is because LLMs have an enormous amount of real-world TypeScript in their training set, but only a small set of contrived examples of tool calls.
3. The approach really shines when an agent needs to string together multiple calls.
	- With the traditional approach, the output of each tool call must be fed into the LLMs's neural network, just to be copied over to the inputs of the next call, wasting time, energy, and tokens.
4. MCP is an uniform way to:
	- expose an API for doing something,
	- along with documentation needed for an LLM to understand it,
	- with authorization handled out-of-band.
5. The "API" exposed by an MCP server is expressed as a set of "tools". Each tool is essentially a **remote procedure call (RPC)** function - it is called with some parameters and returns a response.
6. Most modern LLMs have the capability to use "tools" (sometimes called "function calling"), meaning they are trained to output text in a certain format when they want to invoke a tool.
7. A tool call, though, involves a token that does *not* have any textual equivalent. The LLM is trained (or, more often, fine-tuned) to understand a special token that it can output that means "the following should be interpreted as a tool call", and another special token that means "this is the end of the tool call". Between these two tokens, the LLM will typically write tokens corresponding to some sort of JSON message that describes the call.
![[Pasted image 20260226095625.png]]
![[Pasted image 20260226101351.png]]
> [!IMPORTANT] Why do LLMs not able to perform well when tool calling
> LLMs have seen a lot of code. They have not seen a lot of "tool calls". 
