# Azure Scheduled Events Service
This project enables your Azure Virtual Machines to subscribe to [Scheduled Events](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/scheduled-events) which informs your application about upcoming Azure Maintenance. The project is for Windows Virtual Machines and contains a powershell script that listens and logs the events to Windows Event logs. These logs can be then exported to [Azure Monitor](https://docs.microsoft.com/en-us/azure/virtual-machines/extensions/oms-windows) to then build alerting.

# Steps
1. Place the SchService.ps1 on your Azure Windows Virtual Machine
2. Open a PowerShell command and run the following command to setup the Service.
.\SchService.ps1 -Setup
3. Now run the following command to start the Service
.\SchService.ps1 -Start
4.	Validate the Service status by running the following command and make sure it is running
.\SchService.ps1 -status
5.	Once the service is setup and started, it will log the following events in the Application event. 
6.	The service will now start polling every 10 seconds for any scheduled events and auto approve the same.  Freeze, Reboot, Redeploy and Preempt are the events captures by Schedule events.
7.	When any of the above events are captured by Schedule Event service, it will get logged in the application event log with Event Status, Event Type, Resources (VM Name) and NotBefore(minimum notice period)

# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
