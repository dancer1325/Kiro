# Migrating from VSCode - IDE - Docs - Kiro

Source: https://kiro.dev/docs/guides/migrating-from-vscode/

---

Built on Visual Studio Code's open source foundation, Kiro delivers AI-enhanced development capabilities while preserving the familiar interface you know. This shared architecture ensures a smooth transition when bringing your existing VS Code configuration to Kiro.
Profile migration
Kiro's VS Code foundation enables complete compatibility with your development environment. You can transfer your personalized setupâextensions, themes, configurations, and shortcutsâwith no compatibility concerns.
Manual profile migration
For cross-machine transfers or granular control over your configuration, leverage VS Code's native profile export/import capabilities.
Exporting a profile from vs code
Launch the Command Palette in VS Code (â/Ctrl + Shift + P).
In the Command Palette, enter and select "Preferences: Open Profiles (UI)".
Locate your desired profile in the sidebar.
Access the 3-dot menu and choose Export.
Save locally or publish to a GitHub Gist.
Loading image...
Importing a profile to Kiro
Access Kiro's Command Palette (â/Ctrl + Shift + P).
In the Command Palette, enter and select "Preferences: Open Profiles (UI)".
Open the dropdown beside New Profile and select Import Profile.
Provide the GitHub Gist URL or browse for your local export file.
Confirm by choosing Import to save your configuration.
Activate your profile by selecting it in the sidebar and selecting the checkmark.
Your imported profile includes:
Color themes and UI preferences
Editor and workspace settings
Custom keyboard shortcuts and keybindings
Settings and interface
Settings menus
Kiro extends VS Code's settings architecture with dedicated controls for AI capabilities:
Kiro Settings
Open Settings: Command Palette (â/Ctrl + Shift + P) â "Preferences: Open Settings (UI)"
Navigate to Kiro Agent section within the settings UI
Manage AI behaviors, agent automation, trusted commands, and Kiro-exclusive features
Loading image...
VS Code Settings
Access the same way: Command Palette (â/Ctrl + Shift + P) â "Preferences: Open Settings (UI)"
Your standard VS Code preferences remain fully functional alongside Kiro settings
Version updates
Kiro stays synchronized with VS Code's development cycle through regular rebasing. While we incorporate the latest features and improvements, we strategically select stable VS Code releases to ensure reliability alongside our AI enhancements.
Extension compatibility
Kiro uses the OpenVSX extension registry, ensuring compatibility with open-source extensions. Extensions available in OpenVSX will migrate seamlessly, with many gaining enhanced capabilities through Kiro's AI integration:
Language extensions: Full functionality preserved for OpenVSX-available extensions
Theme extensions: Complete visual compatibility with OpenVSX themes
Debugging extensions: Uninterrupted debugging workflows for compatible extensions
Git extensions: Augmented with intelligent commit generation and automated code review
InfoOnly extensions available in the OpenVSX registry can be imported. Some VS Code Marketplace exclusives may not be available in Kiro.Page updated: November 16, 2025ConclusionBilling for individuals