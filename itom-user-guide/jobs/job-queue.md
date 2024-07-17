# Job Queue
The Job Queue provides a mechanism to create, view, and manage active and completed jobs. The current status and progress of a job can be monitored via the Monitor console. Once a Job has completed, The Console Output provides the sanitized output produced by the package or discover process. It is possible to Cancel a Job if required, and once a job has been canceled the status will be marked canceled.

When a Job completes successfully or fails a Debug Log will be available, which provides information that can be of use when troubleshooting issues. The output provided will depend on the package/discovery job that has been executed.

## Job Queue List
* **Job Id**<br>Job identification number.
* **Name**<br>Name provided for the job when created.
* **Type**<br>The type of Job, can be either Discovery or IT Automation.
* **Status**<br>Shows the current status of the Job.
* **Target**<br>Shows the name of the computer on which the job will run.
* **Child Jobs**<br>Shows if the Job has spawned any children.
* **Created On**<br>Shows the creation date/time for the Job.
* **Started On**<br>Displays the date/time the Job started execution.
* **Completed On**<br>Displays the date/time the Job completed execution.

## Job Queue Toolbar
* **Refresh**<br>A refresh of the list may be required to update Job-status or any new Jobs that have been executed.
* **Type**<br>Filter the list by Job Type.
    * ***All***<br>Lists all jobs.
    * ***Discovery***<br>List all Discovery jobs.
    * ***Package***<br>List all Packaged IT Automation jobs.
    * ***Asset Import***<br>List all Asset Import Jobs.
* **Run State**<br>Filter the list on Status using Status Groups.
    * ***Ready***<br>Defered, Waiting
    * ***Active***<br>Processing Output, Starting.
    * ***Canceling***<br>Canceled, Cancel Request.
    * ***Succeeded***<br>Success
    * ***Failed***<br>AWOL, Failed
    * ***Timed Out***<br>Timed Out, Expired
    * ***Halted***<br>Aborted, Canceled
* **Filter**<br>Free Text filter to search by Name, Operation or Target.
* **Activate**<br>Activate Selected Jobs
* **Cancel**<br>Cancel Selected Jobs
* **Delete**<br>Delete Selected Jobs
* **Create New**<br>Creates a new Discover or IT Automation Job

## Activate Selected Jobs
Enables all selected Deferred Jobs to be Activated for processing

## Cancel Selected Jobs
Where it is required for a Job to be Canceled, for example; maybe the job has stalled or is taking a large amount of time and resources. Canceling a Job will gracefully terminate all initial process(es) spawned by the job, on the target machine.

Once a Job has been started all process Id's are visible within the Job's Monitor. The following shows that a job was started using the "Run As" feature, and thus created three process IDs, The Package Execution process (EspSisExec.exe), The Elevated "Run As" Package Execution Process (EspSisExecRunAs.exe) and finally the package payload (in this example Dotter.exe).

The running process can also be identified using the above PIDs, on the target device by listing the device process list. On a Windows device, this can be achieved via the Task Manager or via the command line using tasklist.exe.

Clicking the Cancel button will be acknowledged, and the status set to "Canceling" and once the processes are terminated the Jobs status will be set to Canceled.

:::tip
In most cases just Canceling a job should suffice, however in cases where this option fails, an Abort option is available to force the termination, accessed via the Job's Details Action Buttons.
:::

## Delete Selected Jobs
A Job can only be deleted while its status is not one of the "Active" group, by the use of the delete button, after which the Job will be removed from the Job Queue list and will no longer be accessible.

<!-- https://wiki.hornbill.com/index.php?title=Job_Queue -->