# Demo

This agent serves as a demo to guide agent development and showcase various agent capabilities.

It has been modified from the version defined in the base repo to also include details on
how to integrate MCP servers with agents.

## How MCP Servers Work with Agents
A new `mcp_tools` field was added to the [index.yaml](./index.yaml) file in order to define and configure MCP support for
agents.

This field allows you to specify the prefixes of the MCP server functions that are generated according to
the MCP servers defined in the [mcp.json](../../mcp.json) file under the `mcpServers` key.

When `argc mcp start` is executed, it populates the main [`functions.json`](../../functions.json) file with
functions that are all prefixed with the name of the corresponding MCP server in the [mcp.json](../../mcp.json).

What this fork does is it allows you to specify which MCP servers you specifically want access to in your agent.

Then, when the `argc mcp start` command is executed, will populate each agent it finds with a non-empty `mcp_tools` field
with all the generated functions from the main `functions.json`.

When you stop the MCP server with `argc mcp stop`, it will also remove the MCP functions from the agent's `functions.json` file.

This allows you to use the agent either with MCP or without, so you don't necessarily have to remember to start the bridge
server every time you want to use your agent if you happen to have separate tools or functions defined in the agent's
tools.sh file.

