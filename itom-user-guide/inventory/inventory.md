# Inventory
In Inventory, you can organize discovered devices, categorize them as managed or unmanaged, and remove them.

Only managed devices can be used a targets for a job. Likewise, inventory details are only available for managed devices. 

When a device is discovered, it is initially marked as unmanaged. You can then manually mark the device as managed. 

Once a device has had a job run against it, a subscription begins and it is not possible to mark the device as unmanaged for 30 days. This 30-day period resets every time a subsequent job is run against that device. Once the 30-day period is over, the same device or any other device can reuse the subscription.

## Topics covered
* [Inventory toolbar](/itom-user-guide/inventory/inventory#inventory-toolbar)
* [Inventory list](/itom-user-guide/inventory/inventory#inventory-list)
* [Device properties](/itom-user-guide/inventory/inventory#device-properties)
* [Managed lists](/itom-user-guide/inventory/inventory#managed-lists)

## Inventory toolbar
The Inventory toolbar allows actions to be executed on one or more inventory items as detailed below and provides various filtering and refresh options.

* **Refresh.** Click this to refresh the display in case any new devices are discovered while you are viewing the list.
* **Show.**
    * **All Managed Inventory.** Show only the devices that are categorized as Managed.
    * **All Unmanaged Inventory.** Show only those categorized as Unmanaged.
    * **Add Selected To a Managed List.** By selecting multiple devices in the list using the checkboxes, you can add these into an available Managed List.
    * **Create List.** Create a new list for managing or grouping devices.
* **Free-text filter.** Search by name, manufacturer, model, or operating system.
* **Action buttons.** Each action applies to one or more selected devices in the inventory list.
    * **Toggle Managed Status.** Toggle between Selected As Managed and Selected as Unmanaged.
    * **Add Selected to A Managed List.** This is only available for Managed CIs.
    * **Delete Device.** This permanently removes the device from the list.

## Inventory list
The inventory list displays the discovered (managed and unmanaged) inventory items and provides access to each item's properties and Job Queue.

User-defined lists are created and populated from here, and dynamic filtering is also available. Sort the list by clicking on the individual column headers; an indicator displayed next to the sort column states the sort order as ascending or descending. 

Select multiple items from the list to execute actions on more than one item. To execute actions on individual items, use the dropdown button next to each item.

* **Action.** Use this dropdown to select from several actions that you can apply against this individual inventory item.
* **Name.** Device hostname. Click on the hostname to display detailed properties for this inventory item.
* **Manufacturer.** Shows the device's manufacturer.
* **Model.** Shows the device's model details.
* **OS.** The device's installed operating system.
* **Ping.** Displays green if the device was able to respond to a ping request.
* **DNS.** Displays green if the device was able to be identified by a DNS lookup.
* **Discovered On.** Shows the discovery date for the device.

## Device properties
Click on the device name to display properties discovered for the selected item. The following information is available:

![Device Properties](/_books/itom-user-guide/inventory/images/device-properties.png)

* **Summary.** Name, Discovered On, Ping, and DNS.
* **Manufacturer / Hardware.** Model, Serial Number, CPU, and Memory.
* **Operating Software.**
* **Network.**
* **Installed OS Options.**
* **Installed Software.** This is filterable.
* **Job Queue.** This provides the same interface as that used within the main Job Queue, with the difference here being that only jobs for the selected item are visible and able to be created. For further details on the functionality of this feature, see [Job Queue](/itom-user-guide/jobs/job-queue).

:::note
For unmanaged devices, only the Summary information is available.
:::

## Managed lists
Managed lists provide a mechanism to allow for IT automations or runbook-jobs execution across multiple devices. They are manually populated and contain managed devices, each of which can exist in various lists.

**To create a managed list:**
1. In the left menu bar, click the ITOM icon and under *Inventory*, click **Managed**.
1. From the Show filter, click the **All Managed Inventory** dropdown and then **+ Create List**.
1. Enter a name for the list and then click **Apply**.

The new list will now appear in the list of filters.

**To add multiple devices to a list:**
1. In the left menu bar, click the ITOM icon and under *Inventory*, click **Managed**.
1. From the list of managed devices, click the checkboxes to select two or more.
1. Click the white plus-sign button.

The list is displayed showing the added entries.

**To add an individual device to a list:**
1. Locate a managed device.
1. Click the down-arrow dropdown to the left of its name and select **+Add To Managed List**.

**To remove multiple devices from a list:**
1. Select the list.
1. Click the checkbox next to each device you want to remove.
1. Click **Remove Selected From...**.
1. Click **Yes** to confirm you want to remove the selected devices.

**To remove an individual device from a list:**
1. From the Show dropdown, select a populated list.
1. Locate a managed device and click the dropdown, then select **+Remove From...**.
1. Click **Yes** to confirm you want to remove the selected device.