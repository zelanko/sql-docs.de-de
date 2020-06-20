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
ms.openlocfilehash: c81a17df03fc770964780332a0fedd1d4ff711a2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940961"
---
# <a name="select-members-business-intelligence-wizard"></a>Elemente auswählen (Business Intelligence-Assistent)
  Mithilfe der Seite **Elemente auswählen** können Sie bestimmen, auf welche Elemente der Business Intelligence-Assistent die Währungsumrechnungsfunktion anwenden soll, die auf der Seite **Optionen für die Währungsumrechnung festlegen** angegeben ist.  
  
> [!NOTE]  
>  Diese Seite wird nicht angezeigt, wenn der Business Intelligence-Assistent vom Dimensions-Designer aus oder durch Klicken mit der rechten Maustaste auf eine Dimension im Projektmappen-Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]gestartet wurde.  
  
## <a name="options"></a>Tastatur  
 **Measuredimension**  
 Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion auf ein oder mehrere Measures in dem Cube anzuwenden.  
  
 Wenn diese Option ausgewählt ist, werden im Raster die in der folgenden Tabelle aufgeführten Optionen angezeigt.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Elemente auswählen**|Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion für das angegebene Measure einzuschließen.|  
|**Hilfs**|Wählen Sie das Measure aus der Wechselkurs-Measuregruppe aus, das den Wechselkurs enthält, der beim Konvertieren des unter **Elemente auswählen** ausgewählten Measures verwendet werden soll.|  
  
 **Kontohierarchie**  
 Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion auf ein oder mehrere Elemente in der Kontohierarchie der Kontodimension anzuwenden, die im Cube enthalten ist. Die Konto Hierarchie ist die Hierarchie innerhalb der Konto Dimension, deren- `Type` Eigenschaft auf *Account*festgelegt ist.  
  
 Wenn diese Option ausgewählt ist, werden im Raster die in der folgenden Tabelle aufgeführten Optionen angezeigt.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Kontoelement**|Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion für das angegebene Element der Kontohierarchie einzuschließen.|  
|**Hilfs**|Wählen Sie das Measure aus der Wechselkurs-Measuregruppe aus, das den Wechselkurs für die Konvertierung der Measures für das unter **Kontoelement** ausgewählte Element enthält.|  
  
 **Kontohierarchie basierend auf Typ**  
 Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion auf alle Elemente von Attributen in der Kontohierarchie anzuwenden, deren `Type`-Eigenschaft auf einen angegebenen Kontotyp festgelegt ist.  
  
 Wenn diese Option ausgewählt ist, werden im Raster die in der folgenden Tabelle aufgeführten Optionen angezeigt.  
  
|Option|Beschreibung|  
|------------|-----------------|  
|**Kontotyp**|Wählen Sie diese Option aus, um die Währungsumrechnungsfunktion für den angegebenen Kontotyp einzuschließen.|  
|**Hilfs**|Wählen Sie das Measure aus der Wechselkurs-Measuregruppe aus, das den Wechselkurs für die Konvertierung der Measures für die Elemente von Attributen enthält, die den unter **Kontotyp** ausgewählten Kontotypen verwenden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Business Intelligence Wizard (F1-Hilfe)](business-intelligence-wizard-f1-help.md)   
 [Cube-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Der Dimensions-Designer &#40;Analysis Services Mehrdimensionale Daten&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
