---
uid: Query_updates
---

# Query updates

When executing a query, you can enable query updates to keep your query result up to date.

These updates may add, remove, or update rows from the initial result returned by your query.

> [!TIP]
> To see which updates a query can support, refer to [query update support](#query-update-support).

## Enabling updates

While GQI allows updates to be enabled or disabled for each query individually, in the UI, this is configured per component.

To control updates, select the component, open the *Settings* pane, and enable or disable the *Data retrieval* > *Update data* setting.

This setting will enable updates for all queries executed by the selected component.

## Query update support

A GQI query can offer various levels of support for updates, depending on the data sources and operators in the query. These are the possible levels, ordered from highest to lowest:

1. Updates through **real-time events**.

   Real-time events occur as soon as a change is detected. These events contain incremental updates in the form of added, removed, or updated rows and cells.

1. Updates through **notification events**.

   Notification events serve as a simplified variant of real-time events, allowing data sources and operators to notify the client that there *may* have been a change, without detailing *what* changed.

   In practice, GQI will keep track of these notifications and relay them to the client every 30 seconds. When the client receives such an event, it will execute the query again to show the most recent data.

1. No support for updates.

> [!IMPORTANT]
> The update support of your query is determined by the **lowest** level of support among the data sources and operators in your query. See [supported data sources](#supported-data-sources) and [supported operators](#supported-operators) for an overview.

## Supported data sources

The overview below lists all data sources that currently have update support. If a data source is not listed here, this means that there is no update support for it yet.

| Data source | Support level | Supported since |
| ----------- | -------- | -------- |
| [Get ad hoc data](xref:Get_ad_hoc_data) | [Real-time events](#query-update-support) | DataMiner 10.4.4/10.5.0 |
| [Get object manager instances](xref:Get_object_manager_instances) | [Real-time events](#query-update-support) | DataMiner 10.5.0/10.5.7 when using the [GQI DxM](xref:GQI_DxM) <!-- RN 42530 --> |
| [Get parameter table by ID](xref:Get_parameter_table_by_ID) | [Real-time events](#query-update-support) | DataMiner 10.3.10/10.4.0 |
| [Get views](xref:Get_views) | [Real-time events](#query-update-support) | DataMiner 10.3.10/10.4.0 |

> [!NOTE]
> These updates may have specific limitations. Check the data source documentation for more details.

## Supported operators

The overview below indicates the support levels for all operators.

| Operator | Support level | Support |
| -------- | ------------- | ------- |
| [Select](xref:GQI_Select) | [Real-time events](#query-update-support) | |
| [Sort](xref:GQI_Sort) | [Real-time events](#query-update-support) | Starting from DataMiner 10.5.0 [CU4]/10.5.7 with the [GQI DxM](xref:GQI_DxM). <!-- RN 42941 --> |
| [Filter](xref:GQI_Sort) | [Real-time events](#query-update-support) / [Notification events](#query-update-support) | When supported, this is mentioned in the relevant data source documentation. |
| All other operators | [Notification events](#query-update-support) | |
