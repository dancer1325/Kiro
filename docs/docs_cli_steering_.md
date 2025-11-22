# Steering - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/steering/

---

What is steering?
Steering gives Kiro persistent knowledge about your project through markdown files in .kiro/steering/. Instead of explaining your conventions in every chat, steering files ensure Kiro consistently follows your established patterns, libraries, and standards.
Key benefits
Consistent Code Generation - Every component, API endpoint, or test follows your team's established patterns and conventions.
Reduced Repetition - No need to explain project standards in each conversation. Kiro remembers your preferences.
Team Alignment - All developers work with the same standards, whether they're new to the project or seasoned contributors.
Scalable Project Knowledge - Documentation that grows with your codebase, capturing decisions and patterns as your project evolves.
Getting started with steering files
Create foundational steering files to establish core project context:
Create a .kiro/steering/ directory in your project root
Add markdown files for your project standards
Kiro will automatically load these files in chat sessions
Product Overview (product.md) - Defines your product's purpose, target users, key features, and business objectives. This helps Kiro understand the "why" behind technical decisions and suggest solutions aligned with your product goals.
Technology Stack (tech.md) - Documents your chosen frameworks, libraries, development tools, and technical constraints. When Kiro suggests implementations, it will prefer your established stack over alternatives.
Project Structure (structure.md) - Outlines file organization, naming conventions, import patterns, and architectural decisions. This ensures generated code fits seamlessly into your existing codebase.
These foundation files form the baseline of Kiro's project understanding.
Creating custom steering files
Extend Kiro's understanding with specialized guidance tailored to your project's unique needs:
Create a new .md file in .kiro/steering/
Choose a descriptive filename (e.g., api-standards.md)
Write your guidance using standard markdown syntax
Use natural language to describe your requirements
Examples:
API specs: #[[file:api/openapi.yaml]]
Component patterns: #[[file:components/ui/button.tsx]]
Config templates: #[[file:.env.example]]
Best practices
Keep Files Focused
One domain per file - API design, testing, or deployment procedures.
Use Clear Names
api-rest-conventions.md - REST API standards
testing-unit-patterns.md - Unit testing approaches
components-form-validation.md - Form component standards
Include Context
Explain why decisions were made, not just what the standards are.
Provide Examples
Use code snippets and before/after comparisons to demonstrate standards.
Security First
Never include API keys, passwords, or sensitive data. Steering files are part of your codebase.
Maintain Regularly
Review during sprint planning and architecture changes
Test file references after restructuring
Treat steering changes like code changes - require reviews
Common steering file strategies
API Standards (api-standards.md) - Define REST conventions, error response formats, authentication flows, and versioning strategies. Include endpoint naming patterns, HTTP status code usage, and request/response examples.
Testing Approach (testing-standards.md) - Establish unit test patterns, integration test strategies, mocking approaches, and coverage expectations. Document preferred testing libraries, assertion styles, and test file organization.
Code Style (code-conventions.md) - Specify naming patterns, file organization, import ordering, and architectural decisions. Include examples of preferred code structures, component patterns, and anti-patterns to avoid.
Security Guidelines (security-policies.md) - Document authentication requirements, data validation rules, input sanitization standards, and vulnerability prevention measures. Include secure coding practices specific to your application.
Deployment Process (deployment-workflow.md) - Outline build procedures, environment configurations, deployment steps, and rollback strategies. Include CI/CD pipeline details and environment-specific requirements.
Custom steering files are stored in .kiro/steering/ and become immediately available across all Kiro CLI chat sessions.Page updated: November 16, 2025SecurityExperimental