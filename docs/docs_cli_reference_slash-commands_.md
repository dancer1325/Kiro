# Slash commands - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/reference/slash-commands/

---

Overview
Slash commands are special commands you can use within an interactive chat session to quickly perform actions without leaving the conversation. They start with a forward slash (/) and provide shortcuts for common tasks.
Using slash commands
Slash commands are only available in interactive chat mode:
bashkiro chat
> /help
Available commands
/help
Display available slash commands and their usage.
bash> /help
/quit
Exit the interactive chat session.
bash> /quit
Aliases: /exit, /q
/clear
Clear the current conversation history.
bash> /clear
Note: This only clears the display, not the saved conversation.
/context
Manage context files and view context window usage. Context rules determine which files are included in your Kiro session and are derived from the current active agent.
bash# Display context rule configuration and matched files
> /context show
# Add context rules (filenames or glob patterns)
> /context add src/app.js
> /context add "*.py"
> /context add "src/**/*.js"
# Remove specified rules
> /context remove src/app.js
# Remove all rules
> /context clear
Available subcommands:
show - Display the context rule configuration and matched files
add - Add context rules (filenames or glob patterns)
remove - Remove specified rules
Notes:
You can add specific files or use glob patterns (e.g., *.py, src/**/*.js)
Agent rules apply only to the current agent
Context changes are NOT preserved between chat sessions. To make changes permanent, edit the agent config file.
The files matched by these rules provide Kiro with additional information about your project or environment
See Context Management for detailed documentation.
/model
Switch to a different AI model.
bash# Show current model
> /model
# Switch model
> /model claude-3-5-sonnet
> /model gpt-4
Example:
bash> /model claude-3-5-sonnet
Switched to model: claude-3-5-sonnet
/agent
Manage agents and switch between different agent configurations.
bash# List all available agents
> /agent list
# Create a new agent
> /agent create my-agent
# Edit an existing agent configuration
> /agent edit my-agent
# Generate an agent configuration using AI
> /agent generate
# Show agent config schema
> /agent schema
# Set default agent for new chat sessions
> /agent set-default my-agent
# Swap to a different agent at runtime
> /agent swap code-reviewer
Available subcommands:
list - List all available agents
create - Create a new agent with the specified name
edit - Edit an existing agent configuration
generate - Generate an agent configuration using AI
schema - Show agent config schema
set-default - Define a default agent to use when kiro-cli chat launches
swap - Swap to a new agent at runtime
Notes:
Agents can be stored globally in ~/.kiro/agents/ or per-workspace in .kiro/agents/
Launch kiro-cli chat with a specific agent using kiro-cli chat --agent agent_name
Set default agent with kiro-cli settings chat.defaultAgent agent_name
See Custom Agents for detailed documentation.
/save
Save the current conversation to a file.
bash# Save <PATH>
> /save /myproject/codereview.json
/load
Load a previously saved conversation.
bash# List available conversations
> /load /myproject/codereview.json
/editor
Open your default editor (defaults to vi) to compose a prompt.
bash> /editor
Opens $EDITOR to compose a longer message.
/reply
Open your editor with the most recent assistant message quoted for reply.
bash> /reply
Useful for referencing and responding to specific parts of the AI's response.
/compact
Summarize the conversation to free up context space.
bash> /compact
Condenses the conversation history while preserving key information, useful when approaching context limits.
/paste
Paste an image from clipboard.
bash> /paste
Adds an image from your system clipboard to the conversation.
/tools
View tools and permissions. By default, Kiro will ask for your permission to use certain tools. You can control which tools you trust so that no confirmation is required.
bash# View all tools and their permissions
> /tools
# Show the input schema for all available tools
> /tools schema
# Trust a specific tool for the session
> /tools trust write
# Revert a tool to per-request confirmation
> /tools untrust write
# Trust all tools (equivalent to deprecated /acceptall)
> /tools trust-all
# Reset all tools to default permission levels
> /tools reset
Available subcommands:
schema - Show the input schema for all available tools
trust - Trust a specific tool or tools for the session
untrust - Revert a tool or tools to per-request confirmation
trust-all - Trust all tools (equivalent to deprecated /acceptall)
reset - Reset all tools to default permission levels
Note: For permanent tool configuration, see Agent Configuration Reference.
/prompts
View and retrieve prompts. Prompts are reusable templates that help you quickly access common workflows and tasks. These templates are provided by the MCP servers you have installed and configured.
bash# List available prompts from a tool or show all available prompts
> /prompts list
# Show detailed information about a specific prompt
> /prompts details code-review
# Get a specific prompt by name
> /prompts get code-review [arg]
# Quick retrieval (without /prompts prefix)
> @code-review [arg]
# Create a new local prompt
> /prompts create my-prompt
# Edit an existing local prompt
> /prompts edit my-prompt
# Remove an existing local prompt
> /prompts remove my-prompt
Available subcommands:
list - List available prompts from a tool or show all available prompts
details - Show detailed information about a specific prompt
get - Get a specific prompt by name
create - Create a new local prompt
edit - Edit an existing local prompt
remove - Remove an existing local prompt
Quick tip: To retrieve a prompt directly, use @<prompt name> [arg] without the /prompts get prefix.
See Manage Prompts for detailed documentation.
/hooks
View context hooks.
bash> /hooks
Display active context hooks for the current session.
/usage
Show billing and credits information.
bash> /usage
View your current usage statistics and remaining credits.
/mcp
See MCP servers loaded.
bash> /mcp
Display Model Context Protocol servers currently active.
/experiment
Toggle experimental features.
bash> /experiment
Enable or disable experimental CLI features.
/todo
View, manage, and resume to-do lists.
bash# View todo
> /todo
# Add todo
> /todo add "Fix authentication bug"
# Complete todo
> /todo complete 1
/issue
Create a new GitHub issue or make a feature request.
bash> /issue
Opens a workflow to submit issues or feature requests to the Kiro team.
/logdump
Create a zip file with logs for support investigation.
bash> /logdump
Generates a diagnostic log bundle for troubleshooting with support.
/changelog
View changelog for Kiro CLI.
bash> /changelog
Display recent updates and changes to the CLI.
Keyboard shortcuts
In interactive mode, you can also use:
Ctrl+C - Cancel current input
Ctrl+J - To insert new-line for multi-line prompt
Ctrl+S - Fuzzy search commands and context files, use tab to select multiple items
Ctrl+T - Toggle tangent mode for isolated conversations (if Tangent mode is enabled)
Up/Down arrows - Navigate command history
Command aliases
Quick reference for command aliases:
CommandAliases/help-/clear/c/context/ctx/model/m/agent/a/save/s/load/l/new/n/history/h/export/e/image/img/file/f/search/find/undo/u/redo/r/exit/quit, /q
Next steps
Learn about CLI Commands for terminal usage
Explore Interactive Chat Mode
Check Context Management for advanced context handling
Page updated: November 18, 2025CLI commandsBuilt-in tools