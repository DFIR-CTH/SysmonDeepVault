
## Event ID 17-18: PipeEvent

> [!NOTE]  
> Detects named pipe usage for lateral movement (PsExec) and process hollowing

- Monitors named pipe creation and connections used for inter-process communication.
- Key for detecting lateral movement tools like PsExec and process hollowing.
- Attackers use pipes to communicate between dropped binaries and legitimate processes.

- Example :

```xml
<RuleGroup name="" groupRelation="or">
	<PipeEvent onmatch="alert">
		<PipeName condition="is">\pipe\epmapper</PipeName>
	</PipeEvent>
	<PipeEvent onmatch="alert">
		<PipeName condition="contains">psexec</PipeName>
	</PipeEvent>
</RuleGroup>
