---
Link:
tags:
  - MCP
  - ML
---
- Uses JSON-RPC 2.0 based exchange protocol
- **Lifecycle Management**
	- Handles connection initialization
	- Capability negotiation
	- Connection termination between clients and servers
- **Server Features**
	- Enables servers to provide core functionality
		- **Tools** for *AI actions*
		- **Resources** for *context data*
		- **Prompts** for *interaction templates* from and to the client
- **Client Features**
	- Enables servers to ask the client to sample from the host LLM
	- Get input from the user
	- Log messages to the client
- **Utility Features**
	- Supports additional capabilities like notifications for real-time updates and progress tracking for long running operations.


# References
---
1. [[Model Context Protocol (MCP)]]
