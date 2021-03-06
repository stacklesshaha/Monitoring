# Monitoring
PowerShell scripts for monitoring SQL Servers

# Get-SQLPatches.ps1

### Synopsis
Get-SQLPatches retrives list of SQL Patches (SP/CU/Hot-fixes) for a Computer.

### Description
Get-SQLPatches uses WMI to retrieve a list of the Win32_OperatingSystem BuildNumber, CSName.
Get-SQLPatches uses Get-ChildItem to retrieve a list of DisplayName, DisplayVersion, InstallDate
from path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall.

### Parameter ComputerName
The Computer name to query. Default: Localhost.

### Exmaple 1
Gets the SQL Server patches from HiramSQL1
~~~
Get-SQLPatches -ComputerName HiramSQL1
~~~

### Exmaple 2
Gets the SQL Server patches from a list of computers in C:\Monitoring\Servers.txt.
~~~
Get-SQLPatches -ComputerName (Get-Content C:\Monitoring\Servers.txt)
~~~

### Exmaple Output
![Example CSV](/KeyPatchLevel-Good.jpg?raw=true "Example CSV")

### Task Scheduler
Info to run it automatically via the Windows Task Scheduler.

**Argument:** `-nologo -executionpolicy bypass -File "C:\Monitoring\Get-SQLPatches.ps1"`

![Action](/TaskSchedulerEditActionPowerShell.png?raw=true "Action")
![Schedule](/TaskSchedulerScheduleMonthly3rdMonday.png?raw=true "Schedule")
![Schedule](/TaskSchedulerGeneralPowerShell.png?raw=true "Schedule")

### Author
Created By: Hiram Fleitas aka. dba2.o [@hiramfleitas](http://twitter.com/hiramfleitas)
Modified: 4/17/2019 05:09:35 PM  
Version 1.0
Commissioned Credit: Anthony Vaquer (Microsoft: Premier Field Engineer - Data & AI)
