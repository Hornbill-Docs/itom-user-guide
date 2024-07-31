# Job Queue
Use the Job Queue to create, view, and manage active and completed jobs. You can check the current status and progress of a job in the Monitor console. Once a job has been completed, the Console Output provides the sanitized output produced by the package or discovery job.

When a job completes successfully or fails, you can view the debug log for information that can be of use when troubleshooting issues. The output provided will depend on the package/discovery job that has been executed.

## Job Queue list

![Job Queue List](_books/itom-user-guide/jobs/images/job-queue-list.png)

* **Job Id**<br>Job identification number.
* **Name**<br>The name provided for the job when created.
* **Type**<br>The type of job which can be either Discovery or IT Automation.
* **Status**<br>Shows the current status of the job.
* **Target**<br>Shows the name of the computer on which the job will run.
* **Child Jobs**<br>Shows whether the job has spawned any children.
* **Created On**<br>Shows the creation date/time for the job.
* **Started On**<br>Displays the date/time the job started execution.
* **Completed On**<br>Displays the date/time the job completed execution.

## Job Queue toolbar
* **Refresh**<br>A refresh of the list may be required to update the job status or any new jobs that have been executed.
* **Type**<br>Filter the list by job type.
    * ***All***<br>Lists all jobs.
    * ***Discovery***<br>List all Discovery jobs.
    * ***Package***<br>List all Packaged IT Automation jobs.
    * ***Asset Import***<br>List all Asset Import jobs.
* **Run State**<br>Filter the list on Status using Status Groups.
    * ***Ready***<br>Deferred, Waiting
    * ***Active***<br>Processing Output, Starting.
    * ***Canceling***<br>Canceled, Cancel Request.
    * ***Succeeded***<br>Success
    * ***Failed***<br>AWOL, Failed
    * ***Timed Out***<br>Timed Out, Expired
    * ***Halted***<br>Aborted, Canceled
* **Filter**<br>Free text filter to search by Name, Operation or Target.
* **Activate**<br>Activate selected jobs
* **Cancel**<br>Cancel selected jobs
* **Delete**<br>Delete selected jobs
* **Create New**<br>Creates a new Discover or IT Automation job

## Create New Jobs
From the Job Queue List, it is possible to create Ad-Hoc Discovery, IT Automation, and Asset Import jobs. These jobs will be added to the Queue and executed once a registered and available SIS server downloads the Job from the cloud for processing. Credentials may be required to execute Jobs and will require creation within the Hornbill KeySafe beforehand. When creating an IT Automation Job a user must be aware of the Package to use and the relevant configuration details. This information can be sourced from the ITOM Package Library.

### Credentials
These are required to execute jobs with the permissions and rights necessary to complete the task. Depending on the Job type, and Package used, one or more Credentials may need to be specified.

* **Admin Credentials**<br>Used when the Package is deployed to the Target Machine and must have administration rights on the Target.
* **Run As Credentials**<br>Once deployed, the Package will need to be executed, by default; this will use the security context of that provided by the Admin Credentials. In some scenarios, this may not suffice as alternative rights may be required. The Run As Credentials will be used to provide an additional Credential for this purpose.

    :::tip
    The Service Account used for the SIS that facilitates the execution of the Job is employed where no Credentials are specified. By default, the Local System account will not have the correct rights to deploy or execute any package on a computer other than the one that the SIS is installed on.
    :::

## Activate Selected Jobs
Enables all selected deferred jobs to be activated for processing.

## Cancel Selected Jobs
Sometimes a job needs to be canceled. For example, the job has stalled or is taking too much time and resources. Canceling a job  gracefully terminates all initial processes spawned by the job, on the target machine.

Once a job has been started, all process IDs are visible within the job's monitor. The following shows that a job was started using the *Run As* feature, and thus created three process IDs: the package execution process (EspSisExec.exe), the elevated *Run As* package execution process (EspSisExecRunAs.exe), and the package payload (in this example, Dotter.exe).

![Monitor Canceled Job](_books/itom-user-guide/jobs/images/monitor-canceled-jobs.png)

Another way to identify the running process is to use the above PIDs on the target device by listing the device process list. On a Windows device, you can do this in the Task Manager or via the command line using tasklist.exe.

![Tasklist](_books/itom-user-guide/jobs/images/canceled-job-tasklist.png)

Click the **Cancel** button to set the status to *Canceling*. Once the processes are terminated, the job's status will be set to *Canceled*.

![Cancel Request Sent](_books/itom-user-guide/jobs/images/cancel-request-sent.png)

:::tip
In most cases, just canceling a job should suffice. However, in cases where this option fails, an abort option is available to force the termination, accessed via the job's *Details* action buttons.
:::

## Delete Selected Jobs
You can delete a job only when its status is not one of the *Active* statuses. Click the *Delete* button to delete a job. The job will be removed from the Job Queue list and will no longer be accessible.

<!-- https://wiki.hornbill.com/index.php?title=Job_Queue -->