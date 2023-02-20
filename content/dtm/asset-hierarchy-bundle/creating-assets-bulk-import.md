---
weight: 30
title: Creating assets via bulk import
layout: redirect
---

To import the entire asset hierarchy with all assets at once, use the bulk import feature.
For each [asset model](/dtm/asset-types/#asset-types), a CSV template is provided.
Fill in the required details in this template and upload the file to create the assets in bulk for the selected asset model.

<a name=""></a>
### To use the bulk import feature

To use the Bulk import feature, you must enable the **Digital Twin** permission for the user's role, following these steps:

1. Navigate to the [Administration application](/users-guide/administration/#overview) via the application switcher in the top right corner.

2. Under **Quick links** click **Roles**.

3. In the **Global roles** tab, select the role to which permissions are to be provided.

4. Select the "Admin" permission for "Digital Twin" in the "Permissions" section.

5. Enable access to the DTM application by selecting the following checkboxes:

	* Under **Application access**, select "Dtm-ms".

	* Under **Custom applications**, select "Digital Twin Manager".

5. Click **Save**.

![Permissions for bulk import](/images/dtm/bulk-import/dtm-bulk-import-assign-permissions.png)

Once the permissions are assigned, the bulk import feature can be used.

{{< c8y-admon-info>}}
If the permissions are not assigned, the CSV template will not be downloaded correctly.
{{< /c8y-admon-info>}}


<a name=""></a>
### To download a CSV template for bulk import

Follow the steps below:

1. Navigate to the **Assets** page and click **Import assets**.

2. The **Import assets** dialog has a dropdown **Choose asset model**. If you have added the asset models, all the root asset models are listed in the dropdown.

3. Select the asset model for which you want to create the asset hierarchy.

	![bulk-import-asset](/images/dtm/bulk-import/dtm-bulk-import-import-assets-window.png)

4. On selection, two additional options appear:

	* **Drop file here** - upload the CSV template as a file, for importing assets in bulk.
	* **Download Template** - download the CSV template for the selected asset model.

	<br/>

5. Click **Download Template** to download the CSV template.


<a name="csv-template-parameters"></a>
### CSV template parameters

The CSV template has the following fields:

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
<td style="text-align:left"><b>AssetModel / DeviceType </b></td>
<td style="text-align:left">Enter the key of the asset model.</td>
<td style="text-align:left">Mandatory</td>
</tr>
<tr>
<td style="text-align:left"><b>AssetName</b></td>
<td style="text-align:left">Provide the name of the asset you want to create.</td>
<td style="text-align:left">Mandatory</td>
</tr>
<tr>
<td style="text-align:left"><b>Path</b></td>
<td style="text-align:left">Remains blank when you create a root asset. For a subasset, provide a path up to the root asset.<br><br>
<b>Example:</b><br>
For an asset called "SE-T101-Blade 1" in the hierarchy "Wind turbine > Rotor > Blade" the path value is "SE-Turbine-101/SE-T101-Rotor", where "SE-Turbine-101" and "SE-T101-Rotor" each represent the respective asset models.</td>
<td style="text-align:left">Mandatory (for subassets)</td>
</tr>
<tr>
<td style="text-align:left"><b>Device ID / External ID</b></td>
<td style="text-align:left">If the asset being created has a device associated with it, then provide the Device ID of the device here</td>
<td style="text-align:left">Optional</td>
</tr>
<tr>
<td style="text-align:left"><b>Description</b></td>
<td style="text-align:left">briefly describes the asset being created.</td>
<td style="text-align:left">Optional</td>
</tr>
<tr>
<td style="text-align:left"><b>Asset properties for the asset model</b></td>
<td style="text-align:left">6th column onwards (in the CSV template), all the asset properties for the root asset models and all its subsequent child asset models are listed.<br/><br/>
Note that the <a href="/dtm/asset-types/#custom-property-types" class="no-ajaxy">Asset property type</a> is also mentioned as a label, for better understanding.<br/>
</td>
<td style="text-align:left">Mandatory</td>
</tr>
</tbody>
</table>

![bulk-import-template](/images/dtm/bulk-import/dtm-bulk-import-template.png)

{{< c8y-admon-info>}}
Modify the excel settings to provide the date in a YYYY-MM-DD format. This prevents auto-correction of the date on input.
{{< /c8y-admon-info>}}

To provide a file input as an asset property value, the file must first be uploaded to a {{< product-c8y-iot >}} tenant using the {{< product-c8y-iot >}} API.

Refer to the [Binaries API](https://{{< domain-c8y >}}/api/core/{{< c8y-current-version >}}/#operation/postBinariesCollectionResource) in the {{< openapi >}} for details on how to upload a file to {{< product-c8y-iot >}}.

The binary ID in the API response must be provided as input for the asset property field with type "file" in the CSV template.
{{< c8y-admon-info>}}
During the bulk import, the file size validation is skipped as the file is already uploaded to the tenant.
{{< /c8y-admon-info>}}

If the type is "Boolean", the input field must be either "true" or "false".
If the type is "enumeration", then the input field must be in the list of values specified during creation of the asset property.
If the type is "text" or "number" and custom criteria were provided during asset property creation, then the input value in CSV template must fulfill all the asset property criteria.

Fill in details for all the assets which must be created as part of the asset hierarchy.

Start with the asset details for root asset model.
Then enter the asset details for child a models under the root asset.
Next, enter the details for the next level in the hierarchy of subassets and repeat until the details for all the assets are entered in the CSV template.
Save the CSV template in your system.


<a name=""></a>
### To upload a CSV template

To upload the CSV template follow the steps below:

1. Click **Import assets** in the **Assets** page.

2. Select the asset model in the **Import assets** dialog.

3. Upload the previously filled and saved CSV template in the **Drop file here** section and click **Import**.

4. If all the inputs are provided correctly, the bulk import is successful, resulting in a success notification. The asset hierarchy and its assets are created successfully.

5. View the newly created assets in the **Assets** page.

If the inputs are not provided in the correct format, the bulk import fails with validation errors, resulting in a **Failed asset imports** notification, showing the issue types, for example, an invalid template or an incorrect asset hierarchy.
No assets are created.

![bulk-import-failed-import](/images/dtm/bulk-import/dtm-bulk-import-failed-asset-imports.png)

If the bulk import fails, review the reported issues and try again.


<a name=""></a>
### Partial import

If the asset hierarchy already exists, and you want to import more assets, it can be achieved by a partial import.

To import a single subasset or the subasset hierarchy:

1. Navigate to the **Asset tree** page of the subasset and download the template using **Import assets**.

2. Fill in the details for the subasset hierarchy in the CSV template. See [CSV template parameters](#csv-template-parameters) for more details.

	{{< c8y-admon-info>}}
From any hierarchy level, the template will be downloaded only for its child hierarchy.
Assets must only be imported for the child hierarchy.
	{{< /c8y-admon-info>}}

3. Enter the details for the subassets in the CSV template.

4. Click **Import assets**.

5. Upload the CSV template in the **Drop file here** section in the **Import assets** dialog and click **Import**.

If all details are mentioned correctly in the CSV template, the subasset hierarchy is created successfully.

An unsuccessful partial import will result in a **Failed asset imports** notification, showing the validation issues.
Review the reported issues and try again.
