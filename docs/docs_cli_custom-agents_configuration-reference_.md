# Agent configuration reference - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/custom-agents/configuration-reference/

---

Every agent configuration file can include the following sections:
name â The name of the agent (optional, derived from filename if not specified).
description â A description of the agent.
prompt â High-level context for the agent.
mcpServers â The MCP servers the agent has access to.
tools â The tools available to the agent.
toolAliases â Tool name remapping for handling naming collisions.
allowedTools â Tools that can be used without prompting.
toolsSettings â Configuration for specific tools.
resources â Resources available to the agent.
hooks â Commands run at specific trigger points.
useLegacyMcpJson â Whether to include legacy MCP configuration.
model â The model ID to use for this agent.
Name field
The name field specifies the name of the agent. This is used for identification and display purposes.
json{
"name": "aws-expert"
}
Description field
The description field provides a description of what the agent does. This is primarily for human readability and helps users distinguish between different agents.
json{
"description": "An agent specialized for AWS infrastructure tasks"
}
Prompt field
The prompt field is intended to provide high-level context to the agent, similar to a system prompt. It supports both inline text and file:// URIs to reference external files.
Inline prompt
json{
"prompt": "You are an expert AWS infrastructure specialist"
}
File URI prompt
You can reference external files using file:// URIs. This allows you to maintain long, complex prompts in separate files for better organization and version control, while keeping your agent configuration clean and readable.
json{
"prompt": "file://./my-agent-prompt.md"
}
File URI path resolution
Relative paths: Resolved relative to the agent configuration file's directory
"file://./prompt.md" â prompt.md in the same directory as the agent config
"file://../shared/prompt.md" â prompt.md in a parent directory
Absolute paths: Used as-is
"file:///home/user/prompts/agent.md" â Absolute path to the file
File URI examples
json{
"prompt": "file://./prompts/aws-expert.md"
}
json{
"prompt": "file:///Users/developer/shared-prompts/rust-specialist.md"
}
McpServers field
The mcpServers field specifies which Model Context Protocol (MCP) servers the agent has access to. Each server is defined with a command and optional arguments.
json{
"mcpServers": {
"fetch": {
"command": "fetch3.1",
"args": []
},
"git": {
"command": "git-mcp",
"args": [],
"env": {
"GIT_CONFIG_GLOBAL": "/dev/null"
},
"timeout": 120000
}
}
}
Each MCP server configuration can include:
command (required): The command to execute to start the MCP server
args (optional): Arguments to pass to the command
env (optional): Environment variables to set for the server
timeout (optional): Timeout for each MCP request in milliseconds (default: 120000)
Tools field
The tools field lists all tools that the agent can potentially use. Tools include built-in tools and tools from MCP servers.
Built-in tools are specified by their name (e.g., read, shell)
MCP server tools are prefixed with @ followed by the server name (e.g., @git)
To specify a specific tool from an MCP server, use @server_name/tool_name
Use * as a special wildcard to include all available tools (both built-in and from MCP servers)
Use @builtin to include all built-in tools
Use @server_name to include all tools from a specific MCP server
json{
"tools": [
"read",
"write",
"shell",
"@git",
"@rust-analyzer/check_code"
]
}
To include all available tools, you can simply use:
json{
"tools": ["*"]
}
ToolAliases field
The toolAliases field is an advanced feature that allows you to remap tool names. This is primarily used to resolve naming collisions between tools from different MCP servers, or to create more intuitive names for specific tools.
For example, if both @github-mcp and @gitlab-mcp servers provide a tool called get_issues, you would have a naming collision. You can use toolAliases to disambiguate them:
json{
"toolAliases": {
"@github-mcp/get_issues": "github_issues",
"@gitlab-mcp/get_issues": "gitlab_issues"
}
}
With this configuration, the tools will be available to the agent as github_issues and gitlab_issues instead of having a collision on get_issues.
You can also use aliases to create shorter or more intuitive names for frequently used tools:
json{
"toolAliases": {
"@aws-cloud-formation/deploy_stack_with_parameters": "deploy_cf",
"@kubernetes-tools/get_pod_logs_with_namespace": "pod_logs"
}
}
The key is the original tool name (including server prefix for MCP tools), and the value is the new name to use.
AllowedTools field
The allowedTools field specifies which tools can be used without prompting the user for permission. This is a security feature that helps prevent unauthorized tool usage.
json{
"allowedTools": [
"read",
"write",
"@git/git_status",
"@server/read_*",
"@fetch"
]
}
You can allow tools using several patterns:
Exact matches
Built-in tools: "read", "shell", "knowledge"
Specific MCP tools: "@server_name/tool_name" (e.g., "@git/git_status")
All tools from MCP server: "@server_name" (e.g., "@fetch")
Wildcard patterns
The allowedTools field supports glob-style wildcard patterns using * and ?:
MCP tool patterns
Tool prefix: "@server/read_*" â matches @server/read_file, @server/read_config
Tool suffix: "@server/*_get" â matches @server/issue_get, @server/data_get
Server pattern: "@*-mcp/read_*" â matches @git-mcp/read_file, @db-mcp/read_data
Any tool from pattern servers: "@git-*/*" â matches any tool from servers matching git-*
Optionally, you can also prefix native tools with the namespace @builtin.
Examples
json{
"allowedTools": [
// Exact matches
"read",
"knowledge",
"@server/specific_tool",
// Native tool wildcards
"r*",                    // Read
"w*",               // Write
@builtin,                // All native tools
// MCP tool wildcards
"@server/api_*",           // All API tools from server
"@server/read_*",          // All read tools from server
"@git-server/get_*_info",  // Tools like get_user_info, get_repo_info
"@*/status",               // Status tool from any server
// Server-level permissions
"@fetch",                  // All tools from fetch server
"@git-*"                   // All tools from any git-* server
]
}
Pattern matching rules
* matches any sequence of characters (including none)
? matches exactly one character
Exact matches take precedence over patterns
Server-level permissions (@server_name) allow all tools from that server
Case-sensitive matching
Unlike the tools field, the allowedTools field does not support the "*" wildcard for allowing all tools. To allow tools, you must use specific patterns or server-level permissions.
ToolsSettings field
The toolsSettings field provides configuration for specific tools. Each tool can have its own unique configuration options.
Note that specifications that configure allowable patterns will be overridden if the tool is also included in allowedTools.
json{
"toolsSettings": {
"write": {
"allowedPaths": ["~/**"]
},
"@git/git_status": {
"git_user": "$GIT_USER"
}
}
}
Resources field
The resources field gives an agent access to local resources. Currently, only file resources are supported, and all resource paths must start with file://.
json{
"resources": [
"file://AmazonQ.md",
"file://README.md",
"file://.amazonq/rules/**/*.md"
]
}
Resources can include:
Specific files
Glob patterns for multiple files
Absolute or relative paths
Hooks field
The hooks field defines commands to run at specific trigger points during agent lifecycle and tool execution.
For detailed information about hook behavior, input/output formats, and examples, see the Hooks documentation.
json{
"hooks": {
"agentSpawn": [
{
"command": "git status"
}
],
"userPromptSubmit": [
{
"command": "ls -la"
}
],
"preToolUse": [
{
"matcher": "shell",
"command": "{ echo \"$(date) - Bash command:\"; cat; echo; } >> /tmp/bash_audit_log"
},
{
"matcher": "aws",
"command": "{ echo \"$(date) - AWS CLI call:\"; cat; echo; } >> /tmp/aws_audit_log"
}
],
"postToolUse": [
{
"matcher": "write",
"command": "cargo fmt --all"
}
]
}
}
Each hook is defined with:
command (required): The command to execute
matcher (optional): Pattern to match tool names for preToolUse and postToolUse hooks. See built-in tools documentation for available tool names.
Available hook triggers:
agentSpawn: Triggered when the agent is initialized.
userPromptSubmit: Triggered when the user submits a message.
preToolUse: Triggered before a tool is executed. Can block the tool use.
postToolUse: Triggered after a tool is executed.
stop: Triggered when the assistant finishes responding.
UseLegacyMcpJson field
The useLegacyMcpJson field determines whether to include MCP servers defined in the legacy MCP configuration files (~/.kiro/settings/mcp.json for global and <cwd>/.kiro/settings/mcp.json for workspace).
json{
"useLegacyMcpJson": true
}
When set to true, the agent will have access to all MCP servers defined in the global and local configurations in addition to those defined in the agent's mcpServers field.
Model field
The model field specifies the model ID to use for this agent. If not specified, the agent will use the default model.
json{
"model": "claude-sonnet-4"
}
The model ID must match one of the available models returned by the Kiro CLI's model service. You can see available models by using the /model command in an active chat session.
If the specified model is not available, the agent will fall back to the default model and display a warning.
Complete example
Here's a complete example of an agent configuration file:
json{
"name": "aws-rust-agent",
"description": "A specialized agent for AWS and Rust development tasks",
"mcpServers": {
"fetch": {
"command": "fetch3.1",
"args": []
},
"git": {
"command": "git-mcp",
"args": []
}
},
"tools": [
"read",
"write",
"shell",
"aws",
"@git",
"@fetch/fetch_url"
],
"toolAliases": {
"@git/git_status": "status",
"@fetch/fetch_url": "get"
},
"allowedTools": [
"read",
"@git/git_status"
],
"toolsSettings": {
"write": {
"allowedPaths": ["src/**", "tests/**", "Cargo.toml"]
},
"aws": {
"allowedServices": ["s3", "lambda"]
}
},
"resources": [
"file://README.md",
"file://docs/**/*.md"
],
"hooks": {
"agentSpawn": [
{
"command": "git status"
}
],
"userPromptSubmit": [
{
"command": "ls -la"
}
]
},
"useLegacyMcpJson": true,
"model": "claude-sonnet-4"
}
Agent configuration files are JSON files that define how your custom agents behave. The filename (without .json) becomes the agent's name.
Quick start
We recommend using the /agent generate command within your active Kiro session to intelligently generate agent configurations with AI assistance.
File locations
You can define local agents and global agents.
Local agents (project-specific)
.kiro/agents/
Local agents are specific to the current workspace and only available when running Kiro CLI from that directory or its subdirectories.
Example:
my-project/
âââ .kiro/
â   âââ agents/
â       âââ dev-agent.json
â       âââ aws-specialist.json
âââ src/
âââ main.py
Global agents (user-wide)
~/.kiro/agents/
Global agents are available from any directory.
Example:
~/.kiro/agents/
âââ general-assistant.json
âââ code-reviewer.json
âââ documentation-writer.json
Agent precedence
When Kiro CLI looks for an agent:
Local first: Checks .kiro/agents/ in the current directory
Global fallback: Checks ~/.kiro/agents/ in the HOME directory
If both locations have agents with the same name, the local agent takes precedence with a warning message.
Configuration fields
name
The agent's name for identification and display.
json{
"name": "aws-expert"
}
description
Human-readable description of the agent's purpose.
json{
"description": "An agent specialized for AWS infrastructure tasks"
}
prompt
High-level context for the agent, similar to a system prompt. Supports inline text or file:// URIs.
Inline:
json{
"prompt": "You are an expert AWS infrastructure specialist"
}
File URI:
json{
"prompt": "file://./my-agent-prompt.md"
}
Path Resolution:
Relative paths: Resolved relative to agent config file
"file://./prompt.md" â Same directory as agent config
"file://../shared/prompt.md" â Parent directory
Absolute paths: Used as-is
"file:///home/user/prompts/agent.md"
mcpServers
MCP servers the agent can access.
json{
"mcpServers": {
"fetch": {
"command": "fetch-server",
"args": []
},
"git": {
"command": "git-mcp",
"args": [],
"env": {
"GIT_CONFIG_GLOBAL": "/dev/null"
},
"timeout": 120000
}
}
}
Fields:
command (required): Command to start the MCP server
args (optional): Arguments for the command
env (optional): Environment variables
timeout (optional): Request timeout in milliseconds (default: 120000)
tools
Tools available to the agent.
json{
"tools": [
"read",
"write",
"shell",
"@git",
"@rust-analyzer/check_code"
]
}
Tool References:
Built-in tools: "read", "shell"
All MCP server tools: "@server_name"
Specific MCP tool: "@server_name/tool_name"
All tools: "*"
All built-in tools: "@builtin"
toolAliases
Remap tool names to resolve naming collisions or create intuitive names.
json{
"toolAliases": {
"@github-mcp/get_issues": "github_issues",
"@gitlab-mcp/get_issues": "gitlab_issues",
"@aws-cloud-formation/deploy_stack_with_parameters": "deploy_cf"
}
}
allowedTools
Tools that can be used without prompting for permission.
json{
"allowedTools": [
"read",
"@git/git_status",
"@server/read_*",
"@fetch"
]
}
Pattern Support:
Exact Matches:
Built-in: "read", "shell"
MCP tool: "@server_name/tool_name"
All server tools: "@server_name"
Wildcards:
Prefix: "code_*" â code_review, code_analysis
Suffix: "*_bash" â execute_bash, run_bash
Single char: "?ead" â read, head
MCP patterns: "@server/read_*", "@git-*/status"
toolsSettings
Configuration for specific tools.
json{
"toolsSettings": {
"write": {
"allowedPaths": ["~/**"]
},
"shell": {
"allowedCommands": ["git status", "git fetch"],
"deniedCommands": ["git commit .*", "git push .*"],
"autoAllowReadonly": true
},
"@git/git_status": {
"git_user": "$GIT_USER"
}
}
}
See Built-in Tools for tool-specific options.
resources
Local resources available to the agent. All paths must start with file://.
json{
"resources": [
"file://README.md",
"file://.kiro/steering/**/*.md",
"file://docs/**/*.md"
]
}
Supports:
Specific files
Glob patterns
Absolute or relative paths
hooks
Commands to run at specific trigger points.
json{
"hooks": {
"agentSpawn": [
{
"command": "git status"
}
],
"userPromptSubmit": [
{
"command": "ls -la"
}
],
"preToolUse": [
{
"matcher": "shell",
"command": "{ echo \"$(date) - Bash:\"; cat; } >> /tmp/audit.log"
}
],
"postToolUse": [
{
"matcher": "write",
"command": "cargo fmt --all"
}
],
"stop": [
{
"command": "npm test"
}
]
}
}
Hook Types:
agentSpawn: When agent is activated
userPromptSubmit: When user submits a prompt
preToolUse: Before tool execution (can block)
postToolUse: After tool execution
stop: When assistant finishes responding
See Hooks for detailed documentation.
model
Model ID to use for this agent.
json{
"model": "claude-sonnet-4"
}
If not specified or unavailable, falls back to default model.
Complete example
json{
"name": "aws-rust-agent",
"description": "Specialized agent for AWS and Rust development",
"prompt": "file://./prompts/aws-rust-expert.md",
"mcpServers": {
"fetch": {
"command": "fetch-server",
"args": []
},
"git": {
"command": "git-mcp",
"args": []
}
},
"tools": [
"read",
"write",
"shell",
"aws",
"@git",
"@fetch/fetch_url"
],
"toolAliases": {
"@git/git_status": "status",
"@fetch/fetch_url": "get"
},
"allowedTools": [
"read",
"@git/git_status"
],
"toolsSettings": {
"write": {
"allowedPaths": ["src/**", "tests/**", "Cargo.toml"]
},
"aws": {
"allowedServices": ["s3", "lambda"],
"autoAllowReadonly": true
}
},
"resources": [
"file://README.md",
"file://docs/**/*.md"
],
"hooks": {
"agentSpawn": [
{
"command": "git status"
}
],
"postToolUse": [
{
"matcher": "write",
"command": "cargo fmt --all"
}
]
},
"model": "claude-sonnet-4"
}
Best practices
Start restrictive: Begin with minimal tool access and expand as needed
Name clearly: Use descriptive names that indicate the agent's purpose
Document usage: Add clear descriptions to help team members understand the agent
Version control: Store agent configurations in your project repository
Test thoroughly: Verify tool permissions work as expected before sharing
Local vs global agents
Use Local Agents For:
Project-specific configurations
Agents needing project files/tools
Development environments with unique requirements
Sharing with team via version control
Use Global Agents For:
General-purpose agents across projects
Personal productivity agents
Agents without project-specific context
Commonly used tools and workflows
Security
Review allowedTools carefully
Use specific patterns over wildcards
Configure toolsSettings for sensitive operations
Test agents in safe environments first
Organization
Use descriptive agent names
Document agent purposes in descriptions
Keep prompt files organized
Version control local agents with projects
Next steps
Creating Custom Agents
Built-in Tools Reference
Hooks Documentation
Agent Examples
Page updated: November 18, 2025Creating custom agentsExamples