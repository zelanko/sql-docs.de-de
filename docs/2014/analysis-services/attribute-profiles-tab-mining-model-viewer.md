---
title: Registerkarte "Attribut profile" (Mining Modell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.profiles.f1
ms.assetid: 17c7e7ae-273c-4a6b-9a35-e8b9b8e65999
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4df97455d2fae8cb3375967a8e37a2329a7509fa
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527912"
---
# <a name="attribute-profiles-tab-mining-model-viewer"></a>Registerkarte "Attributprofile" (Miningmodell-Viewer)
  Mit der Registerkarte **Attributprofile** können Sie anzeigen, welche Auswirkungen die Verteilung der Eingabewerte in einem Naive Bayes-Modellstatus auf die einzelnen Status des Ergebnisattributs hat. Die Verteilung der Werte wird als farbiges Histogramm angezeigt, und alle Verteilungen werden in einem Tabellenformat dargestellt, um das Vergleichen der Werte zu erleichtern.  
  
 **Weitere Informationen:** [Microsoft Naive Bayes-Algorithmus](data-mining/microsoft-naive-bayes-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Naive Bayes-Viewer](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Mining Modell**  
 Wählen Sie ein anzuzeigendes Miningmodell aus der aktuellen Miningstruktur aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie den Viewer aus, der zum Durchsuchen des ausgewählten Miningmodells verwendet werden soll. Sie können den für jedes Miningmodell bereitgestellten benutzerdefinierten Viewer oder den [!INCLUDE[msCoName](../includes/msconame-md.md)] -Viewer für Mininginhalte auswählen. Sie können auch Plug-In-Viewer verwenden, wenn diese verfügbar sind.  
  
 **Legende anzeigen**  
 Wählen Sie diese Option aus, um einen Schlüssel anzuzeigen, der jeden Wert in **Status** einer der im Verteilungsdiagramm verwendeten Farben zuordnet.  
  
 **Histogrammbalken**  
 Wählen Sie aus, wie viele Balken das Histogramm enthalten soll. Sind mehr Balken vorhanden, als Sie für die Anzeige ausgewählt haben, werden die wichtigsten Balken beibehalten, und die restlichen Balken werden unter **Sonstige**gruppiert.  
  
 **Vorhersagbar**  
 Wählen Sie eine vorhersagbare Spalte aus dem Miningmodell aus.  
  
 **Attribut profile**  
 Die Tabelle umfasst die folgenden Spalten:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**Attribute**|Listet die Miningmodellspalten auf, die im Miningmodell enthalten sind.|  
|**Status**|Eine optionale Spalte, die beschreibt, welchen Status die Farbe der entsprechenden Zeile von Attributen darstellt. Verwenden Sie zum Hinzufügen oder Entfernen das Kontrollkästchen **Legende anzeigen** .|  
|**Bevölkerungs**|Zeigt die Verteilung der Attribute über das gesamte Dataset an.|  
|**Spalte für Status des vorhersagbaren Attributs**|Zeigt eine Spalte für jeden Status der vorhersagbaren Spalte an; dabei entspricht jede Zeile einem Eingabeattribut im Modell.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Data Mining-Algorithmen &#40;Analysis Services Data Mining-&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Mining Modell-Viewer &#40;Data Mining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
