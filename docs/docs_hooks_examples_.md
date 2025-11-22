# Hook examples - IDE - Docs - Kiro

Source: https://kiro.dev/docs/hooks/examples/

---

These examples demonstrate real-world hook implementations that you can adapt for your own projects. Each example includes the trigger type, target patterns, and complete hook instructions.
Security pre-commit scanner
This hook helps prevent security leaks by scanning files before they're committed.
Trigger Type: File Save
Target: **/*
Hook Instructions:
Review changed files for potential security issues:
1. Look for API keys, tokens, or credentials in source code
2. Check for private keys or sensitive credentials
3. Scan for encryption keys or certificates
4. Identify authentication tokens or session IDs
5. Flag passwords or secrets in configuration files
6. Detect IP addresses containing sensitive data
7. Find hardcoded internal URLs
8. Spot database connection credentials
For each issue found:
1. Highlight the specific security risk
2. Suggest a secure alternative approach
3. Recommend security best practices
Internationalization helper
This hook ensures that when you update text in your primary language file, translations are kept in sync.
Trigger Type: File Save
Target: src/locales/en/*.json
Hook Instructions:
When an English locale file is updated:
1. Identify which string keys were added or modified
2. Check all other language files for these keys
3. For missing keys, add them with a "NEEDS_TRANSLATION" marker
4. For modified keys, mark them as "NEEDS_REVIEW"
5. Generate a summary of changes needed across all languages
Documentation generator
This hook automatically updates documentation when code changes.
Trigger Type: Manual Trigger
Hook Instructions:
Generate comprehensive documentation for the current file:
1. Extract function and class signatures
2. Document parameters and return types
3. Provide usage examples based on existing code
4. Update the README.md with any new exports
5. Ensure documentation follows project standards
Test coverage maintainer
This hook ensures test coverage remains high as code evolves.
Trigger Type: File Save
Target: src/**/*.{js,ts,jsx,tsx}
Hook Instructions:
When a source file is modified:
1. Identify new or modified functions and methods
2. Check if corresponding tests exist and cover the changes
3. If coverage is missing, generate test cases for the new code
4. Run the tests to verify they pass
5. Update coverage reports
Integration with MCP
Agent Hooks can be enhanced with Model Context Protocol (MCP) capabilities to extend their functionality:
Access to External Tools: Hooks can leverage MCP servers to access specialized tools and APIs
Enhanced Context: MCP provides additional context for more intelligent hook actions
Domain-Specific Knowledge: Specialized MCP servers can provide domain expertise
To use MCP with hooks:
Configure MCP servers
Reference MCP tools in your hook instructions
Set appropriate auto-approval settings for frequently used tools
Use Cases:
Make sure that your Figma design system is respected
Update ticket status after a task is done
Sync a database from sample files within the project folder
Example: validate Figma design
This hook monitors HTML and CSS files and validates that they follow a Figma design using the Figma MCP.
Trigger Type: File Save Hook
Target: *.css *.html
Hook Instructions:
Use the Figma MCP to analyze the updated html or css files and check that they follow
established design patterns in the figma design. Verify elements like hero sections,
feature highlights, navigation elements, colors, and button placements align.
Page updated: November 16, 2025Hook typesManagement