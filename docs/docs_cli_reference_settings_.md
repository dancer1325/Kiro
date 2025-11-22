# Settings - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/reference/settings/

---

Kiro CLI provides extensive customization through settings. You can configure everything from telemetry to chat behavior, key bindings, and feature toggles.
Accessing settings
Manage settings directly from the command line:
bash# List all configured settings
kiro-cli settings list
# List all available settings with descriptions
kiro-cli settings list --all
# View a specific setting
kiro-cli settings telemetry.enabled
# Set a setting
kiro-cli settings telemetry.enabled true
# Delete a setting
kiro-cli settings --delete chat.defaultModel
# Open settings file in editor
kiro-cli settings open
Output formats
bash# Plain text (default)
kiro-cli settings list
# JSON
kiro-cli settings list --format json
# Formatted JSON
kiro-cli settings list --format json-pretty
Settings reference
Telemetry and privacy
SettingTypeDescriptionExampletelemetry.enabledbooleanEnable/disable telemetry collectionkiro-cli settings telemetry.enabled truetelemetryClientIdstringClient identifier for telemetrykiro-cli settings telemetryClientId "client-123"
Chat interface
SettingTypeDescriptionExamplechat.defaultModelstringDefault AI model for conversationskiro-cli settings chat.defaultModel "claude-3-sonnet"chat.defaultAgentstringDefault agent configurationkiro-cli settings chat.defaultAgent "my-agent"chat.greeting.enabledbooleanShow greeting message on chat startkiro-cli settings chat.greeting.enabled falsechat.editModebooleanEnable edit mode for chat interfacekiro-cli settings chat.editMode truechat.enableNotificationsbooleanEnable desktop notificationskiro-cli settings chat.enableNotifications truechat.disableMarkdownRenderingbooleanDisable markdown formattingkiro-cli settings chat.disableMarkdownRendering falsechat.disableAutoCompactionbooleanDisable automatic conversation summarizationkiro-cli settings chat.disableAutoCompaction truechat.enableHistoryHintsbooleanShow conversation history hintskiro-cli settings chat.enableHistoryHints truechat.uiModestringUI variant to usekiro-cli settings chat.uiMode "compact"chat.enableContextUsageIndicatorbooleanShow context usage percentage in promptkiro-cli settings chat.enableContextUsageIndicator true
Knowledge base
SettingTypeDescriptionExamplechat.enableKnowledgebooleanEnable knowledge base functionalitykiro-cli settings chat.enableKnowledge trueknowledge.defaultIncludePatternsarrayDefault file patterns to includekiro-cli settings knowledge.defaultIncludePatterns '["*.py", "*.js"]'knowledge.defaultExcludePatternsarrayDefault file patterns to excludekiro-cli settings knowledge.defaultExcludePatterns '["*.log", "node_modules"]'knowledge.maxFilesnumberMaximum files for indexingkiro-cli settings knowledge.maxFiles 1000knowledge.chunkSizenumberText chunk size for processingkiro-cli settings knowledge.chunkSize 512knowledge.chunkOverlapnumberOverlap between text chunkskiro-cli settings knowledge.chunkOverlap 50knowledge.indexTypestringType of knowledge indexkiro-cli settings knowledge.indexType "fast"
Key bindings
SettingTypeDescriptionExamplechat.skimCommandKeycharKey for fuzzy search commandkiro-cli settings chat.skimCommandKey "f"chat.autocompletionKeycharKey for autocompletion hint acceptancekiro-cli settings chat.autocompletionKey "Tab"chat.tangentModeKeycharKey for tangent mode togglekiro-cli settings chat.tangentModeKey "t"chat.delegateModeKeycharKey for delegate commandkiro-cli settings chat.delegateModeKey "d"
Feature toggles
SettingTypeDescriptionExamplechat.enableThinkingbooleanEnable thinking tool for complex reasoningkiro-cli settings chat.enableThinking truechat.enableTangentModebooleanEnable tangent mode featurekiro-cli settings chat.enableTangentMode trueintrospect.tangentModebooleanAuto-enter tangent mode for introspectkiro-cli settings introspect.tangentMode truechat.enableTodoListbooleanEnable todo list featurekiro-cli settings chat.enableTodoList truechat.enableCheckpointbooleanEnable checkpoint featurekiro-cli settings chat.enableCheckpoint truechat.enableDelegatebooleanEnable delegate toolkiro-cli settings chat.enableDelegate true
API and service
SettingTypeDescriptionExampleapi.timeoutnumberAPI request timeout in secondskiro-cli settings api.timeout 30
Model context protocol (MCP)
SettingTypeDescriptionExamplemcp.initTimeoutnumberMCP server initialization timeoutkiro-cli settings mcp.initTimeout 10mcp.noInteractiveTimeoutnumberNon-interactive MCP timeoutkiro-cli settings mcp.noInteractiveTimeout 5mcp.loadedBeforebooleanTrack previously loaded MCP serverskiro-cli settings mcp.loadedBefore true
Common configuration examples
Basic setup
bash# Enable telemetry
kiro-cli settings telemetry.enabled true
# Set default chat model
kiro-cli settings chat.defaultModel "claude-3-sonnet"
# Disable greeting message
kiro-cli settings chat.greeting.enabled false
Knowledge base configuration
bash# Enable knowledge base
kiro-cli settings chat.enableKnowledge true
# Set file patterns to include
kiro-cli settings knowledge.defaultIncludePatterns '["*.py", "*.js", "*.md", "*.txt"]'
# Set file patterns to exclude
kiro-cli settings knowledge.defaultExcludePatterns '["*.log", "node_modules", ".git", "*.pyc"]'
# Set maximum files to index
kiro-cli settings knowledge.maxFiles 2000
Enable experimental features
bash# Enable thinking tool
kiro-cli settings chat.enableThinking true
# Enable tangent mode
kiro-cli settings chat.enableTangentMode true
# Enable todo lists
kiro-cli settings chat.enableTodoList true
# Enable checkpoints
kiro-cli settings chat.enableCheckpoint true
# Configure key bindings
kiro-cli settings chat.tangentModeKey "t"
kiro-cli settings chat.delegateModeKey "d"
Performance tuning
bash# Increase API timeout for slow connections
kiro-cli settings api.timeout 60
# Adjust knowledge base chunk size
kiro-cli settings knowledge.chunkSize 1024
# Disable auto-compaction for long conversations
kiro-cli settings chat.disableAutoCompaction true
Troubleshooting settings
Invalid setting values
Boolean values: Use true or false (lowercase)
bashkiro-cli settings telemetry.enabled true  # â Correct
kiro-cli settings telemetry.enabled True  # â Wrong
Array values: Use JSON format with single quotes
bashkiro-cli settings knowledge.defaultIncludePatterns '["*.py", "*.js"]'  # â Correct
String values: Use quotes for strings with spaces
bashkiro-cli settings chat.defaultModel "claude-3-sonnet"  # â Correct
Resetting settings
Delete individual settings:
bashkiro-cli settings --delete setting.name
Open settings file for manual editing:
bashkiro-cli settings open
View current settings to identify issues:
bashkiro-cli settings list --all
Settings file issues
If the settings file becomes corrupted:
Back up current settings:
bashkiro-cli settings list --format json > backup.json
Open the settings file:
bashkiro-cli settings open
Verify JSON syntax or restore from backup
Settings file location
Settings are stored in:
macOS: ~/.kiro/settings.json
Linux: ~/.config/kiro/settings.json
You can edit this file directly, but using kiro-cli settings commands is recommended for validation.
Next steps
Configure custom agents
Set up MCP servers
Enable experimental features
CLI Commands Reference
Page updated: November 18, 2025Built-in toolsUpgrading from Q CLI