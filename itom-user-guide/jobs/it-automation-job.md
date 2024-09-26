# IT Automation job
IT Automation jobs are executed on Managed Devices selected from within the ITOM Inventory and can be initiated from various sources such as a Hornbill Business Process or AutoTask. Jobs can be executed on an ad-hoc basis as well as scheduled, or via a Runbook process, all configured via the Hornbill Administration portal. Packages are used to provide the automation payload and may require prerequisites to be in place along with security credentials. This information and details of all configurable parameters are provided via the Package documentation found in the ITOM Package Library.

## Topics covered
- [Creating an IT Automation job](/creating-an-it-automation-job)
- [Job properties](/job-properties)
- [Job details](/job-details)

## Creating an IT Automation job
1. In the ITOM application, navigate to Job Queue.
1. Click **Create New > IT Automation Job**.
1. Enter a name to identify the job.
1. In the Run Package field, click the button to select the required package.
1. Select the required operation.
1. Select the priority.
1. Select a Site Target (SIS). This can be a single server or a group.
1. Select the required target machine. This can be from a previously created list, the inventory, or via manual entry.
1. Enter the relevant credentials as required.
1. In the Extra Credentials section, enter any necessary parameters. The operation selected determines the parameters that are available.
1. Click **Create**.

## Job properties

![IT Automation Job Properties](_books/itom-user-guide/jobs/images/it-automation-job.png)

* **Name.** Identifies the IT Automation job.
* **Package.** The package used to provide the IT Automation payload.
* **Operation.** The operation to perform using the package.
* **Priority.** Set the job's priority. The highest priority, Urgent, pushes the job to the top of the queue. The lowest priority, Idle, pushes the job to the bottom of the queue and only executes the job when the server is in idle mode.
* **Site Target [Group/Server].** Indicates whether the job needs to run on an SIS Group or a single SIS/Managed Configuration Item.
* **Target Machine.** Select the device(s) that the operation will target.
* **Credentials.** Sourced from the KeySafe, these provide the security context to be used for package deployment and execution.
* **Extra Credentials.** Optional credentials used as part of the functionality within the package.
* **Operation Parameters.** Once a package and a Run operation has been selected, any related parameters will be displayed. Mandatory fields are highlighted and hints may be provided in the input box.

## Job details
Once the job has been created, details will be displayed showing information relating to the job, including the status of the job. Monitoring, Console and Debug Logging are provided for displaying the job's progress and to aid with troubleshooting any failures.

![IT Automation Job Details](_books/itom-user-guide/jobs/images/it-automation-job-details.png)

* **Summary.** Shows the current status of the job and its name along with who created it and when.
* **Package Details.** Displays details of the deployment package and configured operation along with any parameters that were specified and the job timeout limit.
* **Target Information.** Provides details of the SIS server that will facilitate the job, the target machine, and the security keys used.
* **Execution Details.** Shows when the job was started and completed along with any result code.

### Monitor
The Monitor frame provides information relating to the execution of the job. The details shown will be dependent on the type of discovery or package that is being executed.

![Monitor IT Automation Job](_books/itom-user-guide/jobs/images/monitor-it-automation-job.png)

The above example shows that the process has started and provides an ID, which can be used to identify the task executing the package on the target machine. Depending on the package configuration, the monitor will specify more than the process ID. In the above case, the package is configured to execute an executable program as a specific user, using the Run As credentials. The first ID is for the process that triggers the package execution, which triggers another process to run an executable using the provided credentials.

### Console Output
All console output from the process will be displayed after this and will depend on the package contents and configuration. Once the job has been completed, if there are any output parameters, they are processed and displayed, and confirmation of the job's successful completion or failure will be output.

Once the job has completed, the Console Output and Debug Log frames become enabled. The Console Output contains only the output produced by the payload, including any error messages.

![IT Automation Console](_books/itom-user-guide/jobs/images/it-automation-console.png)

### Debug Log
In cases where the package may have failed or been completed incorrectly, you can view the debug log to see errors and other technical information.

![IT Automation Debug Log](_books/itom-user-guide/jobs/images/it-automation-debug.png)

The log provides one or more of three possible sections, depending on the job:

* **Full.** Full debug log information.
* **Standard.** Information log entries.
* **Problem.** Warning and error entries that may identify potential problems.

### Action buttons
The action buttons that you see depend on the status and type of job. 
* **Activate this job.** Enables a deferred job to be activated for processing.
* **Schedule.** Allows for a job to be configured to execute on a specific schedule.
* **Copy this job.** Copies the job's properties and allows for a new job to be created once edited.
* **Cancel.** When a job is canceled, its process will be sent a Close message, thus allowing the process to close itself and all child processes in an orderly fashion.
* **Abort.** Aborting a job causes the job to be forcefully terminated immediately, possibly causing child processes to be orphaned. Abort should only be used as a last resort.