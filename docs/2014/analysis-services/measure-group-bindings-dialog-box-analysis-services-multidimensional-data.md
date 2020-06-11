---
title: Dialog Feld ' Messungs Gruppen Bindungen ' (Analysis Services Mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
author: minewiskan
ms.author: owend
ms.openlocfilehash: b4fb4b20fcccdabdf29aaf57dab65b1604a80a9e
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84541602"
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Dialog Feld ' Beziehung definieren ' &#40;Analysis Services Mehrdimensionale Daten&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md)   
 [Analysis Services Designer und Dialog Felder &#40;Mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
