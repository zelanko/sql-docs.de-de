---
title: Anzeigen der Formel für ein Zeitreihenmodell Modells (Datamining) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- Time Series Viewer [Analysis Services]
ms.assetid: 825ef719-2f44-4979-be01-5a81f54e1a53
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 11427eb72ea27bd93e8cb360afcf1221ab19b05a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36162149"
---
# <a name="view-the-formula-for-a-time-series-model-data-mining"></a>Anzeigen der Formel für ein Zeitreihenmodell (Data Mining)
  Die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series-Viewer InData Mining-Designer bietet die einfachste Möglichkeit zum Anzeigen der Details in einem Zeitreihenmodell verwendeten Regressionsformel.  
  
 Sie können die Regressionsformel für ein Zeitreihenmodell extrahieren, indem Sie den Modellinhalt abfragen. Jedoch zur Anzeige der kompletten Formel für ARTXP oder ARIMA wir empfehlen die Verwendung der **Mininglegende** von der [Microsoft Time Series-Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md), der alle Konstanten im lesbaren Format dargestellt.  
  
 Wenn Sie ein gemischtes Modell erstellen, werden die ARIMA- und die ARTXP-Analyse in separaten Strukturen erstellt. Sie sind am Stammknoten miteinander verknüpft, der das Modell darstellt. Die Strukturen der ARIMA- und der ARTXP-Struktur unterscheiden sich stark. Zum Beispiel ist die ARTXP-Struktur tatsächlich eine Baumstruktur (wie eine Entscheidungsstruktur), wohingegen die ARIMA-Struktur eine Reihe von gleitenden Durchschnitten darstellt. Obwohl die beiden Darstellungen der Übersichtlichkeit halber in einem Modell gezeigt werden, müssen Sie sie dennoch als zwei unabhängige Modelle behandeln. Die Gleichungen sind auch völlig unterschiedlich und können nicht kombiniert oder verglichen werden.  
  
 Sie können zeitreihenmodelle auch anzeigen, indem Sie mit der [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md). Weitere Informationen über den Inhalt von einem Zeitreihenmodell finden Sie unter [Miningmodellinhalt Zeitreihenmodelle &#40;Analysis Services – Data Mining&#41;](mining-model-content-for-time-series-models-analysis-services-data-mining.md).  
  
### <a name="to-view-the-artxp-regression-formula-for-a-time-series-model"></a>So zeigen Sie die ARTXP-Regressionsformel für ein Zeitreihenmodell an  
  
1.  Wählen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]das Zeitreihenmodell aus, das Sie anzeigen möchten, und klicken Sie auf **Durchsuchen**.  
  
     - oder -  
  
     Wählen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das Zeitreihenmodell aus, und klicken Sie dann auf die Registerkarte **Miningmodell-Viewer** .  
  
2.  Klicken Sie auf die Registerkarte **Modell** .  
  
3.  Wenn das Modell mehrere Strukturen enthält, wählen Sie aus der Dropdownliste **Struktur** eine einzelne Struktur aus.  
  
    > [!NOTE]  
    >  Ein Modell hat stets mehrere Strukturen, wenn mehr als eine Datenreihe vorliegt. Sie sehen jedoch im **Time Series-Viewer** nicht so viele Strukturen wie im [Microsoft Generic Content Tree Viewer](../microsoft-generic-content-tree-viewer-data-mining.md). Der Grund hierfür liegt darin, dass der Time Series-Viewer die ARIMA- und ARTXP-Informationen für jede Datenreihe zu einer einzelnen Darstellung kombiniert.  
  
4.  Klicken Sie auf einen Blattknoten in der Struktur.  
  
     Knoten, die als **Datenreihe** bezeichnet werden, sind immer Blattknoten und können eine Gleichung enthalten. Wenn ein **(Alle)** -Knoten keine untergeordneten Knoten besitzt, kann er ebenfalls eine Gleichung enthalten.  
  
5.  Wenn die **Mininglegende** nicht verfügbar ist, klicken Sie mit der rechten Maustaste auf den Knoten, und wählen Sie **Legende anzeigen**aus.  
  
     Die ARTXP-Formel wird in der ersten Hälfte der **Mininglegende**als **Strukturknotenformel**angezeigt.  
  
### <a name="to-view-the-arima-formula-for-a-time-series-model"></a>So zeigen Sie die ARTxp-Formel für ein Zeitreihenmodell an  
  
1.  Wählen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]das Zeitreihenmodell aus, das Sie anzeigen möchten, und klicken Sie auf **Durchsuchen**.  
  
     - oder -  
  
     Wählen Sie in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]das Zeitreihenmodell aus, und klicken Sie dann auf die Registerkarte **Miningmodell-Viewer** .  
  
2.  Klicken Sie auf die Registerkarte **Modell** .  
  
3.  Wenn das Modell mehrere Strukturen enthält, wählen Sie aus der Dropdownliste **Struktur** eine einzelne Struktur aus.  
  
    > [!NOTE]  
    >  Das Modell hat stets mehrere Strukturen, wenn Sie mehr als eine Datenreihe einschließen.  
  
4.  Klicken Sie auf einen Knoten in der Struktur.  
  
     Die ARIMA-Formel wird in der zweiten Hälfte der **Mininglegende**als **ARIMA-Formel**angezeigt.  
  
5.  Wenn die **Mininglegende** nicht verfügbar ist, klicken Sie mit der rechten Maustaste auf den Knoten, und wählen Sie **Legende anzeigen**aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodell-Viewer miningmodelltasks und Anweisungen](mining-model-viewer-tasks-and-how-tos.md)   
 [Durchsuchen eines Modells mit dem Microsoft Time Series-Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md)   
 [Beispiele für Abfragen von Zeitreihenmodellen](time-series-model-query-examples.md)  
  
  