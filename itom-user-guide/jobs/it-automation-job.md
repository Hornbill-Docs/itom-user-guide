# IT Automation Job
IT Automation jobs are executed on Managed Devices selected from within the ITOM Inventory and can be initiated from various sources such as a Hornbill Business Process or AutoTask. Jobs can be executed on an ad-hoc basis as well as scheduled, or via a Runbook process, all configured via the Hornbill Administration portal. Packages are used to provide the automation payload and may require prerequisites to be in place along with security credentials. This information and details of all configurable parameters are provided via the Package documentation found in the ITOM Package Library.

## Creating an IT Automation Job
1. Select the Create New option
1. Select IT Automation Job
1. Enter Name to identify the Job
1. Select the required Package via the SelectPackageButton.png button
1. Select the required Operation
1. Select the Priority
1. Select a Site Target (SIS). This can be a single Server or a Group
1. Select the required Target Machine. This can be from a previously created List, the Inventory or via Manual entry.
1. Enter the relevant Credentials as required
1. Enter any necessary parameters. The selected Operation will determine the parameters that are available.
1. Click Create button

## Job Properties

![IT Automation Job Properties](_books/itom-user-guide/jobs/images/it-automation-job.png)

* **Name**<br>Name provided to identify the IT Automation Job.
* **Package**<br>Package used to provide the IT Automation payload.
* **Operation**<br>Operation to perform using the package
* **Priority**<br>Set the Jobs Priority which ranges from Urgent - Execute the Job as soon as possible, pushing the Job to the top of the queue to Only execute the Job when the server is in idle mode, and will also push the Job to the bottom of the queue
* **Site Target**<br>Specify the SIS Server or Group that will facilitate the Automation Job.
* **Target Machine**<br>Select the Device(s) that the Operation will target.
* **Credentials**<br>Sourced from the KeySafe, provides the security context to be used for package deployment and execution.
* **Extra Credentials**<br>Optional credentials used as part of the functionality within the package.
* **Operation Parameters**<br>Once a package and a Run Operation has been selected, any related parameters will be displayed; mandatory fields are highlighted and hints may be provided in the input box.

## Job Details
Once the job has been created, details will be displayed showing information relating to the job, including the status of the job. Monitoring, Console and Debug Logging are provided for displaying the job's progress and to aid with troubleshooting any failures.

![IT Automation Job Details](_books/itom-user-guide/jobs/images/it-automation-job-details.png)

* **Summary**<br>Shows the current status of the job and its name along with who created it and when.
* **Package Details**<br>Displays details of the deployment package, configured operation along with any parameters that were specified and job timeout limit.
* **Target Information**<br>Provides details of the SIS server that will facilitate the job, target machine and the security keys used.
* **Execution Details**<br>The execution details show when the job was started and completed along with any result code.

### Monitor
The Monitor frame provides information relating to the execution of the job; the details shown will be dependent on the type of discovery or package that is being executed.

![Monitor IT Automation Job](_books/itom-user-guide/jobs/images/monitor-it-automation-job.png)

The above example shows that the process has started and provides an id, which can be used to identify the task executing the package on the target machine. Depending on the package configuration, the monitor will specify more than the process ID. In the above case, the package is configured to execute an executable program as a specific user, using the "Run As Credentials". The first ID is for the process that triggers the package execution, which triggers another process to run an executable using the provided credentials.

### Console Output
All console output from the process will be displayed after this and will depend on the package contents and configuration. Once the job has been completed if there are any output parameters, they are processed and displayed, and confirmation of the job's successful completion or failure will be output.

Once the job has completed the Console Output and Debug Log frames will become enabled. The Console Output provides a view of only the console output, including any error messages.

![IT Automation Console](_books/itom-user-guide/jobs/images/it-automation-console.png)

### Debug Log
In cases where the Package may have failed or been completed incorrectly, the Debug Log can be used to review errors and other technical information.

![IT Automation Debug Log](_books/itom-user-guide/jobs/images/it-automation-debug.png)

The Log provides three sections:

* **Full**<br>Full debug log information
* **Standard**<br>Information log entries
* **Problem**<br>Warning and Error, entries that may identify potential problems

:::tip
The section's output will depend on the job, and thus some sections may not be available. This is also similar to the action buttons below of which only some of the buttons will appear depending on the status and type of job.
:::

### Action Buttons
* **Activate this Job**<br>Enables a Deferred Job to be Activated for processing.
* **Schedule**<br>Allows for a job to be configured to execute on a specific schedule.
* **Copy this Job**<br>Copies the job's properties and allows for a new job to be created once edited.
* **Cancel**<br>When a job is canceled its process will be sent a close message, therefore, allowing the process to close itself and all child processes in an orderly fashion.
* **Abort**<br>Aborting a Job causes the Job to be forcefully terminated immediately possibly causing child processes to be orphaned, and should only be used as a last resort.