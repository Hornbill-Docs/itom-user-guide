# Package Creator
The Package Creator allows for the creation of user-defined Packages for use on an instance. A Package consists of a single Package Info file and with additional resource files where required. The info file contains all the details regarding operations and all parameters that may be necessary. Although it is possible to create a Package manually, a form-based editor is provided to simplify uploading and organizing resources. These files are used to provide or support a package's operations a can be a combination of one or more scripts, executables and other supported filetypes. In addition to uploading files, an interface is also provided to create and edit various file types via a browser-based editor that supports syntax highlighting.

## Toolbar
* **Refresh**<br>
* **Target OS**<br>Operating System that the package was designed for execution.
    * Windows 32/64-bit
    * Apple macOS
    * Generic Linux
* **Purpose**<br>Dynamic list populated from the Purpose field of entriies in the list.
* **Filter by package**<br>Free text filter on Package.
* **Create a Package**<br>Create an IT Automation Package.
* **Delete**<br>Delete selected Package(s).

## Package List
* **Package**<br>Unique name given to the Package.
* **Purpose**<br>Summary of the intended use of the package.
* **Target OS**<br>Operating System that the package was designed for execution.
* **Published**<br>Late Published version of the packacge.
* **Created On**<br>Date that the package was created.
* **Created By**<br>The account used to create the package.
* **Last Updated On**<br>Date the package was last updated.
* **Last Updated By**<br>The account last used to update the package.

### Create a New Package
1. From the Package Creator list, click the `+` button.
1. Enter a new Package Name.
1. Click `Create`.

### Open an Existing Package
1. Locate the Package in the Package Creator list.
1. Click on the Package name.

### Delete a Package
1. From the Package Creator list click the tick box next to each package to delete.
1. Click the delete button.

## Package Editor
The package editor displays a list of resources used, one of which is the Package Info file created by the system. This file contains the configuration details that define the packages operations and how any additional resources are used. Selecting the file displays a form used to edit the details; it is also possible to edit the file in its raw XML format via the built-in editor. Additional resources such as scripts, data files can be created directly from within the interface via an editor, administrators can upload binary files such as executables and windows installer files.

### Package Content Toolbar
* **Upload**<br>Uploads files to the current folder.
* **New Folder**<br>Creates a new Folder.
* **New File**<br>Creates a new file in the current folder.
* **Baseline**<br>Creates a new baseline of the current package.
* **Save**<br>Saves amended package details.

## Package Information
The Package Info file is viewed and modified via a form, displayed by default when entering the editor or whenever the file is selected. The following details can be edited via the form excluding the Package ID and Name:
* **Package ID**<br>A GUID that uniquely identifies the package will be generated on creation.
* **Package**<br>The name of the package entered during creation.
* **Description**<br>Description of the packages content.
* **Purpose**<br>Summary of the intended use of the package.
* **Vendor ID**<br>Defined by the creator of the package (Hornbill packages will set to "Hornbill").
* **Target OS**<br>Specifies the target operating system that the package is designed to run on.

Selecting the XML View button on the toolbar switches the form editor to a text editor where an administrator can edit the file in its native XML format. This can be useful when making changes that can be quite tedious using the form view, such as generic modifications to packaging operations.

## Package Operations
A package must contain one or more operations; each will perform an action that can be defined using one of a number of the command types. The Comand Type selected will depend on the Operating System to target the package and the functionality required. Some operations will require files to be created or uploaded before they can be configured, executing a script. Other operations such as those that execute as a single command can be configured via the interface provided.

### Creating an Operation
1. Click the Add Operation button, located on the Package Operations section.
1. Enter a unique Operation name.
1. Enter a Description of the operation.
1. Select the Command Type.
1. Click Add.

:::tip
The selected Type determines whether a command is entered or a file is selected, where a file is required, it must already have been created or uploaded to the package.
:::

### Operation Properties
* **Operation**<br>Mandatory Name used to select the package when creating a Job.
* **Description**<br>Describes the functionality provided by the operation.
* **Command Type**<br>Provides a list of supported command types.
* **Timeout**<br>Number of seconds before the operation times out, and setting the status of the Job to Timed Out.
* **Options/Args**<br>Specifies arguments that are passed to the specified command at runtime. The format required is dependant on the Command Type being used, below are some typical examples:
    * ***Powershell***<br>parameter1 ... parameterx -Arg1 <value> -Arg2
    * ***Windows batch file***<br>/O /A <value> parameter1 ... parameterx
    * ***Linux Script<br>***-arg1 <value> -arg2 --long-arg parameter1 ... parameterx

### Input Parameters
Input parameters are only required if the operation requires data to be passed to it. They allow for values to be dynamically applied at execution for use by the operation. Each parameter can be identified as required (mandatory) and given a specific data type used for basic validation. Parameters can be manually assigned or populated via variables generated within a Runbook, BPM or Autotask process.

To create a new parameter, from the Add Operation form:

1. Click the Add Parameter button
1. Select Optional or Required from the drop-down
1. Set the Data type from the drop-down
1. Enter the parameter Name
1. If required, enter a Default value
1. Enter the Hint text
1. Specify if the parameter is sensitive

* **Requirement**<br>Each parameter can be specified as Required or Optional.
* **Type**<br>Specifys one of the following data types that can be entered: String, Number or Boolean. This will be used for basic validation when parameter values are entered.
* **Parameter name**<br>Used to identify the parameter when adding it to the arguments/options list.
* **Default value**<br>Each parameter can be provided with default value.
* **Hint**<br>Describes the parameter and is visible during data entry.
* **Actions**<br>Action buttons.
    * ***Sensitivety***<br>A Toggle that marks a parameter as sensitive (struck out eye) and thus will not show its value during data entry.
    * ***Delete***<br>Removes the parameter.