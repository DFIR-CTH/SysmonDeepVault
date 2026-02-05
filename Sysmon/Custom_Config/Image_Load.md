## Event ID 7: Image Loaded

- This event will look for DLLs loaded by processes, which is useful when hunting for DLL Injection and DLL Hijacking attacks. It is recommended to exercise caution when using this Event ID as it causes a high system load. This event will use the Image, Signed, ImageLoaded, and Signature XML tags. 

- Example :

```xml
<RuleGroup name="" groupRelation="or">
	<ImageLoad onmatch="include">
	 	<ImageLoaded condition="contains">\Temp\</ImageLoaded>
	</ImageLoad>
</RuleGroup>
```

The above code snippet will look for any DLLs that have been loaded within the \Temp\ directory. 

**If a DLL is loaded within this directory it can be considered an anomaly and should be further investigateded.**
