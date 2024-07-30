# Runbooks
Orchestration is fulfilled via the creation of a Runbook, enabling different operations to be bound together within a business process to perform a complete end to end solution. Allowing for the standardization/automation of best practices that improve efficiency, reliability and reducing user error. As an example, the onboarding of a new user could require the following to be set-up / configured:

* AD User Account creation
* Mailbox Creation
* Forum / Wiki Access
* Software Installation
* Database Access rights

The above actions are most likely conditional based on information passed to the Runbook and logic provided by Hornbill's Powerful Business Process Workflow tool. Only features specific to Runbooks will be discussed and any differences that there may be; for further details, refer to the Business Process Designer documentation. One of the main omissions is the use of Stages and Checkpoints as they are not required for use within a Runbook Process.

## Runbooks List

![Runbook List](_books/itom-user-guide/runbooks/images/runbooks-list.png)

* **Runbook**<br>The name of the Runbook.
* **Category**<br>Runbook Category.
* **Created By**<br>The User that created the Runbook process.
* **Created On**<br>Runbook Process creation date.
* **Updated By**<br>The User that last updated the Rnbook process.
* **Published version**<br>Runbook published version number.
* **Active State**<br>Identifies Active or De-Activated Runbooks.
* **Action Buttons**<br>Enables actions to be executed on the adjacent Runbook.
    * ***Publish***<br>Open the Publishing Manager.
    * ***Copy***<br>Createa a new copy of the Runbook.
    * ***Rename***<br>Rename the Runbook.
    * ***Delete***<br>Delete the Runbook.
    * ***Invoke***<br>Execute the Runbook.

## Toolbar

![Runbook List](_books/itom-user-guide/runbooks/images/runbooks-toolbar.png)

* **Filter**<br>Free Text Filter on Runbook, Category & Created By.
* **Dropdown Filter**<br>Active State filter.
* **Search Button**<br>Searches process for a Set Value.
* **Manage Executed Processes**<br>Displays all executed processes, provides troubleshooting and process control features.
* **Create New**<br>Creates a new Runbook process.
* **Delete**<br>Delete selected Runbook(s).

## Runbook Workflow
One significant difference with the workflow, as used within Applications such as Service Manager, is the definition of input and output parameters. Runbook process can be called via an applications workflow, using a Runbook Process node where the process can set and use the parameters the same as for system nodes.

![Runbook List](_books/itom-user-guide/runbooks/images/runbook-workflow.png)

### Process Nodes
The following nodes are available for use within the Runbook processes and function mostly identically to how they work within the BPM Engine except for the parameter "Auto" and suspend features. We recommended that all parameters be manually entered or populated using variables and not The "Auto" feature, which relies on executing within the context of an application. Any nodes that can suspend the process will not be available for use within a Runbook, as they should be able to execute with no user interaction seamlessly.

* **Hornbill Automation**<br>Invoke Actions within a Hornbill Application or Core Feature.
* **Cloud Automation**<br>Interact with third-party systems via a Hornbill iBridge automation.
* **IT Automation**<br>Invoke an ITOM Package operation.
* **Decision**<br>Used to control the flow of a process based on the outcome of the previous node(s), with more complex logic possible via custom expressions using process variables. Each decision node allows for a maximum of three outcomes, where more than this is required, it is also possible to chain decision nodes with the use of a No Match outcome.
* **End**<br>Successfully terminate the process, allowing for values to be assigned, manually or via variables, to the output parameters as defined in the Runbook Processes settings.
* **Abort**<br>Abandons the process and sets the status to "Failed", allowing for a message to be manually supplied or sourced via a variable.
* **Start Parallel Processing**<br>Allows a process stage to invoke more than one stream of actions and for these to run in parallel. Adding this node will enable multiple process streams to be defined, and these will run independently until brought back together by the Finish Parallel Processing node. Examples of this would be a requirement for assigning tasks to different teams, but there is no dependency or need to complete one before the other can be created and invoked in parallel.
* **Finish Parallel Processing**<br>Use this node to bring together and finish the individual process lines initiated from a Start Parallel Processing node.

### Runbook Process Settings

![Runbook List](_books/itom-user-guide/runbooks/images/runbook-workflow-settings.png)

* **Input Parameters**<br>Parameters which can be used throughout the process.
* **Output Parameters**<br>Parameters which will be passed on to the calling process.
* **Category**<br>Allowing for categorisation & searching.
* **Description**<br>Allowing for searching.
* **Display Options**<br>Normal/Projector - providing a more high contrast viewing alternative.
* **Access Granted To**<br>Access can be granted based on Role, User or Group.

:::tip
IF the "Access Granted To" is set, the system will limit then the ability to run this particular Runbook to either specific users and those users who are members of the configured Groups
:::