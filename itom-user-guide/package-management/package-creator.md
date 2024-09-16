# Package Creator
The Package Creator requires the DevOps subscription tier.

With the Package Creator, you can create user-defined packages for use on an instance. A package consists of a single info file (called Package Info) along with additional resource files where required. The info file contains all the details regarding operations and all parameters that may be necessary.

A form-based editor simplifies the uploading and organizing of resources. These resource files are used to provide or support a package's operations and can be a combination of one or more scripts, executables, and other supported file types.

In addition to uploading files, you can also create and edit various file types via a browser-based editor that supports syntax highlighting.

![Package Creator List](_books/itom-user-guide/package-management/images/package-list.png)

## Topics covered
* [Toolbar](/itom-user-guide/package-management/package-creator#toolbar)
* [Package list](/itom-user-guide/package-management/package-creator#package-list)
* [Package editor](/itom-user-guide/package-management/package-creator#package-editor)
* [Package information](/itom-user-guide/package-management/package-creator#package-information)
* [Package operations](/itom-user-guide/package-management/package-creator#package-operations)
* [Baselining and publishing](/itom-user-guide/package-management/package-creator#baselining-and-publishing)

## Toolbar
* **Refresh.** Click this to refresh the display.
* **Target OS.** The operating system on which the package was designed for execution.
    * Windows 32/64-bit
    * Apple macOS
    * Generic Linux
* **Purpose.** A dynamic list populated from the Purpose field of entries in the list.
* **Filter by package.** A free-text filter.
* **Add button (plus sign).** Click this to create an IT automation package.
* **Delete button (trash can).** Delete the selected package(s).

## Package list
* **Package Name.** A unique name given to the package.
* **Purpose.** A summary of the intended use of the package.
* **Target OS.** The operating system on which the package was designed for execution.
* **Published.** The last published version of the package.
* **Created On.** The date that the package was created.
* **Created By.** The account used to create the package.
* **Last Updated On.** The date the package was last updated.
* **Last Updated By.** The account last used to update the package.

**To create a new package:**
1. From the Package Creator list, click the `+` button.
1. Enter a name for the package.
1. Click **Create**.

**To open an existing package:**
1. Locate the package in the Package Creator list.
1. Click on the package name.

**To delete an individual package or multiple packages:**
1. From the Package Creator list, click the checkbox next to each package you want to delete.
1. Click **Delete**.

## Package editor
The package editor displays a list of resources used, one of which is the Package Info file created by the system. This file contains the configuration details that define the package's operations and how any additional resources are used. Selecting the file displays a form used to edit the details; it is also possible to edit the file in its raw XML format via the built-in editor. Additional resources such as scripts and data files can be created directly from within the interface via an editor. Administrators can upload binary files such as executables and Windows installer files.

### Package content toolbar

![Package Content](_books/itom-user-guide/package-management/images/package-content.png)


* **Upload.** Uploads files to the current folder.
* **New Folder.** Creates a new folder.
* **New File.** Creates a new file in the current folder.
* **Baseline.** Creates a new baseline of the current package.
* **Save.** Saves amended package details.

## Package information
The Package Info file is viewed and modified via a form, displayed by default when entering the editor or whenever the file is selected. The following details can be edited via the form excluding the Package ID and Name.

![Package Properties](_books/itom-user-guide/package-management/images/package-properties.png)

* **Package ID.** A GUID that uniquely identifies the package will be generated on creation.
* **Package.** The name of the package entered during creation.
* **Description.** A description of the package's content.
* **Purpose.** A summary of the intended use of the package.
* **Vendor ID.** This is defined by the creator of the package. (Hornbill packages will set to "Hornbill".)
* **Target OS.** The target operating system on which the package is designed to run.

Selecting the **XML View** button on the toolbar switches the form editor to a text editor via which an administrator can edit the file in its native XML format. This can be useful when making changes that can be tedious using the form view, such as generic modifications to packaging operations.

## Package operations
A package must contain one or more operations; each will perform an action that can be defined using one of a number of command types. The command type selected will depend on the operating system to target the package and the functionality required. Some operations will require files to be created or uploaded before they can be configured, executing a script. Other operations such as those that execute as a single command can be configured via the interface provided.

![Package Operations](_books/itom-user-guide/package-management/images/package-operations.png)

**To create an operation:**
1. Click the **Add Operation** button, located on the Package Operations section.
1. Enter a unique name for the operation.
1. Enter a description of the operation.
1. Select the command type.
1. Click **Add**.

:::note
The selected command type determines whether a command is entered or a file is selected. When a file is required, it must already have been created or uploaded to the package.
:::

### Operation properties
* **Operation.** A mandatory name used to select the package when creating a job.
* **Description.** This describes the functionality provided by the operation.
* **Command Type.** A list of supported command types.
* **Timeout.** The number of seconds before the operation times out, at which point the status of the job is set to Timed Out.
* **Options/Args.** The arguments that are passed to the specified command at runtime. The format required is dependent on the command type being used. The following are some typical examples:
    * **Powershell.** `parameter1 ... parameterx -Arg1 <value> -Arg2`
    * **Windows batch file.** `/O /A <value> parameter1 ... parameterx`
    * **Linux script.** `-arg1 <value> -arg2 --long-arg parameter1 ... parameterx`

### Input parameters
Input parameters are only required if the operation requires data to be passed to it. They allow for values to be dynamically applied at execution for use by the operation. Each parameter can be identified as required (mandatory) and given a specific data type used for basic validation. Parameters can be manually assigned or populated via variables generated within a Runbook, BPM, or Autotask process.

![Package Input Params](_books/itom-user-guide/package-management/images/package-operations-input.png)

* **Requirement dropdown.** Each parameter can be specified as Required or Optional.
* **Type dropdown.** Specifies which of the following data types that can be entered: String, Number, or Boolean. This will be used for basic validation when parameter values are entered.
* **Parameter name.** Identifies the parameter when adding it to the arguments/options list.
* **Default value.** Each parameter can be provided with a default value.
* **Hint.** Describes the parameter and is visible during data entry.
* **Action buttons.**
    * **Sensitivity.** A toggle that marks a parameter as sensitive (a struck-out eye icon). When toggled to sensitive, the parameter's value will not be shown during data entry.
    * **Delete.** Removes the parameter.

**To create a new parameter:**
1. From the Add Operation form, click **Add Parameter**.
1. From the Requirement dropdown, select **Optional** or **Required**.
1. From the Type dropdown, select the data type.
1. Enter the parameter name.
1. If required, enter a default value.
1. Enter the hint text.
1. Specify whether the parameter is sensitive.

### Adding parameters to Options/Args
For values to be passed to an operation command, a parameter is required in the Options/Args field. The ordering and format will depend on what is required by the target of the specified command type. Input parameters have the syntax of `{param.<parameter name>}` and are placed where the value is expected when the command is executed.

![Package Operations Params Selector](_books/itom-user-guide/package-management/images/package-operation-param-selector.png)

You enter parameters manually. However, if you type the letters 'pa', a list of all of the operation's input parameters is provided, from which you can select for easy entry. Entering any further characters will filter the list based on whether any entries contain the entered characters.

During the execution of the operation, if the parameter value is blank, nothing is output. This may not be the desired effect, as detailed in the following scenarios:
* The parameter is passed as a positional parameter and requires an empty string to be passed if blank. To ensure an empty string is passed when the value is blank, the parameter should be encapsulated within quotes: `"{param.ParamA}"`
* The parameter value is paired with an option such as `-option {param.ParamA}`. If the value of `{param.ParamA}` is blank, the option is not removed. You can fix this by encapsulating the option within the parameter definition like this: `{-option param.ParamA}`.

#### Possible supported combinations
|Format|Parameter Value|Output|
|-|-|-|
|&lt;option&gt; {param.name}|abcd|-option abcd|
|&lt;option&gt; {param.name}|&lt;empty string&gt;|-option|
|{&lt;option&gt; param.name}|abcd|-option abcd|
|{&lt;option&gt; param.name}|&lt;empty string&gt;|&lt;blank&gt;|

:::tip
The `option` can be any text and thus allow for all formats of options and arguments that may be required, such as `/O`, `-Output`, `--Out-file`, or even `start`. In order to specify this format, edit the parameter after it has been added, or type it in manually.
:::

### Output parameters
Output parameters allow output from the package operation to be accessed after an IT automation has been executed. When executed within a BPM process or Runbook, the process can access the output parameters via self-named variables enabling the values to be used as inputs to other nodes within the process. Similar to input parameters, each output parameter can be specified as required and each is provided with a data type.

![Package Output Params](_books/itom-user-guide/package-management/images/package-operations-output-params.png)

**To create a new parameter:**
1. In the Add Package Operation form, click **Add Parameter**.
* **Requirement.** Each parameter can be specified as Required or Optional. If a required parameter is not returned in the operation's output, the IT automation will return a failure after the package has been executed.
* **Type.** Specifies the data type that the parameter must be: String, Number, or Boolean. This is used for basic validation when parameter values are entered.
* **Parameter name.** Used to identify output parameters returned by the operation.
* **Default value.** Each parameter can be given a default value.

### Output parameters syntax
Output parameters are processed after the execution of an IT automation and are identified by the output using the following syntax:

`{{SISJobOutputParameterStart:<param-name>}}<value>{{SISJobOutputParameterEnd}}`

* **`<param-name>`** The name of the configured output parameter.
* **`<value>`** The value to store. One entry is required for each required parameter.

Providing the formatted output is relatively straightforward when the script or program is designed in-house. However, attempting to use a third-party script or program that is not modifiable can prove difficult. In these circumstances, there are still options available, as follows:
* Create a wrapper script and reformat the output to match the required syntax.
* Use the script's or program's return code to provide feedback.

Utilizing the return codes can be a quick and simple way to capture output parameter values that can be used logically within a process. The Options/Args field can specify input parameters for the command and contain the logic to deal with any return code. The following examples show what can be achieved for different command types:

#### Windows commands
|Command Type|Run Command|
|-|-|
|Command|cmd /c find|
|Options/Args|"{param.searchstring}" "C:\ProgramData\Hornbill\Site Integration Server\log\EspSisService.log" && echo {{SISJobOutputParameterStart:outcome}}OK {{SISJobOutputParameterEnd}} echo {{SISJobOutputParameterStart:outcome}}FAIL{{SISJobOutputParameterEnd}} |

#### Linux commands
|Command Type|Run Command|
|-|-|
|Command|grep|
|Options/Args|/var/log/syslog -e "{param.searchstring}"; error=$?; if [ $error == 0 ]; then echo "{{SISJobOutputParameterStart:outcome}}OK{{SISJobOutputParameterEnd}}"; else echo "{{SISJobOutputParameterStart:outcome}}FAIL{{SISJobOutputParameterEnd}}"; echo "{{SISJobOutputParameterStart:errors}}$error{{SISJobOutputParameterEnd}}"; fi|

#### Powershell commands
|Command Type|Run Command|
|-|-|
|Command|powershell -Command|
|Options/Args|"& { if(Select-String -Path 'C:\ProgramData\Hornbill\Site Integration Server\log\EspSisService.log' -Pattern '{param.searchstring}' -Quiet) {Write-Host '{{SISJobOutputParameterStart:outcome}}OK{{SISJobOutputParameterEnd}}'} else {Write-Host '{{SISJobOutputParameterStart:outcome}}FAIL{{SISJobOutputParameterEnd}}' }" }|

### Managing files

![Package File Editor](_books/itom-user-guide/package-management/images/package-file-editor.png)

In addition to being able to upload files for use by operations, you can also create files directly via the interface. The editor supports the following file types and also provides enhanced usability with the use of syntax highlighting.

|File Type|Description|
|-|-|
|.bat|Command Prompt Batch process files|
|.ps1|Powershell and Powershell Core scripts|
|.js|Javascript|
|.sh|Unix/Linux and macOS Shell script|
|.txt|Text format file|
|.json|JavaScript Object Notation file|
|.csv|Comma Separated Value file|

:::note
Be careful, as the following settings will affect the entire instance.

Some of the above files are restricted by default; these can be allowed by disabling the system setting `security.fileUploadRestriction.entity.fileAttachments.enable`.<br>Alternatively, you can remove the relevant extensions from the system setting `security.fileUploadRestriction.entity.fileAttachments.types`.
:::

**To upload a file:**

![Package File Upload](_books/itom-user-guide/package-management/images/package-content.png)

1. Click the **Upload File** button.
1. From the file list, select the file to upload.
1. Select the file to view in the editor pane.

**To create a new folder:**
1. Click the **Add New Folder** button.
1. Enter a name for the folder.

**To add a new file:**
1. Click the **Add New File** button.
1. Enter a name for the file.

The following actions are executed on individual files and folders; ensure that the correct file or folder is selected first from the file list. The menu options are context-sensitive and will only display the options relevant to the selected item.

![Package File Editor Toolbar](_books/itom-user-guide/package-management/images/package-file-editor-toolbar.png)

**To delete a file or folder:**
1. Select the file or folder to delete.
1. Click the **Delete** button.

**To download a file:**
1. Select the file to download.
1. Click the **Upload** button.
    
The file will appear in the browser's Downloads folder.

**To save a file:**<br>
The **Save** button is enabled when a file is loaded into the editor and its contents have changed. Clicking **Save** will save the changes and reset the button's state. Exiting the editor also prompts to save the file, with the option to save, cancel, or ignore the changes.

## Baselining and publishing
A baseline is a snapshot of a package's current state. A baseline is only available once the package is in a state where it is ready to be published (at least one package operation must exist).

![Package Baseline Version](_books/itom-user-guide/package-management/images/package-content-baseline-versions.png)

The draft version of a package is the only version that can be updated. Once the package is ready for release, the draft copy can be baselined, creating a new version. This latest version is then available for packaging and installation on the Installed Packages list.

To enable the baseline once the initial package has been created, you must highlight the Package Info file in the file list. Once clicked, a confirmation popup appears, and the dropdown next to the **Baseline** button will display a list of baselined versions.

To publish and install or to download a baselined version, select the relevant version from the list. The **Baseline** button will change to the package and install when clicked. Two options are provided:

![Package Draft Install](_books/itom-user-guide/package-management/images/package-content-draft-install.png)

* **Package and Install.** Build the package and add to the Install Packages list, overwriting any existing version.
* **Package and Download.** Build the package and download to the local computer.

The package details will be read-only. To change any details, select the draft version by clicking the **View Draft** button.

**To baseline and publish a new version of a package:**
1. Select the ITOM Package Creator.
1. From the list, select a package.
1. Click **Baseline**.
1. Select the **Baseline** button dropdown.
1. Select the last version.
1. Click **Package and Install**, and select **Package and Install**.
1. Use the breadcrumbs to go back to the Package Creator list.

The package should now appear in the list with the latest version shown. All subsequent jobs, including previously scheduled jobs, will now use the newly published version.