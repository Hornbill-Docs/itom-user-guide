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

