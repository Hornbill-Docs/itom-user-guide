# Job Scheduling
You can schedule discovery and automation jobs to execute in the future, once only or as a regular occurrence. A log is produced detailing information relating to the job being scheduled to be executed at the set time. In the Job History, you can view detailed information for each execution; there is one entry for each time the specific job is run. Drilling down into the Job History allows the Monitor, Console Output, and Debug Log to be viewed as per ad-hoc jobs discussed earlier.

## Toolbar
The Scheduled Jobs view provides a list of all past and future scheduled jobs. From here you can refresh, filter, delete, and create new scheduled jobs.

* **Refresh**<br>Refresh the list of scheduled jobs.
* **Type**<br>Filter the list by Discovery, Runbook, and IT Automation Jobs.
* **Status**<br>Filter the list by the available statuses including All, Disabled, Scheduled, Failed, and Completed.
* **Filter**<br>Free text search that filters the list based on name and tag.
* **Delete Selected**<br>Delete any scheduled job that has been selected in the list using the checkboxes.
* **Create New**<br>Create a new Discovery, Runbook, or IT Automation job.

:::tip
The view is generally refreshed when the state of the job changes, and can also be refreshed using the **Refresh** button at the top of the view. Where there are a large number of entries, paging is available.
:::

## Job Types
There are three types of scheduled Jobs:
* **Discovery Schedule**<br>Schedule a discovery, to locate devices and retrieve inventory details.
* **Runbook Schedule**<br>Schedule a Runbook process, to orchestrate IT Automations.
* **IT Automation Schedule**<br>Schedule an automation job to execute a single operation.

For each job, the following sections will need to be completed, and depending on the type of job one of the following group of settings will appear and also required completion: Discovery, IT Automation or Runbook.

### Scheduled Job
* **Name**<br>A Scheduled Job must be given a name, which does not have to be unique.
* **Tag**<br>An optional Tag can be added which can help when filtering the Scheduled Job list.

### Schedule
For each schedule, a Time Zone (Default is GMT) can be specified and the given start date and time. The following options are available:

* **Run Once**<br>These Jobs are executed once at the scheduled time and will stay in the Job scheduling list with the status "Waiting" and once finished either "Completed" or "Failed". The scheduled date can be selected via the calendar control and the time from the drop-down buttons.
* **Run Daily**<br>A Job can be run every day of the week at a particular time or for particular days in the week. It is also possible to specify that the schedule be executed x number of times (10 by default). Setting the option to "-1" enables the schedule never to expire.
* **Run Monthly**<br>Monthly jobs can are scheduled to run on a particular date and then on the same day and time every month or particular months in the year.
* **Run Every Period**<br>This schedule allows for jobs to be executed every (n) minute(s) on specific weekdays in specific months.

:::tip
Except for Run Once, each Job will be run a configurable number of times after which the scheduled Job will stop. If you want to run the Job indefinitely, you will need to change the default value of 10 to -1
:::

### Discovery Settings
* **Site Target [Group/Server]**<br>whether the job needs to run on an SIS Group or a single SIS/Managed CI.
* **Protocol**<br>A device is identified as discovered once it can be accessed and its inventory retrieved. This is achieved by probing its Operating System (OS) using various methods depending on the device's Operating System. The probe will be initiated from the SIS server and does not require any software to be uploaded to the device. To achieve this, a protocol will be required for the SIS to access the device. Which protocol will depend on the OS and what is supported, in general for Windows devices WMI is used along with DCOM or WinRM, and for Linux / Unix (inc Apple Mac) Secure Shell (SSH) is used.
* **Discovery Mode**<br>The Discover Mode dictates the method that identifies devices on the Network. Each mode will have specific settings; these will be visible in the Discover Mode Settings section. It is only possible to have a single mode per Job, if more than one is required a new Job will need to be created for each one.
* **Priority**<br>Set the Jobs Priority which ranges from Urgent - Execute the Job as soon as possible, pushing the Job to the top of the queue to Only execute the Job when the server is in idle mode, and will also push the Job to the bottom of the queue.
* **Ping Check Settings**<br>
    * ***Ping check Discovered***<br>[Yes / No] Check that the discovered machine is pinged - if ICMP is disabled or firewalled, then select "No", as this can cause the discovery to be significantly slower.
    * ***Timeout***<br>
    * ***Hop Count***<br>

### IT Automation Settings
* **Package**<br>Package used to provide the IT Automation payload.
* **Operation**<br>Operation to perform using the package.
* **Priority**<br>Set the Jobs Priority which ranges from Urgent - Execute the Job as soon as possible, pushing the Job to the top of the queue to Only execute the Job when the server is in idle mode, and will also push the Job to the bottom of the queue.
* **Site Target**<br>Specify the SIS Server or Group that will facilitate the Automation Job.
* **Target Machine**<br>Select the Device(s) that the Operation will target.
* **Credentials**<br>Sourced from the KeySafe, provides the security context to be used for package deployment and execution.
* **Extra Credentials**<br>Optional credentials used as part of the functionality within the package.
* **Operation Parameters**<br>Once a package and a Run Operation has been selected, any related parameters will be displayed; mandatory fields are highlighted and hints may be provided in the input box.

### Runbook Settings
* **Runbook**<br>Name of the Runbook to execute.
* **Input Parameters**<br>Parameters appear once a Runbook has been selected, mandatory fields are highlighted and hints may be provided in the field box.

## Log
This view provides a list of logs for the selected job, including the Run ID, Log creation Timestamp and Status. This view is only available once the first scheduled job has been executed.

A log entry will be created for each time the scheduled job is triggered and placed on the job queue. Clicking on the Run ID button i.e. [View Log 123] will reveal the log entry details. The details shown will differ dependant on the type of job that is scheduled and whether it succeeded or failed. All entries will contain a <jobId> tag which includes the ID of the Job placed on the queue. The ID can is used to identify a listing on the Job History list or the Job Queue, providing access to the Job Details, Monitoring, Console and Logs.

The following are some examples of successful and error log entries.

### IT Automation
Scheduled XMLMC call success:
```
<?xml version="1.0" encoding="utf-8" ?>
<methodCallResult status="ok">
	<params>
		<job>
			<jobId>447</jobId>
			<computer>computer:EXCH2K16</computer>
			<sisTarget>sis:TEST</sisTarget>
			<childJobCount>0</childJobCount>
		</job>
	</params>
</methodCallResult>
```

### Successful Discovery
Scheduled XMLMC call success:
```
<?xml version="1.0" encoding="utf-8" ?>
<methodCallResult status="ok">
	<params>
		<jobId>349</jobId>
	</params>
</methodCallResult>
```

### Failed Discovery
Scheduled XMLMC call failed:

```
<?xml version="1.0" encoding="utf-8" ?>
<methodCallResult status="fail">
	<state>
		<code>0203</code>
		<service>automation</service>
		<operation>sisRunDiscoveryJob</operation>
		<error>Non-digit characters found in the element <ldapCredentials>, the expected data type is 'unsignedInt'. The value was [] at location '/methodCall/params/options/ldapCredentials'</error>
	</state>
</methodCallResult>
```

## Job History
The Job History provides a similar list to that used for the Job Queue, minus details of the existence of child Jobs. Like the Log, it contains an entry for each execution of the scheduled job. Here it is possible to access the Job execution in the same way as can be achieved via the Job Queue where these jobs will also be visible.

It is not possible to Delete a Job while the status is in a "Running" state and or Run if in a "Deferred" state. Clicking on the job name will display the details of the Job identically to that seen via the Job Queue.