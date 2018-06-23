---
title: Neuronales Netzwerk (Miningmodell-Viewer) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.miningmodeleditor.neuralnet.f1
ms.assetid: 18d87e7b-a821-40ea-9bd8-c6fecf189a1c
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2db48dccb854d2dc51eaae3b8202324a8feed9aa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049586"
---
# <a name="neural-network-mining-model-viewer"></a>Neuronales Netzwerk (Miningmodell-Viewer)
  Verwenden Sie den **Viewer für neuronale Netzwerke** , um Miningmodelle zu durchsuchen, die auf dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Neural Network-Algorithmus oder dem [!INCLUDE[msCoName](../includes/msconame-md.md)] Logistic Regression-Algorithmus aufgebaut sind.  
  
 **Weitere Informationen finden Sie unter:** [Microsoft Neural Network-Algorithmus](data-mining/microsoft-neural-network-algorithm.md), [Microsoft Logistic Regression-Algorithmus](data-mining/microsoft-logistic-regression-algorithm.md),[Modell mit dem Microsoft-Viewer für neuronale Netzwerke durchsuchen](data-mining/browse-a-model-using-the-microsoft-neural-network-viewer.md)  
  
## <a name="options"></a>Tastatur  
 **Viewerinhalt**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein anzuzeigendes Miningmodell aus der aktuellen Miningstruktur aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Ereignisanzeige**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den benutzerdefinierten Viewer oder den **Microsoft Generic Content Tree Viewer**verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Eingabe**  
 Wählen Sie in diesem Bereich Eingabeattribute und Werte aus, damit Sie später untersuchen können, wie sich diese auf das Ergebnis auswirken.  
  
|value|Description|  
|-----------|-----------------|  
|**Attribut**|Wählen Sie ein Eingabeattribut aus der Liste aus. Wenn Sie die Standardauswahl, lassen  **\<alle >**, das Diagramm zeigt eine Liste aller Eingabeattribute, sortiert nach ihren Auswirkungen auf das vorhersagbare Attribut.|  
|**ReplTest1**|Wählen Sie einen Wert für das Eingabeattribut aus.|  
  
 **Ausgabe**  
 Wählen Sie mit diesen Steuerelementen ein vorhersagbares Attribut und einen Wert für die Analyse und den Vergleich im Balkendiagramm aus. Wenn Sie die Auswahl nicht ändern, werden im Balkendiagramm die obersten zwei Ergebnisstatuswerte verglichen.  
  
|value|Description|  
|-----------|-----------------|  
|**Ausgabeattribut**|Wählen Sie ein vorhersagbares Attribut aus. Wenn Sie die Spalte beim Erstellen des Modells nicht als vorhersagbar definiert haben, ist das Hinzufügen hier nicht möglich.|  
|**Wert 1**|Wählen Sie einen Status des vorhersagbaren Attributs aus, der mit dem in **Wert 2**enthaltenen Wert verglichen wird.<br /><br /> Sie können zwei beliebige diskrete oder diskretisierte Werte vergleichen. Sie können jedoch keinen Wert mit seinem Komplement vergleichen wie in anderen Viewern.|  
|**Der Wert 2**|Wählen Sie einen Status des vorhersagbaren Attributs aus, der mit dem in **Wert 1**enthaltenen Wert verglichen wird.|  
  
 **Variablen**  
 In diesem Bereich der Registerkarte **Neuronales Netzwerk** wird ein interaktives Balkendiagramm angezeigt, das von den ausgewählten Werten für Eingabe- und Ergebnisattribute abhängt. Da in einem neuronalen Netzwerk die Wahrscheinlichkeit berechnet wird, dass ein bestimmter Wert Auswirkungen auf ein bestimmtes Ergebnis hat, können Sie eine beliebige Kombination von Eingaben auswählen, und im Balkendiagramm wird angezeigt, welche Auswirkungen diese Kombination auf das Paar von Ergebnissen hat, die Sie vergleichen.  
  
|value|Description|  
|-----------|-----------------|  
|**Attribut**|Zeigt den Namen des unter **Attribut**ausgewählten vorhersagbaren Attributs an.|  
|**ReplTest1**|Zeigt den Wert für das ausgewählte Eingabeattribut an.|  
|**Begünstigt \<Wert 1 >**|Zeigt einen Balken an, der angibt, wie sehr sich diese Attribut/Wert-Kombination auf das in **Wert 1** ausgewählte Zielergebnis auswirkt.|  
|**Begünstigt \<Wert 2 >**|Zeigt einen Balken an, der angibt, wie sehr sich diese Attribut/Wert-Kombination auf das in **Wert 2** ausgewählte Zielergebnis auswirkt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Datamining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  