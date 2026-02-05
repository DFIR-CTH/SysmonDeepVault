## Event ID 10: ProcessAccess

> [!NOTE]  
> Monitors process memory/handle access for privilege escalation and credential dumping

- This event monitors when a process accesses another process's memory or handles.
- Use sparingly due to high volume - focus on drivers/filesystem reads and privilege escalation attempts.
- Common for credential dumping (LSASS access) and advanced persistence techniques.

- Example:

```xml
<RuleGroup name="" groupRelation="or">
	<ProcessAccess onmatch="alert">
		<SourceImage condition="is">lsass.exe</SourceImage>
		<TargetImage condition="is">mimikatz.exe</TargetImage>
	</ProcessAccess>
</RuleGroup>
```
The above monitors processes accessing LSASS (credential store) - key for detecting Mimikatz and similar tools
