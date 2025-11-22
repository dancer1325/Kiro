# Built-in tools - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/reference/built-in-tools/

---

Kiro CLI includes a collection of built-in tools that enhance your terminal experience with AI-powered assistance for common development tasks.
File read
Tool name: read
Description: Reads files, folders and images
bash> what dependencies does my application have
Reading file: src/snake/package.json, all lines (using tool: read)
â Successfully read 1417 bytes from src/snake/package.json
- Completed in 0.86s
> Your application has:
Runtime Dependencies:
- typescript (^3.5.1) - TypeScript compiler
- gh-pages (^2.0.1) - GitHub Pages deployment
Dev Dependencies:
- sass (^1.20.3) - CSS preprocessing
- eslint (^5.16.0) + TypeScript plugins - Code linting
- jest (^29.5.0) + ts-jest - Testing framework
No external game libraries or frameworks.
You can also configure the read tool in the agent configuration to have specific access to the files and folders in your project, giving you granular control over what the Kiro can read.
json{
"toolsSettings": {
"read": {
"allowedPaths": ["~/projects", "./src/**"],
"deniedPaths": ["d1/denied/path/", "d2/denied/path/**/file.txt"]
}
}
}
Configuration options
OptionTypeRequiredDescriptionallowedPathsarray of pathsNoPaths that can read without prompting.deniedPathsarray of pathsNoPaths that are denied.
Path values can be glob patterns similar to the behavior as gitignore. For example, ~/temp would match ~/temp/child and ~/temp/child/grandchild
File write
Tool name: write
Description: Tool for creating and editing files
bash> collect best practices for writing typescript code and save it to the kiro steering folder as codingpractices.md
I'll create the following file: src/snake/.kiro/steering/codingpractices.md (using tool: write)
Purpose: Create TypeScript coding best practices document
+     1: # TypeScript Coding Best Practices
+     2:
+     3: ## Type Safety
+     4: - Enable strict mode in `tsconfig.json` (`strict: true`)
+     5: - Avoid `any` type - use `unknown` for truly dynamic types
+     6: - Use explicit return types for functions
+     7: - Leverage type inference where it improves readability
+     8: - Use union types instead of enums when possible
+     9: - Prefer `interface` for object shapes, `type` for unions/intersections
+    10:
+    11: ## Code Organization
+    12: - One class/interface per file (exceptions for small related types)
+    13: - Group related functionality into modules
+    14: - Use barrel exports (`index.ts`) for clean imports
+    15: - Keep functions small and focused (single responsibility)
+    16: - Separate business logic from presentation logic
Configuration
json{
"toolsSettings": {
"write": {
"allowedPaths": ["~/projects/output.txt", "./src/**"],
"deniedPaths": ["/d1/denied/path/", "/d2/denied/path/**/file.txt"]
}
}
}
Configuration options
OptionTypeRequiredDescriptionallowedPathsarray of pathsNoPaths that can be written to without prompting.deniedPathsarray of pathsNoPaths that are denied.
Path values can be glob patterns similar to the behavior as gitignore. For example, ~/temp would match ~/temp/child and ~/temp/child/grandchild
Execute AWS commands
Tool name: aws
Description: Tool for making AWS CLI calls with the specified service, operation, and parameters
bash list my s3 buckets
Running aws cli command (using tool: aws):
Service name: s3api
Operation name: list-buckets
Parameters:
Region: us-east-1
Label: List all S3 buckets
Configuration
json{
"toolsSettings": {
"aws": {
"allowedServices": ["s3", "lambda", "ec2"],
"deniedServices": ["eks", "rds"],
"autoAllowReadonly": true
}
}
}
Configuration options
OptionTypeDefaultDescriptionallowedServicesarray of strings[]List of AWS services that can be accessed without promptingdeniedServicesarray of strings[]List of AWS services to deny. Deny rules are evaluated before allow rulesautoAllowReadonlybooleanfalseWhether to automatically allow read-only operations (get, describe, list, ls, search, batch_get) without prompting
Introspect Kiro CLI capabilities
Tool name: introspect
Description: Provide information about Kiro CLI capabilities, features, commands, and documentation. This tool accesses Kiro CLI's built-in documentation and help content to answer questions about the CLI's functionality.
bash> what can you do
Introspecting to get you the right information (using tool: introspect) - Completed in 0.68s
> I can help you with a wide range of tasks:
File Operations
- Read, write, and edit files
- List directories and search for patterns
- Process images
Command Execution
- Run bash commands on your system
- Execute scripts and build tools
- Manage processes
Usage
The introspect tool is automatically used when you ask questions about Kiro CLI itself, such as:
"What can you do?"
"How do I save conversations?"
"What commands are available?"
"Do you have feature X?"
Behavior
Tries to provide the information that is explicitly documented
Accesses README, built-in tools documentation, experiments, and settings information
Automatically enters tangent mode when configured to do so and if we set the setting introspect.tangentMode = true.
Submit an issue or feature request
Tool name: report
Description: Opens the browser to a pre-filled GitHub issue template to report chat issues, bugs, or feature requests.
This tool has no configuration options.
Knowledge tool (experimental)
Tool name: knowledge
Description: Store and retrieve information in a knowledge base across chat sessions. Provides semantic search capabilities for files, directories, and text content.
This tool has no configuration options.
Thinking tool (experimental)
Tool name: thinking
Description: An internal reasoning mechanism that improves the quality of complex tasks by breaking them down into atomic actions.
This tool has no configuration options.
ToDo list tool (experimental)
Tool name: todo
Description:
Create and manage ToDo lists for tracking multi-step tasks.
This tool has no configuration options.
Using tool settings in agent configuration
Tool settings are specified in the toolsSettings section of the agent configuration file. Each tool's settings are specified using the tool's name as the key.
For MCP server tools, use the format @server_name/tool_name as the key:
json{
"toolsSettings": {
"write": {
"allowedPaths": ["~/projects"]
},
"@git/git_status": {
"git_user": "$GIT_USER"
}
}
}
Tool permissions
Tools can be explicitly allowed in the allowedTools section of the agent configuration:
json{
"allowedTools": [
"read",
"knowledge",
"@git/git_status"
]
}
If a tool is not in the allowedTools list, the user will be prompted for permission when the tool is used unless an allowed toolSettings configuration is set.
Some tools have default permission behaviors:
read and report are trusted by default
shell, write, and aws prompt for permission by default, but can be configured to allow specific commands/paths/services
Next steps
Agent Integration - Use tools with custom agents
MCP Integration - Connect external tools via MCP
Settings - Configure tool preferences
Troubleshooting - Common tool issues
Page updated: November 18, 2025Slash commandsSettings