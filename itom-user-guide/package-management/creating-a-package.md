# Creating a Package
Hornbill ITOM provides you with the ability to create your own user-defined packages, of which you can use to create IT Automations and enhance Runbooks processes. This guide will take you through the basics of creating the different types of packages that are available, publishing and executing them. Packages can be as simple operation such as executing an OS command or executable thru to the creation of a complex script.

Packages contain a number of operations that provide some functionality to be used within an IT Automation. In general, the operations contained within a package would relate in some form, i.e User Account Management (Create, Delete, Disable, Enable, etc.). However, it is completely up to yourself what operations are contained within a package. You could, for example, have a package called toolbox, which contains operations for User Management, TCP/IP Utilities, File Management etc. This would no doubt become a little confusing and difficult to manage in the long term.

Package operation command types:

* Run an OS Command
* Run a Windows Installer
* Run a Windows Executable
* Batch Script
* Windows Powershell
* Powershell Core
* Linux Shell Script

## Run a Command
1. From the ITOM page select Package Creator
1. Click the New Pacakge button
1. Enter a Package name: TCP Utilities
1. Set Target OS to Windows Universal
1. Click Add Operation button
1. Enter the following details:
    * Operation: Ping
    * Description: Ping a device using the parameters -n, host
    * Command Type: Run Command
    * Command: cmd /c ping.exe
    * Timeout(secs): 60
    * Options/Args: -n {param.count} {param.host}
1. Click Add Parameter button
1. Set the following attributes:
    * Required
    * Number
    * Parameter Name: count
    * Default value: 3
    * Hint: Number of echo requests to send.
1. Click Add Parameter button
1. Set the following attributes:
    * Required
    * string
    * Parameter Name: host
    * Hint: Target device hostname.
1. Click Apply
1. Click Baseline button
1. Select Version 1 via the Drop Down Adjacent to the Baseline button
1. Click Package and Install drop down, and select Package and Install

### Executing the Package Operation
1. Navigate to (Home > ITOM > Job Queue)
1. Click Create New button, and select IT Automation Job
1. Select Run Package: private:{instance-name} > General Purpose > TCP Utilities (Version 1)
1. Click Apply
1. Enter the following details:
    * Name: Ping Computer
    * Run Operation: ping
    * Site Target: Server | <SIS Server>
    * Target Machine: Inventory |<target computer>
    * Admin Credentials: Network Admin
1. Click Create

## Windows Installer Package
1. From the ITOM page select Package Creator
1. Click the New Package button
1. Enter a Package name: Software Installer
1. Set Target OS to Windows Universal
1. Click Upload File button
1. Select the following file: C:\ Documents\ITOM\Packages\Demo.msi
1. Click on Package Info
1. Click Add Operation button
1. Enter the following details:
    * Operation: Install
    * Description: Install Windows application
    * Command Type: Windows Installer
    * Package: Demo.msi
    * Action: Install Software
1. Click Add
1. Click Add Operation button
1. Enter the following details:
    * Operation: Uninstall
    * Description: Uninstall Windows application
    * Command Type: Windows Installer
    * Package: Demo.msi
    * Action: Uninstall Software
1. Click Add
1. Click Baseline button
1. Select Version 1 via the Drop Down Adjacent to the Baseline button
1. Click Package and Install drop down, and select Package and Install

### Execute Installation Job
1. Navigate to (Home > ITOM > Job Queue)
1. Click Create New button, and select IT Automation Job
1. Select Package: private:{instance-name} > General Purpose > Software Installer (Version 1)
1. Click Apply
1. Enter the following details:
    * Name: Software Installation
    * Run Operation: Install
    * Site Target: Server | <SIS Server>
    * Target Machine: Inventory |<target computer>
    * Admin Credentials: 'Network Admin
1. Click Create
1. Verify that the following software exists on the target:
    * Name: Generic Business Application
    * Publisher: Acme Software Ltd

### Execute Uninstallation Job
1. Navigate to (Home > ITOM > Job Queue)
1. Click Create New button, and select IT Automation Job
1. Select Package: private:{instance-name} > General Purpose > Software Installer (Version 1)
1. Click Apply
1. Enter the following details:
    * Name: Software Uninstallation
    * Run Operation: UniInstall
    * Site Target: Server | <SIS Server>
    * Target Machine: Inventory |<target computer>
    * Admin Credentials: Network Admin
1. Click Create
1. Verify that the following the software no longer exists on the target:
    * Name: Generic Business Application
    * Publisher: Acme Software Ltd

## Windows Executable Package
1. From the ITOM page select Package Creator
1. Click the New Package NewPackageButton.png button
1. Enter a Package name: Windows Executable
1. Set Target OS to Windows Universal
1. Click Upload File button
1. Select the following file: C:\ Documents\ITOM\Packages\ShowHarry.exe
1. Click on Package Info
1. Click Add Operation button
1. Enter the following details:
    * Operation: Show Harry
    * Description: Windows Executable - Show Harry.exe
    * Command Type: Windows Executable
    * Run File: ShowHarry.exe
1. Click Add
1. Click Baseline button
1. Select Version 1 via the Drop Down Adjacent to the Baseline button
1. Click Package and Install drop down, and select Package and Install

### Execute Job
1. Navigate to (Home > ITOM > Job Queue)
1. Click Create New (+) button, and select IT Automation Job
1. Select Run Package: private:{instance-name} > General Purpose > Windows Executable (Version 1)
1. Click Apply
1. Enter the following details:
    * Name: Windows Executable
    * Run Operation: Show Harry
    * Site Target: Server | <SIS Server>
    * Target Machine: Inventory |<target computer>
    * Admin Credentials: Network Admin
1. Click Create

## PowerShell Script Package
1. From the ITOM page select Package Creator
1. Click the New Package button
1. Enter a Package name: Disk Information
1. Set Target OS to Windows Universal
1. Click the Add new File Button
1. Enter filename as: diskinfo.ps1 and click Apply
1. Click Add Operation button
1. Enter the following details:
    * Operation: Get Details
    * Description: Information for a Selected Disk Drive
    * Command Type: Windows PowerShell
    * Set the Script to: diskinfo.ps1
    * Timeout(secs): 60

### Input Parameters
1. Click Add Parameter button
1. Set the following attributes:
    * Required
    * Number
    * Parameter Name: Dirve
    * Default value: C
    * Hint: Enter the Drive Letter.

### Output Parameters
1. Click Add Parameter button
1. Set the following attributes:
    * Required
    * string
    * Parameter Name: outcome
    * Click Add
1. Add the following optional string output parameters:
    * Label
    * Size
    * FreeSpace
    * errors
1. Click Apply

### Add Script Content
1. Click on the script driveinfo.ps1
1. Enter the following code:

```
# Example PS ITOM Package Script
# Input Parameters
Param (
    [String]$Drive = "C"
)

# Operation Logic
try {
$volinfo = Get-Volume -DriveLetter $Drive -ErrorAction STOP
} catch {
    # Command failed exit with error mesage
    Write-Output "{{SISJobOutputParameterStart:outcome}}Fail{{SISJobOutputParameterEnd}}"
    Write-Output "{{SISJobOutputParameterStart:errors}}$_.Exception.message{{SISJobOutputParameterEnd}}"
    Exit 0
}

# Package Output Parameters
Write-Output "{{SISJobOutputParameterStart:Label}}$($volinfo.FileSystemLabel){{SISJobOutputParameterEnd}}"
Write-Output "{{SISJobOutputParameterStart:Size}}$($volinfo.Size){{SISJobOutputParameterEnd}}"
Write-Output "{{SISJobOutputParameterStart:FreeSpace}}$($volinfo.SizeRemaining){{SISJobOutputParameterEnd}}"
Write-Output "{{SISJobOutputParameterStart:outcome}}OK{{SISJobOutputParameterEnd}}"
Exit 0
```

1. Click the Save Button
1. Click on th Package Info Entry
1. Click Baseline button
1. Select Version 1 via the Drop Down Adjacent to the Baseline button
1. Click Package and Install drop down, and select Package and Install

### Executing the Package Operation
1. Navigate to (Home > ITOM > Job Queue)
1. Click Create New button, and select IT Automation Job
    * Name: Get Drive C Information
1. Select Package: <instance-name> > General Purpose > Disk Information
1. Click Apply
1. Enter the following details:
    * Operation: Get Details
    * Site Target: Server | <SIS Server>
    * 
    * Target Machine: Inventory |<target computer>
    * Admin Credentials: Network Admin
    * Drive: C
1. Click Create