---
Link:
tags:
  - MCP
  - ML
---
# Brief Introduction
- The transport layer manages communication channels and authentication between clients and servers. It handles connection establishment, message framing, and secure communication between MCP participants
- **STDIO Transport**
	- Uses standard input/output streams for direct process communication between local processes on the same machine, providing optimal performance with no network overhead.
- **Streamable HTTP Transport**
	- Uses HTTP POST for client-to-server messages with optional Server-Sent Events for streaming capabilities.
	- This transport enables remote server communication and supports standard HTTP authentication methods including bearer tokens, API keys, and custom headers. MCP recommends using OAuth to obtain authentication tokens.


# References
---
1. [[Model Context Protocol (MCP)]]
