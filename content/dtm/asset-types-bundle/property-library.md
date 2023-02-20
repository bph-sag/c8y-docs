---
weight: 20
layout: redirect
title: Asset properties

helpContent: 
- label: asset-properties
  title: Asset Properties
  content: "Asset properties are the parameters that define an asset model. One or more asset properties are used to define an asset model.

  
  Asset properties can be reused in multiple asset models. You can build your asset property library by adding asset properties which can be used to define any asset model.
  
  
  To add a new asset property, click **Add asset property**."
---
Asset properties are the parameters that define an [asset model](/dtm/asset-types/#asset-types). One or more asset properties are used to define an asset model. Asset properties are created in the **Asset properties** page.

<a name="create-custom-property"></a>
### To create an asset property

When you navigate to the **Asset properties** page following **Configuration > Asset properties** for the first time, there will be no asset properties present in the system.

If you use a tenant which already has asset properties defined, you find the list of defined asset properties on the left. You see the selected asset property definition on the right.

To create an asset property, click **Add asset property** on the bottom left. Enter the required data in the form (see description below) and click **Save**.

![Create a new asset property](/images/dtm/custom-property/dtm-property-library-create-property.png)

Asset properties have the following parameters:

<table>
<col width="20">
<col width="50">
<col width="30">
<thead>
<tr>
<th style="text-align:left">Field</th>
<th style="text-align:left">Description</th>
<th style="text-align:left">Mandatory / Optional</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left"><b>Label</b></td>
<td style="text-align:left">Refers to the name of the asset property. The asset property is further addressed using the information provided here.</td>
<td style="text-align:left">Mandatory</td>
</tr>
<tr>
<td style="text-align:left"><b>Key</b></td>
<td style="text-align:left">Used to uniquely identify and store the asset property in the DTM application.<br/><br/>
Note that the key is automatically generated based on the label. You can modify the automatically generated key to suit to your needs only during asset property creation. You cannot edit the key after the asset property is created.
</td>
<td style="text-align:left">Mandatory</td>
</tr>
<tr>
<td style="text-align:left"><b>Description</b></td>
<td style="text-align:left">Provides a brief description of the asset property.</td>
<td style="text-align:left">Optional</td>
</tr>
<tr>
<td style="text-align:left"><b>Complex property toggle</b></td>
<td style="text-align:left">Used to create a complex asset property, that contains one or multiple key-value pairs. By default, the toggle is switched off.</td>
<td style="text-align:left">Optional</td>
</tr>
<tr>
<td style="text-align:left"><b>Type</b></td>
<td style="text-align:left">Defines the type of the asset property. It can be any of the following categories – <a href="#custom-text" class="no-ajaxy">Text</a>, <a href="#custom-number" class="no-ajaxy">Number</a>, <a href="#custom-file-upload" class="no-ajaxy">File upload</a>, <a href="#custom-date-picker" class="no-ajaxy">Date picker</a>, <a href="#custom-enumeration" class="no-ajaxy">Enumeration</a>, or <a href="#custom-boolean" class="no-ajaxy">Boolean</a>.</td>
<td style="text-align:left">Mandatory</td>
</tr>
<tr>
<td style="text-align:left"><b>Default value</b></td>
<td style="text-align:left">Defines the default value for the parameter. You can modify the content when creating an asset using this asset property.</td>
<td style="text-align:left">Optional</td>
</tr>
</tbody>
</table>

{{< c8y-admon-info>}}
The **Default value** field is only shown if the selected **Type** is either "Text" or "Number".
{{< /c8y-admon-info>}}

Once you have defined all necessary asset properties for your project, you must define the [asset models](/dtm/asset-types/#asset-types).


<a name="custom-property-types"></a>
### Asset property types

To further define the asset property you can select one of the six following options listed under **Type**:


<a name="custom-text"></a>
#### Text

Select **Text** if the asset property value is a string, for example, a wind turbine manufacturer name. Enter a valid text.

 If you select **Text**, the following fields appear:

*	**Min Length**:

Enter the minimum length of the text that must be provided for this asset property during the asset creation. Any text below the minimum length is not accepted.

If not selected, no minimum length criteria is set for this asset property during the asset creation.

* **Max Length**:

Enter the maximum length of the text that must be provided for this asset property during the asset creation. Any text above the maximum length is not accepted.

If the entered text exceeds the maximum length, you get notified of the incidence and the asset creation is cancelled.

* **RegExp**:

Enter a valid regular expression. During the asset creation, you must provide the asset property value, which adheres to the regular expression.

**Example:**

If the asset property is "Generator code" with the regular expression "^MCGEN[a-zA-Z0-9]*$", all generator  codes have to start with the prefix “MCGEN”.


<a name="default-value"></a>
#### Default value

Assigns a default value to the asset property. If this field is left empty in the asset property, you must enter a value during the asset creation.

{{< c8y-admon-info>}}
The default value has to adhere to all validations provided beforehand. If you selected a property of the type "Text", you can set the **Min length**, **Max length** and/or **RegExp** and the default value must fulfill all set validations.
{{< /c8y-admon-info>}}

**Example:**

If the asset property is "Generator code" with a **Min length** of 8, a **Max length** of 20 and the **RegExp** defined as "^MCGEN[a-zA-Z0-9]*$", the default value must fulfill all of these three criteria. If it does not, this results in a validation error. The respective field will be highlighted to modify its content to fit the criteria.


<a name="custom-number"></a>
#### Number

For this type you must provide a numeric value for the asset creation, for example, the height of a wind turbine tower.

The type **Number** contains the following fields for additional information:

* **Minimum**:

If selected, enter a number in the field on the right. When you create the asset, the asset property value cannot be lower or less than the minimum provided.

{{< c8y-admon-info>}}

If you entered a [default value](/dtm/asset-types/#default-value) beforehand, it needs to be greater than or equal to the minimum provided. By default, this box is not selected.

{{< /c8y-admon-info>}}


* **Maximum**:

If selected, enter a number in the field on the right. When you create the asset, the asset property value cannot exceed the **Maximum** provided.

{{< c8y-admon-info>}}

If you entered a [default value](/dtm/asset-types/#default-value) beforehand, it needs to be lesser than or equal to the **Maximum** entered here. By default, this box is not checked.

{{< /c8y-admon-info>}}


* **Default value**:
Assigns a default value to the asset property. If this field is left empty in the asset property, you must enter a value during the asset creation.

{{< c8y-admon-info>}}

If the **Minimum** and/or **Maximum** is checked, the given **Default value** is validated against one or both of these values.

{{< /c8y-admon-info>}}

**Example:**

If the asset property is "Tower height" with a **Minimum** of 80 and a **Maximum** of 110, the **Default value** must be between 80 and 110.


<a name="custom-date-picker"></a>
#### Date Picker

If selected, you must select a date from the calendar displayed in the dialog window during the asset creation.

**Example:**

If "Installation date" is a property of the "Wind turbine" asset, then you must select the installation date of the wind turbine when creating the asset.


<a name="custom-enumeration"></a>
#### Enumeration

Select **Enumeration** to list several values that apply to this asset property.

If selected, a second field appears below. Here, enter all desired information separated by a comma.

During asset creation, these values appear as options in the dropdown menu. Select one of the options to initialize the asset property with that option.

**Example:**

If you create an asset property for a wind turbine "drivetrain type" and the type must be either Gearbox or Direct-drive, you have to provide these options separated by a comma when creating the asset property.

![Asset property enumeration](/images/dtm/custom-property/dtm-property-library-type-enum.png)

<a name="custom-boolean"></a>
#### Boolean

If selected, the presence of the asset property can either be true or false during the asset creation.

An asset with this asset property shows a checkbox. Selecting this checkbox sets the asset property value to true.

**Example:**

If you create an asset property called "Yaw system" to identify wind turbines that rotate towards the wind direction during upwind conditions, the asset property must be created with the type "Boolean". When you create an asset for a wind turbine with a yaw system present, it is then initialized to "true". If there is no yaw system present, the asset is initialized to "false".

<a name="custom-file-upload"></a>
#### File upload

This option allows you to upload a file during the asset creation.

If selected, enter the allowed file types separated by a comma in the **Allowed file types** field. Provide the maximum file size for uploads in the **Max file size in MB** field. When you create an asset with this asset property, you can only upload files that adhere to the allowed file types with their file size not exceeding the set limit.

{{< c8y-admon-info>}}

If there is a file size limit set for the tenant, you see the limit along with the field name for **Max file size in MB**.<br>
During the bulk import, the file size validation is skipped as the file is already uploaded to the tenant.


{{< /c8y-admon-info>}}

**Example:**

To upload the schematic diagram for a wind turbine, you name the asset property "Wind turbine schematic" and specify the file type of the schematic file. Then upload the respective file. Once the asset is created, you can view this file for future reference.


<a name=""></a>
### To edit an asset property

1. Select the desired asset property in the **Asset properties** to see all the details on the right of the screen.
2. Edit any content of the asset property.
3. Click **Save** to save your changes.
4. If this property is used by any asset model, in the resulting confirmation dialog, select **Confirm** to continue to save your changes.


<a name=""></a>
### To search and filter asset properties

1. Navigate to the **Asset properties** page.
2. Enter the desired name in the search field on the top left.
3. Click the search icon.

All asset properties matching the search values are displayed on the screen on the left. If the search entry does not match with any asset properties, you see a notification.


<a name=""></a>
### To delete an asset property

Select the respective asset property in the **Asset properties** and click **Delete** on the bottom right.

In the resulting confirmation dialog, click **Confirm** to continue.

{{< c8y-admon-info>}}

If the asset property you want to delete is part of an existing asset, you see an error notification and the asset property is not deleted.

{{< /c8y-admon-info>}}


<a name=""></a>
### Types of asset properties

There are two types of asset properties, both fulfill different requirements:

<a name=""></a>
#### Simple asset property

A simple asset property consists of a single key value pair. This option is set by default when creating new asset properties.

In the **Asset properties** simple asset properties are listed with their type.

 **Example:**

 If the asset property is called "Tower height", you use the key "tower_height" with the Default value of "70" (see image below).

 ![Simple asset property](/images/dtm/custom-property/dtm-property-library-simple-custom-property.png)

<a name=""></a>
#### Complex asset property

A complex asset property consists of multiple key value pairs, meaning, it contains a root object followed by one or more key value pairs. You can select the complex asset property option by switching on the toggle. If you switch on the toggle, you must define each key value pair as well as providing a Type for each pair.

In the **Asset properties** complex asset properties are listed with the label "Object".

You see the preview of data model on the right side of properties section.

 **Example:**
 
If the asset property is called "Gearbox specifications" with the key "gearbox_specifications", then power, speed increasing ratio and weight are the multiple key value pairs defining the property "Gearbox specifications". Switch on the **Complex property** toggle (see image below). Enter the required information for all key value pairs and click **Save**.

![Complex asset property](/images/dtm/custom-property/dtm-property-library-complex-property.png)