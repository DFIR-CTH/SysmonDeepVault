
## Installing Sysmon

- The installation for Sysmon is fairly straightforward and only requires downloading the binary from the [Microsoft](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) website.
- You can also download all of the Sysinternals tools with a PowerShell command if you wanted to rather than grabbing a single binary.
- It is also recommended to use a Sysmon config file along with Sysmon to get more detailed and high-quality event tracing.
- As an example config file we will be using the sysmon-config file from the SwiftOnSecurity GitHub repo. 

- You can find the Sysmon binary from the [Microsoft Sysinternals website](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon). 

- You can also download the [Microsoft Sysinternal Suite](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon) or use the below command to run a PowerShell module download and install all of the Sysinternals tools. 

# PowerShell command: 
```bash
Download-SysInternalsTools C:\Sysinternals
```

- To fully utilize Sysmon you will also need to download a Sysmon config or create your own config.
- We suggest downloading the [sysmonconfig.xml](https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml) sysmon-config. A Sysmon config will allow for further granular control over the logs as well as more detailed event tracing. 

- To start Sysmon you will want to open a new PowerShell or Command Prompt as an Administrator. 

- Then, run the below command it will execute the Sysmon binary, accept the end-user license agreement, and use [sysmonconfig.xml](https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml) config file. 

# Command Used: 

```bash
sysmon64.exe -accepteula -i <Downloads\sysmonconfig.xml>
```

- Now that Sysmon is started with the configuration file we want to use, we can look at the Event Viewer to monitor events.
- The event log is located under Applications and Services Logs/Microsoft/Windows/Sysmon/Operational

Note: At any time you can change the configuration file used by uninstalling or updating the current configuration and replacing it with a new configuration file. For more information look through the [Sysmon help menu](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon). 
