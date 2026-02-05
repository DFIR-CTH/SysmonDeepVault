## Event ID 3: Network Connection

- The network connection event will look for events that occur remotely. 
- This will include files and sources of suspicious binaries as well as opened ports.
- This event will use the Image and DestinationPort XML tags. 

- Example :

```xml
<RuleGroup name="" groupRelation="or">
	<NetworkConnect onmatch="include">
	 	<Image condition="image">nmap.exe</Image>
	 	<DestinationPort name="Alert,Metasploit" condition="is">4444</DestinationPort>
	</NetworkConnect>
</RuleGroup>
```

The above code snippet includes two ways to identify suspicious network connection activity.

- The first way will identify files transmitted over open ports.
- In this case, we are specifically looking for nmap.exe which will then be reflected within the event logs.
- The second method identifies open ports and specifically port 4444 which is commonly used with Metasploit.
- If the condition is met an event will be created and ideally trigger an alert for the SOC to further investigate.
