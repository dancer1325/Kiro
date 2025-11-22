# Server directory - IDE - Docs - Kiro

Source: https://kiro.dev/docs/mcp/servers/

---

Extend Kiro's capabilities with MCP servers that connect to external services, databases, and tools. Browse the directory below and click Add to Kiro for one-click installation.
WarningMCP servers are third-party tools. Only install servers from trusted sources and review their documentation and licensing. Kiro is not responsible for third-party MCP servers.
MCP server directory
NameInstallDescriptionAWS Documentation+ Add to KiroAccess to AWS documentation, search capabilities, and content recommendations. Requires UV InstalledAzure+ Add to KiroInteract with Azure services and resources. Requires Node installedChrome DevTools+ Add to KiroControl and inspect a live Chrome browser with DevTools for automation, debugging, and performance analysis. Requires Node installedContext7+ Add to KiroUp-to-date code documentation for any library or framework. Requires Node installedDocker+ Add to KiroManage Docker containers and images. Requires Node installedDynatrace+ Add to KiroInteract with Dynatrace Observability Platform. Requires Node installedFilesystem+ Add to KiroSecure file operations within allowed directories. Requires Node installedGCP+ Add to KiroManage Google Cloud Platform resources. Requires Node installedGit+ Add to KiroRead, search, and manipulate Git repositories. Requires Node installedGitHub+ Add to KiroInteract with GitHub repositories, issues, and pull requests. Requires Docker InstalledKubernetes+ Add to KiroInteract with Kubernetes clusters. Requires Node installedLLM.txt+ Add to KiroAccess to LLM.txt documentation and resourcesMemory+ Add to KiroKnowledge graph-based persistent memory system for AI agents. Requires Node installedMongoDB+ Add to KiroInteract with MongoDB databases. Requires Node installedPlaywright+ Add to KiroBrowser automation with Playwright for web scraping, screenshots, and test code generation. Requires Node installedPostgreSQL+ Add to KiroQuery and manage PostgreSQL databases. Requires Node installedSequential Thinking+ Add to KiroDynamic and reflective problem-solving through iterative thinking. Requires Node installedStrands Agent+ Add to KiroAccess documentation about Strands Agents. Requires UV InstalledWeb Search+ Add to KiroSearch the web using Brave Search API. Requires Node installed
Share your MCP server
Create one-click installation links that let users add your MCP server to Kiro instantly.
Install link schema
URL Format:
https://kiro.dev/launch/mcp/add?name=<server-name>&config=<url-encoded-config>
Query Parameters:
ParameterTypeRequiredDescriptionnameStringYesDisplay name for the MCP serverconfigStringYesURL-encoded JSON configuration object (see MCP Configuration for schema)
Generate an install link
Use these helper functions to programmatically create installation links for your MCP server. These links work universally across GitHub, web browsers, and documentation.
JavaScript/TypeScript:
javascriptfunction createKiroInstallLink(name, config) {
const encodedName = encodeURIComponent(name);
const encodedConfig = encodeURIComponent(JSON.stringify(config));
return `https://kiro.dev/launch/mcp/add?name=${encodedName}&config=${encodedConfig}`;
}
// Example 1: Local server with command execution
const localServerLink = createKiroInstallLink('aws-docs', {
command: 'uvx',
args: ['awslabs.aws-documentation-mcp-server@latest'],
env: { FASTMCP_LOG_LEVEL: 'ERROR' },
disabled: false,
autoApprove: []
});
// Example 2: Remote server with URL endpoint
const remoteServerLink = createKiroInstallLink('aws-knowledge', {
url: 'https://knowledge-mcp.global.api.aws',
disabled: false,
autoApprove: []
});
// Example 3: Server with environment variables
const dbServerLink = createKiroInstallLink('postgresql', {
command: 'npx',
args: ['-y', '@modelcontextprotocol/server-postgres'],
env: { POSTGRES_CONNECTION_STRING: 'postgresql://localhost:5432/mydb' },
disabled: false,
autoApprove: []
});
Python:
pythonimport json
from urllib.parse import urlencode, quote
def create_kiro_install_link(name: str, config: dict) -> str:
"""
Creates a Kiro install link for one-click MCP server installation
Args:
name: Display name for the MCP server
config: MCP server configuration dictionary
Returns:
Formatted HTTPS install link URL
"""
encoded_name = quote(name)
encoded_config = quote(json.dumps(config))
return f"https://kiro.dev/launch/mcp/add?name={encoded_name}&config={encoded_config}"
# Example usage
link = create_kiro_install_link('my-server', {
'command': 'npx',
'args': ['-y', '@myorg/my-mcp-server'],
'disabled': False,
'autoApprove': []
})
Command Line (Bash):
bash#!/bin/bash
# Function to create Kiro install link
create_kiro_link() {
local name="$1"
local config="$2"
# URL encode the parameters
local encoded_name=$(printf %s "$name" | jq -sRr @uri)
local encoded_config=$(printf %s "$config" | jq -sRr @uri)
echo "https://kiro.dev/launch/mcp/add?name=${encoded_name}&config=${encoded_config}"
}
# Example usage
CONFIG='{"command":"npx","args":["-y","@modelcontextprotocol/server-git"],"disabled":false,"autoApprove":[]}'
create_kiro_link "git" "$CONFIG"
Add the Kiro badge
Include the Add to Kiro badge in your project's README or documentation to let users install your MCP server with a single click:
html<a href="https://kiro.dev/launch/mcp/add?name=my-server&config=%7B%22command%22%3A%22npx%22...%7D">
<img src="https://kiro.dev/images/add-to-kiro.svg" alt="Add to Kiro" />
</a>
Markdown:
markdown[![Add to Kiro](https://kiro.dev/images/add-to-kiro.svg)](https://kiro.dev/launch/mcp/add?name=my-server&config=%7B%22command%22%3A%22npx%22...%7D)
When clicked, users are prompted to open Kiro with the server configuration pre-filled. If the prompt doesn't work, the page displays the server name and a retry button.
Discover more MCP servers
The directory above features curated servers, but hundreds more are available in the MCP ecosystem.
Official resources
MCP Registry - Browse the official registry of community-contributed MCP servers with detailed documentation and installation instructions.
Model Context Protocol Organization - Explore reference implementations and official servers maintained by the MCP team.
Package registries
npm (Node.js) - Search for mcp-server or @modelcontextprotocol/server-* to find JavaScript/TypeScript implementations.
PyPI (Python) - Search for mcp-server or packages with MCP in the name to find Python implementations.
Page updated: November 20, 2025ConfigurationTools