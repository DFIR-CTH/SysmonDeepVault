## Event ID 8: CreateRemoteThread

- The CreateRemoteThread Event ID will monitor for processes injecting code into other processes. The CreateRemoteThread function is used for legitimate tasks and applications. However, it could be used by malware to hide malicious activity. This event will use the SourceImage, TargetImage, StartAddress, and StartFunction XML tags.

- Example :

```xml
<RuleGroup name="" groupRelation="or">
	<CreateRemoteThread onmatch="include">
	 	<StartAddress name="Alert,Cobalt Strike" condition="end with">0B80</StartAddress>
	 	<SourceImage condition="contains">\</SourceImage>
	</CreateRemoteThread>
</RuleGroup>
```

The above code snippet shows two ways of monitoring for CreateRemoteThread.

- The first method will look at the memory address for a specific ending condition which could be an indicator of a Cobalt Strike beacon.
- The second method will look for injected processes that do not have a parent process. This should be considered an anomaly and require further investigation. 
