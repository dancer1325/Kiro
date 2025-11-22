# Security - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/mcp/security/

---

Security is critical when integrating external MCP servers with your development workflow. The MCP security model in Kiro CLI is designed with these principles:
Explicit Permission: Tools require explicit user permission before execution
Local Execution: MCP servers run locally on your machine
Isolation: Each MCP server runs as a separate process
Transparency: Users can see what tools are available and what they do
Security considerations
When using MCP servers with Kiro CLI, keep these security principles in mind:
Trust and verification
Only install MCP servers from trusted sources
Review tool descriptions and documentation before installation
Check for security advisories and updates
Access control
Use least-privilege principles for server permissions
Limit file system access to necessary directories only
Restrict network access where possible
Use environment variables for sensitive credentials
Credential management
Never hardcode API keys or tokens in configuration files
Use environment variables for sensitive data
Rotate credentials regularly
Store credentials securely using system keychains
Network security
Use HTTPS for remote MCP servers
Verify SSL/TLS certificates
Be cautious with servers that require broad network access
Monitor network traffic for unusual activity
Monitoring and auditing
Review MCP server logs regularly
Monitor for unexpected behavior
Keep track of installed servers and their permissions
Remove unused or untrusted servers promptly
Best practices
Configuration security
bash# Use environment variables for sensitive data
export MCP_API_KEY="your-secure-key"
export DATABASE_URL="your-connection-string"
# Configure MCP server with environment variables
kiro-cli mcp add my-server --env MCP_API_KEY --env DATABASE_URL
Next steps
Explore Examples
Return to MCP Overview
Page updated: November 16, 2025ExamplesSteering