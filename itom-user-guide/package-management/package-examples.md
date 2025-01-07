# Package Examples
The following are some examples from the Hornbill Package Library, detailing there use for IT Automation. Packages can be utilised from within the ITOM job queue and Scheduler, as well as being accessible from within ITOM Runbooks and the Hornbill BPM tool. Additional packages are available and accessed via the ITOM Package Library.

### Windows Target Device Execution Requirements
* These packages requires the installation of the Active Directory PowerShell module on the target machine executing the scripts (the correct Remote Server Administration Tools (RSAT) package for your OS version). See Remote Server Administration Tool for further information.
* If the script execution policy on the target machine executing the operations has the Execution Policy set to Restricted, then this will need to be updated to something less restrictive. Packaged Powershell scripts are currently not signed; the recommendation is to set the execution policy to Remote Signed. See the PowerShell Documentation for more information.

## Acticve Directory User Management
The Active Directory User Management package for Hornbill's IT Operations Management (ITOM) contains several administrative operations that perform actions on User objects within your on-premises Active Directory domains.

### Create User
PackageADCreateUserOptionsBlur.png
Creates a user at the specified path, with the option to set various additional parameters. This operation provides the ability to create a new AD User account within a domain.

1. Navigate to (Home > ITOM > Job Queue)
1. Click the Create New button, and select IT Automation
1. Enter Name: Create New User : ITOM User One
1. Click the Installed Packages button
1. Select private:hornbill > Managing Active Directory Users > Active Directory User Management (Version x)
1. Click Apply
1. Set the Folowing Setiings and Credentials:
    * Run Operation : Create
    * Site Target : Server and select an Instance
    * Target Device : Inventory and select a Device
    * Admin Credentials : Network Admin
1. Set the following Operation Paramenters
    * Given Name : ITOM
    * Surname : User One    
    * SamAccountName : ITOMUser1
    * Path : CN=Users, DC=hornbill, DC=qa
    * AccountPassword : Passw0rd
    * Display Name ; User One, ITOM
    * Name : ITOM User One
1. Click `Create`

###  Reset Password
Forces a password reset for an Active Directory account using the new provided password.

1. Navigate to (Home > ITOM > Job Queue)
1. Click the Create New button, and select IT Automation
1. Enter Name: Reset User Password : ITOM User One
1. Click the Installed Packages button
1. Select private:hornbill > Managing Active Directory Users > Active Directory User Management (Version x)
1. Click `Apply`
1. Set the Folowing Setiings and Credentials:
    * Run Operation : Reset Password
    * Site Target : Server and select an Instance
    * Target Device : Inventory and select a Device
    * Admin Credentials : Network Admin
1. Set the following Operation Paramenters
    * UserIdentity : ITOMUser1
    * Password: Passw0rd1234
1. Click `Create`

## Active Directory Groups
### Create Group
Creates a Distribution or Security Group at the specified path, with the option to set various additional parameters.

1. Navigate to (Home > ITOM > Job Queue)
1. Click the Create New button, and select IT Automation
1. Enter Name: Create Security Group : Test Group
1. Click the Installed Packages button
1. Select private:hornbill& gt; Managing Active Directory Group Memberships gt; Active Directory Group Management (Version x)
1. Click Apply
1. Set the Folowing Settings and Credentials:
    * Run Operation : Create
    * Site Target : Server and select an Instance
    * Target Device : Inventory and select a Device
    * Admin Credentials : Network Admin
1. Set the following Operation Paramenters
    * Name: Test Group
    * SamAccountName: TestGroup
    * DisplayNAme: Test Group
    * Path: CN=Users,DC=hornbill,DC=qa
    * GroupCategory: Security
    * GroupScope: DomainLocal
    * Description: ITOM Testing Group
1. Click `Create`

### Add User
Add an existing Active Directory Account to an AD Group.

1. Navigate to (Home > ITOM > Job Queue)
1. Click the Create New button, and select IT Automation
1. Enter Name: Add User to Test Group
1. Click the Installed Packages button
1. Select private:hornbill& gt; Managing Active Directory Group Memberships gt; Active Directory Group Management (Version x)
1. Click `Apply`
1. Set the Folowing Setiings and Credentials:
    * Run Operation : Add User
    * Site Target : Server and select an Instance
    * Target Device : Inventory and select a Device
    * Admin Credentials : Network Admin
1. Set the following Operation Paramenters
    * MemberIdentity: CN=ITOM User One,CN=Users,DC=hornbill,DC=qa
    * GroupIdentity: CN=Test Group,CN=Users,DC=hornbill,DC=qa
1. Click `Create`