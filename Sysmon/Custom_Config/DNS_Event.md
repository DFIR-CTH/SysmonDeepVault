## Event ID 22: DNS Event

- This event will log all DNS queries and events for analysis. 
- The most common way to deal with these events is to exclude all trusted domains that you know will be very common "noise" in your environment.
- Once you get rid of the noise you can then look for DNS anomalies. This event uses QueryName XML tags. 

- Example :

```xml
<RuleGroup name="" groupRelation="or">
	<DnsQuery onmatch="exclude">
	 	<QueryName condition="end with">.microsoft.com</QueryName>
	</DnsQuery>
</RuleGroup> 
```

The above code snippet will get exclude any DNS events with the .microsoft.com query. This will get rid of the noise that you see within the environment.  
