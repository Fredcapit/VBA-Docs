---
title: KeysBoundTo.Creator property (Word)
keywords: vbawd10.chm160891881
f1_keywords:
- vbawd10.chm160891881
ms.prod: word
api_name:
- Word.KeysBoundTo.Creator
ms.assetid: cafa763f-738e-6ce6-aaf5-f6c7b301a71b
ms.date: 06/08/2017
ms.localizationpriority: medium
---


# KeysBoundTo.Creator property (Word)

Returns a 32-bit integer that indicates the application in which the specified object was created. Read-only **Long**.


## Syntax

_expression_.**Creator**

_expression_ Required. A variable that represents a '[KeysBoundTo](Word.keysboundto.md)' object.


## Remarks

If the object was created in Microsoft Word, the **Creator** property returns the hexadecimal number 4D535744, which represents the string "MSWD." This property was primarily designed to be used on the Macintosh, where each application has a four-character creator code. For example, Microsoft Word has the creator code MSWD. For additional information about this property, consult the language reference Help included with Microsoft Office Macintosh Edition.


## See also


[KeysBoundTo Collection Object](Word.keysboundto.md)

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]