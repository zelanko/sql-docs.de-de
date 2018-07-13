---
title: Registerkarte ' Kreuzvalidierung ' (Mininggenauigkeitsdiagrammsicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.crossvalidation.f1
ms.assetid: bd215a68-1ad7-4046-9c44-ec8e2be13a64
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a30cf9ce920f7e0416e46dd87044ef7e3d52318c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169821"
---
# <a name="cross-validation-tab-mining-accuracy-chart-view"></a>Übergreifende Überprüfung (Registerkarte, Mininggenauigkeitsdiagramm-Sicht)
  Mithilfe der übergreifenden Überprüfung können Sie eine Miningstruktur in Querschnitte partitionieren und Modelle anhand der einzelnen Querschnitte iterativ trainieren und testen. Sie geben eine Anzahl von Aufteilungen für die Daten an. Die einzelnen Aufteilungen werden der Reihe nach als Testdaten verwendet, während mit den jeweils verbleibenden Daten ein neues Modell trainiert wird. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] generiert dann eine Gruppe vorgegebener genauigkeitsmetriken für jedes Modell. Durch den Vergleich der Metriken für die für die einzelnen Querschnitte generierten Modelle erhalten Sie Aufschluss über die Zuverlässigkeit des Miningmodells für das ganze Dataset.  
  
 Weitere Informationen finden Sie unter [Cross-Validation &#40;Analysis Services - Data Mining&#41;](data-mining/cross-validation-analysis-services-data-mining.md).  
  
> [!NOTE]  
>  Die übergreifende Überprüfung kann nicht bei Modellen verwendet werden, die mithilfe des [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus oder des [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering-Algorithmus erstellt wurden. Wenn Sie den Bericht für eine Miningstruktur mit diesen Typen von Modellen ausführen, werden die Modelle im Bericht nicht berücksichtigt.  
  
## <a name="task-list"></a>Aufgabenliste  
  
-   Geben Sie die Anzahl von Aufteilungen an.  
  
-   Geben Sie die maximale Anzahl von Fällen an, die für die übergreifende Überprüfung zu verwenden sind.  
  
-   Geben Sie die vorhersagbare Spalte an.  
  
-   Geben Sie optional einen vorhersagbaren Status an.  
  
-   Legen Sie optional Parameter fest, mit denen gesteuert wird, wie die Genauigkeit der Vorhersage bewertet wird.  
  
-   Klicken Sie auf **Ergebnisse abrufen** , um die Ergebnisse der übergreifenden Überprüfung anzuzeigen.  
  
## <a name="uielement-list"></a>Liste der Benutzeroberflächenelemente  
 **Foldanzahl**  
 Geben Sie die Anzahl von zu erstellenden Aufteilungen (oder Partitionen) an. Der Minimalwert ist 2. Das bedeutet, dass die eine Hälfte des Datasets zum Testen und die andere zum Trainieren verwendet wird.  
  
 Der Maximalwert für Sitzungsminingstrukturen ist 10.  
  
 Der Maximalwert ist 256, wenn die Miningstruktur in einer Instanz von [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]gespeichert ist.  
  
> [!NOTE]  
>  Wenn Sie die Anzahl der Aufteilungen erhöhen, verlängert sich entsprechend auch die für die Ausführung der Kreuzvalidierung erforderliche Zeit um n. Wenn der Wert von **Foldanzahl** zu hoch ist, können unter Umständen Leistungsprobleme auftreten.  
  
 **Maximale Anzahl von Fällen**  
 Geben Sie die maximale Anzahl von Fällen an, die für die übergreifende Überprüfung zu verwenden sind. Die Anzahl von Fällen in einer bestimmten Aufteilung entspricht dem Wert **Maximale Anzahl von Fällen** geteilt durch den Wert **Foldanzahl** .  
  
 Wenn Sie **0**verwenden, werden alle Fälle in den Quelldaten für die übergreifende Überprüfung verwendet.  
  
 Es gibt keinen Standardwert.  
  
> [!NOTE]  
>  In dem Maße, in dem Sie die Anzahl von Fällen erhöhen, nimmt auch die Verarbeitungszeit zu.  
  
 **Target-Attribut**  
 Wählen Sie in der Liste der in allen Modellen vorhandenen vorhersagbaren Spalten eine Spalte aus. Sie können jeweils nur eine vorhersagbare Spalte auswählen, wenn Sie eine übergreifende Überprüfung ausführen.  
  
 Wählen Sie **Cluster**aus, wenn Sie nur Clustermodelle testen möchten.  
  
 **Zielstatus**  
 Geben Sie einen Wert ein, oder wählen Sie in einer Dropdownliste von Werten einen Zielwert aus.  
  
 Der Standardwert ist `null`. Dieser gibt an, dass alle Status zu testen sind.  
  
 Bei Clustermodellen deaktiviert.  
  
 **target**  **threshold**  
 Geben Sie einen Wert zwischen 0 und 1 an, mit dem die Vorhersagewahrscheinlichkeit angegeben wird, oberhalb derer ein vorhergesagter Status als richtig gewertet wird. Der Wert kann in Schritten von 0,1 festgelegt werden.  
  
 Der Standardwert ist `null`. Dieser gibt an, dass die wahrscheinlichste Vorhersage als richtig gewertet wird.  
  
> [!NOTE]  
>  Sie können den Wert zwar auf 0,0 festlegen, dadurch wird jedoch die Verarbeitungszeit erhöht, und es werden keine brauchbaren Ergebnisse geliefert.  
  
 **Ergebnisse abrufen**  
 Klicken Sie hierauf, um die übergreifende Überprüfung des Modells mit den angegebenen Parametern zu starten.  
  
 Das Modell wird in die angegebene Anzahl von Aufteilungen partitioniert, und für jede Aufteilung wird ein separates Modell getestet. Deshalb kann es einige Zeit dauern, bis die übergreifende Überprüfung Ergebnisse zurückgibt.  
  
 Weitere Informationen zum Interpretieren der Ergebnisse des Berichts für die übergreifende Überprüfung finden Sie unter [Measures im Kreuzvalidierungsbericht](data-mining/measures-in-the-cross-validation-report.md).  
  
## <a name="setting-the-accuracy-threshold"></a>Festlegen des Genauigkeitsschwellenwerts  
 Sie können den Standardwert zum Messen der Vorhersagegenauigkeit steuern, indem Sie einen Wert für **Ziel****schwellenwert** festlegen. Ein Schwellenwert stellt eine Art von Genauigkeitsleiste dar. Jeder Vorhersage wird eine Wahrscheinlichkeit der Richtigkeit des vorhergesagten Werts zugewiesen. Wenn Sie also den **Ziel****schwellenwert** auf einen Wert festlegen, der näher an 1 liegt, muss die Wahrscheinlichkeit für eine bestimmte Vorhersage ziemlich hoch sein, damit diese als gute Vorhersage gewertet wird. Wenn Sie umgekehrt den **Ziel****schwellenwert** auf einen Wert festlegen, der näher an 0 liegt, werden auch Vorhersagen mit niedrigeren Wahrscheinlichkeitswerten als „gute“ Vorhersagen gewertet.  
  
 Es gibt keinen empfohlenen Schwellenwert, da die Wahrscheinlichkeit einer Vorhersage von der Datenmenge und dem Typ der Vorhersage abhängt. Prüfen Sie einige Vorhersagen auf verschiedenen Wahrscheinlichkeitsstufen, um eine geeignete Genauigkeitsleiste für Ihre Daten zu bestimmen. Diese Vorgehensweise ist von Bedeutung, da der Wert, den Sie für **Ziel****schwellenwert** verwenden, Auswirkungen auf die gemessene Genauigkeit des Modells hat.  
  
 Angenommen, es werden drei Vorhersagen für einen bestimmten Zielstatus erstellt, und die Wahrscheinlichkeiten für die einzelnen Vorhersagen liegen bei 0,05, 0,15 und 0,8. Wenn Sie den Schwellenwert auf 0,5 festgelegt haben, wird nur eine Vorhersage als richtig gewertet. Wenn Sie den **Ziel****schwellenwert** auf 0,10 festgelegt haben, werden zwei der Vorhersagen als richtig gewertet.  
  
 Wenn **Ziel** **Schwellenwert** nastaven NA hodnotu `null`, dies ist der Standardwert, wird die wahrscheinlichste Vorhersage für jeden Fall als richtig gewertet. In dem gerade genannten Beispiel sind 0,05, 0,15 und 0,8 die Wahrscheinlichkeiten für Vorhersagen in drei verschiedenen Fällen. Obwohl die Wahrscheinlichkeiten sehr unterschiedlich sind, würde jede Vorhersage als richtig gewertet, da jeder Fall nur eine Vorhersage generiert und es sich dabei um die besten Vorhersagen für diese Fälle handelt.  
  
## <a name="see-also"></a>Siehe auch  
 [Tests und Überprüfung &#40;Datamining&#41;](data-mining/testing-and-validation-data-mining.md)   
 [Übergreifende Überprüfung &#40;Analysis Services – Datamining&#41;](data-mining/cross-validation-analysis-services-data-mining.md)   
 [Measures in der Kreuzvalidierungsbericht](data-mining/measures-in-the-cross-validation-report.md)   
 [Datamining-gespeicherte Prozeduren &#40;Analysis Services – Datamining&#41;](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
  
