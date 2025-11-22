# Configuration - IDE - Docs - Kiro

Source: https://kiro.dev/docs/mcp/configuration/

---

This guide provides detailed information on configuring Model Context Protocol (MCP) servers with Kiro, including configuration file structure, server setup, and best practices.
Configuration file structure
MCP configuration files use JSON format with the following structure:
json{
"mcpServers": {
"local-server-name": {
"command": "command-to-run-server",
"args": ["arg1", "arg2"],
"env": {
"ENV_VAR1": "hard-coded-variable",
"ENV_VAR2": "${EXPANDED_VARIABLE}"
},
"disabled": false,
"autoApprove": ["tool_name1", "tool_name2"],
"disabledTools": ["tool_name3"]
},
"remote-server-name": {
"url": "https://endpoint.to.connect.to",
"headers": {
"HEADER1": "value1",
"HEADER2": "value2"
},
"disabled": false,
"autoApprove": ["tool_name1", "tool_name2"],
"disabledTools": ["tool_name3"]
}
}
}
Configuration properties
Remote server
PropertyTypeRequiredDescriptionurlStringYesHTTPS endpoint for the remote MCP server (or HTTP endpoint for localhost)headersObjectNoHeaders to pass to the MCP server during connectionenvObjectNoEnvironment variables for the server processdisabledBooleanNoWhether the server is disabled (default: false)autoApproveArrayNoTool names to auto-approve without promptingdisabledToolsArrayNoTool names to omit when calling the Agent
Local server
PropertyTypeRequiredDescriptioncommandStringYesThe command to run the MCP serverargsArrayYesArguments to pass to the commandenvObjectNoEnvironment variables for the server processdisabledBooleanNoWhether the server is disabled (default: false)autoApproveArrayNoTool names to auto-approve without promptingdisabledToolsArrayNoTool names to omit when calling the Agent
Configuration locations
You can configure MCP servers at two levels:
Workspace Level: .kiro/settings/mcp.json
Applies only to the current workspace
Ideal for project-specific MCP servers
User Level: ~/.kiro/settings/mcp.json
Applies globally across all workspaces
Best for MCP servers you use frequently
If both files exist, configurations are merged with workspace settings taking precedence.
Creating configuration files
Using the command palette
Open the command palette:
Mac: Cmd + Shift + P
Windows/Linux: Ctrl + Shift + P
Search for "MCP" and select one of these options:
Kiro: Open workspace MCP config (JSON) - For workspace-level configuration
Kiro: Open user MCP config (JSON) - For user-level configuration
Using the Kiro panel
Open the Kiro panel
Select the Open MCP Config icon
json{
"mcpServers": {
"web-search": {
"command": "npx",
"args": [
"-y",
"@modelcontextprotocol/server-bravesearch"
],
"env": {
"BRAVE_API_KEY": "${BRAVE_API_KEY}"
}
}
}
}
Environment variables
Many MCP servers require environment variables for authentication or configuration:
json{
"mcpServers": {
"server-name": {
"env": {
"API_KEY": "${YOUR_API_KEY}",
"DEBUG": "true",
"TIMEOUT": "30000"
}
}
}
}
Disabling servers temporarily
To temporarily disable an MCP server without removing its configuration:
json{
"mcpServers": {
"server-name": {
"disabled": true
}
}
}
Security considerations
When configuring MCP servers, follow security best practices to protect your credentials and system:
Use environment variable references (e.g., ${API_TOKEN}) instead of hardcoding sensitive values
Never commit configuration files with credentials to version control
Only connect to trusted remote servers
Review tool permissions before adding them to autoApprove
For comprehensive security guidance, see the MCP Security Best Practices page.
Troubleshooting configuration issues
If your MCP configuration isn't working:
Validate JSON syntax:
Ensure your JSON is valid with no syntax errors
Check for missing commas, quotes, or brackets
Verify command paths:
Make sure the command specified exists in your PATH
Try running the command directly in your terminal
Check environment variables:
Verify that all required environment variables are set
Check for typos in environment variable names
Save configuration changes:
Changes to MCP configuration apply automatically when you save the file
Simply save the config file (Cmd+S) and servers will reconnect
Page updated: November 20, 2025MCPServer directory