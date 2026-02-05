## Event ID 15: FileCreateStreamHash

- This event will look for any files created in an alternate data stream. 
- This is a common technique used by adversaries to hide malware. This event uses TargetFilename XML tags.

- Example :

```xml
<RuleGroup name="" groupRelation="or">
	<FileCreateStreamHash onmatch="include">
	 	<TargetFilename condition="end with">.hta</TargetFilename>
	</FileCreateStreamHash>
</RuleGroup> 
```

The above code snippet will look for files with the .hta extension that have been placed within an alternate data stream.
