---
title: SlideShowWindow.Active property (PowerPoint)
keywords: vbapp10.chm507011
f1_keywords:
- vbapp10.chm507011
ms.prod: powerpoint
api_name:
- PowerPoint.SlideShowWindow.Active
ms.assetid: b0832de7-0379-dfc1-b904-6e1de4110e38
ms.date: 06/08/2017
ms.localizationpriority: medium
---


# SlideShowWindow.Active property (PowerPoint)

Returns whether the specified pane or window is active. Read-only.


## Syntax

_expression_.**Active**

_expression_ A variable that represents a [SlideShowWindow](PowerPoint.SlideShowWindow.md) object.


## Return value

MsoTriState


## Remarks

The value returned by the **Active** property can be one of these **MsoTriState** constants.



|Constant|Description|
|:-----|:-----|
|**msoFalse**|The specified pane or window is inactive.|
|**msoTrue**| The specified pane or window is active.|

## Example

This example checks to see if the presentation file  _"test.ppt"_ is in the active window. If not, it saves the name of the presentation that is currently active in the variable `oldWin` and activates the _"test.ppt"_ presentation.


```vb
With Application.Presentations("test.ppt").Windows(1)

    If Not .Active Then

        Set oldWin = Application.ActiveWindow

        .Activate

    End If

End With
```


## See also


[SlideShowWindow Object](PowerPoint.SlideShowWindow.md)

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]