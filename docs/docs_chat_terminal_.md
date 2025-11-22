# Terminal integration - IDE - Docs - Kiro

Source: https://kiro.dev/docs/chat/terminal/

---

Overview
Transform your development workflow with Kiro's terminal integration. Instead of memorizing command syntax or switching between windows, describe what you want to accomplish and Kiro translates your requests into executable commands, maintains context across operations, and provides a secure approval system that keeps you in control while managing dependencies, navigating git workflows, or exploring your codebase.
Getting started
Simply describe what you want to do in natural language. For example:
"Install the project dependencies"
"Check the git status"
"Find all TypeScript files in the src folder"
"Run the development server"
Kiro translates your request into the appropriate terminal command and asks for your approval before executing. You'll review the suggested command and choose to Modify, Reject, Run, or Run and Trust, then see the output directly in chat.
Loading image...
TipLong-running commands like Dev Servers are automatically managed by Kiro, running in dedicated terminals without blocking your workflow.
How it works
When Kiro suggests a command, you have four options:
Modify - Edit the command before running
Reject - Cancel execution
Run - Execute once
Run and Trust - Execute and trust similar commands in the future
Loading image...
Trust commands
For security, Kiro asks for approval before running any command. You can streamline this process by configuring which commands to trust automatically.
WarningThe trust system puts responsibility on you to carefully configure trusted command patterns. Commands with potentially dangerous operations (like rm -rf) will be accepted if they match your trusted patterns.
Kiro uses simple string prefix matching to determine if a command should be automatically trusted. You can configure trusted commands in Settings â Trusted Commands at both the user level (global across all workspaces) and workspace level (specific to your current project).
Loading image...
Exact matching
Checks for the exact base string.
If you have trusted commands list as ["npm install", "git status"]:
CommandResultnpm installâ
Trusted and runs automaticallygit statusâ
Trusted and runs automaticallynpm install --saveâ Requires approval (not exact match)git status --shortâ Requires approval (not exact match)
Partial wildcard matching
Uses * to match variations of a specific command.
If you have trusted commands list as ["npm install *"]:
CommandResultnpm installâ
Trusted (matches "npm install *")npm install --saveâ
Trusted (matches "npm install *")npm install expressâ
Trusted (matches "npm install *")npm run buildâ Requires approval (doesn't start with "npm install ")npm testâ Requires approval (doesn't start with "npm install ")
Full wildcard matching & complex commands
Uses * to trust any command string that starts with the specified prefix. The trust system only checks the beginning of the command string - if it matches, the entire command is trusted, including any chained commands, pipes, or redirects that follow.
If you have trusted commands list as ["npm *", "git *"]:
CommandResultnpm installâ
Trusted (matches "npm *")npm install --saveâ
Trusted (matches "npm *")npm run buildâ
Trusted (matches "npm *")npm run build | tee logâ
Trusted (starts with "npm ")npm install && docker build .â
Trusted (starts with "npm ")git add . && git commit -m "update"â
Trusted (starts with "git ")docker build .â Requires approval (no matching prefix)
Universal trust
WarningUsing wildcards (*) in trusted commands is an over-permissive configuration. This automatically approves all terminal commands without review, which can pose significant security risks including data loss, system modifications, or unauthorized access. Only use wildcards if you completely trust the environment and understand all potential commands.
If you have trusted commands list as ["*"]:
CommandResultAny commandâ
Trusted - use with extreme caution
Using terminal context
Reference recent output from your active terminal in your conversations with #terminal. Important: #terminal always refers to the currently active/visible terminal window. If you have multiple terminals open, make sure the terminal you want to reference is active before using #terminal in your chat.
This feature allows Kiro to analyze command results, debug errors, and suggest solutions based on your actual terminal session.
#terminal analyze the error from the last npm run build
Kiro maintains awareness of command history and outputs, enabling:
Error Analysis - Understanding why commands failed with specific error messages
Output Interpretation - Explaining complex command results and logs
Follow-up Actions - Suggesting next steps based on actual results
Pattern Recognition - Identifying recurring issues across multiple commands
Environment Debugging - Helping resolve system and dependency conflicts
Troubleshooting
For issues with terminal integration and manual setup instructions, see the Shell Integration troubleshooting guide.Page updated: November 16, 2025Vibe vs. SpecDev servers