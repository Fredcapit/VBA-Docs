---
title: VisDrawSplineFlags enumeration (Visio)
keywords: vis_sdr.chm70105
f1_keywords:
- vis_sdr.chm70105
ms.prod: visio
ms.assetid: d5bd35db-4fbd-f1dd-01fc-9e45eb8c4c59
ms.date: 06/08/2017
ms.localizationpriority: medium
---


# VisDrawSplineFlags enumeration (Visio)

Flags to pass to the **DrawSpline** and **DrawPolyline** methods.



|Constant|Value|Description|
|:-----|:-----|:-----|
| **visPolyarcs**|256|Draw a sequence of arcs rather than a sequence of line segments.|
| **visPolyline1D**|8|Draw a shape that has one-dimensional (1D) behavior.|
| **visSpline1D**|8|Draw a shape that has 1D behavior.|
| **visSplineAbrupt**|4|Break the spline whenever an abrupt change of direction or curvature in the point's trail is detected.|
| **visSplineDoCircles**|2|Recognize circular segments in the given array of points and generate circular arcs for those segments.|
| **visSplinePeriodic**|1|Draw a periodic spline.|

[!include[Support and feedback](~/includes/feedback-boilerplate.md)]