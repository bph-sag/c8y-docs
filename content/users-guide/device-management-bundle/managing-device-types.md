---
weight: 50
title: Managing device types
layout: redirect
helpcontent:
  - label: managing-device-types
    title: Managing device types
    content: "To process data from various device types, Cumulocity IoT uses device protocols. Each device protocol is configured for a particular device protocol type (for example Modbus, LoRa, LWM2M).


  To add a new device protocol, click **Add device protocol** at the top right, select a device protocol type and configure it following the instructions for the particular type in the *Protocol integration guide*."
---

To process data from various device types, {{< product-c8y-iot >}} uses device protocols which are stored in a database.

Click **Device protocols** in the **Device types** menu in the navigator.

In the **Device protocols** page you will find a list with all device protocols available in your account.

![Device protocols](/images/users-guide/DeviceManagement/devmgmt-device-protocols.png)

The device protocol list shows the following information:

* the device protocol type (for example Modbus, CANOpen, LoRa)
* the device type name
* the number of resources for the device (at the right)

### To add a device protocol

1. Click **Add device protocol** in the top menu bar.
2. Select one of the available device protocol types from the list.
3. In the resulting dialog box, enter a name and an optional description for the device protocol and click **Create**.
4. Enter the configuration for the device protocol. The configuration of the device protocol depends on the protocol type. <br>
For details on configuring device protocols, follow the documentation of the particular device type you want to create, see [Protocol integration guide](/protocol-integration/overview).
5. Click **Save**.

The device protocol will be added to the device database.

### To import a device protocol

To add a device protocol from an existing protocol, perform the following steps:

1. Click **Import** in the top menu bar.
2. Either select the device protocol to be imported from a list of predefined protocols or load it from a file by browsing.
3. Provide a name for the new protocol and click **Save**.

The device protocol will be added to the device database.

### To edit a device protocol

To edit a device protocol, just click on the protocol or click the menu icon at the right of the row and then click **Edit**.

Details on the fields can be found in the documentation of the particular device type, see [Protocol integration guide](/protocol-integration/overview).

### To delete a device protocol

To delete a device protocol, click the menu icon at the right of the row and then click **Delete**.

The device protocol will be deleted from the device database.

### To export a device protocol

To export a device protocol, click the menu icon at the right of the row and then click **Export**.

The device protocol will be exported to your file system.
