---
title: BoundObjectFrame.Height property (Access)
keywords: vbaac10.chm10930
f1_keywords:
- vbaac10.chm10930
ms.prod: access
api_name:
- Access.BoundObjectFrame.Height
ms.assetid: 53f59551-041e-dc9e-4eee-ed0d5cad0603
ms.date: 02/08/2019
ms.localizationpriority: medium
---


# BoundObjectFrame.Height property (Access)

Gets or sets the height of the specified object in [twips](../language/glossary/vbe-glossary.md#twip). Read/write **Integer**.


## Syntax

_expression_.**Height**

_expression_ A variable that represents a **[BoundObjectFrame](Access.BoundObjectFrame.md)** object.


## Remarks

For report controls, you can set the **Height** property when you print or preview a report only by using a macro or an event procedure specified in a section's **OnFormat** event property setting.

Microsoft Access automatically sets the **Height** property when you create or size a control or when you size a window in form Design view or report Design view.

The height of controls is measured from the center of their borders so that controls with different border widths align correctly. 




[!include[Support and feedback](~/includes/feedback-boilerplate.md)]