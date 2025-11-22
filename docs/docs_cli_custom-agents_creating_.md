# Creating custom agents - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/custom-agents/creating/

---

Custom agents allow you to tailor Kiro CLI behavior for specific tasks by defining which tools are available, what permissions are granted, and what context is automatically included.
Quick start
You can create an agent configuration using a slash command from within a Kiro CLI chat session. It will guide you through the process of configuring the agent:
> /agent generate
â Enter agent name:  Â· backend-specialist
â Enter agent description:  Â· You are specialist in backend coding practices
â Agent scope Â· Local (current workspace)
Select MCP servers (use Space to toggle, Enter to confirm): markdown-downloader (node), code-analysis (uv)
â Agent 'backend-specialist' has been created and saved successfully!
Alternatively, you can also use the CLI command to create a new custom agent:
bashkiro-cli agent create --name my-agent
This will guide you through the setup process and create a configuration file at ~/.kiro/agents/my-agent.json.
Agent configuration file
Custom agents are defined using JSON configuration files. Here's a basic example:
json{
"name": "my-agent",
"description": "A custom agent for my workflow",
"tools": ["read","write"],
"allowedTools": ["read"],
"resources": ["file://README.md", "file://.kiro/steering/**/*.md"],
"prompt": "You are a helpful coding assistant",
"model": "claude-sonnet-4"
}
Using your custom agent
Start a new chat session - which uses the default agent ("kiro_default") and swap to an agent using the agent slash command
bash> /agent swap
Choose one of the following agents
â¯ rust-developer-agent
kiro_default
backend-specialist
After selecting an agent, you will see the following:
bashâ Choose one of the following agents Â· backend-specialist
[backend-specialist] >
Alternatively, start a chat session with your custom agent:
bashkiro-cli --agent my-agent
Next steps
Explore Agent Configuration options in detail
Page updated: November 18, 2025Custom agentsConfiguration reference