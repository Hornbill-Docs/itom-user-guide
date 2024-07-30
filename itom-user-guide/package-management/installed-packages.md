# Installed Packages
Provides the ability to view and manage installed packages, including the ability to install / update packages via the Package Library and manually upload them. Packages that Hornbill provides are published to the package library and will be fully supported and maintained.

![Installed Package List](_books/itom-user-guide/package-management/images/installed-package-list.png)

## Packages Tool Bar
* **Refresh**<br>A refresh of the list may be required to display any new devices that were discovered while you are viewing the list.
* **Target OS**<br>Filters the Package list based on the Target Operating System.
* **Vendor**<br>Selecting on any of these will filter the list by the selected Vendor. The content of this list will depend on the uploaded/installed packages. Packages that have been supplied by Hornbill will have the vendor ID of "private:Hornbill".
* **Purpose**<br>The Purpose Filter options like the Vendor will depend on uploaded/installed packages as the Vendor will have defined the purpose. Some examples might be; Managing Active Directory Groups, or Hyper-V Virtual Machine Management.
* **Library**<br>Open the Package Library for Package Installation and Updating.
* **Upload**<br>Upload and install a package.
* **Remove**<br>Remove selected packages.

## Packages List
Displays the list of all installed packages.

* **Package Name**<br>The Name of the Installed Package.
* **Status**<br>Shows the current status of the package.
* **Vendor**<br>The name of the Organization that created the package.
* **Purpose**<br>Provides a summary of the package's use, such as Active Directory Group Memberships or User admin.
* **Target OS**<br>The Operating System that the package targets.
* **Version**<br>Displays the package's Version number.
* **Imported On**<br>Shows the date that the package was uploaded or Installed via the Package Library.
* **Imported By**<br>Display the user that Installed / Uploaded the package.

:::tip
Hovering over the Information icon at the beginning of the package list entry provides a more detailed description.
:::

## Upload a Package
Packages can be provided externally, possibly from third-party vendors or via consultancy; they will need to be uploaded to an instance to use these packages. A valid package will have an extension of .pkg and is uploaded and installed via the Upload button.

## Remove a Package
An administrator can remove packages by selecting one or more packages from the list and clicking on the Remove button. Once removed, the package will no longer be available for use by any new or existing IT Automation job.

:::tip
All scheduled jobs utilizing the package will fail once the Job executes, the failure will appear within the Jobs Log. A failure message will also appear when opening a scheduled Job that uses the package.
:::