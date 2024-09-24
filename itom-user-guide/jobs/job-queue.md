# Job Queue
Use the Job Queue to create, view, and manage active and completed jobs. You can check the current status and progress of a job in the Monitor console. Once a job has been completed, the Console Output provides the sanitized output produced by the package or discovery job.

When a job completes successfully or fails, you can view the debug log for information that can be of use when troubleshooting issues. The output provided will depend on the package or discovery job that has been executed.

## Topics covered
- [Job Queue list](/job-queue-list)
- [Job Queue toolbar](/job-queue-toolbar)
- [Creating new jobs](/creating-new-jobs)
- [Activating, canceling, and deleting jobs](/activating-canceling-and-deleting-jobs)

## Job Queue list

![Job Queue List](_books/itom-user-guide/jobs/images/job-queue-list.png)

* **Job Id.** The job identification number.
* **Name.** The name provided for the job when created.
* **Type.** The type of job, either Discovery or IT Automation.
* **Status.** The current status of the job.
* **Target.** The name of the computer on which the job will run.
* **Child Jobs.** Shows whether the job has spawned any children.
* **Created On.** The creation date and time for the job.
* **Started On.** The date and time the job started execution.
* **Completed On.** The date and time the job completed execution.

## Job Queue toolbar
* **Refresh.** Refresh the list to update the job status of any new jobs that have been executed.
* **Type.** Filter the list by job type:
    * **All.** Lists all jobs.
    * **Discovery.** Lists all Discovery jobs.
    * **Package.** Lists all Packaged IT Automation jobs.
    * **Asset Import.** Lists all Asset Import jobs.
* **Run State.** Filter the list on Status using the following status groups:
    * **Ready.** Deferred, Waiting.
    * **Active.** Processing Output, Starting.
    * **Canceling.** Canceled, Cancel Request.
    * **Succeeded.** Success.
    * **Failed.** AWOL, Failed.
    * **Timed Out.** Timed Out, Expired.
    * **Halted.** Aborted, Canceled.
* **Filter.** A free-text filter to search by Name, Operation, or Target.
* **Activate.** Click to activate selected jobs.
* **Cancel.** Click to cancel selected jobs.
* **Delete.** Click to delete selected jobs.
* **Create New.** Click to create a new Discovery or IT Automation job.

## Creating new jobs
From the Job Queue list, you can create Discovery, IT Automation, and Asset Import jobs. These jobs will be added to the queue and executed once a registered and available SIS server downloads the job from the cloud for processing. Credentials may be required to execute jobs and will require creation within the [Hornbill KeySafe](/esp-config/security/keysafe) beforehand.

When creating an IT Automation job, you must know the package to use and the relevant configuration details. You can find this information in the [ITOM Package Reference](/itom-packages/welcome).

### Credentials
Credentials are required to execute jobs with the permissions and rights necessary to complete the task. Depending on the job type and the package used, one or more credentials may need to be specified.

* **Admin credentials.** Used when the package is deployed to the target machine and must have administration rights on the target.
* **Run As credentials.** Once deployed, the package will need to be executed. By default, this will use the security context of that provided by the Admin credentials. In some scenarios, alternative rights may also be required; it is the Run As credentials that will be used to provide an additional credential for this purpose.

    :::tip
    When no credentials are specified, the Service account used for the SIS that facilitates the execution of the job is employed. By default, the local System account will not have the correct rights to deploy or execute any package on a computer other than the one that the SIS is installed on.
    :::

## Activating, canceling, and deleting jobs

Near the **Create New** button, there are three action buttons you can use to activate, cancel, and delete jobs. To take these actions on one or more jobs, select each job by clicking its checkbox next to its Job ID.

### Activate Selected Jobs Now
Click this button to enable all selected deferred jobs to be activated for processing.

### Cancel Selected Jobs
Sometimes a job needs to be canceled. For example, the job has stalled or is taking too much time and resources. Canceling a job  gracefully terminates all initial processes spawned on the target machine by the job.

Once a job has been started, all process IDs are visible within the job's monitor. The following shows that a job was started using the *Run As* feature, and thus created three process IDs: the package execution process (EspSisExec.exe), the elevated *Run As* package execution process (EspSisExecRunAs.exe), and the package payload (in this example, Dotter.exe).

![Tasklist](_books/itom-user-guide/jobs/images/canceled-job-tasklist.png)

Another way to identify the running process is to use the above process IDs on the target device by listing the device process list. On a Windows device, you can do this in the Task Manager or via the command line using tasklist.exe.

![Monitor Canceled Job](_books/itom-user-guide/jobs/images/monitor-canceled-jobs.png)

Click the **Cancel** button to set the status to *Canceling*. Once the processes are terminated, the job's status will be set to *Canceled*.

![Cancel Request Sent](_books/itom-user-guide/jobs/images/cancel-request-sent.png)

:::tip
In most cases, just canceling a job should suffice. However, in cases where this option fails, an abort option is available to force the termination, accessed via the job's **Details** action buttons.
:::

### Delete Selected Jobs
You can delete a job only when its status is not one of the Active statuses (*Processing Output* or *Starting*). To delete a job, click the **Delete** button. The job will be removed from the Job Queue list and will no longer be accessible.

<!-- https://wiki.hornbill.com/index.php?title=Job_Queue -->