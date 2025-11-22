# CLI commands - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/reference/cli-commands/

---

This page provides a comprehensive reference for all Kiro CLI commands and their arguments.
Global arguments
These arguments work with any Kiro CLI command:
ArgumentShortDescription--verbose-vIncrease logging verbosity (can be repeated: -v, -vv, -vvv)--agent-vStart a conversation using a specific custom agent configuration--help-hShow help information--version-VShow version information--help-allPrint help for all subcommands
Commands
kiro-cli agent
Start an interactive chat session with a specific agent configuration.
Syntax:
bashkiro-cli agent [OPTIONS] [COMMAND]
Subcommands:
SubcommandDescriptionlistList the available agents.createCreate an agent config.editEdit an existing agent configvalidateValidate a config with the given pathmigrateMigrate profiles to agent Note that doing this is potentially destructive to agents that are already in the global agent directoriesset-defaultDefine a default agent to use when starting a session
Examples:
bashkiro-cli inline enable
kiro-cli inline disable
kiro-cli inline status
kiro-cli inline set-customization
kiro-cli inline show-customizations --format json
Arguments:
ArgumentDescription--no-interactivePrint first response to STDOUT without interactive mode--resume / -rResume the previous conversation from this directory--agentSpecify which agent to use--trust-all-toolsAllow the model to use any tool without confirmation--trust-toolsTrust only specified tools (comma-separated list)INPUTThe first question to ask (positional argument)
Examples:
bash# Start interactive chat
kiro-cli
# Ask a question directly
kiro-cli chat "How do I list files in Linux?"
# Non-interactive mode with trusted tools
kiro-cli chat --no-interactive --trust-all-tools "Show me the current directory"
# Resume previous conversation
kiro-cli chat --resume
# Use specific agent
kiro-cli chat --agent my-agent "Help me with AWS CLI"
kiro-cli chat
Start an interactive chat session with Kiro. When no subcommand is specified, kiro defaults to kiro-cli chat.
Syntax:
bashkiro-cli chat [OPTIONS] [INPUT]
Arguments:
ArgumentDescription--no-interactivePrint first response to STDOUT without interactive mode--resume / -rResume the previous conversation from this directory--agentSpecify which agent to use--trust-all-toolsAllow the model to use any tool without confirmation--trust-toolsTrust only specified tools (comma-separated list)INPUTThe first question to ask (positional argument)
Examples:
bash# Start interactive chat
kiro-cli
# Ask a question directly
kiro-cli chat "How do I list files in Linux?"
# Non-interactive mode with trusted tools
kiro-cli chat --no-interactive --trust-all-tools "Show me the current directory"
# Resume previous conversation
kiro-cli chat --resume
# Use specific agent
kiro-cli chat --agent my-agent "Help me with AWS CLI"
kiro-cli translate
Translate natural language instructions to executable shell commands using AI.
Syntax:
bashkiro-cli translate [OPTIONS] [INPUT...]
Arguments:
ArgumentShortDescription--n-nNumber of completions to generate (max 5)INPUTNatural language description (positional arguments)
Examples:
bashkiro-cli translate "list all files in the current directory"
kiro-cli translate "find all Python files modified in the last week"
kiro-cli translate "compress all log files older than 30 days"
kiro-cli translate -n 3 "search for text in files"
kiro-cli doctor
Diagnose and fix common installation and configuration issues.
Syntax:
bashkiro-cli doctor [OPTIONS]
Arguments:
ArgumentShortDescription--all-aRun all diagnostic tests without fixes--strict-sError on warnings--format-fOutput format: plain, json, json-pretty
Examples:
bashkiro-cli doctor
kiro-cli doctor --all
kiro-cli doctor --strict
kiro-cli update
Update Kiro CLI to the latest version.
Syntax:
bashkiro-cli update [OPTIONS]
Arguments:
ArgumentShortDescription--non-interactive-yDon't prompt for confirmation--relaunch-dashboardRelaunch dashboard after update (default: true)
Examples:
bashkiro-cli update
kiro-cli update --non-interactive
kiro-cli theme
Get or set the visual theme for the autocomplete dropdown menu.
Syntax:
bashkiro-cli theme [OPTIONS] [THEME]
Arguments:
ArgumentDescription--listList all available themes--folderShow the theme directory pathTHEMETheme name: dark, light, system
Examples:
bashkiro-cli theme --list
kiro-cli theme dark
kiro-cli theme light
kiro-cli theme system
kiro-cli integrations
Manage system integrations for Kiro.
Syntax:
bashkiro-cli integrations [SUBCOMMAND] [OPTIONS]
Subcommands:
SubcommandDescriptioninstallInstall an integrationuninstallUninstall an integrationreinstallReinstall an integrationstatusCheck integration status
Options:
--silent / -s: Suppress status messages
--format / -f: Output format (for status command)
Examples:
bashkiro-cli integrations install
kiro-cli integrations status
kiro-cli integrations uninstall --silent
kiro-cli inline
Manage inline suggestions (ghost text) that appear as you type.
Syntax:
bashkiro-cli inline [SUBCOMMAND] [OPTIONS]
Subcommands:
SubcommandDescriptionenableEnable inline suggestionsdisableDisable inline suggestionsstatusShow current statusset-customizationSelect a customization modelshow-customizationsShow available customizations
Examples:
bashkiro-cli inline enable
kiro-cli inline disable
kiro-cli inline status
kiro-cli inline set-customization
kiro-cli inline show-customizations --format json
kiro-cli login
Authenticate with Kiro.
Syntax:
bashkiro-cli login [OPTIONS]
Arguments:
ArgumentDescription--use-device-flowUse OAuth device flow for authentication
Examples:
bashkiro-cli login
kiro-cli login --use-device-flow
kiro-cli logout
Sign out of your kiro-cli session.
Syntax:
bashkiro-cli logout
kiro-cli whoami
Display information about the current user and authentication status.
Syntax:
bashkiro-cli whoami [OPTIONS]
Arguments:
ArgumentShortDescription--format-fOutput format: plain, json, json-pretty
Examples:
bashkiro-cli whoami
kiro-cli whoami --format json
kiro-cli settings
Manage kiro-cli configuration settings.
Syntax:
bashkiro-cli settings [SUBCOMMAND] [OPTIONS] [KEY] [VALUE]
Arguments:
ArgumentShortDescription--delete-dDelete a setting--format-fOutput format: plain, json, json-prettyKEYSetting key (positional)VALUESetting value (positional)
Subcommands:
SubcommandDescriptionopenOpen settings file in default editorlistList configured settingslist --allList all available settings with descriptions
Examples:
bash# View all settings
kiro-cli settings list
# View all available settings
kiro-cli settings list --all
# Get a specific setting
kiro-cli settings telemetry.enabled
# Set a setting
kiro-cli settings telemetry.enabled true
# Delete a setting
kiro-cli settings --delete chat.defaultModel
# Open settings file
kiro-cli settings open
# JSON output
kiro-cli settings list --format json-pretty
kiro-cli diagnostic
Run diagnostic tests to troubleshoot issues.
Syntax:
bashkiro-cli diagnostic [OPTIONS]
Arguments:
ArgumentShortDescription--format-fOutput format: plain, json, json-pretty--forceForce limited diagnostic output
kiro-cli issue
Create a GitHub issue for feedback or bug reports.
Syntax:
bashkiro-cli issue [OPTIONS] [DESCRIPTION...]
Arguments:
ArgumentShortDescription--force-fForce issue creationDESCRIPTIONIssue description (positional)
Examples:
bashkiro-cli issue
kiro-cli issue "Autocomplete not working in zsh"
kiro-cli version
Display version information and changelog.
Syntax:
bashkiro-cli version [OPTIONS]
Arguments:
ArgumentDescription--changelogShow changelog for current version--changelog=allShow changelog for all versions--changelog=x.x.xShow changelog for specific version
Examples:
bashkiro-cli version
kiro-cli version --changelog
kiro-cli version --changelog=all
kiro-cli version --changelog=1.5.0
kiro-cli mcp
Manage Model Context Protocol (MCP) servers.
Syntax:
bashkiro-cli mcp [SUBCOMMAND] [OPTIONS]
Subcommands:
kiro-cli mcp add
Add or replace a configured MCP server.
Arguments:
ArgumentDescription--nameServer name (required)--commandLaunch command (required)--scopeScope: workspace or global--envEnvironment variables: key1=value1,key2=value2--timeoutLaunch timeout in milliseconds--forceOverwrite existing server
Example:
bashkiro-cli mcp add --name my-server --command "node server.js" --scope workspace
kiro-cli mcp remove
Remove an MCP server.
Arguments:
ArgumentDescription--nameServer name (required)--scopeScope: workspace or global
Example:
bashkiro-cli mcp remove --name my-server --scope workspace
kiro-cli mcp list
List configured MCP servers.
Syntax:
bashkiro-cli mcp list [SCOPE]
Example:
bashkiro-cli mcp list
kiro-cli mcp list workspace
kiro-cli mcp list global
kiro-cli mcp import
Import server configuration from a file.
Arguments:
ArgumentDescription--fileConfiguration file (required)--forceOverwrite existing serversSCOPEScope: workspace or global
Example:
bashkiro-cli mcp import --file config.json workspace
kiro-cli mcp status
Get the status of an MCP server.
Arguments:
ArgumentDescription--nameServer name (required)
Example:
bashkiro-cli mcp status --name my-server
Log files
Kiro CLI maintains log files for troubleshooting:
Locations:
macOS: $TMPDIR/kiro-log/
Linux: $XDG_RUNTIME_DIR or /tmp/kiro-log/
Log Levels:
Set via KIRO_LOG_LEVEL environment variable:
error: Only errors (default)
warn: Warnings and errors
info: Info, warnings, and errors
debug: Debug info and above
trace: All messages including detailed traces
Example:
bash# Enable debug logging
export KIRO_LOG_LEVEL=debug
kiro-cli chat
# For fish shell
set -x KIRO_LOG_LEVEL debug
kiro-cli chat
Warning: Log files may contain sensitive information including file paths, code snippets, and command outputs. Be cautious when sharing logs.
Next steps
Slash Commands Reference
Settings Configuration
Troubleshooting Guide
Page updated: November 18, 2025VPC endpoints (AWS PrivateLink)Slash commands