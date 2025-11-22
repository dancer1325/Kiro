# Model context protocol (MCP) - IDE - Docs - Kiro

Source: https://kiro.dev/docs/mcp/

---

Model Context Protocol (MCP) extends Kiro's capabilities by connecting to specialized servers that provide additional tools and context. This guide helps you set up, configure, and use MCP servers with Kiro.
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
Enabling MCP support
After creating your configuration file:
Open Settings with Cmd + , (Mac) or Ctrl + , (Windows/Linux)
Search for "MCP"
Enable the MCP support setting
Using the MCP servers tab
The Kiro panel includes an MCP servers tab that shows:
All configured MCP servers
Connection status indicators
Quick access to server tools
To use this feature:
Select the Kiro icon in the activity bar
Navigate to the MCP servers tab
Click any tool name to insert a placeholder prompt in the chat
Troubleshooting
If you encounter issues with MCP servers:
Checking MCP logs
Open the Kiro panel
Select the Output tab
Choose "Kiro - MCP Logs" from the dropdown
Common issues and solutions
IssueSolutionConnection failuresVerify prerequisites are installed correctlyPermission errorsCheck that tokens and API keys are validTool not respondingReview MCP logs for specific error messagesConfiguration not loadingValidate JSON syntax and save the config file
Additional resources
Official MCP Documentation
Next steps
Now that you have created a hook file, you can further learn about hooks here:
Configuring MCPs - Learn about configuring Model Context Protocol (MCP) servers
MCP Server management - Learn how to use common MCP servers with examples
Using MCP Tools - Learn how to effectively use MCP tools with Kiro
Best Practices - Best practices for effective MCP usage
Page updated: November 16, 2025SteeringConfiguration