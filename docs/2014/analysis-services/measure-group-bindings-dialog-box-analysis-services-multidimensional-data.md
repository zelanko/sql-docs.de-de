---
title: Measuregruppe Measuregruppenbindungen (Dialogfeld) (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
caps.latest.revision: 14
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2c306ba41e8ebb6fe2615be0bec8f3cebd560e65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37226410"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Measuregruppenbindung' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Measuregruppenbindungen** können Sie direkte Beziehungen zwischen Attributen ohne Granularität in einer Cubedimension und Spalten in einer Measuregruppe für eine Beziehung regulärer Dimensionen erstellen und ändern, sowie Optionen für die Verarbeitung von NULL-Werten für jedes Attribut in einer Cubedimension mithilfe des Dialogfelds **Beziehung definieren** angeben.  
  
## <a name="options"></a>Tastatur  
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
|**NULL-Verarbeitung**|Wählen Sie eine Option zur NULL-Verarbeitung für das Attribut aus. Weitere Informationen zu den Optionen für die NULL-Verarbeitung finden Sie unter [NullProcessing-Element &#40;ASSL&#41;](scripting/properties/nullprocessing-element-assl.md).|  
  
## <a name="see-also"></a>Siehe auch  
 [Das Dialogfeld Beziehung definieren &#40;Analysis Services – mehrdimensionale Daten&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md)   
 [Analysis Services-Designer und-Dialogfelder &#40;mehrdimensionale Daten&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
