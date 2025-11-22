# Chat - IDE - Docs - Kiro

Source: https://kiro.dev/docs/chat/

---

Kiro offers a chat panel where you can interact with your code through natural language conversations. Just tell Kiro what you need. Ask questions about your codebase, request explanations for complex logic, generate new features, debug tricky issues, and automate repetitive tasksâall while Kiro maintains complete context of your project.
Loading image...
Key features
Contextual UnderstandingAsk questions about your entire codebase, get explanations, or request edits with full awareness of your project structureSmart Intent DetectionKiro intelligently determines whether you want information or action, adapting its responses to match your workflow needsVibe vs Spec sessionsChat sessions can be either vibe or spec sessions. Learn more about the differences between these two.Dev ServersRun long-running processes in the background without blocking your workflow
Getting started
Accessing chat
There are multiple ways to access the chat in your development environment:
Keyboard Shortcut: Press Cmd+L (Mac) or Ctrl+L (Windows/Linux) to open the chat panel
Command Palette: Press Cmd+Shift+P (Mac) or  Ctrl+Shift+P (Windows/Linux) and search for "Kiro: Open Chat"
Secondary Side Bar: Click the Kiro chat icon toggle using Cmd+Opt+B (Mac) or Ctrl+Alt+B in the top bar on the right to open the chat panel
Your first conversation
Once the chat panel is open:
Type your question or request in natural language in the chat input
Press Enter to send your message
Kiro will analyze your request and respond appropriately
Example requests to get started:
Ask about your code
"Explain how authentication works in this project"
Generate new code
"Create a React component for a user profile page"
Fix issues
"Help me fix the error in this function"
Smart intent detection
Kiro intelligently analyzes your messages to understand whether you want information or action. When you ask questions like "How does this work?" or "What's the purpose of this code?",
Kiro recognizes this as an information request and responds with explanations and documentation without modifying your code. When you use directives like "Create a component" or "Fix this bug", Kiro identifies this as an action request and will propose or implement the necessary code changes, execute commands, or manage files accordingly. This seamless intent recognition allows for natural conversation without requiring explicit commands to switch between information and action modes.
Context management
Kiro's power comes from its deep understanding of your codebase context. It automatically analyzes open files in the editor, including their dependencies and structure, but you can also explicitly provide additional context.
Context providers
Use the # symbol in the chat input to access context providers:
ProviderDescriptionExample#codebaseAllow Kiro to automatically find relevant files across your project#codebase explain the authentication flow#fileReference specific files in your codebase#auth.ts explain this implementation#folderReference a specific folder and its contents#components/ what components do we have?#git diffReference the current Git changes#git diff explain what changed in this PR#terminalInclude recent output from your active terminal and command history#terminal help me fix this build error#problemsInclude all problems in the current file#problems help me resolve these issues#urlInclude web documentation#url:https://docs.example.com/api explain this API#codeInclude specific code snippets in the context#code:const sum = (a, b) => a + b; explain this function#repositoryInclude a map of your repository structure#repository how is this project organized?#currentReference the currently active file in the editor#current explain this component#steeringInclude specific steering files for guidance#steering:coding-standards.md review my code#docsReference documentation files and content#docs:api-reference.md explain this API endpoint#specReference all files from a specific spec (requirements, design, tasks)#spec:user-authentication update the design file to include password reset flow#mcpAccess Model Context Protocol tools and services#mcp:aws-docs how do I configure S3 buckets?
You can combine multiple context providers in a single request:
#codebase #auth.ts explain how authentication works with our database
TipThe #terminal context provider is particularly powerful for debugging and troubleshooting. When you include #terminal in your message, Kiro can access your recent command history, outputs, and error messages to provide targeted assistance.Common scenarios:
Build failures: #terminal My build is failing, what's the issue?
Test debugging: #terminal These tests aren't passing, help me understand why
Git issues: #terminal I'm stuck on this merge conflict
Dependency problems: #terminal npm install is throwing errors
Kiro can analyze the actual terminal output, understand error patterns, and suggest specific solutions based on what happened in your terminal session. For detailed examples and best practices, see the Terminal Integration guide.
Sessions and history
Kiro maintains conversation history within sessions, allowing for continuous context-aware interactions.
Managing sessions
Create New Sessions: Start fresh conversations for different topics or projects. Click on + icon in the chat panel to start a new session
Switch between Sessions: Easily navigate between ongoing conversations through the tab switcher
View History: Access previous interactions and their outcomes through the History button
Task Tracking: Monitor the progress of ongoing and completed tasks through the Task list button
Execution history
Kiro maintains a detailed history of sessions that includes actions taken such as code changes, commands executed,
search results, file operations, and more. You can search, restore, or delete a specific session.
Loading image...Page updated: November 16, 2025Best practicesModel selection