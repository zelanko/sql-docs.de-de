---
title: Erstellen von Drillthroughabfragen mit DMX | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 72c540463b5bf2b1dff262731fddbc5d258a1de6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151701"
---
# <a name="create-drillthrough-queries-using-dmx"></a>Erstellen von Drillthroughabfragen mit DMX
  Für alle Modelle, die Drillthrough unterstützen, können Fall- und Strukturdaten durch Erstellen einer DMX-Abfrage in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] oder einem beliebigen anderen Client abgerufen werden.  
  
> [!WARNING]  
>  Zum Anzeigen der Daten muss Drillthrough aktiviert werden, wofür Sie die entsprechenden Berechtigungen benötigen.  
  
## <a name="specifying-drillthrough-options"></a>Angeben von Drillthroughoptionen  
 Die allgemeine Syntax zum Abrufen von Modell- und Strukturfällen sieht folgendermaßen aus:  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 Weitere Informationen zur Verwendung von DMX-Abfragen zum Zurückgeben von Falldaten finden Sie unter [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) und [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).  
  
## <a name="examples"></a>Beispiele  
 Bei der folgenden DMX-Abfrage werden die Falldaten für eine bestimmte Produktreihe von einem Zeitreihenmodell zurückgegeben. Die Abfrage gibt außerdem die Spalte `Amount` zurück, die zwar nicht im Modell verwendet wurde, jedoch in der Miningstruktur verfügbar ist.  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 In diesem Beispiel wird ein Alias verwendet, um die Strukturspalte umzubenennen. Wenn Sie der Strukturspalte keinen Alias zuordnen, wird die Spalte mit dem Namen "Expression" zurückgegeben. Dies ist das Standardverhalten für alle unbenannten Spalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Drillthroughabfragen &#40;Datamining&#41;](drillthrough-queries-data-mining.md)   
 [Drillthrough für Miningstrukturen](drillthrough-on-mining-structures.md)  
  
  
