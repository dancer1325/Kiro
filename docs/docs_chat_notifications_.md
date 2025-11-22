# Agent Notifications - IDE - Docs - Kiro

Source: https://kiro.dev/docs/chat/notifications/

---

Kiro agent notifications provide native system notifications for important agent execution events. These OS-level notifications ensure you stay informed about agent progress even when Kiro is running in the background or you're working in other applications.
Loading image...
TipYou can also configure usage notifications to help you monitor your credit consumption and avoid unexpected charges. For more information, see Managing proactive usage notifications.
Agent notification types
Action Required - Agent needs user input or approval to continue (e.g., permission to run shell commands)
Success - Agent execution completes successfully (e.g., spec task completion, code generation finished)
Failure - Agent execution encounters an error or fails (e.g., spec creation failure)
Configuring agent notifications
Open Settings: Command Palette (â/Ctrl + Shift + P).
Search for Agent: Notifications. The various Agent notification types will be listed.
Select the specific Agent notification types that you'd like to enable.
You can disable notifications by unselecting the checkbox next to each notification type.
Troubleshooting agent notifications
Agent notifications not appearing
Check notification settings - Ensure notifications are enabled in Kiro settings
Verify system permissions - Grant notification permissions to Kiro in your OS settings
Check Do Not Disturb - Ensure your system's Do Not Disturb mode isn't blocking notifications
Focus state - Remember that notifications are suppressed when Kiro is focused (if enabled)
Restart if needed - Restart Kiro if notifications stop working after system changes
Page updated: November 15, 2025Diagnostics toolCheckpoints