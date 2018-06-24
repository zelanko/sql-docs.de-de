---
title: Attribut Profile Registerkarte "(Miningmodell-Viewer) | Microsoft Docs
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
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: a6c9c5e0dfee13c8c0bd08ad5d1c6433d16ca7df
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059038"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a>Registerkarte "Attributprofile" (Miningmodell-Viewer)
  Mit der Registerkarte **Attributprofile** können Sie anzeigen, welche Auswirkungen die Verteilung der Eingabewerte in einem Naive Bayes-Modellstatus auf die einzelnen Status des Ergebnisattributs hat. Die Verteilung der Werte wird als farbiges Histogramm angezeigt, und alle Verteilungen werden in einem Tabellenformat dargestellt, um das Vergleichen der Werte zu erleichtern.  
  
 **Weitere Informationen finden Sie unter:** [Microsoft Naive Bayes-Algorithmus](data-mining/microsoft-naive-bayes-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Tastatur  
 **Viewerinhalt**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein anzuzeigendes Miningmodell aus der aktuellen Miningstruktur aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Ereignisanzeige**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den für jedes Miningmodell bereitgestellten benutzerdefinierten Viewer oder den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Viewer für Mininginhalte auswählen. Sie können auch Plug-In-Viewer verwenden, wenn diese verfügbar sind.  
  
 **Legende anzeigen**  
 Wählen Sie diese Option aus, um einen Schlüssel anzuzeigen, der jeden Wert in **Status** einer der im Verteilungsdiagramm verwendeten Farben zuordnet.  
  
 **Histogrammbalken**  
 Wählen Sie aus, wie viele Balken das Histogramm enthalten soll. Sind mehr Balken vorhanden, als Sie für die Anzeige ausgewählt haben, werden die wichtigsten Balken beibehalten, und die restlichen Balken werden unter **Sonstige**gruppiert.  
  
 **Vorhersagbare**  
 Wählen Sie eine vorhersagbare Spalte aus dem Miningmodell aus.  
  
 **Attributprofile**  
 Die Tabelle enthält folgende Spalten:  
  
|value|Description|  
|-----------|-----------------|  
|**Attribute**|Listet die Miningmodellspalten auf, die im Miningmodell enthalten sind.|  
|**Zustände**|Eine optionale Spalte, die beschreibt, welchen Status die Farbe der entsprechenden Zeile von Attributen darstellt. Verwenden Sie zum Hinzufügen oder Entfernen das Kontrollkästchen **Legende anzeigen** .|  
|**Auffüllung**|Zeigt die Verteilung der Attribute über das gesamte Dataset an.|  
|**Spalte für Status des vorhersagbaren Attributs**|Zeigt eine Spalte für jeden Status der vorhersagbaren Spalte an; dabei entspricht jede Zeile einem Eingabeattribut im Modell.|  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Datamining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  