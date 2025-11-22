# TODO lists - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/experimental/todo-lists/

---

The TODO list feature enables Kiro to automatically create and modify task lists, while providing you with commands to view and manage existing TODO lists.
Getting started
TODO lists are automatically created when Kiro breaks down complex tasks. You can then manage these lists using the /todo command.
Enable TODO lists
bashkiro-cli settings chat.enableTodoList true
Basic usage
bash/todo view      # View existing TODO lists
/todo resume    # Resume a TODO list
How it works
Automatic creation
Kiro automatically creates TODO lists when:
You ask for help with multi-step tasks
A complex problem needs to be broken down
You explicitly request a TODO list
Example:
> Make a todo list with 3 read-only tasks.
I'll create a todo list with 3 read-only tasks for you.
ð ï¸  Using tool: todo_list (trusted)
â®
â TODO:
[ ] Review project documentation
[ ] Check system status
[ ] Read latest updates
â®
â Completed in 0.4s
Task management
Kiro can:
Create TODO lists
Mark tasks as complete
Add/remove tasks
Load TODO lists by ID
Search for existing TODO lists
You can:
View TODO lists
Resume TODO lists
Delete TODO lists
Commands
/todo view
Display and select a TODO list to view its contents, showing task descriptions and completion status.
bash/todo view
Interactive selection shows:
â Completed lists (green checkmark)
â In-progress lists with completion count (red X with progress)
Example:
> /todo view
? Select a to-do list to view: âº
â¯ â Unfinished todo list (0/3)
â Completed todo list (3/3)
/todo resume
Show an interactive menu of available TODO lists with their current progress status. Selecting a list loads it back into your chat session, allowing Kiro to continue where it left off.
bash/todo resume
Example:
> /todo resume
â³ Resuming: Read-only tasks for information gathering
ð ï¸  Using tool: todo (trusted)
â®
â TODO:
[x] Review project documentation
[ ] Check system status
[ ] Read latest updates
â®
â Completed in 0.1s
/todo clear-finished
Remove all completed TODO lists from storage. This helps clean up your workspace by removing lists where all tasks have been completed.
bash/todo clear-finished
/todo delete
Delete specific TODO lists or all lists at once.
bash/todo delete           # Interactive selection to delete one list
/todo delete --all     # Delete all TODO lists
Options:
--all - Delete all TODO lists without interactive selection
Storage
TODO lists are persisted across sessions
Each list is saved as a JSON file with:
Unique timestamp-based ID
Task descriptions and completion status
Context updates from completed tasks
Modified file paths
Overall list description
Directory structure
my-project/
âââ .kiro/
â   âââ cli-todo-lists/
â       âââ 1234567890-task-list.json
â       âââ 1234567891-another-list.json
âââ src/
âââ main.py
Interactive selection
All commands use interactive selection allowing you to:
Navigate with arrow keys
Press Enter to select
Press Esc to cancel
Use cases
Breaking down complex tasks
> I need to migrate our database from MySQL to PostgreSQL
Let me create a TODO list for this migration:
ð ï¸  Using tool: todo
â TODO: Database Migration
[ ] Backup current MySQL database
[ ] Set up PostgreSQL instance
[ ] Create schema migration scripts
[ ] Test migration on staging
[ ] Perform production migration
[ ] Verify data integrity
Tracking multi-step implementations
> Help me implement user authentication
I'll break this down into manageable steps:
ð ï¸  Using tool: todo
â TODO: User Authentication Implementation
[ ] Set up authentication library
[ ] Create user model and database schema
[ ] Implement registration endpoint
[ ] Implement login endpoint
[ ] Add password hashing
[ ] Create JWT token generation
[ ] Add authentication middleware
[ ] Write tests for auth flow
Resuming previous work
> /todo resume
? Select a to-do list to resume: âº
â¯ â User Authentication Implementation (3/8)
â Database Migration (1/6)
â Code Refactoring (5/5)
# Select "User Authentication Implementation"
â³ Resuming: User Authentication Implementation
Let's continue with the authentication implementation.
We've completed the first 3 tasks. Next up is implementing the login endpoint...
Best practices
Managing lists
Use clear-finished regularly to remove completed lists
Resume lists to continue complex multi-step tasks
Check view to see progress without resuming
Workflow integration
Let Kiro create TODO lists for complex tasks automatically
Use resume to pick up where you left off in previous sessions
Check view to see what tasks remain before resuming work
Organization
Work in project directories where TODO lists are relevant
Complete tasks in order for better context
Delete old lists when no longer needed
Limitations
Functionality
Cannot manually edit TODO list files
Cannot merge or split TODO lists
Cannot reorder tasks after creation
Troubleshooting
Tasks not updating
If task completion isn't being tracked:
Ensure TODO list is active: Resume the list first
Let Kiro mark tasks: Don't manually edit JSON files
Check for errors: Look for error messages in chat
Tool vs command
todo tool
The todo tool is for Kiro to call. Kiro can:
Create TODO lists
Mark tasks as complete
Add/remove tasks
Load TODO lists with given ID
Search for existing TODO lists
/todo command
The /todo command is for you to manage existing TODO lists. You can:
View TODO lists
Resume TODO lists
Delete TODO lists
Clear finished lists
Example workflow
1. Start complex task
> I need to set up CI/CD for our project
2. Kiro creates TODO list
ð ï¸  Using tool: todo_list
â TODO: CI/CD Setup
[ ] Choose CI/CD platform
[ ] Create pipeline configuration
[ ] Set up build stage
[ ] Add test stage
[ ] Configure deployment stage
[ ] Set up environment variables
[ ] Test pipeline
3. Work through tasks
Kiro works through tasks, marking them complete as you go.
4. Resume later
> /todo resume
? Select a to-do list to resume: âº
â¯ â CI/CD Setup (4/7)
# Continue where you left off
5. Clean up when done
> /todo clear-finished
Next steps
Experimental Features Overview
Checkpointing
Custom Agents
Page updated: November 18, 2025Tangent modeThinking tool