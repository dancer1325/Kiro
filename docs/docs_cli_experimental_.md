# Experimental features - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/experimental/

---

Kiro CLI includes experimental features that provide advanced functionality. These features are in active development and can be toggled on/off using the /experiment command.
Important notes
â ï¸ Experimental features may change or be removed at any time
â ï¸ Experience might not be perfect
â ï¸ Use at your own discretion in production workflows
These features are provided to gather feedback and test new capabilities. Please report issues through the kiro issue command.
Managing experiments
Use the /experiment command to toggle experimental features:
bash/experiment
This shows an interactive menu where you can:
See current status of each experiment (ON/OFF)
Toggle experiments by selecting them
View descriptions of what each experiment does
Available experiments
Knowledge management
Command: /knowledge
Enables persistent context storage and retrieval across chat sessions with semantic search capabilities.
Features:
Store and search through files, directories, and text content
Semantic search for better context retrieval
Persistent knowledge base across sessions
Agent-specific knowledge isolation
Enable:
bashkiro-cli settings chat.enableKnowledge true
Learn more about Knowledge Management â
Tangent mode
Command: /tangent or Ctrl+T
Create conversation checkpoints to explore side topics without disrupting your main conversation flow.
Features:
Create conversation checkpoints
Explore tangential topics
Return to main conversation thread
Preserve conversation context
Enable:
bashkiro-cli settings chat.enableTangentMode true
Learn more about Tangent Mode â
TODO lists
Tool: todo | Command: /todo
Enables Kiro to create and modify TODO lists automatically, with commands for you to view and manage them.
Features:
Kiro automatically creates TODO lists when appropriate
View, manage, and delete TODOs
Resume existing TODO lists
Persisted across chat sessions
Enable:
bashkiro-cli settings chat.enableTodoList true
Learn more about TODO Lists â
Thinking tool
Shows AI reasoning process for complex problems with step-by-step thought processes.
Features:
Transparent decision-making process
Step-by-step reasoning display
Useful for debugging and learning
Better understanding of conclusions
Enable:
bashkiro-cli settings chat.enableThinking true
Learn more about Thinking Tool â
Checkpointing
Command: /checkpoint
Enables session-scoped checkpoints for tracking file changes using Git-like commands.
Features:
Snapshots file changes into shadow git repo
List, expand, diff, and restore checkpoints
Conversation history unwinds when restoring
Auto-enables in git repositories
Manual initialization for non-git directories
Enable:
bashkiro-cli settings chat.enableCheckpoint true
Basic Usage:
bash/checkpoint list                    # Show checkpoints
/checkpoint expand <tag>            # Show detailed checkpoint info
/checkpoint diff <tag1> [tag2]      # Compare checkpoints
/checkpoint restore [<tag>]         # Restore to checkpoint
/checkpoint clean                   # Delete session shadow repo
Learn more about Checkpointing â
Context usage percentage
Shows context window usage as a percentage in the chat prompt with color-coded indicators.
Features:
Displays percentage in prompt (e.g., "[rust-agent] 6% >")
Color-coded indicators:
Green: Less than 50% usage
Yellow: 50-89% usage
Red: 90-100% usage
Helps monitor context consumption
Enable:
bashkiro-cli settings chat.enableContextUsageIndicator true
Delegate
Launch and manage asynchronous task processes, running Kiro chat sessions with specific agents in parallel.
Features:
Launch background tasks using natural language
Run parallel chat sessions with specific agents
Monitor task progress independently
Agent approval flow for security
Enable:
bashkiro-cli settings chat.enableDelegate true
Usage:
Use natural language to ask Kiro to launch a background task:
Can you create a background task to analyze the performance of our API endpoints?
Then check on results:
Check the status of my API analysis task
Show me the results from the background analysis
Learn more about Delegate â
Settings integration
Experiments are stored as settings and persist across sessions:
bash# View all experimental settings
kiro-cli settings list | grep -i enable
# Enable/disable specific experiments
kiro-cli settings chat.enableKnowledge true
kiro-cli settings chat.enableTangentMode true
kiro-cli settings chat.enableTodoList true
kiro-cli settings chat.enableThinking true
kiro-cli settings chat.enableCheckpoint true
kiro-cli settings chat.enableContextUsageIndicator true
kiro-cli settings chat.enableDelegate true
Fuzzy search support
All experimental commands are available in fuzzy search (Ctrl+S):
/experiment - Manage experimental features
/knowledge - Knowledge base commands (when enabled)
/todo - TODO list commands (when enabled)
/tangent - Tangent mode toggle (when enabled)
/checkpoint - Checkpoint commands (when enabled)
Best practices
Test in safe environments: Try experimental features on non-critical projects first
Provide feedback: Report issues and suggestions using kiro issue
Stay updated: Check release notes for changes to experimental features
Understand limitations: Read individual feature documentation for known issues
Have backups: Some features modify files (checkpointing, TODO lists)
Troubleshooting
Feature not working
Verify feature is enabled:
bashkiro-cli settings list | grep -i enable
Check for error messages in chat
Try disabling and re-enabling:
bashkiro-cli settings chat.enableFeatureName false
kiro-cli settings chat.enableFeatureName true
Restart Kiro CLI
Commands not available
Ensure the feature is enabled before using its commands. For example, /knowledge only works when knowledge management is enabled.
Next steps
Knowledge Management
Tangent Mode
TODO Lists
Settings Configuration
Page updated: November 18, 2025SteeringKnowledge management