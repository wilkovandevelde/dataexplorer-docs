---
title:  dayofweek()
description: Learn how to use the dayofweek() function to return the `timespan` since the preceding Sunday.
ms.reviewer: alexans
ms.topic: reference
ms.date: 08/11/2024
---
# dayofweek()

> [!INCLUDE [applies](../includes/applies-to-version/applies.md)] [!INCLUDE [fabric](../includes/applies-to-version/fabric.md)] [!INCLUDE [azure-data-explorer](../includes/applies-to-version/azure-data-explorer.md)] [!INCLUDE [monitor](../includes/applies-to-version/monitor.md)] [!INCLUDE [sentinel](../includes/applies-to-version/sentinel.md)]

Provides the number of days since the preceding Sunday, as a `timespan`.

To convert `timespan` to `int`, see [Convert timespan to integer](#convert-timespan-to-integer).

## Syntax

`dayofweek(`*date*`)`

[!INCLUDE [syntax-conventions-note](../includes/syntax-conventions-note.md)]

## Parameters

| Name | Type | Required | Description |
|--|--|--|--|
| *date* | `datetime` |  :heavy_check_mark: | The datetime for which to determine the day of week.|

## Returns

Returns the `timespan` since midnight at the beginning of the preceding Sunday, rounded down to an integer number of days.

## Examples

The follow example shows how to extract the day of the week from a specified datetime value.

:::moniker range="azure-data-explorer"
> [!div class="nextstepaction"]
> <a href="https://dataexplorer.azure.com/clusters/help/databases/Samples?query=H4sIAAAAAAAAAysoyswr4eUKycxNLS5IzFOwVUhJrMxPK09NzdZISSxJLQFKaBhampjrGhrqGhsoGBpYGQCRqaYmAHvwNxk6AAAA" target="_blank">Run the query</a>
::: moniker-end

```kusto
print
Timespan = dayofweek(datetime(1947-11-30 10:00:05))
```

**Output**

|Timespan|
|--|
|00:00:00|

The following example returns 1, indicating that the specified datetime is a Monday.

:::moniker range="azure-data-explorer"
> [!div class="nextstepaction"]
> <a href="https://dataexplorer.azure.com/clusters/help/databases/Samples?query=H4sIAAAAAAAAAysoyswr4eUKycxNLS5IzFOwVUhJrMxPK09NzdZISSxJLQFKaBhamhvoGpjqGhpqagIA76Tx5DEAAAA%3D" target="_blank">Run the query</a>
::: moniker-end

```kusto
print
Timespan = dayofweek(datetime(1970-05-11))
```

**Output**

|Timespan|
|--|
|1.00:00:00|

### Convert timespan to integer

The following example returns the number of days both as a `timespan` and as data type `int`.

:::moniker range="azure-data-explorer"
> [!div class="nextstepaction"]
> <a href="https://dataexplorer.azure.com/clusters/help/databases/Samples?query=H4sIAAAAAAAAA8tJLVFIyS%2B3TUmszE8rT03N1khJLEktycxN1TC0NDfQNdU1NNLUtOYqKMrMK1EIAYoXFyTmKdiCNOkoeALFbBVK8oFyGkABfcMUTQCfJzyAUQAAAA%3D%3D" target="_blank">Run the query</a>
::: moniker-end

```kusto
let dow=dayofweek(datetime(1970-5-12));
print Timespan = dow, Integer = toint(dow/1d)
```

**Output**

|Timespan|Integer|
|--|--|
|2.00:00:00|2|

## Related content

* [The timespan data type](scalar-data-types/timespan.md)
* [startofweek function](./startofweek-function.md)
* [endofweek function](./endofweek-function.md)
* [week_of_year function](./week-of-year-function.md)
* [ago function](./ago-function.md)
