# Delegate - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/experimental/delegate/

---

Delegate enables launching and managing asynchronous task processes, allowing you to run Kiro chat sessions with specific agents in parallel to your main conversation.
Overview
The delegate feature allows you to:
Launch background tasks using natural language
Run parallel Kiro chat sessions with specific agents
Monitor task progress independently
Continue your main conversation while tasks run
Enabling delegate
bashkiro-cli settings chat.enableDelegate true
Or use the experiment command:
bash/experiment
# Select "Delegate" from the list
How it works
Task creation
Use natural language to ask Kiro to launch a background task:
> Can you create a background task to analyze the performance of our API endpoints?
Kiro will:
Understand the task requirements
Determine if an agent is needed
Request approval if using an agent
Launch the task in the background
Return control to your main conversation
Agent approval flow
Tasks with agents:
Require explicit approval
Show agent details before execution
Display agent configuration and permissions
Tasks without agents:
Run with a warning about trust-all permissions
May have broader access to tools
Task management
Once delegated, tasks work independently. You can:
Check progress at any time
Read results when complete
Delete tasks when no longer needed
Usage examples
Example 1: Code analysis
> Can you create a background task to analyze the performance of our API endpoints?
I'll create a background task to analyze your API performance.
Agent: performance-analyzer
Tools: read, shell, aws
Resources: api-docs, performance-metrics
Approve this agent? (y/n): y
â Task created: api-performance-analysis
Task ID: task-abc123
Status: Running
You can continue working while the analysis runs in the background.
> Great! Now help me with the frontend code...
# Continue main conversation
> Check the status of my API analysis task
Let me check on that task...
Task: api-performance-analysis (task-abc123)
Status: Complete
Duration: 2m 34s
Results:
- Analyzed 15 API endpoints
- Found 3 performance bottlenecks
- Generated optimization recommendations
Would you like me to show you the detailed results?
Example 2: Test suite execution
> Run our test suite in the background while I work on the new feature
I'll start the test suite in a background task.
â Task created: test-suite-run
Task ID: task-def456
Status: Running
# Continue working on feature
> How's the test suite doing?
Let me check...
Task: test-suite-run (task-def456)
Status: Running (45% complete)
Progress: 127/283 tests passed
Still running. I'll let you know when it's complete.
Example 3: Documentation generation
> Generate API documentation in the background
I'll create a task to generate your API documentation.
â Task created: api-docs-generation
Task ID: task-ghi789
Status: Running
# Work on other things
> Show me the results from the documentation task
Task: api-docs-generation (task-ghi789)
Status: Complete
Generated documentation for:
- 23 API endpoints
- 15 data models
- 8 authentication methods
Documentation saved to: docs/api/
Task lifecycle
1. Creation
> Create a background task to [description]
Kiro analyzes the request and determines:
What agent (if any) is needed
What tools are required
What resources to access
2. Approval (if needed)
If an agent is required, you'll see:
Agent: task-agent-name
Description: What this agent does
Tools: List of tools it can use
Resources: Files it can access
Approve this agent? (y/n):
3. Execution
Task runs in the background while you continue your main conversation.
4. Monitoring
Check status anytime:
> Check on [task name]
> What's the status of my background task?
> Show me task progress
5. Completion
When complete, you can:
> Show me the results from [task name]
> What did the background task find?
6. Cleanup
Delete tasks when done:
> Delete the [task name] task
> Clean up completed tasks
Best practices
When to use delegate
Long-running operations: Test suites, builds, analysis
Independent tasks: Work that doesn't need your input
Parallel work: Multiple tasks that can run simultaneously
Background monitoring: Continuous checks or watches
When not to use
Interactive tasks: Work requiring your input
Quick operations: Tasks that complete in seconds
Dependent work: Tasks that need results from main conversation
Simple commands: Direct execution is faster
Task organization
Use descriptive names: Make tasks easy to identify
Monitor progress: Check on long-running tasks periodically
Clean up completed tasks: Delete when no longer needed
Limit concurrent tasks: Too many may slow down system
Security considerations
Agent approval
Always review agent details before approval:
Tools: What can the agent do?
Resources: What files can it access?
Permissions: What operations are allowed?
Trust-all warning
Tasks without agents run with elevated permissions:
Can access all tools
May have broader file access
Should be used carefully
Best practices
Review agent configurations: Understand what you're approving
Use specific agents: Create agents with minimal required permissions
Monitor task activity: Check what tasks are doing
Delete sensitive results: Clean up tasks with sensitive data
Limitations
Concurrency
Limited number of concurrent tasks
System resources shared between tasks
May impact performance with many tasks
Task isolation
Tasks run independently
Cannot directly communicate with main conversation
Results must be explicitly retrieved
Persistence
Tasks are session-scoped
May not survive session restarts
Results should be saved if needed long-term
Troubleshooting
Task not starting
Verify delegate is enabled:
bashkiro-cli settings chat.enableDelegate
Check for errors: Look for error messages in chat
Try simpler task: Test with a basic task first
Cannot check task status
Verify task ID: Ensure you're using correct task name/ID
Check if task completed: Completed tasks may be cleaned up
List all tasks: Ask Kiro to show all active tasks
Agent approval issues
Review agent details carefully: Ensure you understand permissions
Check agent exists: Verify agent is properly configured
Try without agent: Some tasks can run without specific agents
Advanced usage
Custom agents for tasks
Create specialized agents for common background tasks:
json{
"name": "test-runner",
"description": "Runs test suites in background",
"tools": ["shell", "read"],
"allowedTools": ["shell"],
"toolsSettings": {
"shell": {
"allowedCommands": ["npm test", "pytest", "cargo test"]
}
}
}
Task patterns
Analysis Tasks:
> Analyze code quality in the background
> Run security scan as a background task
> Generate performance report in background
Build Tasks:
> Build the project in the background
> Compile and run tests as a background task
> Generate production bundle in background
Monitoring Tasks:
> Monitor log files in the background
> Watch for file changes as a background task
> Track system metrics in background
Related features
Experimental Features
Custom Agents
TODO Lists
Next steps
Create custom agents for tasks
Configure agents
Enable other experimental features
Page updated: November 18, 2025CheckpointingHooks