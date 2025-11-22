# Completions & autocomplete - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/autocomplete/

---

Kiro CLI provides two AI-powered assistance features to help you work more efficiently in your terminal:
Autocomplete Dropdown Menu: A graphical menu showing available command options
Inline Suggestions: Gray "ghost text" that appears as you type
These features work independently and support hundreds of popular command line tools including git, npm, docker, and aws.
Autocomplete dropdown menu
The autocomplete dropdown appears to the right of your cursor when typing commands, showing available options, subcommands, and arguments that you can select using arrow keys.
Using autocomplete
The autocomplete dropdown is automatically enabled after you install Kiro CLI:
Open your terminal or command prompt
Start typing a command
A graphical menu will appear showing available options
Use arrow keys to navigate suggestions
Press Tab or Enter to select an option
Configuration
Customize the autocomplete behavior:
bash# Enable/disable autocomplete
kiro-cli settings autocomplete.disable false  # enable
kiro-cli settings autocomplete.disable true   # disable
# Change theme
kiro-cli theme dark
kiro-cli theme light
kiro-cli theme system
# View current theme
kiro-cli theme
# List available themes
kiro-cli theme --list
Inline suggestions
Inline suggestions appear as gray "ghost text" directly on your command line as you type. This feature works independently from the dropdown menu.
Using inline suggestions
Inline suggestions are enabled by default:
Start typing a command
Gray ghost text will appear showing potential completions
Press the right arrow key or Tab to accept
Continue typing to ignore the suggestion
Managing inline suggestions
Control inline suggestions with the kiro-cli inline command:
bash# Enable inline suggestions
kiro-cli inline enable
# Disable inline suggestions
kiro-cli inline disable
# Check current status
kiro-cli inline status
# Set customization
kiro-cli inline set-customization [ARN]
# Show available customizations
kiro-cli inline show-customizations
Supported tools
The autocomplete system supports hundreds of command line tools:
Popular tools
Git: Branch names, commit hashes, file paths
Docker: Container names, image tags, commands
npm/yarn: Package names, scripts, dependencies
kubectl: Resources, namespaces, contexts
terraform: Resources, providers, variables
aws: Services, regions, resource names
Language tools
Python: pip, poetry, conda
Node.js: npm, yarn, pnpm
Ruby: gem, bundle
Go: go mod, go build
System tools
Standard Unix/Linux commands
Package managers (apt, brew, yum)
File operations (ls, find, grep)
Troubleshooting
Autocomplete not working
If autocomplete isn't appearing:
Verify installation: kiro-cli --version
Check if disabled: kiro-cli settings autocomplete.disable
Restart your terminal
Try a different shell (bash, zsh, fish)
Inline suggestions issues
If inline suggestions aren't working:
Check status: kiro-cli inline status
Enable if disabled: kiro-cli inline enable
Verify shell compatibility
Check terminal emulator support
Page updated: November 16, 2025HooksBilling for individuals