# Discovery job
With discovery jobs, you can find all devices operating within your organization.

You initiate the process of discovery through a designated SIS server, using one of the various discovery methods available. This crucial step requires the provision of Admin credentials through the secure Hornbill KeySafe, which must have been previously established. Once an IP address has been identified, the device's details are retrieved using advanced methods such as WMI via DCOM, WinRM, or SSH. The SIS server initiates a probe on the device’s operating system (OS) using various methods depending on the OS. No software needs to be uploaded to the device. The information retrieved is then used to mark the device as discovered, and stored in the inventory for future reference.

To ensure accuracy and completeness, an optional ping request can be sent to each device. If successful, the device will be marked as pingable, providing further confirmation of its presence on the network. For Unix/Linux devices, information is obtained through the use of SSH and local system tools, which may vary depending on the distribution being used. This comprehensive approach allows for a thorough gathering of data, including details about the device's hardware, operating system, components, installed software, and network-related information.

The retrieved data serves as a valuable source for importing assets into the Service Manager application, providing a seamless integration of information for efficient management. With this advanced discovery process, organizations can stay on top of their assets and ensure optimal performance and security.

## Topics covered
- [Creating a discovery job](#creating-a-discovery-job)
- [Job properties](#job-properties)
- [Job details](#job-details)

## Creating a discovery job
1. In the ITOM application, navigate to Job Queue.
1. Click **Create New** > **Discovery Job**.
1. Enter a name to identify the job.
1. Select a Site Target (SIS). This can be a single server or a group.
1. Select the required protocol.
1. Select the required discovery mode.
1. Select the priority.
1. Enter the relevant Discovery Mode settings and admin credentials.
1. Click **Create**.

![Create Discovery Job](/_books/itom-user-guide/jobs/images/create-discovery-job.png)

## Job properties
* **Name.** Identifies the discovery job.
* **Site Target [Group/Server].** Indicates whether the job needs to run on an SIS Group or a single SIS/Managed Configuration Item.
* **Protocol.** A device is identified as discovered once it can be accessed and its inventory retrieved. A protocol is needed so the SIS can access the device. Which protocol is needed depends on the OS and what is supported. In general, for Windows devices, WMI is used along with DCOM or WinRM; for Linux/Unix (including Apple Mac), Secure Shell (SSH) is used.
    * **Auto.** Will attempt to access the device using all of the provided protocols, in the following order: WinRM, DCOM, and SSH, using the first successful one.
    * **WinRM.** Provides secure and firewall-friendly communications to access the WMI. This feature is supported on Windows 2008R2 and later, and Windows 7 and later.
    * **DCOM.** Communication relies on RPC (remote procedure calls) and can be tricky to configure over firewalls. Widely supported on the Windows platform, this protocol is mainly used to access legacy devices.
    * **SSH.** Secure Shell is a network communication protocol that allows for remote connection between two computers to communicate and share data, commonly used but not exclusively by Linux/Unix (including Apple Mac) devices. The protocol can be used on Windows devices but may require additional software to be installed and configured.
* **Discovery Mode.** The [discovery mode](/itom-user-guide/jobs/discovery-job#discovery-modes) dictates the method that identifies devices on the network.
* **Priority.** Set the job's priority. The highest priority, Urgent, pushes the job to the top of the queue. The lowest priority, Idle, pushes the job to the bottom of the queue and only executes the job when the server is in idle mode.
* **Ping Check Settings.**
    * **Ping check discovered.** [Yes / No] Check that the discovered machine is pinged. If ICMP is disabled or firewalled, then select **No**, as this can cause the discovery to be significantly slower.
    * **Timeout.**
    * **Hop Count.**

### Discovery modes
Each mode will have specific settings that you set when creating a new discovery job. Each job can have only one discovery mode; if more than one mode is required, you must create a new job for each one.

#### Active Directory mode
This mode searches Active Directory to provide a list of Windows devices (servers, domain controllers, and workstations) from a defined starting point (search base) within the directory, and recurse through all domains, containers, and OUs.

* **Container.** This setting specifies the starting point (search base), within the directory tree. Enter the FQDN to specify the root of a domain. If specifying a container or OU, add a "/" and its name domain.local/Users.
* **Admin Credentials.** The account details created in the Hornbill KeySafe of type Username + Password. If not supplied, then the Windows NT Service Account used for the SIS will be used. In both cases, the account used must have the required Read permission to access Active Directory, as well as administrative rights to access the retrieved devices.

#### LDAP Server mode
This mode connects to a directory service that supports the LDAP protocol in order to extract a list of devices to be discovered. A recursive search is performed from the specified LDAP root retrieving resources with the attribute objectClass set to `computer`. Additional search criteria can be provided via the use of standard search strings.

* **LDAP Server.** The hostname, FQDN, or IP address of the server where the directory service is hosted.
* **LDAP Root Directory.** The distinguished name specifying the starting location from within the directory. If this field is left blank, the entire directory will be scanned.
* **LDAP Filter.** Standard LDAP search criteria.
* **LDAP Credentials.** Account details created in the Hornbill KeySafe of type Username + Password or LDAP authentication. If not supplied, then anonymous access will be attempted. The account used must have the required Read permission to access the directory.
* **Admin Credentials.** Account details created in the Hornbill KeySafe of type Username + Password. If not supplied, then the Windows NT Service Account used for the SIS will be used. In both cases, the account used must have the required Read permission to access Active Directory, and administrative rights to access the retrieved devices.

#### Manual List mode
This mode allows for one or more device names or addresses to be used by the discovery process. Entries can be in the form of any of the following:

* **Machine / IP / CIDR List.** One or more of the following (separated by spaces): FQDN, Hostname, IP, or CIDR list.

    ||Example|
    |-|-|
    |Machine (FQDN or Hostname)|computer01.acme.co.uk or computer01|
    |IP Address|Single IP Address x.x.x.x (192.168.1.1)<br>IP Range x.x.x.x-x (192.168.0.1-254) Provides a list 254 addresses (192.168.0.1 -> 192.168.0.254)<br>IP Range x.x.x.x-x.x (192.168.0.1-255.254) Provides a list 65534 addresses (192.168.0.1 -> 192.168.255.254)
    |CIDR|x.x.x.x/x (192.168.0.0/24) Provides a list 254 addresses (192.168.0.1 -> 192.168.0.254)

* **Admin Credentials.** Account details created in the Hornbill KeySafe of type Username + Password. If not supplied, then the Windows NT Service Account used for the SIS will be used. In both cases, the account used must have the required Read permission to access Active Directory, and administrative rights to access the retrieved devices.

#### Network Enumeration mode
This mode utilizes the Windows NT Computer Browser service to retrieve a list of devices actively connected to the network. For each job, only member devices from a single domain or workgroup can be returned; thus, a separate job will be required for each. It may be necessary to enable the Computer Browser service on at least one Windows computer. If so, we recommend that this is done on the server hosting the SIS. It may also be required to enable NetBIOS over TCP/IP on all the individual Windows computers. In order to discover Windows computers that are a member of a workgroup, at least one of the computers within the workgroup will also require the Computer Browser service to be enabled.

* **Domain.** The NetBIOS name given to the Active Directory domain or Windows workgroup.
* **Admin Credentials.** Account details created in the Hornbill KeySafe of type Username + Password. If not supplied, then the Windows NT Service Account used for the SIS will be used. In both cases, the account used must have the required Read permission to access Active Directory, and administrative rights to access the retrieved devices.

#### Browser Service List mode
This mode utilizes the Windows NT Computer Browser service to retrieve a list of devices actively connected to the network. For each job, only member devices from a single domain or workgroup can be returned; thus a separate job will be required for each. It may be necessary to enable the Computer Browser service on at least one Windows computer. If so, we recommend that this is done on the server hosting the SIS. It may also be required to enable NetBIOS over TCP/IP on all the individual Windows computers. In order to discover Windows computers that are a member of a workgroup, at least one of the computers within the workgroup will also require the Computer Browser service to be enabled.

* **Domain.** The NetBIOS name given to the Active Directory domain or Windows workgroup
* **Admin Credentials.** Account details created in the Hornbill KeySafe of type Username + Password. If not supplied, then the Windows NT Service Account used for the SIS will be used. In both cases, the account used must have the required Read permission to access Active Directory, and administrative rights to access the retrieved devices.

## Job details
Once a job is completed, information is displayed in the Monitor and Console Output, including debug logging that can help with troubleshooting failures.

* **Summary.** The current status of the job and its name, along with who created it and when.
* **Discovery Options.** Details of the options used by the discovery process. This information will differ depending on the discovery mode used.
* **Target Information.** Details of the SIS server that will facilitate the job, the target machine, and the credentials used.
* **Execution Details.** When the job was started and completed along with any result code.

### Execution log
The execution log provides information relating to the execution of the job. The details shown depend on the method of discovery used.

![Monitor Discovery Job](/_books/itom-user-guide/jobs/images/monitor-discovery-job.png)

The above example shows that discovery has started and has initiated two processes on the SIS server: a standalone (EspSiSExec.exe) and a payload (ESPSisDiscovery.exe).

The console output shows the process and confirmation of successful completion or failure.

### Console Output
The console output is accessible once the job has been completed and will contain only the output produced by the payload, including any error messages.

![Console Discovery Job](/_books/itom-user-guide/jobs/images/console-discovery-job.png)

### Debug Log
When the discovery may have failed or completed incorrectly, you can view the debug log to see errors and other technical information.

![Debug Discovery Job](/_books/itom-user-guide/jobs/images/debug-discovery-job.png)

The log provides one or more of three possible sections, depending on the job:

* **Full.** Full debug log information.
* **Standard.** Information log entries.
* **Problem.** Warning and error entries that may identify potential problems.