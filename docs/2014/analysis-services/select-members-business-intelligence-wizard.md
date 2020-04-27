---
title: Mitglieder auswählen (Business Intelligence-Assistent) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.currencyconversion.memberconversion.f1
ms.assetid: 1a147461-d594-41e7-a41d-09d2d003e1e0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7cc66896eb1735d09991644dd49c03b5a94c208d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66069433"
---
# <a name="select-members-business-intelligence-wizard"></a>Elemente auswählen (Business Intelligence-Assistent)
  Mithilfe der Seite **Elemente auswählen** können Sie bestimmen, auf welche Elemente der Business Intelligence-Assistent die Währungsumrechnungsfunktion anwenden soll, die auf der Seite **Optionen für die Währungsumrechnung festlegen** angegeben ist.  
  
> [!NOTE]  
>  Diese Seite wird nicht angezeigt, wenn der Business Intelligence-Assistent vom Dimensions-Designer aus oder durch Klicken mit der rechten Maustaste auf eine Dimension im Projektmappen-Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]gestartet wurde.  
  
## <a name="options"></a>Optionen  
 **Measuredimension**  
 Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion auf ein oder mehrere Measures in dem Cube anzuwenden.  
  
 Wenn diese Option ausgewählt ist, werden im Raster die in der folgenden Tabelle aufgeführten Optionen angezeigt.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Elemente auswählen**|Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion für das angegebene Measure einzuschließen.|  
|**Measures**|Wählen Sie das Measure aus der Wechselkurs-Measuregruppe aus, das den Wechselkurs enthält, der beim Konvertieren des unter **Elemente auswählen** ausgewählten Measures verwendet werden soll.|  
  
 **Kontohierarchie**  
 Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion auf ein oder mehrere Elemente in der Kontohierarchie der Kontodimension anzuwenden, die im Cube enthalten ist. Die Konto Hierarchie ist die Hierarchie innerhalb der Konto `Type` Dimension, deren-Eigenschaft auf *Account*festgelegt ist.  
  
 Wenn diese Option ausgewählt ist, werden im Raster die in der folgenden Tabelle aufgeführten Optionen angezeigt.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Kontoelement**|Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion für das angegebene Element der Kontohierarchie einzuschließen.|  
|**Measures**|Wählen Sie das Measure aus der Wechselkurs-Measuregruppe aus, das den Wechselkurs für die Konvertierung der Measures für das unter **Kontoelement** ausgewählte Element enthält.|  
  
 **Kontohierarchie basierend auf Typ**  
 Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion auf alle Elemente von Attributen in der Kontohierarchie anzuwenden, deren `Type`-Eigenschaft auf einen angegebenen Kontotyp festgelegt ist.  
  
 Wenn diese Option ausgewählt ist, werden im Raster die in der folgenden Tabelle aufgeführten Optionen angezeigt.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Kontotyp**|Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion für den angegebenen Kontotyp einzuschließen.|  
|**Measures**|Wählen Sie das Measure aus der Wechselkurs-Measuregruppe aus, das den Wechselkurs für die Konvertierung der Measures für die Elemente von Attributen enthält, die den unter **Kontotyp** ausgewählten Kontotypen verwenden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Business Intelligence Wizard (F1-Hilfe)](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Der Dimensions-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
