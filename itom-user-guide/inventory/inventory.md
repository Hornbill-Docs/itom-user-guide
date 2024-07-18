# Inventory
The Inventory Viewer provides an interface to organize discovered devices and categorize them as Managed / Un-Managed Devices, as well as removing them. Once marked as Managed, a device subscription is consumed for a minimum of 30 days, after which this or any other Un-managed device will be able to re-use it. Inventory details and the execution of IT Automation jobs are only available for Managed Devices.

Lists are a great way to organize and maintain managed devices within the viewer and provide a mechanism for IT Automation Job deployment to multiple targets.

## Inventory Toolbar
The Inventory toolbar allows actions to be executed on one or more inventory items as detailed below and provides various filtering and refresh options.

* **Refresh**<br>A refresh of the list may be required to display any new devices discovered while you are viewing the list.
* **Show**<br>
    * ***All Managed Inventory***<br>Show only the devices that categorized as Managed.
    * ***All Un-managed Inventory***<br>Show only those categorized as Un-managed.
    * ***Add Selected To a Managed List***<br>By selecting multiple devices in the list using the checkboxes, you can add these into an available Managed List.
    * ***Create List***<br>Create a new list for managing or grouping devices.
* **Free Text Filter**<br>Free Text filter to search by Name, Manufacturer, Model or Operating System.
* **Action Buttons**<br>Each Action applies to one or more selected devices in the Inventory List.
    * ***Toggle Managed Status***<br>Set Selected As Managed / Set Selected as Un-managed.
    * ***Add Selected to A Managed List***<br>This is only available for Managed CIs
    * ***Delete Device***<br>This will permanently remove the device from the list.

## Inventory List
The inventory list displays the discovered (Managed or Un-Managed) Inventory items and provides access to an items properties and Job Queue. User-defined lists are created and populated from here, and dynamic filtering is also available. Sort the list by clicking on the individual column headers, an indicator displayed next to the sort column stating the sort order as Ascending (AdminToolListHeaderAsc.png) or Descending (AdminToolListHeaderDesc.png). Select Multiple items from the list to execute actions on more than one item; alternatively, the dropdown button next to each item is used to perform actions for individual items.

* **Action**<br>Using this drop-down icon, you can select from several actions that you can apply against this individual inventory item.
* **Name**<br>Device hostname. Clicking on the hostname will display a detailed Properties list for this inventory item.
* **Manufacturer**<br>Shows the devices manufacturer.
* **Model**<br>Devices model details.
* **OS**<br>The devices installed Operating System.
* **Ping**<br>Displays "Green" if the device was able to respond to a ping request.
* **DNS**<br>Displays "Green" if the device was able to be identified by a DNS lookup.
* **Discovered On**<br>Shows the discovery date for the device.

## Device Properties
Clicking on the Device Name will display properties discovered for the selected item; the following information is available:

* Summary (Name, Discovered On, Ping, DNS)
* Manufacturer / Hardware (showing Model, Serial Number, CPU & Memory)
* Operating System
* Network
* Installed OS Options
* Installed Software (filterable)
* Job Queue
    Provides the same interface to that used within the main Job Queue, with the difference here being that only jobs for the selected item will be visible and able to be created. For further details on the functionality of this feature, refer to the Job Queue documentation:

:::tip
For Un-managed devices, only the Summary information is available.
:::

## Managed Lists
These lists provide a mechanism to allow for IT Automations or Runbook jobs execution across multiple devices. They are manually populated and contain managed devices, each of which can exist in various lists.

### Create a Managed List
1. Navigate to (Home > ITOM > Inventory Viewer)
1. From the Show filter Select + Create List
1. Enter a name for the List
1. The new list will now appear in the list of filters

### Adding Devices to a List
#### Multiple
1. From the Inventory View select two or more Managed Devices
2. Click the Add to Managed List MenuPlusWhite.png button:
3. The List is displayed showing the added entries

#### Individual
1. Locate a Managed Device
1. Click the dropdown and select +Add To Managed List

### Removing Devices from a List
#### Multiple
1. Select the required List
1. Click the checkbox next to each entry to be removed
1. Select Remove Selected From ... MenuMinusButtonWhite.png button
1. Click Yes on the Confirmation box; to remove devices from the list

#### Individual
1. From the Show dropdown, select a populated List
1. Locate a Managed Device
1. Click the dropdown and select +Remove From ...
1. Click Yes on the Confirmation box, to remove devices from the list