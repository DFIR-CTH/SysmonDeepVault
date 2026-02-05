
## Event ID 23: FileDelete

> [!NOTE]  
> Detects tamper cleanup and anti-forensic file deletion activity

- Logs file deletion events, useful for detecting tamper cleanup and anti-forensic activity.
- Focus on suspicious locations like %TEMP%, staging directories, and script artifacts.
- Helps track attackers cleaning up after execution.

- Example:

```xml
<RuleGroup name="" groupRelation="or">
	<FileDelete onmatch="alert">
		<TargetFilename condition="contains">powershell</TargetFilename>
	</FileDelete>
	<FileDelete onmatch="alert">
		<TargetFilename condition="begin with">%TEMP%</TargetFilename>
	</FileDelete>
</RuleGroup>
