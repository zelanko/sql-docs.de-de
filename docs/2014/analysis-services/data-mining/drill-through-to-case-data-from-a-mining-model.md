---
title: Drillthrough zu Falldaten aus einem Mining Modell | Microsoft-Dokumentation
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
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
|**Microsoft Tree-Viewer**|Registerkarte **Entscheidungs** Struktur|Klicken Sie auf einen Strukturknoten.<br /><br /> **Hinweis** Vermeiden Sie die Verwendung von Drillthrough auf dem `All` Knoten, da es sehr lange dauern kann, bis Ergebnisse zurückgegeben werden.|  
|**Microsoft Cluster-Viewer**|**Cluster Diagramm**|Klicken Sie auf einen Clusterknoten.|  
|**Microsoft Cluster-Viewer**|**Cluster profile**|Klicken Sie auf eine beliebige Stelle in der Clusterspalte.|  
|**Microsoft Association Viewer**|Registerkarte **Regeln**|Klicken Sie auf eine Zeile, die einen Satz von Regeln enthält.|  
|**Microsoft Association Viewer**|Registerkarte " **Itemsets** "|Klicken Sie auf eine Zeile, die ein Itemset enthält.|  
|**Microsoft Sequence Clustering-Viewer**|Registerkarte **Regeln**|Klicken Sie auf eine Zeile, die einen Satz von Regeln enthält.|  
|**Microsoft Sequence Clustering-Viewer**|Registerkarte " **Itemsets** "|Klicken Sie auf eine Zeile, die ein Itemset enthält.|  
  
> [!NOTE]  
>  Einige Modelle können keinen Drillthrough verwenden. Die Möglichkeit eines Drillthrough hängt von dem für die Erstellung des Modells verwendeten Algorithmus ab. Eine Liste der Miningmodelltypen, die Drillthrough unterstützen, finden Sie unter [Drillthroughabfragen &#40;Data Mining&#41;](drillthrough-queries-data-mining.md)festlegen.  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>So zeigen Sie Drillthroughdaten von einem Miningmodell an  
  
1.  Öffnen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]die Miningstruktur, die das gewünschte Miningmodell enthält.  
  
2.  Klicken Sie im Data Mining-Designer auf die Registerkarte **Miningmodell-Viewer** .  
  
3.  Wählen Sie das Modell aus der Dropdownliste **Miningmodell** aus.  
  
4.  Wählen Sie einen Viewer aus der Dropdownliste **Viewer** aus, und klicken Sie mit der rechten Maustaste auf den entsprechenden Knoten.  
  
5.  Wählen Sie **Drillthrough**und anschließend entweder **Nur Modellspalten**oder **Modell- und Strukturspalten** , um das Fenster **Drillthrough** zu öffnen.  
  
6.  Um die Daten in die Zwischenablage zu kopieren, klicken Sie mit der rechten Maustaste auf eine beliebige Zeile in der Tabelle, und wählen Sie **Alle kopieren**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Drillthrough-Abfragen &#40;Data Mining-&#41;](drillthrough-queries-data-mining.md)  
  
  
