# Model selection - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/chat/model-selection/

---

Kiro provides three powerful AI agent options to handle your development tasks: Auto, Claude Sonnet 4.0, Claude Sonnet 4.5, and Claude Haiku 4.5. Each offers distinct advantages depending on your needs and usage patterns.
Available models
Auto (recommended)
Auto is Kiro's default intelligent model router that combines multiple frontier models with advanced optimization techniques.
Key benefits:
Cost-effective â Approximately 23% less expensive than direct Sonnet 4 usage
Smart routing â Automatically chooses the optimal model for each task
Consistent quality â Delivers Sonnet 4-level results across different task types
Plan efficiency â Makes your usage limits go further
What model does Auto use?
Auto uses best in class LLM models (Claude Sonnet 4 and alike) to provide you the best quality for the type of tasks assigned to the agent. We maintain a very high bar to ensure that the quality of what is offered under Auto compares to or exceeds the quality of separate models made available to our users.
Claude Sonnet 4.0
Direct access to Anthropic's Claude Sonnet 4.0 model for users who prefer consistent model selection or have specific requirements for using this particular model.
Key benefits:
Predictable behavior â Same model for all interactions
Direct access â No routing or optimization layers
Full control â Complete transparency in model selection
Claude Sonnet 4.5
An experimental preview of Anthropic's Claude Sonnet 4.5 model for users who want to test the latest Anthropic model.
Key benefits:
Task optimization â Better performance on specialized tasks
Advanced logic â Enhanced reasoning capabilities
Extended memory â Improved context handling for longer conversations
Cost comparison
Understanding the credit consumption differences:
ModelCredit UsageExample Task CostAuto1.0x10 creditsClaude Sonnet 4.01.3x13 creditsClaude Sonnet 4.51.3x13 credits
Choosing the right model
Auto
Consider using Auto when:
Cost efficiency matters â You want to maximize your plan's value
General development work â Most coding, debugging, and planning tasks
Variable task types â Working on diverse projects with different requirements
Plan optimization â You want your limits to stretch further
Sonnet 4.0 & Sonnet 4.5
Consider using Sonnet 4.0 or Sonnet 4.5 when:
Consistency is critical â You need predictable model behavior
Specific requirements â Your workflow depends on Sonnet 4's particular capabilities
Model transparency â You prefer knowing exactly which model handles each request
Budget flexibility â Higher costs aren't a primary concern
How to switch models
In the chat interface
Loading image...
Kiro CLI setting
bashkiro-cli settings chat.defaultModel claude-sonnet4
Best practices
Maximizing efficiency
Start with Auto â Use it as your default for most tasks
Monitor usage â Track how different models affect your plan consumption
Switch strategically â Use Sonnet 4 or Sonnet 4.5 for specific high-stakes tasks
Experiment â Try both models for similar tasks to compare results
Cost management
Plan accordingly â Factor model choice into your tier selection
Track patterns â Understand which tasks benefit most from each model
Optimize workflows â Adjust development practices based on model strengths
Consider overages â Enable if you need flexibility beyond plan limits
Page updated: November 16, 2025ChatPrompts