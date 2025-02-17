---
title: ShadowFormat.Obscured property (Publisher)
keywords: vbapb10.chm3670273
f1_keywords:
- vbapb10.chm3670273
ms.prod: publisher
api_name:
- Publisher.ShadowFormat.Obscured
ms.assetid: 9bc7382e-50cf-0364-6b5a-8aa46a12d8fb
ms.date: 06/13/2019
ms.localizationpriority: medium
---


# ShadowFormat.Obscured property (Publisher)

Returns or sets an **[MsoTriState](office.msotristate.md)** value indicating whether the shadow of the specified shape appears filled in and is obscured by the shape. Read/write.


## Syntax

_expression_.**Obscured**

_expression_ A variable that represents a **[ShadowFormat](Publisher.ShadowFormat.md)** object.


## Return value

MsoTriState


## Remarks

The **Obscured** property value can be one of the **MsoTriState** constants declared in the Microsoft Office type library and shown in the following table.

|Constant|Description|
|:-----|:-----|
| **msoFalse**|The shadow of the specified shape does not appear filled in and is not obscured by the shape if the shape has no fill.|
| **msoTriStateMixed**|A return value indicating a combination of **msoTrue** and **msoFalse** for the specified shape range.|
| **msoTriStateToggle**|A set value that switches between **msoTrue** and **msoFalse**.|
| **msoTrue**|The shadow of the specified shape appears filled in and is obscured by the shape even if the shape has no fill.|

## Example

This example sets the horizontal and vertical offsets of the shadow for shape three on page one of the active publication. The shadow is offset 5 points to the right of the shape and 3 points above it. If the shape does not already have a shadow, this example adds one to it. The shadow will be filled in and obscured by the shape, even if the shape has no fill.

```vb
With ActiveDocument.Pages(1).Shapes(3).Shadow 
 .Visible = True 
 .OffsetX = 5 
 .OffsetY = -3 
 .Obscured = msoTrue 
End With
```

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]