# Hook types - IDE - Docs - Kiro

Source: https://kiro.dev/docs/hooks/types/

---

Agent Hooks support various trigger types, each designed for specific automation scenarios. Understanding these types helps you choose the right approach for your workflow needs.
On file create
Trigger when new files matching specific patterns are created in your workspace.
Use Cases:
Generate boilerplate code for new components
Add license headers to new files
Set up test files when creating implementation files
Example: React Component Setup
When a new React component file is created, add:
1. Import statements for React and necessary hooks
2. A functional component with TypeScript props interface
3. Export statement
4. Basic styling if applicable
5. A skeleton test file in the appropriate directory
On file save
Trigger when files matching specific patterns are saved.
Use Cases:
Run linting and formatting
Update related files
Generate documentation
Run tests for changed files
Example: Update Test Coverage
When a JavaScript/TypeScript file is saved:
1. Identify the corresponding test file
2. Update tests to maintain coverage for any new functions
3. Run the tests to verify they pass
4. Update any snapshots if necessary
On file delete
Trigger when files matching specific patterns are deleted.
Use Cases:
Clean up related files
Update import references in other files
Maintain project integrity
Example: Clean Up References
When a component file is deleted:
1. Find all imports of this component across the codebase
2. Remove or comment out those import statements
3. Suggest replacements if appropriate
Manual trigger
Manually execute a hook.
Use Cases:
On-demand code reviews
Documentation generation
Security scanning
Performance optimization
Example: Code Review Button
Review the current file for:
1. Code quality issues
2. Potential bugs
3. Performance optimizations
4. Security vulnerabilities
5. Accessibility concerns
Page updated: November 16, 2025HooksExamples