## Event ID 24: ClipboardChange

> [!NOTE]  
> Monitors clipboard changes for credential harvesting and data exfiltration

- Monitors clipboard content changes for data exfiltration attempts.
- Low volume event but high value for detecting copy-paste of credentials/secrets.
- Useful for insider threats and post-exploitation data staging.

**Example:**

```xml
<RuleGroup name="" groupRelation="or">
	<ClipboardChange onmatch="alert">
		<Image condition="contains">powershell</Image>
	</ClipboardChange>
	<ClipboardChange onmatch="alert">
		<Image condition="contains">cmd</Image>
	</ClipboardChange>
</RuleGroup>

Detects when PowerShell or CMD processes modify clipboard content (credential harvesting).
