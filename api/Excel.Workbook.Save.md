---
title: Workbook.Save method (Excel)
keywords: vbaxl10.chm199144
f1_keywords:
- vbaxl10.chm199144
ms.prod: excel
api_name:
- Excel.Workbook.Save
ms.assetid: 466d891d-fb4c-fb0a-474b-dedb3c4ea7a7
ms.date: 05/29/2019
ms.localizationpriority: medium
---


# Workbook.Save method (Excel)

Saves changes to the specified workbook.


## Syntax

_expression_.**Save**

_expression_ A variable that represents a **[Workbook](Excel.Workbook.md)** object.


## Remarks

To open a workbook file, use the **[Open](Excel.Workbooks.Open.md)** method.

To mark a workbook as saved without writing it to a disk, set its **[Saved](Excel.Workbook.Saved.md)** property to **True**.

The first time you save a workbook, use the **[SaveAs](Excel.Workbook.SaveAs.md)** method to specify a name for the file.


## Example

This example saves the active workbook.

```vb
ActiveWorkbook.Save
```

<br/>

This example saves all open workbooks and then closes Microsoft Excel.

```vb
For Each w In Application.Workbooks 
    w.Save 
Next w 
Application.Quit
```

<br/>

This example uses the **BeforeSave** event to verify that certain cells contain data before the workbook can be saved. The workbook cannot be saved until there is data in each of the following cells: D5, D7, D9, D11, D13, and D15.

```vb
Private Sub Workbook_BeforeSave(ByVal SaveAsUI As Boolean, Cancel As Boolean)
   'If the six specified cells don't contain data, then display a message box with an error
   'and cancel the attempt to save.
   If WorksheetFunction.CountA(Worksheets("Sheet1").Range("D5,D7,D9,D11,D13,D15")) < 6 Then
      MsgBox "Workbook will not be saved unless" & vbCrLf & _
      "All required fields have been filled in!"
      Cancel = True
   End If
End Sub
```



[!include[Support and feedback](~/includes/feedback-boilerplate.md)]
