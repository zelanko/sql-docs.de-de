---
title: Microsoft Generic Content Tree Viewer (Data Mining) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.contentviewer.f1
ms.assetid: 751b4393-f6fd-48c1-bcef-bdca589ce34c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ba3b64847e2f63a96533a0f57cee41208176a7b7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66077811"
---
# <a name="microsoft-generic-content-tree-viewer-data-mining"></a>Microsoft Generic Content Tree Viewer (Data Mining)
  Der **Microsoft Generic Content Tree Viewer** zeigt ausführliche Informationen über den Inhalt eines Data Mining-Modells in einem standardisierten HTML-Tabellenformat an. Diese Sicht ist hilfreich, da sie die zugrunde liegende Struktur des Modells zeigt sowie Details zu Koeffizienten, die Verteilung von Werten und vieles mehr.  
  
 Die tatsächlich in der Tabelle angezeigten Inhalte variieren je nach verwendetem Algorithmus und können Spalten, Regeln, Eigenschaften, Attribute, Knoten und Formeln umfassen. Weitere Informationen zu Modellinhalten und zur Interpretation der Informationen eines jeden Modelltyps finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).  
  
 Für die im Viewer angezeigten Informationen wird eine gemeinsame Struktur verwendet, die auf dem Schemarowset für Miningmodelle basiert. Das Schemarowset für den Inhalt ist ein allgemeines Framework zum Speichern von Mustern, Statistiken und weiteren Inhalten eines Data Mining-Modells. Eine Liste der Spalten im Data Mining-Schemarowset für Miningmodelle finden Sie unter [DMSCHEMA_MINING_MODEL_CONTENT-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).  
  
## <a name="options"></a>Optionen  
 **Knotenbeschriftung (Eindeutige ID)**  
 In diesem Bereich wird eine Liste aller Knoten im ausgewählten Miningmodell angezeigt. Die Knoten werden abhängig vom angezeigten Modelltyp unterschiedlich in der Struktur angeordnet.  
  
 Sie können auf die einzelnen Knoten klicken, um Details über den Knoten im Bereich **Knotendetails** anzuzeigen.  
  
 **Knotendetails**  
 Zeigt ausführliche Informationen über den Inhalt des ausgewählten Knotens an. In jedem Knoten werden die dazugehörigen Informationen in einem standardisierten Format gespeichert, der Inhalt und die Bedeutung der Tabellenzeilen sind jedoch abhängig vom Typ des angezeigten Modells oder Knotens. Die Informationen für einen Knoten, der eine Regel in einem Zuordnungsmodell darstellt, unterscheiden sich z. B. von den Informationen bei einem Knoten, der eine Struktur in einem Entscheidungsstrukturmodell darstellt.  
  
 Informationen zur Interpretation der Knoteninformationen eines bestimmten Modelltyps finden Sie unter [Miningmodellinhalt &#40;Analysis Services – Data Mining&#41;](data-mining/mining-model-content-analysis-services-data-mining.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Abfragen](data-mining/data-mining-queries.md)  
  
  
