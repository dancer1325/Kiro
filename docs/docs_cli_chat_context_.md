# Context management - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/chat/context/

---

Choosing the right context approach
Kiro offers three ways to provide context, each optimized for different use cases:
ApproachContext Window ImpactPersistenceBest ForAgent ResourcesAlways active (consumes tokens)Persistent across sessionsEssential project files, standards, configsSession ContextAlways active (consumes tokens)Current session onlyTemporary files, quick experimentsKnowledge BasesOnly when searchedPersistent across sessionsLarge codebases, extensive documentation
Decision flowchart
Use this decision tree to choose the appropriate context approach:
Is your content larger than 10MB or contains thousands of files?
Yes â Use Knowledge Bases
No â Continue to step 2
Do you need this context in every conversation?
Yes â Use Agent Resources
No â Use Session Context
Quick reference:
Essential project files (README, configs, standards) â Agent Resources
Large codebases or documentation sets â Knowledge Bases
Temporary files for current task â Session Context
Understanding context window impact
Context files and agent resources consume tokens from your context window on every request, whether referenced or not. Use /context show to monitor token usage:
kiro-cli chat
/context show
Total: ~1100 tokens
Token limits: Context files are limited to 75% of your model's context window. Files exceeding this limit are automatically dropped.
Knowledge bases don't consume context window space until searched, making them ideal for large reference materials. For more information, see Knowledge base context (for large datasets).
Managing context
Context files contain information you want Kiro to consider during your conversations. These can include project requirements, coding standards, development rules, or any other information that helps Kiro provide more relevant responses.
Configuring persistent context with agent resources
The recommended way to configure context is through the resources field in your agent configuration file. This creates persistent context that is available every time you use the agent.
Add file paths or glob patterns to the resources array in your agent config:
json{
"name": "my-agent",
"description": "My development agent",
"resources": [
"file://README.md",
"file://docs/**/*.md",
"file://src/config.py"
]
}
Resources must be prefixed with file:// to be included as context files. These files will be automatically available in all chat sessions using this agent.
Adding temporary session context
You can temporarily add files to your current chat session using the /context add command. These additions are only available for the current session and will not persist when you start a new chat session.
kiro-cli chat
/context add README.md
Added 1 path(s) to context.
Note: Context modifications via slash command is temporary.
You can also add multiple files at once using glob patterns:
kiro-cli chat
/context add docs/*.md
Added 3 path(s) to context.
Note: Context modifications via slash command is temporary.
To make context changes permanent, add the files to your agent's resources field instead. For more information, see Configuring persistent context with agent resources.
Knowledge base context (for large datasets)
For large codebases, documentation sets, or reference materials that would exceed context window limits, use knowledge bases. Knowledge bases provide semantic search capabilities without consuming context window space until searched.
Enable knowledge bases:
kiro-cli settings chat.enableKnowledge true
Add content to a knowledge base:
kiro-cli chat
/knowledge add /path/to/large-codebase --include "/*.py" --exclude "node_modules/"
Knowledge bases are searched on-demand by Kiro when relevant information is needed, making them ideal for large reference materials.
Viewing context
To view your current context, use the /context show command:
kiro-cli chat
/context show
ð¤ Agent (my-agent):
README.md (1 match)
docs/**/*.md (3 matches)
ð¬ Session (temporary):
(none)
4 matched files in use:
ð¤ README.md (~250 tkns)
ð¤ docs/architecture.md (~150 tkns)
ð¤ docs/api-guide.md (~320 tkns)
ð¤ docs/best-practices.md (~200 tkns)
Total: ~920 tokens
The output shows:
ð¤ Agent: Persistent context from your agent's resources field
ð¬ Session: Temporary context added during the current session
Removing context
To remove files from your current session context, use the /context rm command:
kiro-cli chat
/context rm src/temp-file.py
Removed 1 path(s) from context.
Note: Context modifications via slash command is temporary.
To clear all session context, use the /context clear command:
kiro-cli chat
/context clear
Cleared context
Note: Context modifications via slash command is temporary.
Note: You cannot remove agent-defined context using /context commands. To permanently remove context, edit your agent's resources field.
Common use cases
Here are some common use cases for context management:
Migrating from session context to agent resources
If you find yourself repeatedly adding the same context files using /context add commands, consider moving them to your agent's resources field for persistence:
Note the files you frequently add with /context add
Edit your agent configuration file using /agent edit or by directly modifying the file
Add the file paths to the resources array with file:// prefix
Save the agent configuration
Example migration:
bash# Instead of running these commands every session:
> /context add README.md
> /context add docs/*.md
# Add them to your agent config once:
{
"resources": [
"file://README.md",
"file://docs/**/*.md"
]
}
When to use knowledge bases
Consider knowledge bases when:
Your context files exceed the token limit (75% of context window)
You have large codebases or documentation sets
You need semantic search across extensive materials
You want to avoid constant context window consumption
Example: Instead of adding a large codebase as context files:
This would consume too many tokens:
/context add src/**/*.py
Use knowledge base instead:
/knowledge add src/ --include "/*.py" --exclude "pycache/"
Setting a default agent with context
You can configure a default agent that includes your preferred context files:
kiro-cli settings chat.defaultAgent my-project-agent
This ensures your context is automatically available in new chat sessions without needing to specify the agent each time.
Best practices
Context file organization
Keep context files focused and relevant to avoid token limits
Use descriptive filenames that indicate their purpose
Organize rules and documentation in logical directory structures
Consider file size - very large files may consume significant tokens
Performance considerations
Monitor token usage with /context show to stay within limits
Use specific glob patterns rather than overly broad ones
Remove unused context files from agent configurations
Consider splitting large context files into smaller, focused files
Use knowledge bases for large datasets to avoid context window consumption
Security considerations
Avoid including sensitive information in context files
Use .gitignore to prevent accidental commits of sensitive context
Review context files regularly to ensure they don't contain outdated information
Be mindful of what information is shared when using context in conversations
Related documentation
Slash Commands - In-chat context commands
CLI Commands - Terminal context commands
Interactive Chat Mode - Using context in chat
Page updated: November 16, 2025PromptsResponding to messages