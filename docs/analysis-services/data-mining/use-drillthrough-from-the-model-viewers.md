---
title: Verwenden von Drillthrough mit den Viewern | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 95baad39c12dde057e76b25d8303ed6385b6b07e
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="use-drillthrough-from-the-model-viewers"></a>Verwenden von Drillthrough mit den Modell-Viewern
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Abhängig vom Modelltyp können Sie Drillthrough von den Durchsuchen-Viewern auf der Registerkarte **Miningmodell-Viewer** des Data Mining-Designers verwenden, um die im Miningmodell verwendeten Fälle zu prüfen oder zusätzliche Spalten in der Miningstruktur anzuzeigen. Obwohl viele Modelltypen kein Drillthrough unterstützen, da die Muster im Modell nicht direkt mit bestimmten Fällen verknüpft werden können, unterstützen die folgenden Modelltypen Drillthrough.  
  
 Drillthrough muss für das Modell aktiviert worden sein, und Sie benötigen die entsprechenden Berechtigungen. Die Drillthroughoption könnte auch deaktiviert werden, wenn sich das Modell in einem nicht verarbeiteten Status befindet, und zwar unabhängig von, ob das Modell zuvor verarbeitet wurde und Inhalte besitzt. Um Modellfalldaten mithilfe von Drillthrough abzurufen, muss der Cache der Struktur und des Modells jeweils aktuell sein.  
  
### <a name="use-drillthrough-in-the-microsoft-tree-viewer"></a>Verwenden von Drillthrough im Microsoft Struktur-Viewer  
  
1.  Wählen Sie im Data Mining-Designer ein Entscheidungsstrukturmodell und anschließend die Option **Modell durchsuchen** aus, um das Modell im **Microsoft Struktur-Viewer**zu öffnen. Klicken Sie in SQL Server Management Studio mit der rechten Maustaste auf das Modell, und wählen Sie **Durchsuchen**aus.  
  
2.  Klicken Sie mit der rechten Maustaste auf einen beliebigen Knoten im Strukturdiagramm, und wählen Sie **Drillthrough ausführen**aus.  
  
3.  Wählen Sie eine der folgenden Optionen aus: **Nur Modellspalten** oder **Modell- und Strukturspalten**. Wenn Sie nicht über Berechtigungen verfügen, ist unter Umständen keine Option verfügbar.  
  
4.  Das Dialogfeld **Drillthrough ausführen** wird geöffnet, in dem die Falldaten und/oder Strukturdaten angezeigt werden. Die Titelleiste des Dialogfelds enthält auch eine Beschreibung des Knotens, von dem aus die Drillthroughabfrage ausgeführt wurde.  
  
5.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in den Ergebnissen, und wählen Sie **Alles kopieren** aus, um die Ergebnisse in der Zwischenablage zu speichern.  
  
### <a name="use-drillthrough-in-the-microsoft-cluster-viewer"></a>Verwenden von Drillthrough im Microsoft Cluster-Viewer  
  
1.  Wählen Sie im Data Mining-Designer ein Clusteringmodell aus, und wählen Sie **Modell durchsuchen** aus, um das Modell im **Microsoft Cluster-Viewer**zu öffnen. Klicken Sie in SQL Server Management Studio mit der rechten Maustaste auf das Modell, und wählen Sie **Durchsuchen**aus.  
  
2.  Klicken Sie auf der Registerkarte **Cluster** mit der rechten Maustaste auf einen beliebigen Knoten.  
  
3.  Wählen Sie **Drillthrough ausführen**und anschließend eine der folgenden Optionen aus: **Nur Modellspalten** oder **Modell- und Strukturspalten**. Wenn Sie nicht über Berechtigungen verfügen, ist unter Umständen keine Option verfügbar.  
  
4.  Das Dialogfeld **Drillthrough ausführen** wird geöffnet, in dem die Falldaten und/oder Strukturdaten angezeigt werden. Die Titelleiste des Dialogfelds enthält auch eine Beschreibung, die den Cluster für die Fälle kennzeichnet.  
  
5.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in den Ergebnissen, und wählen Sie **Alles kopieren** aus, um die Ergebnisse in der Zwischenablage zu speichern.  
  
### <a name="use-drillthrough-in-the-microsoft-association-rules-viewer"></a>Verwenden von Drillthrough im Microsoft Association Rules-Viewer  
  
1.  Wählen Sie im Data Mining-Designer ein Zuordnungsmodell aus, und wählen Sie **Modell durchsuchen** aus, um das Modell im **Microsoft Association Rules-Viewer**zu öffnen. Klicken Sie in SQL Server Management Studio mit der rechten Maustaste auf das Modell, und wählen Sie **Durchsuchen**aus.  
  
2.  Klicken Sie auf der Registerkarte **Regeln** mit der rechten Maustaste auf eine beliebige Zeile, die eine Regel darstellt. Klicken Sie auf der Registerkarte **Itemsets** auf eine beliebige Zeile, die ein Itemset enthält.  
  
3.  Wählen Sie **Drillthrough ausführen**und anschließend eine der folgenden Optionen aus: **Nur Modellspalten** oder **Modell- und Strukturspalten**. Wenn Sie nicht über Berechtigungen verfügen, ist unter Umständen keine Option verfügbar.  
  
4.  Das Dialogfeld **Drillthrough ausführen** wird geöffnet, in dem die Falldaten und/oder Strukturdaten angezeigt werden. Die Titelleiste des Dialogfelds enthält auch eine Beschreibung zur Identifizierung des Regelnamens.  
  
5.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in den Ergebnissen, und wählen Sie **Alles kopieren** aus, um die vollständigen Fallergebnisse in der Zwischenablage zu speichern. Sie können auch **Kopieren** auswählen, um nur den ausgewählten Fall zu kopieren. Wenn das Modell eine geschachtelte Tabellenspalte enthält, wird nur der Name der geschachtelten Tabellenspalte eingefügt. Wenn Sie die Datenwerte in der geschachtelten Tabellenspalte für die einzelnen Fälle abrufen möchten, müssen Sie eine Abfrage für den Modellinhalt erstellen.  
  
### <a name="use-drillthrough-in-the-microsoft-sequence-cluster-viewer"></a>Verwenden von Drillthrough im Microsoft Sequence Cluster-Viewer  
  
1.  Wählen Sie im Data Mining-Designer ein Clusteringmodell aus, und wählen Sie **Modell durchsuchen** aus, um das Modell im **Microsoft Cluster-Viewer**zu öffnen. Klicken Sie in SQL Server Management Studio mit der rechten Maustaste auf das Modell, und wählen Sie **Durchsuchen**aus.  
  
2.  Klicken Sie auf der Registerkarte **Clusterdiagramm**mit der rechten Maustaste auf einen beliebigen Knoten, der einen Cluster darstellt. Klicken Sie auf der Registerkarte **Clusterprofile** an einer beliebigen Stelle in einem Clusterprofil oder in dem Cluster, das die gesamte Modellauffüllung darstellt.  
  
3.  Wählen Sie **Drillthrough ausführen**und anschließend eine der folgenden Optionen aus: **Nur Modellspalten** oder **Modell- und Strukturspalten**. Wenn Sie nicht über Berechtigungen verfügen, ist unter Umständen keine Option verfügbar.  
  
4.  Das Dialogfeld **Drillthrough ausführen** wird geöffnet, in dem die Falldaten und/oder Strukturdaten angezeigt werden. Die Titelleiste des Dialogfelds enthält auch eine Beschreibung, die den Cluster für die Fälle kennzeichnet.  
  
5.  Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in den Ergebnissen, und wählen Sie **Alles kopieren** aus, um die Ergebnisse in der Zwischenablage zu speichern. Wenn das Modell eine geschachtelte Tabellenspalte enthält, wird nur der Name der geschachtelten Tabellenspalte eingefügt. Wenn Sie die Datenwerte in der geschachtelten Tabellenspalte für die einzelnen Fälle abrufen möchten, müssen Sie eine Abfrage für den Modellinhalt erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodell-Viewer miningmodelltasks und Anweisungen](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Drillthrough für Miningmodelle](../../analysis-services/data-mining/drillthrough-on-mining-models.md)   
 [Drillthrough in Miningstrukturen](../../analysis-services/data-mining/drillthrough-on-mining-structures.md)  
  
  
