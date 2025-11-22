# Model context protocol (MCP) - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/mcp/

---

Model Context Protocol (MCP) extends Kiro's capabilities by connecting to specialized servers that provide additional tools and context. This guide helps you set up, configure, and use MCP servers with Kiro.
TipWithin an interactive chat session, you can use the /mcp slash command to see which MCP servers are currently loaded. See Slash Commands for more details.
What is MCP?
MCP is a protocol that allows Kiro to communicate with external servers to access specialized tools and information. For example, the AWS Documentation MCP server provides tools to search, read, and get recommendations from AWS documentation directly within Kiro.
With MCP, you can:
Access specialized knowledge bases and documentation
Integrate with external services and APIs
Extend Kiro's capabilities with domain-specific tools
Create custom tools for your specific workflows
Setting up MCP
Prerequisites
Before using MCP, make sure you have:
The latest version of Kiro installed
Any specific prerequisites for the MCP servers you want to use (listed in each server's documentation)
Managing MCP servers
There are two ways of integrating MCP servers with Kiro CLI:
Command line management
bash# Add new MCP server
kiro-cli mcp add github \
--url "mcp://github.com/api" \
--auth-token "$GITHUB_TOKEN" \
--type "http"
Configuration file
json{
"mcpServers": {
"local-server-name": {
"command": "command-to-run-server",
"args": ["arg1", "arg2"],
"env": {
"ENV_VAR1": "value1",
"ENV_VAR2": "value2"
},
"disabled": false
},
"remote-server-name": {
"url": "https://endpoint.to.connect.to",
"type": "http",
"headers": {
"HEADER1": "value1",
"HEADER2": "value2"
},
"disabled": false
}
}
}
Troubleshooting
If you encounter issues with MCP servers:
Checking MCP logs
Common issues and solutions
IssueSolutionConnection failuresVerify prerequisites are installed correctlyPermission errorsCheck that tokens and API keys are validTool not respondingReview MCP logs for specific error messagesConfiguration not loadingValidate JSON syntax and save the config file
Additional resources
Official MCP Documentation
Next steps
Now that you understand MCP basics, explore these resources:
Examples - Practical examples of using MCP servers with Kiro CLI
Security Best Practices - Best practices for secure MCP usage
Page updated: November 16, 2025TroubleshootingExamples