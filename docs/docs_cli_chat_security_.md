# Security considerations - CLI - Docs - Kiro

Source: https://kiro.dev/docs/cli/chat/security/

---

Kiro provides powerful capabilities that can modify your system and AWS resources. Understanding security implications and following best practices helps you use these capabilities safely.
Understanding security risks
When using Kiro, be aware of the following potential security risks:
Unintended system changes: Kiro may interpret your requests in unexpected ways, leading to unintended modifications
AWS resource modifications: Resources could be created, modified, or deleted, potentially affecting production environments or incurring costs
Data loss: Commands that delete or overwrite files could result in data loss
Security vulnerabilities: Commands might compromise system security if not properly reviewed
These risks are significantly increased when using /tools trust-all or /acceptall, which bypass confirmation prompts.
Specific examples of risks include:
A request to "clean up old files" might delete important configuration files
A request to "optimize my EC2 instances" might terminate running instances
A request to "fix security issues" might modify permissions in ways that expose sensitive data
WarningDon't use /tools trust-all or /acceptall mode in production environments or when working with sensitive data or resources. You are responsible for all actions performed by Kiro.
General security best practices
When using Kiro in any environment, especially those with sensitive files, private keys, tokens, or other confidential information, consider implementing these security measures:
Restricting file access
By default, Kiro can read files without asking for permission each time (Read is trusted by default). For sensitive environments, you can restrict this behavior:
bash/tools untrust read
With this setting, Kiro will ask for your explicit permission before reading any file. This gives you granular control over which files Kiro can access during your session.
You can also make this setting persistent by adding it to your shell startup script:
bashecho 'alias kiro-cli="kiro-cli --untrust-fs-read"' >> ~/.bashrc
This ensures that every new Kiro session starts with Read untrusted, requiring explicit permission for file access.
Additional security measures
For environments with highly sensitive information, consider these additional measures:
Use in a dedicated development environment that doesn't contain sensitive credentials or data
Store sensitive files outside your project directories or in locations with restricted permissions
Use environment variables for sensitive values instead of hardcoding them in files
Consider using /tools untrust aws to require explicit permission before making AWS API calls
Use steering to define security guidelines and restrictions
Using /tools trust-all safely
If you must use /tools trustall or /acceptall for specific workflows, follow these safety practices to minimize risks:
Only use in development or testing environments, never in production
Enable /tools trust-all only for specific tasks, then immediately disable it using /tools reset to return to default permissions
Back up important data before enabling /tools trust-all
Use AWS credentials with minimal permissions when /tools trust-all is enabled
Carefully monitor all actions Kiro agent takes while /tools trust-all is enabled
To return to the default permission settings after using /tools trust-all, use the reset command:
bash/tools reset
This reverts all tools to their default permission levels, with only Read trusted by default.
Related documentation
Permissions - Managing access controls
Context Management - Controlling what data is shared
Authentication - Secure login methods
Privacy and Security - Overall security practices
Page updated: November 18, 2025ImagesCustom agents