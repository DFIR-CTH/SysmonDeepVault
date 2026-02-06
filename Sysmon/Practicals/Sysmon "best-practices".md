
## Sysmon "Best Practices"

- Sysmon offers a fairly open and configurable platform for you to use. 
- Generally speaking, there are a few best practices that you could implement to ensure you're operating efficiently and not missing any potential threats.

- A few common best practices are outlined and explained below.

> [!NOTE]
> Exclude > Include
> 
> Example : Exclude Legitimate Events from rule, that reduces False-Positives.

- When creating rules for your Sysmon configuration file it is typically best to prioritize excluding events rather than including events. This prevents you from accidentally missing crucial events and only seeing the events that matter the most.

> [!NOTE]
> CLI gives you further control

> As is common with most applications the CLI gives you the most control and filtering allowing for further granular control. You can use either Get-WinEvent or wevutil.exe to access and filter logs. As you incorporate Sysmon into your SIEM or other detection solutions these tools will become less used and needed. 

> [!NOTE]
> Know your environment before implementation

> Knowing your environment is important when implementing any platform or tool. You should have a firm understanding of the network or environment you are working within to fully understand what is normal and what is suspicious in order to effectively craft your rules.

---

**Filtering Events with PowerShell**

- To view and filter events with PowerShell we will be using Get-WinEvent along with XPath queries. We can use any XPath queries that can be found in the XML view of events. We will be using wevutil.exe to view events once filtered. 
- The command line is typically used over the Event Viewer GUI as it allows for further granular control and filtering whereas the GUI does not. 

```bash
Filter by Event ID: */System/EventID=<ID>

Filter by XML Attribute/Name: */EventData/Data[@Name="<XML Attribute/Name>"]

Filter by Event Data: */EventData/Data=<Data>
```

- We can put these filters together with various attributes and data to get the most control out of our logs.

- Look below for an example of using Get-WinEvent to look for network connections coming from port 4444.

```bash
Get-WinEvent -Path <Path to Log> -FilterXPath '*/System/EventID=3 and */EventData/Data[@Name="DestinationPort"] and */EventData/Data=4444'
```
