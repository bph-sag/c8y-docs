---
weight: 30
title: Viewing audit logs
layout: redirect
---

Auditing shows in the query log the queries being executed and in the system log the operations that users have carried out.

### Query log

In the navigator, select **Auditing** and then **Query log** to view the query log.

{{< c8y-admon-info >}}
The {{< product-c8y-iot >}} DataHub feature for storing query profiles needs to be enabled. The profiles are deleted after a retention period, so for older months profiles may no longer be available.
{{< /c8y-admon-info >}}

At the top of the page you can select either offload or ad-hoc queries, define a text filter on the offloading task/ad-hoc query string, and select a time period. Use the pagination buttons at the bottom of the page to navigate through the result list.

For each offloading query, the following information is provided:

| Column name | Description
| ---         |  ---
| Offloading task | The task name of the offloading pipeline, complemented by a status icon showing success or failure of the pipeline execution
| Runtime (s) | The runtime of the execution in seconds
| Data scanned (MB) | The amount of data the offloading query has read from the Operational Store of {{< product-c8y-iot >}}
| Data billed (MB) | The amount of data being billed (depending also on your contract); amounts of data less than 10 MB in an offloading query will be billed as if they were 10 MB
| Details | The internal task UUID in an expandable box

For each ad-hoc query, the following information is provided:

| Column name | Description
| ---         |  ---
| User | The username of the Dremio user, which has been used to execute the query
| Query | The SQL query, complemented by a status icon showing success or failure of the query execution
| Runtime (s) | The runtime of the execution in seconds
| Data scanned (MB) | The amount of data the ad-hoc query has read from the data lake
| Data billed (MB) | The amount of data being billed (depending also on your contract); amounts of data less than 10 MB in an ad-hoc query will be billed as if they were 10 MB
| Details | The query string as well as a link to the associated Dremio job in an expandable box

### System log

In the navigator, select **Auditing** and then **System log** to view the system log.

At the top of the page you can select log entries having status all/successful/errorneous/running, define a text filter on the log entries, and select a time period. Use the pagination buttons at the bottom of the page to navigate through the result list.

For each log entry, the following information is provided:

| Column name | Description
| ---         |  ---
| User | The user that has carried out the operation
| Event | The type of operation
| Details | The details of the operation and, if available, further information in an expandable box
