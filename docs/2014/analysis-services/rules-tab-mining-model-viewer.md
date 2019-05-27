---
title: "\"Regeln\" (Miningmodell-Viewer) | Microsoft-Dokumentation"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.associationrules.rules.f1
ms.assetid: 705d5492-b58f-45d9-94d7-ed57b7025823
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fca78578046122a1598df096e45965367b7880ad
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66070103"
---
# <a name="rules-tab-mining-model-viewer"></a>Registerkarte "Regeln" (Miningmodell-Viewer)
  Im Bereich **Regeln** in einem Zuordnungsmodell können Sie die Regeln anzeigen, die vom Algorithmus aus den Daten extrahiert wurden. Regeln beschreiben, in welcher Beziehung Elemente zueinander stehen, und können zum Erstellen von Empfehlungen verwendet werden.  
  
 Mit den Optionen im Viewer können Sie die Anzahl der im Viewer angezeigten Regeln filtern.  
  
> [!WARNING]  
>  Standardmäßig werden nur die Regeln im Viewer angezeigt, die über dem in **Minimale Wahrscheinlichkeit** definierten Schwellenwert für die Wahrscheinlichkeit liegen. Dieser Wert kann im Viewer nicht verringert werden, da der Wahrscheinlichkeitsschwellenwert für Regelausgaben beim Erstellen des Modells bestimmt wird. Weitere Informationen finden Sie unter [Technische Referenz für den Microsoft Association-Algorithmus](data-mining/microsoft-association-algorithm-technical-reference.md).  
  
 **Weitere Informationen finden Sie unter** [Microsoft Association-Algorithmus](data-mining/microsoft-association-algorithm.md), [Durchsuchen eines Modells mit dem Microsoft Association Rules-Viewer](data-mining/browse-a-model-using-the-microsoft-association-rules-viewer.md)  
  
## <a name="options"></a>Optionen  
 **Viewerinhalt aktualisieren**  
 Lädt das Miningmodell im Viewer neu.  
  
 **Miningmodell**  
 Wählen Sie ein anzuzeigendes, in der aktuellen Miningstruktur enthaltenes Miningmodell aus. Das Miningmodell wird im dazugehörigen Viewer geöffnet.  
  
 **Viewer**  
 Wählen Sie einen Viewer aus, mit dem das ausgewählte Miningmodell angezeigt werden soll. Sie können für jedes Miningmodell den benutzerdefinierten Viewer oder den **Microsoft Generic Content Tree Viewer**verwenden. Sie können auch Plug-In-Viewer verwenden, falls diese verfügbar sind.  
  
 **Minimale Wahrscheinlichkeit**  
 Ändern Sie diesen Wert, um die erforderliche minimale Wahrscheinlichkeit festzulegen, damit eine Regel im Viewer angezeigt wird. Wenn Sie den Wert für die Wahrscheinlichkeit erhöhen, wird die Anzahl der angezeigten Regeln verringert.  
  
 **Minimale Wichtigkeit**  
 Ändern Sie diesen Wert, um die erforderliche minimale Wichtigkeit festzulegen, damit eine Regel im Viewer angezeigt wird. Wenn Sie den Wert für die Wichtigkeit erhöhen, wird die Anzahl der angezeigten Regeln verringert.  
  
 **Filterregel**  
 Geben Sie einen Zeichenfolgenwert ein, um die Anzahl der im Viewer angezeigten Regeln zu filtern.  
  
 Sie können auch reguläre .NET-Ausdrücke als Filterkriterien eingeben. Der folgende Ausdruck gibt z. B. alle Regeln zurück, die 'Road Bottle Cage' auf der linken Seite der Regel enthalten:  
  
 `\bRoad\b.\bBottle\b.\bCage\b.*->.*`  
  
 Beachten Sie, dass Sie die Sicht möglicherweise aktualisieren müssen, damit die Filterkriterien angewendet werden. Sie können auch die Option **Langen Namen anzeigen** aktivieren und deaktivieren, um die Liste zu aktualisieren.  
  
 Standardmäßig wird ein Filterkriterium auf den vollständigen Namen der Attribut/Wert-Kombination angewendet. Wenn Sie nur den Attributnamen anzeigen, ist daher möglicherweise nicht gleich erkennbar, dass das Filterkriterium richtig angewendet wurde. Wählen Sie in der Dropdownliste **Anzeigen** die Option **Attributnamen und Wert anzeigen**aus, und überprüfen Sie, ob die Liste der Itemsets richtig gefiltert wurde.  
  
 **Anzeigen**  
 Passen Sie an, wie die Regel im Viewer angezeigt wird. Sie können eine der drei folgenden Optionen auswählen:  
  
-   Attributnamen und Wert anzeigen  
  
-   Nur Attributwert anzeigen  
  
-   Nur Attributnamen anzeigen  
  
 **Langen Namen anzeigen**  
 Zeigt den vollständigen Namen der Regel so an, wie er im Inhalt des Miningmodells enthalten ist.  
  
 **Maximale Zeilenanzahl**  
 Beschränkt die Anzahl der Regeln, die im Viewer angezeigt werden.  
  
 **Wahrscheinlichkeit**  
 In dieser Spalte im Diagramm wird die Wahrscheinlichkeit für jede Regel angezeigt.  
  
 Sie können auf die Spaltenüberschrift klicken, um nach Wahrscheinlichkeit zu sortieren.  
  
 **Wichtigkeit**  
 In dieser Spalte im Diagramm wird die Wichtigkeit für jede Regel angezeigt.  
  
 Sie können auf die Spaltenüberschrift klicken, um nach Wichtigkeit zu sortieren.  
  
 **Rule**  
 In dieser Spalte im Diagramm wird die Textbeschreibung für jede Regel angezeigt, dabei wird das mit den Optionen **Anzeigen** und **Langen Namen anzeigen**angegebene Format verwendet.  
  
 Sie können auf die Spaltenüberschrift klicken, um nach dem Text der Regel zu sortieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Data Mining-Algorithmen &#40;Analysis Services – Data Mining&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Miningmodell-Viewer &#40;Data Mining-Modelldesigner&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Data Mining-Modell-Viewer](data-mining/data-mining-model-viewers.md)  
  
  
