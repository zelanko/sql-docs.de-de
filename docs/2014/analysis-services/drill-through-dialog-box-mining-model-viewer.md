---
title: Drillthrough (Dialog Feld) (Mining Modell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.drillthrough.f1
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c065e36dd20646312d04379ea61b96d37a47a262
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081484"
---
# <a name="drill-through-dialog-box-mining-model-viewer"></a>Dialogfeld "Drillthrough" (Miningmodell &ndash; Viewer)
  Wenn Sie ein Miningmodell mithilfe der Registerkarte **Miningmodell-Viewer** im Data Mining-Designer anzeigen, können Sie einen Drillthrough in die Details der Falldaten ausführen, wenn in dem Modell Drillthrough aktiviert ist. Wenn in der zugrunde liegenden Miningstruktur Drillthrough aktiviert ist, werden zudem in der Miningstruktur auch dann Spalten angezeigt, wenn diese Spalten nicht in dem Miningmodell enthalten waren. In der Spaltenliste sind die Strukturspalten mit dem Präfix "Struktur" gekennzeichnet.  
  
> [!NOTE]  
>  Sie können keinen Drillthrough auf einer vorhandenen Miningstruktur aktivieren. Stattdessen müssen Sie die Miningstruktur erneut erstellen und Drillthrough während des Erstellungsprozesses aktivieren.  
  
 Informationen über das Zugreifen auf Falldaten über die verschiedenen Miningmodell-Viewer, die Drillthrough unterstützen, **finden Sie unter** [Ausführen von Drillthroughs für Falldaten aus einem Miningmodell](data-mining/drill-through-to-case-data-from-a-mining-model.md).  
  
## <a name="options"></a>Optionen  
 **Klassifizierte Fälle für**  
 Zeigt die Definition der Regeln Itemset und Cluster an, die im ausgewählten Knoten enthalten sind.  
  
 **Spaltenliste**  
 Zeigt die Spalten im Modell an, gefolgt von den Strukturspalten.  
  
 **Hinweis** Strukturspalten werden nur angezeigt, wenn Drillthrough auf der Miningstruktur aktiviert ist und wenn Sie die Option **Model- und Strukturspalten**gewählt haben. Um die Spalten anzuzeigen, müssen Drillthroughberechtigungen außerdem sowohl im Miningmodell als auch in der Miningstruktur aktiviert sein.  
  
 Struktur Spalten, die nicht im Modell enthalten sind, werden als **Struktur\< angezeigt. der Spaltenname>**.  
  
> [!NOTE]  
>  Sie können an einer beliebigen Stelle im Spaltenraster mit der rechten Maustaste klicken und **Alle kopieren** auswählen, um die Drillthroughdaten in tabulatorgetrenntem Format in die Zwischenablage zu kopieren. Die kopierten Daten enthalten nur die Falldaten, nicht die Knotendefinition.  
  
 **Theater**  
 Klicken Sie auf die Schaltfläche mit dem grünen Pfeil, um die Daten zu aktualisieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Drillthrough-Abfragen &#40;Data Mining-&#41;](data-mining/drillthrough-queries-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Tasks und Anweisungen für Miningmodell-Viewer](data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
