## Sysmon Config Overview

- Sysmon requires a config file in order to tell the binary how to analyze the events that it is receiving.

- You can create your own Sysmon config or you can download a config.

- Here is an example of a high-quality config that works well for identifying anomalies created by [SwiftOnSecurity](https://github.com/SwiftOnSecurity/sysmon-config): Sysmon-Config. 

- Sysmon includes 29 different types of Event IDs, all of which can be used within the config to specify how the events should be handled and analyzed.

- Below we will go over Event IDs and show examples of how they are used within config files.

- When creating or modifying configuration files you will notice that a majority of rules in sysmon-config will exclude events rather than include events. 

- This will help filter out normal activity in your environment that will in turn decrease the number of events and alerts you will have to manually audit or search through in a SIEM. 

- On the other hand, there are rulesets like the [ION-Storm](https://github.com/ion-storm/sysmon-config) sysmon-config fork that takes a more proactive approach with it's ruleset by using a lot of include rules.

- You may have to modify configuration files to find what approach you prefer.

- Configuration preferences will vary depending on what SOC team so prepare to be flexible when monitoring.

- Sysmon config.xml supports "~12" main event types with include/exclude rules (conditions: Image, CommandLine, hashes, paths, etc.) for detection tuning, evasion resistance, FP reduction, efficiency, and pre-hunt—unlimited combinations via <RuleGroup name="..." onmatch="include/exclude">.

## List_Of_Main_Event_Types :

[ProcessCreate (1)](Custom_Config/Process_Creation.md)  
[FileCreate (11)]()  
[RegistryEvent (12-14)]()  
[NetworkConnect (3)]()  
[ProcessAccess (10)]()  
[DriverLoad (6)]()  
[ImageLoad (7)]()  
[DNSQuery (22)]()  
[FileDelete (23)]()  
[PipeEvent (17-18)]()  
[WMIEvent (19-20)]()  
[ClipboardChange (24)]()


# Detection/Optimization Examples Table

| **Section (EventID)**       | **Detection / Optimization Examples**                                                                 |
|-----------------------------|--------------------------------------------------------------------------------------------------------|
| ProcessCreate (1)           | Include LOLBins (certutil.exe); exclude msedge.exe noise; hash suspicious parents                     |
| FileCreate (11)             | Include $env:TEMP/*.exe; exclude Windows\WinSxS; detect persistence                                    |
| RegistryEvent (12-14)       | HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run; exclude HKCU prefs; catch reg save parents         |
| NetworkConnect (3)          | Include port 5985 (WinRM), 445 (SMB); exclude 127.0.0.1; C2 beaconing                                 |
| ProcessAccess (10)          | Drivers/filesystem reads (advanced); high CPU—use sparingly for privesc                               |
| DriverLoad (6)              | Unsigned drivers; kernel evasion                                                                      |
| ImageLoad (7)               | DLL injection; exclude signed MS; AMSI bypass                                                         |
| DNSQuery (22)               | Suspicious domains; exclude CDNs; high FP—tune heavily                                                |
| FileDelete (23)             | Tamper cleanup; include %TEMP%                                                                        |
| PipeEvent (17-18)           | Named pipes (PsExec); interproc comms                                                                 |
| WMIEvent (19-20)            | WMI abuse; privesc                                                                                    |
| ClipboardChange (24)        | Data exfil; low volume                                                                                |
