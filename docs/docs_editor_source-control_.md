# Source Control - IDE - Docs - Kiro

Source: https://kiro.dev/docs/editor/source-control/

---

Kiro's Source Control view provides comprehensive Git integration with AI-enhanced features to streamline your version control workflow.
Commit message generation
Kiro automatically generates meaningful commit messages based on your staged changes using AI analysis of your code modifications.
How to generate commit messages
Stage your changes in the Source Control panel
Click ðª button next to the commit message input field
Review the generated message - Kiro analyzes your changes and creates a descriptive commit message
Edit if needed - You can modify the generated message before committing
Commit your changes using the generated or edited message
Tip: You can set up a custom keyboard shortcut for Kiro: Generate Commit Message in your keyboard settings for faster access.
Message format
Kiro follows the Conventional Commits format with detailed body sections:
<type>(<scope>): <subject>
- First change or addition
- Second change or improvement
- Third change if applicable
- Why this change was needed (if relevant)
Conventional commit types
feat: New features
fix: Bug fixes
docs: Documentation changes
style: Formatting changes
refactor: Code restructuring
test: Adding/updating tests
chore: Maintenance tasks
perf: Performance improvements
ci: CI/CD changes
Example
feat(docs): add comprehensive Source Control documentation
- Create new documentation page for Source Control features
- Update interface documentation to link to Source Control page
- Provide detailed explanation of AI-powered commit message generation
- Describe diff context provider and commit message generation process
Git diff context provider
You can include your current git changes in any chat conversation by typing #Git Diff. This allows Kiro to see your staged and unstaged changes, making it easier to get contextual help with your modifications.
Example usage
Hey Kiro, can you fix the merge conflicts? #Git Diff
Troubleshooting
Git operations failing
Check your Git configuration and credentials
Ensure you have proper permissions for the repository
Page updated: November 16, 2025Codebase indexingMulti-root workspaces