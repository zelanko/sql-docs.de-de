---
title: Measuregruppe Measuregruppenbindungen (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c803d434fac98c6f2397465738599bac5fa1d8ad
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62727967"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Measuregruppenbindung' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Measuregruppenbindungen** können Sie direkte Beziehungen zwischen Attributen ohne Granularität in einer Cubedimension und Spalten in einer Measuregruppe für eine Beziehung regulärer Dimensionen erstellen und ändern, sowie Optionen für die Verarbeitung von NULL-Werten für jedes Attribut in einer Cubedimension mithilfe des Dialogfelds **Beziehung definieren** angeben.  
  
## <a name="options"></a>Optionen  
 **Measuregruppentabelle**  
 Zeigt den Namen der Faktentabelle für die ausgewählte Measuregruppe an.  
  
 **Attribute**  
 Zeigt ein Raster aus Attributen und Dimensionstabellen an. Wählen Sie ein Attribut aus, um dessen Eigenschaften unter **Beziehung** zu erstellen oder zu ändern. Das Raster enthält die folgenden Spalten:  
  
|Option|Definition|  
|------------|----------------|  
|**Attributname**|Zeigt den Namen des Attributs an.|  
|**Dimensionstabelle**|Zeigt den Namen der Dimensionstabelle an, auf der das Attribut basiert.|  
  
 **Beziehung**  
 Zeigt ein Raster für die Beziehungen zwischen Dimensionstabellenspalten für das ausgewählte Attribut und Faktentabellenspalten für die ausgewählte Measuregruppe an. Außerdem wird die Option zur Verarbeitung von NULL-Werten für die Beziehung angezeigt. Das Raster enthält die folgenden Spalten:  
  
|Option|Definition|  
|------------|----------------|  
|**Dimensionsspalten**|Zeigt die Spalten der Dimensionstabelle an, auf denen das unter **Attribute** ausgewählte Attribut basiert.|  
|**Measuregruppenspalten**|Wählen Sie entweder **Von Dimension geerbt** aus, um die von der Dimension geerbte Measuregruppenbeziehung zu verwenden, oder wählen Sie eine Spalte aus der Faktentabelle aus, auf der die Measuregruppe basiert, um eine Beziehung explizit zu definieren.|  
|**NULL-Verarbeitung**|Wählen Sie eine Option zur NULL-Verarbeitung für das Attribut aus. Weitere Informationen zu den Optionen für die NULL-Verarbeitung finden Sie unter [NullProcessing-Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/nullprocessing-element-assl).|  
  
## <a name="see-also"></a>Siehe auch  
 [Das Dialogfeld Beziehung definieren &#40;Analysis Services – mehrdimensionale Daten&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md)   
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
