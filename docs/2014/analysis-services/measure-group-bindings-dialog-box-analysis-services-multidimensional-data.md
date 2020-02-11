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
manager: craigg
ms.openlocfilehash: 4d3d04692ac6576e76d2b630fb5cacb4f57db959
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077859"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a>Dialogfeld 'Measuregruppenbindung' (Analysis Services – Mehrdimensionale Daten)
  Mithilfe des Dialogfelds **Measuregruppenbindungen** können Sie direkte Beziehungen zwischen Attributen ohne Granularität in einer Cubedimension und Spalten in einer Measuregruppe für eine Beziehung regulärer Dimensionen erstellen und ändern, sowie Optionen für die Verarbeitung von NULL-Werten für jedes Attribut in einer Cubedimension mithilfe des Dialogfelds **Beziehung definieren** angeben.  
  
## <a name="options"></a>Tastatur  
 **Tabelle für Measure-Gruppe**  
 Zeigt den Namen der Faktentabelle für die ausgewählte Measuregruppe an.  
  
 **Attribute**  
 Zeigt ein Raster aus Attributen und Dimensionstabellen an. Wählen Sie ein Attribut aus, um dessen Eigenschaften unter **Beziehung** zu erstellen oder zu ändern. Das Raster enthält die folgenden Spalten:  
  
|Option|Definition|  
|------------|----------------|  
|**Attribut Name**|Zeigt den Namen des Attributs an.|  
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
  
  
