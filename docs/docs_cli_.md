# Get started - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/

---

* 's features
  * Interactive Chat
  * Engage with Kiro through natural conversation in your terminal
  * Custom AgentsCreate and deploy specialized agents for your workflows
  * MCP IntegrationConnect external tools and data sources through Model Context Protocol
  * Smart HooksAutomate workflows with intelligent pre/post command hooks.Agent SteeringSteer Kiro agent with your best practices and preferences.Auto CompleteIntelligent command completion with context awareness.
* use cases
  * Interactive Development
    * Chat with Kiro directly in your terminal for instant help
  * Custom Automation
    * Create specialized agents for your specific workflows
  * Team Standardization
    * Use team level best practises and preferences
  * External Integrations
    * Connect tools and services through MCP servers
  * Intelligent Assistance
    * Get context-aware suggestions and auto-completion
  * Workflow Optimization
    * Automate repetitive tasks with smart hooks

* TODO: miss Kiro CLI

What is Kiro CLI?
Kiro CLI is a tool that allows you to interact with Kiro’s AI agents directly from your terminal. The CLI enables you to use AI for tasks like writing, reviewing, modifying code, and automating workflows, all within your command-line environment. It understands your codebase and speeds up development through adaptive, natural dialogue. Kiro CLI carries over steering files and MCP configurations from the Kiro IDE, leveraging the Auto agent to deliver the best results at the best price.

What are the main use cases of Kiro CLI?
The Kiro CLI is perfect for:

Interactive Development: Chat with Kiro directly in your terminal for instant help
Custom Automation: Create specialized agents for your specific workflows
Team Standardization: Use team level best practices and preferences with steering
External Integrations: Connect tools and services through MCP servers
Intelligent Assistance: Get context-aware suggestions and autocomplete
Workflow Optimization: Automate repetitive tasks with smart hooks


What are the main features of Kiro CLI?
Kiro CLI’s core features include:

Interactive Chat: Engage with Kiro through natural conversation in your terminal.
Custom Agents: Create and deploy specialized agents for your workflows.
MCP Integration: Connect external tools and data sources through Model Context Protocol.
Smart Hooks: Automate workflows with intelligent pre/post command hooks.
Agent Steering: Steer Kiro agents with your best practices and preferences.
Auto Complete: Intelligent command completion with context awareness.


How does Kiro CLI maintain context?
Kiro CLI maintains context primarily through directory-based conversation persistence and explicit context management options. Kiro CLI uses a directory-based system for conversation persistence, automatically associating chat sessions with specific working directories. It maintains context through both automatic and explicit mechanisms: automatically by preserving project-specific conversation history within directories (accessible via kiro chat), and explicitly through features like @workspace modifiers, file/folder specifications, and steering files. Kiro CLI also supports dynamic context addition through hooks and allows manual context management via /save and /load commands for conversation histories. This approach helps to ensure that relevant project context is maintained throughout development conversations.


How are the Kiro IDE and CLI licensed?
Kiro IDE and Kiro CLI are both distributed under a standard proprietary license as part of the Kiro developer experience.

For users upgrading from the Q Developer CLI, you can use the existing GitHub repository to report issues. The Q Developer CLI repository remains available and open source for anyone who wishes to use it.


Does Kiro CLI have separate pricing from Kiro IDE?
No. Kiro CLI pricing is included in the standard Kiro pricing tiers.

What environments are supported for Kiro CLI?
Kiro CLI is supported on macOS and specific Linux environments, including AppImage and Ubuntu.