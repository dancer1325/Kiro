# Best practices - IDE - Docs - Kiro

Source: https://kiro.dev/docs/mcp/security/

---

This guide outlines security best practices for configuring and using Model Context Protocol (MCP) servers with Kiro, helping you protect sensitive information and maintain system security.
Understanding MCP security
MCP servers extend Kiro's capabilities by connecting to external services and APIs. Since all MCP servers are third-party code, this introduces potential security considerations that should be addressed:
Access to sensitive information: MCP servers may require API keys or tokens
External code execution: MCP servers run code outside of Kiro's sandbox
Data transmission: Information flows between Kiro and external services
Source verification: Review the source code and verify the server comes from a trusted source before using
Isolation: Run servers in isolated environments when possible and limit the permissions granted
Secure configuration
Protecting API keys and tokens
Never commit configuration files with sensitive tokens to version control
Create tokens with minimal permissions necessary for the MCP server to function (for example, use fine-grained personal access tokens for GitHub instead of classic tokens)
Limit access scope to only the repositories or resources needed
Regularly rotate API keys and tokens used in configurations
Use environment variables when possible instead of hardcoding values
Example: Using environment variables
Instead of hardcoding tokens in your configuration:
json{
"mcpServers": {
"github": {
"env": {
"GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_TOKEN}"
}
}
}
}
Set the environment variable in your shell:
bashexport GITHUB_TOKEN=your-token-value
Approved environment variables
For security, Kiro only expands environment variables that are explicitly approved. Only variables in the approved list will be expanded when found in MCP config files.
When you add or modify an MCP server configuration that includes unapproved environment variables, Kiro displays a security warning popup listing the variables that need approval. You can approve them directly from the popup or manage them in settings.
To manage approved environment variables:
Open Kiro settings
Search for "Mcp Approved Env Vars"
Add the environment variables you want to allow for expansion
This prevents MCP servers from accessing arbitrary environment variables on your system.
Configuration file permissions
Restrict access to your MCP configuration files:
bash# Set restrictive permissions on user-level config
chmod 600 ~/.kiro/settings/mcp.json
# Set restrictive permissions on workspace-level config
chmod 600 .kiro/settings/mcp.json
Safe tool usage
Tool approval process
Review each tool request carefully before approval
Check the parameters being passed to the tool
Understand what the tool will do before approving it
Deny any suspicious requests that don't match your current task
Auto-approval guidelines
Only auto-approve tools that:
Don't have write access to sensitive systems
Come from trusted sources with verified code
Are used frequently in your workflow
Have limited scope of what they can access
json{
"mcpServers": {
"aws-docs": {
"autoApprove": [
"mcp_aws_docs_search_documentation",
"mcp_aws_docs_read_documentation"
]
}
}
}
Workspace isolation
Using workspace-level configurations
Use workspace-level configurations for project-specific MCP servers:
project-a/
âââ .kiro/
â   âââ settings/
â       âââ mcp.json  # Project A specific servers
project-b/
âââ .kiro/
â   âââ settings/
â       âââ mcp.json  # Project B specific servers
This ensures that:
MCP servers only run when working in the relevant project
Tokens and configurations are isolated between projects
Security risks are contained to specific workspaces
Monitoring and auditing
Checking MCP logs
Regularly review MCP logs to monitor server activity:
Open the Kiro panel
Select the Output tab
Choose "Kiro - MCP Logs" from the dropdown
Auditing tool usage
Periodically review which tools you've approved:
Check your MCP configuration for auto-approved tools
Review the MCP logs for tool usage patterns
Monitor server activity for unexpected behavior
Remove auto-approval for tools you no longer use frequently
Responding to security incidents
If you suspect a security issue with an MCP server:
Disable the server immediately in your configuration
Revoke any tokens or API keys associated with the server
Check for unauthorized activity in the connected services
Report the issue to the MCP server maintainer
Additional security measures
Network security
Use firewalls to restrict outbound connections from MCP servers
Consider using a VPN for sensitive MCP server connections
Monitor network traffic to and from MCP servers
System security
Keep your system updated with security patches
Run MCP servers with minimal privileges
Use separate user accounts for running sensitive MCP servers
Page updated: November 20, 2025ToolsGuides