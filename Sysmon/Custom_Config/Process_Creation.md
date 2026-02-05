## Event ID 1: Process Creation

- This event will look for any processes that have been created.

- You can use this to look for known suspicious processes or processes with typos that would be considered an anomaly. 

- This event will use the CommandLine and Image XML tags.

- Example : 

```xml
<RuleGroup name="" groupRelation="or">
	<ProcessCreate onmatch="exclude">
	 	<CommandLine condition="is">C:\\Windows\\system32\\svchost.exe -k appmodel -p -s camsvc</CommandLine>
	</ProcessCreate>
</RuleGroup>
```


The above code snippet is specifying the Event ID to pull from as well as what condition to look for. 

- In this case, it is excluding the "svchost.exe" process from the event logs.

