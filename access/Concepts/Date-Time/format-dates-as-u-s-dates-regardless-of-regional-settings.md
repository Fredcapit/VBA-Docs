---
title: Format dates as U.S. dates regardless of regional settings
ms.prod: access
ms.assetid: d2e9121d-d950-0f63-9a28-53613a205465
ms.date: 09/21/2018
ms.localizationpriority: medium
---


# Format dates as U.S. dates regardless of regional settings

When you use Visual Basic for Applications (VBA) to concatenate dates into an SQL string, you must use a standard U.S. date format, regardless of the region that you have set in the **Regional Settings** tool in **Control Panel**. This topic contains a custom function that will convert any date into a U.S. date format.


```vb
Function MakeUSDate(DateIn As Variant) As String 
 
    ' Do nothing if the value is not a date. 
    If Not IsDate(DateIn) Then Exit Function 

    ' Format the date value as a U.S. date formatted string expression.
    MakeUSDate = "#" & Month(DateIn) & "/" & Day(DateIn) & "/" & Year(DateIn) & "#"

End Function
```

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]