# SysmonDeepVault

## 🔐 [SYSMON_OVERVIEW]() 

 
- From the Microsoft Docs, "System Monitor (Sysmon)" is a Windows system service and device driver that, once installed on a system, remains resident across system reboots to monitor and log system activity to the Windows event log. 

- It provides detailed information about 

                                        [process creations],

                                        [network connections], 

                                        [changes to file creation time]

- By collecting the events it generates using Windows Event Collection or SIEM agents and subsequently analyzing them, you can identify malicious or anomalous activity and understand how intruders and malware operate on your network.

- Sysmon gathers detailed and high-quality logs as well as event tracing that assists in identifying anomalies in your environment.

-  Sysmon is most commonly used in conjunction with security information and event management (SIEM) system or other log parsing solutions that aggregate, filter, and visualize events.

- When installed on an endpoint, Sysmon will start early in the Windows boot process. In an ideal scenario, the events would be forwarded to a SIEM for further analysis.

- **Events within Sysmon are stored in Applications and Services Logs/Microsoft/Windows/Sysmon/Operational** {In Windows Event Viewer}


## 🛠️📜 [SYSMON_CONFIG_OVERVIEW]()

