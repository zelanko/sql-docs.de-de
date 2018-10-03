---
title: Registerkarte "Itemsets" (Miningmodell-Viewer) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.itemsets.f1
ms.assetid: 95b2b805-b142-4064-9c80-4b1b3fe2fe63
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 60c5dc93ea10042ff87b48bdb8ca4c8d6de1108b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48060340"
---
# <a name="itemsets-tab-mining-model-viewer"></a>Registerkarte "Itemsets" (Miningmodell-Viewer)
  Im Bereich **Itemsets** werden die häufig in einem Miningmodell für Zuordnungsregeln enthaltenen Itemsets angezeigt. Da ein Zuordnungsmodell viele Itemsets enthalten kann, werden im Viewer Steuerelemente bereitgestellt, mit denen Sie die im Viewer angezeigten Itemsets filtern können.  
  
 **Weitere Informationen:** [Microsoft Association-Algorithmus](data-mining/microsoft-association-algorithm.md), [Modell mit dem Microsoft-Viewer für Zuordnungsregeln durchsuchen](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a>Tastatur  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein anzuzeigendes, in der aktuellen Miningstruktur enthaltenes Miningmodell aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie einen Viewer aus, mit dem das ausgewählte Miningmodell angezeigt werden soll. Sie können entweder den benutzerdefinierten Viewer für Zuordnungsmodelle oder den [!INCLUDE[msCoName](../includes/msconame-md.md)] Generic Content Tree Viewer verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Minimaler Unterstützungswert**  
 Ändern Sie diesen Wert, um den Unterstützungswert festzulegen, den ein Itemset enthalten muss, um im Viewer angezeigt zu werden. Der Standardwert, der beim ersten Öffnen des Modells angezeigt wird, wird vom Modell berechnet, Sie können ihn jedoch ändern, um mehr oder weniger Itemsets anzuzeigen.  
  
 **Mindestgröße des Itemsets**  
 Ändern Sie diesen Wert, um die Mindestanzahl von Elementen festzulegen, die in einem Itemset enthalten sein müssen, bevor das Itemset im Viewer angezeigt werden kann.  
  
 **Filteritemset**  
 Geben Sie einen Zeichenfolgenwert ein, um die Anzahl der im Viewer angezeigten Itemsets zu filtern.  
  
 Sie können auch reguläre .NET-Ausdrücke als Filterkriterien eingeben. Der folgende Ausdruck gibt z. B. alle Itemsets zurück, die 'Road Bottle Cage' enthalten:  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*`  
  
 Beachten Sie, dass Sie die Sicht möglicherweise aktualisieren müssen, damit die Filterkriterien angewendet werden. Sie können auch die Option **Langen Namen anzeigen** aktivieren und deaktivieren, um die Liste zu aktualisieren.  
  
 Standardmäßig wird ein Filterkriterium auf den vollständigen Namen der Attribut/Wert-Kombination angewendet. Wenn Sie nur den Attributnamen anzeigen, ist daher möglicherweise nicht gleich erkennbar, dass das Filterkriterium richtig angewendet wurde. Wählen Sie in der Dropdownliste **Anzeigen** die Option **Attributnamen und Wert anzeigen**aus, und überprüfen Sie, ob die Liste der Itemsets richtig gefiltert wurde.  
  
 **Anzeigen**  
 Passen Sie an, wie das Itemset im Viewer angezeigt wird. Sie können eine der drei folgenden Optionen auswählen:  
  
-   Attributnamen und Wert anzeigen  
  
-   Nur Attributwert anzeigen  
  
-   Nur Attributnamen anzeigen  
  
 Beachten Sie, dass mit dieser Option das Modell nicht erneut abgefragt wird. Es werden nur die Attribute oder Werte gefiltert, die angezeigt werden.  
  
 **Langen Namen anzeigen**  
 Wählen Sie diese Option aus, um den vollständigen Namen des Itemsets anzuzeigen, wie er im Miningmodellinhalt angezeigt wird.  
  
 **Maximale Zeilenanzahl**  
 Beschränkt die Anzahl der Itemsets, die im Viewer angezeigt werden. Standardmäßig werden Itemsets in absteigender Reihenfolge nach Unterstützung sortiert, durch Verringern dieses Werts wird die Liste daher auf die häufigsten Itemsets eingeschränkt.  
  
 **Unterstützung**  
 Zeigt den Unterstützungswert der einzelnen Itemsets an.  
  
 **Größe**  
 Zeigt an, wie viele Elemente in jedem Itemset vorhanden sind.  
  
 **Itemsets**  
 Zeigt die Beschreibung für jedes Itemset an. Standardmäßig werden Itemsets als durch Trennzeichen getrennte Liste von Attributen und ihren Werten dargestellt. Mit der Option **Anzeigen** können Sie ändern, wie sie angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Datamining-Algorithmen &#40;Analysis Services – Datamining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Datamining-Modell-Designer&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
