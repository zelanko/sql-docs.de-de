---
title: Drillthrough (Dialogfeld) (Miningmodell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.drillthrough.f1
ms.assetid: 42b78399-143d-4f44-90e0-b545ffb79e10
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d26fcb3d26570adafe340f190e7a91c82fd2ef3a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48066953"
---
# <a name="drill-through-dialog-box-mining-model-viewer"></a>Dialogfeld "Drillthrough" (Miningmodell &ndash; Viewer)
  Wenn Sie ein Miningmodell mithilfe der Registerkarte **Miningmodell-Viewer** im Data Mining-Designer anzeigen, können Sie einen Drillthrough in die Details der Falldaten ausführen, wenn in dem Modell Drillthrough aktiviert ist. Wenn in der zugrunde liegenden Miningstruktur Drillthrough aktiviert ist, werden zudem in der Miningstruktur auch dann Spalten angezeigt, wenn diese Spalten nicht in dem Miningmodell enthalten waren. In der Spaltenliste sind die Strukturspalten mit dem Präfix "Struktur" gekennzeichnet.  
  
> [!NOTE]  
>  Sie können keinen Drillthrough auf einer vorhandenen Miningstruktur aktivieren. Stattdessen müssen Sie die Miningstruktur erneut erstellen und Drillthrough während des Erstellungsprozesses aktivieren.  
  
 Informationen über das Zugreifen auf Falldaten über die verschiedenen Miningmodell-Viewer, die Drillthrough unterstützen, **finden Sie unter** [Ausführen von Drillthroughs für Falldaten aus einem Miningmodell](data-mining/drill-through-to-case-data-from-a-mining-model.md).  
  
## <a name="options"></a>Tastatur  
 **Klassifizierte Fälle für**  
 Zeigt die Definition der Regeln Itemset und Cluster an, die im ausgewählten Knoten enthalten sind.  
  
 **Spaltenliste**  
 Zeigt die Spalten im Modell an, gefolgt von den Strukturspalten.  
  
 **Hinweis** Strukturspalten werden nur angezeigt, wenn Drillthrough auf der Miningstruktur aktiviert ist und wenn Sie die Option **Model- und Strukturspalten**gewählt haben. Um die Spalten anzuzeigen, müssen Drillthroughberechtigungen außerdem sowohl im Miningmodell als auch in der Miningstruktur aktiviert sein.  
  
 Strukturspalten, die nicht im Modell enthalten sind, werden als **Struktur.\< Spaltenname >**.  
  
> [!NOTE]  
>  Sie können an einer beliebigen Stelle im Spaltenraster mit der rechten Maustaste klicken und **Alle kopieren** auswählen, um die Drillthroughdaten in tabulatorgetrenntem Format in die Zwischenablage zu kopieren. Die kopierten Daten enthalten nur die Falldaten, nicht die Knotendefinition.  
  
 **Wiedergeben**  
 Klicken Sie auf die Schaltfläche mit dem grünen Pfeil, um die Daten zu aktualisieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Drillthroughabfragen &#40;Datamining&#41;](data-mining/drillthrough-queries-data-mining.md)   
 [Miningmodell-Viewer &#40;Datamining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Tasks und Anweisungen für den Miningmodell-Viewer](data-mining/mining-model-viewer-tasks-and-how-tos.md)  
  
  
