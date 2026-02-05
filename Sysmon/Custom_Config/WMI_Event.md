## Event ID 19-20: WMIEvent

> [!NOTE]  
> Detects WMI abuse for persistence, reconnaissance, and remote execution

- Logs WMI query execution and filter creation used for persistence and reconnaissance.
- Common for scheduled tasks, process enumeration, and remote execution.
- Attackers abuse WMI for stealthy persistence avoiding traditional startup locations.

**Example:**

```xml
<RuleGroup name="" groupRelation="or">
	<WmiEvent onmatch="alert">
		<Query condition="contains">SELECT * FROM Win32_Process</Query>
	</WmiEvent>
	<WmiEvent onmatch="alert">
		<Query condition="contains">cmd.exe</Query>
	</WmiEvent>
</RuleGroup>
```

This catches WMI reconnaissance queries and command execution attempts via WMI.
