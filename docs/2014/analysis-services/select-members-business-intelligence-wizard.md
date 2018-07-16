---
title: Wählen Sie Elemente (Business Intelligence-Assistent) | Microsoft-Dokumentation
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
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 8b1bdcf78e3a7fd35da53e7a39bea5c24e217ae8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37321240"
---
# <a name="select-members-business-intelligence-wizard"></a>Elemente auswählen (Business Intelligence-Assistent)
  Mithilfe der Seite **Elemente auswählen** können Sie bestimmen, auf welche Elemente der Business Intelligence-Assistent die Währungsumrechnungsfunktion anwenden soll, die auf der Seite **Optionen für die Währungsumrechnung festlegen** angegeben ist.  
  
> [!NOTE]  
>  Diese Seite wird nicht angezeigt, wenn der Business Intelligence-Assistent vom Dimensions-Designer aus oder durch Klicken mit der rechten Maustaste auf eine Dimension im Projektmappen-Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]gestartet wurde.  
  
## <a name="options"></a>Tastatur  
 **Measures-dimension**  
 Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion auf ein oder mehrere Measures in dem Cube anzuwenden.  
  
 Wenn diese Option ausgewählt ist, werden im Raster die in der folgenden Tabelle aufgeführten Optionen angezeigt.  
  
|Option|Description|  
|------------|-----------------|  
|**Elemente auswählen**|Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion für das angegebene Measure einzuschließen.|  
|**Measures**|Wählen Sie das Measure aus der Wechselkurs-Measuregruppe aus, das den Wechselkurs enthält, der beim Konvertieren des unter **Elemente auswählen** ausgewählten Measures verwendet werden soll.|  
  
 **Kontohierarchie**  
 Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion auf ein oder mehrere Elemente in der Kontohierarchie der Kontodimension anzuwenden, die im Cube enthalten ist. Die Kontohierarchie ist die Hierarchie innerhalb der Kontodimension, deren `Type` -Eigenschaftensatz auf *Konto*.  
  
 Wenn diese Option ausgewählt ist, werden im Raster die in der folgenden Tabelle aufgeführten Optionen angezeigt.  
  
|Option|Description|  
|------------|-----------------|  
|**Kontoelement**|Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion für das angegebene Element der Kontohierarchie einzuschließen.|  
|**Measures**|Wählen Sie das Measure aus der Wechselkurs-Measuregruppe aus, das den Wechselkurs für die Konvertierung der Measures für das unter **Kontoelement** ausgewählte Element enthält.|  
  
 **Kontohierarchie basierend auf Typ**  
 Wählen aus, um die Währungsumrechnungsfunktion auf alle Elemente gelten in der Kontohierarchie Attributen, deren `Type` -Eigenschaft auf einen angegebenen Kontotyp festgelegt ist.  
  
 Wenn diese Option ausgewählt ist, werden im Raster die in der folgenden Tabelle aufgeführten Optionen angezeigt.  
  
|Option|Description|  
|------------|-----------------|  
|**Kontotyp**|Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion für den angegebenen Kontotyp einzuschließen.|  
|**Measures**|Wählen Sie das Measure aus der Wechselkurs-Measuregruppe aus, das den Wechselkurs für die Konvertierung der Measures für die Elemente von Attributen enthält, die den unter **Kontotyp** ausgewählten Kontotypen verwenden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Business Intelligence-Assistent F1-Hilfe](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Dimensions-Designer &#40;Analysis Services – mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
