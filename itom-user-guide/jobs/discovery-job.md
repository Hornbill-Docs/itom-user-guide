# Discovery Job
The process of discovery is initiated through a designated SIS server, utilizing one of the various discovery methods available. This crucial step requires the provision of Admin Credentials through the secure Hornbill KeySafe, which must have been previously established. Once an IP address has been identified, the device's details are retrieved using advanced methods such as WMI via DCOM, WinRM, or SSH. This information is then used to mark the device as discovered and stored in the Inventory for future reference.

To ensure accuracy and completeness, an optional ping request can be sent to each device. If successful, the device will be marked as pingable, providing further confirmation of its presence on the network. For Unix/Linux devices, information is obtained through the use of SSH and local system tools, which may vary depending on the distribution being used. This comprehensive approach allows for a thorough gathering of data, including details about the device's hardware, operating system, components, installed software, and network-related information.

The retrieved data serves as a valuable source for importing assets into the Service Manager application, providing a seamless integration of information for efficient management. With this advanced discovery process, organizations can stay on top of their assets and ensure optimal performance and security.

## Creating a Discovery
1. Open the ITOM application
1. Navigate to Job Queue
1. Select the `Create New` button
1. Select `Discover Job`
1. Enter Name to identify the Job
1. Select a Site Target (SIS). This can be a single Server or a Group
1. Select the required Protocol
1. Select the required Discovery Mode
1. Select the Priority
1. Enter the relevant Discovery Mode Settings and Admin Credentials
1. Click the Create button

![Create Discovery Job](_books/itom-user-guide/jobs/images/create-discovery-job.png)

## Job Properties
* **Name**<br>Name given to identify this Discovery Job
* **Site Target [Group / Server ]**<br>Whether the job needs to run on an SIS Group or a single SIS/Managed CI
* **Protocol**<br>A device is identified as discovered once it can be accessed and its inventory retrieved. This is achieved by probing its Operating System (OS) using various methods depending on the device's Operating System. The probe will be initiated from the SIS server and does not require any software to be uploaded to the device. To achieve this, a protocol will be required for the SIS to access the device. Which protocol will depend on the OS and what is supported, in general for Windows devices WMI is used along with DCOM or WinRM, and for Linux / Unix (inc Apple Mac) Secure Shell (SSH) is used.
* **Discovery Mode**<br>The Discover Mode dictates the method that identifies devices on the Network. Each mode will have specific settings; these will be visible in the Discover Mode Settings section. It is only possible to have a single mode per Job, if more than one is required a new Job will need to be created for each one.
* **Priority**<br>Set the Jobs Priority which ranges from Urgent - Execute the Job as soon as possible, pushing the Job to the top of the queue to Only execute the Job when the server is in idle mode, and will also push the Job to the bottom of the queue.
* **Ping Check Settings**<br>
    * ***Ping check Discovered***<br>[Yes / No] Check that the discovered machine is pinged - if ICMP is disabled or firewalled, then select "No", as this can cause the discovery to be significantly slower.
    * ***Timeout***<br>
    * ***Hop Count***<br>

## Job Details
Once completed, the details of the job will be displayed, showing information relating to the status of the job. The progress of the job is available via the Monitor and Console Output with Debug Logging provided to aid with troubleshooting failures.

* **Summary**<br>Shows the current status of the job and its name along with who created it and when.
* **Discovery Options**<br>Displays details of the options used by the discovery process, this will differ depending on the discovery mode used.
* **Target Information**<br>Provides details of the SIS server that will facilitate the job, target machine and the Credentials used.
* **Execution Details**<br>The execution details show when the job was started and completed along with any result code.

### Execution Log
The Execution Log provides information relating to the execution of the job; the details shown will be dependent on the method of Discovery used.

![Monitor Discovery Job](_books/itom-user-guide/jobs/images/monitor-discovery-job.png)

The above example shows that Discovery has started and has initiated two processes, a Standalone (EspSiSExec.exe) and a Payload (ESPSisDiscovery.exe), on the SIS server.

All console output from the process is output, and confirmation of successful completion or failure will be output.

### Console Output
The Console Output is accessible once the job has been completed and will contain only the output produced by the payload, including any error messages.

![Console Discovery Job](_books/itom-user-guide/jobs/images/console-discovery-job.png)

### Debug Log
In cases where the Discovery may have failed or been completed incorrectly, the Debug log is used to review any errors and other technical information.

![Debug Discovery Job](_books/itom-user-guide/jobs/images/debug-discovery-job.png)

The Log provides three sections:

* **Full**<br>Full debug log information.
* **Standard**<br>Information log entries.
* **Problem**<br>Warning and Error, entries that may identify potential problems.

:::tip
The sections output will depend on the job, and thus some sections may not be available
:::