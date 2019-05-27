---
title: Drillthrough zu Falldaten aus einem Miningmodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- drillthrough [Analysis Services]
ms.assetid: b4d3f350-e543-4ea9-b3a2-b4f7c0a9ae27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d683c9dc9a201b1f4351ee00d718ad0d7917606
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66084613"
---
# <a name="drill-through-to-case-data-from-a-mining-model"></a>Ausführen von Drillthroughs für Falldaten aus einem Miningmodell
  Wenn Sie in einem Miningmodell Drillthrough für die Modellfälle aktiviert haben, können Sie beim Durchsuchen des Modells detaillierte Informationen über die Fälle abrufen, die für die Erstellung des Modells verwendet wurden. Wenn in der zugrunde liegenden Miningstruktur ebenfalls Drillthrough für Strukturfälle aktiviert wurde und Sie über die entsprechenden Berechtigungen verfügen, können Sie Informationen aus der Miningstruktur zurückgeben. Dies kann Spalten einschließen, die nicht im Miningmodell enthalten sind.  
  
 Wenn die Miningstruktur keinen Drillthrough für die zugrunde liegenden Daten gestattet, jedoch das Miningmodell, können Sie nur Informationen der Modellfälle anzeigen, nicht jedoch der Miningstruktur.  
  
> [!NOTE]  
>  Sie können einem vorhandenen Miningmodell die Funktion für einen Drillthrough hinzufügen, indem Sie die `AllowDrillthrough`-Eigenschaft auf `True` festlegen. Nachdem Sie Drillthroughs aktiviert haben, muss das Modell jedoch erneut verarbeitet werden, bevor Sie die Falldaten anzeigen können. Weitere Informationen finden Sie unter [Aktivieren von Drillthrough für ein Miningmodell](enable-drillthrough-for-a-mining-model.md).  
  
 In Abhängigkeit von dem verwendeten Viewer können Sie den Knoten für den Drillthrough folgendermaßen auswählen:  
  
|Name des Viewers|Name des Bereichs oder der Registerkarte|Knoten auswählen|  
|-----------------|----------------------|-----------------|  
|**Microsoft Struktur-Viewer**|Registerkarte**Entscheidungsstruktur** |Klicken Sie auf einen Strukturknoten.<br /><br /> **Beachten Sie** nach Möglichkeit keinen Drillthrough auf die `All` Knoten, da es zurückgeben von Ergebnissen sehr lange dauern kann.|  
|**Microsoft Cluster-Viewer**|**Clusterdiagramm**|Klicken Sie auf einen Clusterknoten.|  
|**Microsoft Cluster-Viewer**|**Clusterprofile**|Klicken Sie auf eine beliebige Stelle in der Clusterspalte.|  
|**Microsoft Association Rules-Viewer**|Registerkarte**Regeln** |Klicken Sie auf eine Zeile, die einen Satz von Regeln enthält.|  
|**Microsoft Association Rules-Viewer**|Registerkarte**Itemsets** |Klicken Sie auf eine Zeile, die ein Itemset enthält.|  
|**Microsoft Sequence Cluster-Viewer**|Registerkarte**Regeln** |Klicken Sie auf eine Zeile, die einen Satz von Regeln enthält.|  
|**Microsoft Sequence Cluster-Viewer**|Registerkarte**Itemsets** |Klicken Sie auf eine Zeile, die ein Itemset enthält.|  
  
> [!NOTE]  
>  Einige Modelle können keinen Drillthrough verwenden. Die Möglichkeit eines Drillthrough hängt von dem für die Erstellung des Modells verwendeten Algorithmus ab. Eine Liste der Miningmodelltypen, die Drillthrough unterstützen, finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>So zeigen Sie Drillthroughdaten von einem Miningmodell an  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]die Miningstruktur, die das gewünschte Miningmodell enthält.  
  
2.  Klicken Sie im Data Mining-Designer auf die Registerkarte **Miningmodell-Viewer** .  
  
3.  Wählen Sie das Modell aus der Dropdownliste **Miningmodell** aus.  
  
4.  Wählen Sie einen Viewer aus der Dropdownliste **Viewer** aus, und klicken Sie mit der rechten Maustaste auf den entsprechenden Knoten.  
  
5.  Wählen Sie **Drillthrough**und anschließend entweder **Nur Modellspalten**oder **Modell- und Strukturspalten** , um das Fenster **Drillthrough** zu öffnen.  
  
6.  Um die Daten in die Zwischenablage zu kopieren, klicken Sie mit der rechten Maustaste auf eine beliebige Zeile in der Tabelle, und wählen Sie **Alle kopieren**.  
  
## <a name="see-also"></a>Siehe auch  
 [Drillthroughabfragen &#40;Data Mining&#41;](drillthrough-queries-data-mining.md)  
  
  
