---
Link:
tags:
  - ML
  - MCP
---
# Introduction
- MCP is an open-source standard for connecting AI applications to external systems.
- Using MCP, AI applications like Claude or ChatGPT can connect to data sources (e.g., local files, databases), tools (e.g., search engines, calculators) and workflows (e.g., specialized prompts) - enabling them to access key information and perform tasks.
- Think of MCP like a USB-C port for AI applications.
# What can MCP enable?
- Agents can access your Google Calendar and Notion, acting as a more personalized AI assistant.
- Claude Code can generate an entire web app using a Figma design
- Enterprise chatbots can connect to multiple databases across an organization, empowering users to analyze data using chat.
- AI models can create 3D designs on Blender and print them out using a 3D printer.
# Why does MCP matter?
- **Developers**: MCP reduces development time and complexity when building, or integrating with, an AI application or agent.
- **AI applications or agents**: MCP provides access to an ecosystem of data sources, tools and apps which will enhance capabilities and improve the end-user experience.
- **End-users**: MCP results in more capable AI applications or agents which can access your data and take actions on your behalf when necessary.
# Scope
- **[[MCP Specification]]**
	- A specification of MCP that outlines the implementation requirements for clients and servers.
- **[[MCP SDKs]]**
	- SDKs for different programming languages that implement MCP.
- **[[MCP Development Tools]]**
	- Tools for developing MCP servers and clients, including the MCP Inspector
- **[[MCP Reference Server Implementations]]**
	- Reference implementations of MCP servers.
# Concepts of MCP
## Participants
- MCP follows a client-server architecture where an MCP host establishes connections to one or more MCP servers.
- The MCP host accomplishes this by creating one MCP client for each MCP server. Each MCP client maintains a dedicated connection with its corresponding MCP server.
- Local MCP servers that use the **STDIO transport** typically serve a single MCP client, whereas remote MCP servers that use the **Streamable HTTP transport** will typically serve many MCP clients.
- **MCP Host**: The AI application that coordinates and manages one or multiple MCP clients.
- **MCP Client**: A component that maintains a connection to an MCP server and obtains context from an MCP server for the MCP host to use.
- **MCP Server**: A program that provides context to MCP clients.
![[Pasted image 20260106122308.png]]
## Layers
- **[[Data layer]]**: Defines the JSON-RPC based protocol for client-server communication, including lifecycle management, and core primitives, such as tools, resources, prompts and notifications.
- **[[Transport Layer]]**: Defines the communication mechanisms and channels that enable data exchange between clients and servers, including transport-specific connection establishment, message framing, and authorization.
> [!NOTE] NOTE
> Conceptually, the data layer is the inner layer, while the transport layer is the outer layer.
## Primitives
MCP primitives define what clients and servers can offer each other. These primitives specify the types of contextual information that can be shared with AI applications and the range of actions that can be performed.
Primitives *servers* can expose:
- **Tools**: Executable functions that AI applications can invoke to perform actions (e.g., file operations, API calls, database queries)
- **Resources**: Data sources that provide contextual information to AI applications (e.g., file contents, database records, API responses)
- **Prompts**: Reusable templates that help structure interactions with language models (e.g., system prompts, few-shot examples)
> [!NOTE]
> Each primitive type has associated methods for discovery (`*/list`), retrieval (`*/get`), and in some cases, execution (`tools/call`). MCP clients will use the `*/list` methods to discover available primitives. This design allows listings to be *dynamic*.

Primitives *clients* can expose:
- **Sampling**: Allows servers to request language model completions from the client's AI application. This is useful when servers' authors want access to a language model, but want to stay model independent and not include a language model SDK in their mcp server. They can use the `sampling/complete` method to request a language model completion from the client's AI application.
- **Elicitation**: Allows servers to request additional information from users. This is useful when servers' authors want to get more information from the user, or ask for confirmation of an action. They can use the `elicitation/request` method to request additional information from the user.
- **Logging**: Enables servers to send log messages to clients for debugging and monitoring purposes.
- 

# References
---
1. 
