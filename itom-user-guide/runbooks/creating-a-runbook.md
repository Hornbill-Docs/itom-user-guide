
# Creating a Runbook
Hornbill's ITOM Runbooks enables you to provide Orchestration by enabling more than one package operation to be executed as part of a process. Process logic can be applied to dictate whether an operation will be executed and the order of execution.

## Creating a Runbook Process
1. From the ITOM page, select `Runbooks`
1. Click the `Add New Runbook(+)` button
1. Enter a Name
1. The Runbook Process Designer will open.

    ![Runbook Process](/_books/itom-user-guide/runbooks/images/runbook-process.png)

## Building a Runbook Process
1. Select the connection line between the Start and End nodes
1. Right-click on the selected line and select “Add node between connected nodes”

    ![Node Menu](/_books/itom-user-guide/runbooks/images/runbook-node-menu.png)

1. Select IT Automation.
1. The new node will be added to the canvas with a warning icon to indicate that it requires setting up.

    ![IT Automation Node](/_books/itom-user-guide/runbooks/images/it-automation-node.png)

1. Hover over the IT Automation node, and click on the Cog icon to open the properties of this node.

    ![IT Automation Node](/_books/itom-user-guide/runbooks/images/it-automation-settings.png)

1. Enter Run Harry as the Display name
1. Click the Add Package button

    ![IT Automation Node](/_books/itom-user-guide/runbooks/images/package-selection.png)

1. Select Harry Hornbill
1. Confirm the Run Operation is set to Show Harry
1. Set Target Machine type to Machine, and select a Computer
1. Click Save draft button

## Publish a Runbook Process
1. Click the `Publishing Manager` button.

   ![IT Automation Node](/_books/itom-user-guide/runbooks/images/publish.png)

1. Click the `Publish` button
1. Click `Runbooks` from the breadcrumbs at the top of the page.

## Executing a Runbook Process
### Manual Execution
1. Locate the Runbook Entry on the Runbooks list
1. Click the `Invoke` action button

### Scheduled Execution
1. Navigate to (Home > ITOM > Job Scheduling)
1. Click the Create New button, and Select Runbook Schedule
1. Enter the following Schedule details:
    * Name: Harry Hornbill
    * Schedule: Run Once
    * Runbook: Run Harry
1. Set the following Operation Parameters to True:
1. Click Enable Schedule
1. Navigate to (Home > ITOM > Job Scheduling)
1. Wait for the Job schedule Time, and Click on the Job Name: Harry Hornbill
1. Click Job History
1. Confirm the Status of the Job