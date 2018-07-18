---
title: Zielsucheszenario (Tabellenanalysetools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- scenario analysis
- goal seek scenario
ms.assetid: efe50306-cf7c-46b3-9cc4-e7f0b6968b0c
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2f17c85c7296daaead3b24b4d4002ad9c1be7221
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187297"
---
# <a name="goal-seek-scenario-table-analysis-tools-for-excel"></a>Zielsucheszenario (Tabellenanalysetools für Excel)
  ![Ziel suchen-Schaltfläche in Tabellenanalysetools](media/tat-goalseek.gif "Zielsuche-Schaltfläche in Tabellenanalysetools")  
  
 Die **Zielsuche** Szenario ist eine Ergänzung zu den [was geschieht, wenn](what-if-scenario-table-analysis-tools-for-excel.md) Szenario. Die **What-If** Tool informiert Sie die Auswirkungen einer Änderung, während die **Zielsuche** Tool informiert Sie die zugrunde liegenden Faktoren, die geändert werden müssen, um ein gewünschtes Ergebnis zu erzielen.  
  
 Angenommen, Sie möchten die Kundenzufriedenheit erhöhen. Sie können **Zielsuche** Analysen, um zu bestimmen, welche Faktoren die Kundenzufriedenheit zu erhöhen, und entscheiden, ob diese Änderungen kosteneffizient sind am wahrscheinlichsten werden würde.  
  
 Nach Abschluss der Analyse durch das Tool werden zwei neue Spalten in der Quelldatentabelle erstellt. Diese Spalten zeigen die *Wahrscheinlichkeit* , die das gewünschte Ergebnis erreicht werden kann, und ggf. die empfohlene Änderung.  
  
 Das Tool kann ein Dataset analysieren und Voraussagen für den gesamten Satz treffen, oder Sie können die Analyse erstellen und dann Szenarios einzeln testen.  
  
## <a name="using-the-goal-seek-scenario-tool"></a>Verwenden des Zielsucheszenario-Tools  
  
1.  Öffnen Sie eine Excel-Tabelle.  
  
2.  Klicken Sie auf **Szenarien**, und wählen Sie **Zielsuche**.  
  
3.  In der **Szenarienanalyse: Zielsuche** wählen Sie im Dialogfeld die Spalte, die das Ziel enthält Wert aus der Liste.  
  
4.  Geben Sie den Wert an, den Sie erzielen möchten.  
  
     Wenn das Spaltenziel fortlaufende numerische Werte enthält, können Sie auch eine gewünschte Zunahme oder Abnahme des Werts angeben. Beispielsweise empfiehlt sich **Sales** wie die Spalte und gibt an, dass das Ziel eine Steigerung von 120 % ist.  
  
     Sie können das Ziel auch als Wertebereich angeben, indem Sie eine Unter- und Obergrenze angeben.  
  
5.  Geben Sie die Spalte an, die die Werte enthält, die Sie ändern möchten. Wählen Sie mit anderen Worten die Spalte aus, die bearbeitet werden muss, um das gewünschte Ergebnis zu erzielen.  
  
6.  Klicken Sie optional auf **Spalten für die Analyse auswählen**, und wählen Sie Spalten, die nützliche Informationen enthalten. Heben Sie die Auswahl der Spalten auf, die nicht zur Analyse beitragen.  
  
    > [!NOTE]  
    >  Heben Sie die Auswahl nicht für Spalten auf, die Sie entweder für das Ziel oder die Änderung verwenden. Diese Spalten sind erforderlich.  
  
7.  Geben Sie an, ob Sie Vorhersagen für die gesamte Tabelle oder nur für die ausgewählten Ziele erstellen möchten.  
  
8.  Bei Auswahl der **ganze Tabelle** können das Tool wird die Vorhersagen auf die Quelltabelle in zwei neuen Spalten hinzugefügt.  
  
9. Wenn Sie die Option **in dieser Zeile**, die Ergebnisse der Analyse werden ausgegeben, um das Dialogfeld zur Überprüfung. Das Dialogfeld bleibt geöffnet, damit Sie damit fortfahren können, andere Werte und Ziele auszuprobieren.  
  
### <a name="requirements"></a>Anforderungen  
 Für dieses Tool wird der Microsoft Logistic Regression-Algorithmus verwendet, der numerische oder diskrete Werte verarbeiten kann.  
  
 Sie können die Vorhersage mehrere Male ausführen und zu einem späteren Zeitpunkt andere Spalten auswählen. Es muss jedoch jede Kombination aus Ziel und Änderung separat berechnet werden.  
  
 Sie erzielen bessere Ergebnisse, wenn Sie Spalten zur Analyse auswählen, die nützliche Informationen enthalten. Wenn Sie jedoch zu wenige Spalten einbeziehen, ist es u. U. schwierig, ein Ergebnis zu erzielen.  
  
 Stellen Sie beim Erstellen von Vorhersagen sicher, dass Sie eine Zeile auswählen, die nicht bereits das gewünschte Ergebnis enthält, andernfalls erhalten Sie einen Fehler. Mit anderen Worten: Wenn der Zweck einer Zielsuche ist, begünstigende Faktoren für einen Fahrradkauf zu ermitteln, sollten nur Kunden einbezogen werden, die noch kein Fahrrad gekauft haben.  
  
## <a name="understanding-the-results-of-goal-seek-analysis"></a>Grundlegendes zu den Ergebnissen der Zielsucheanalyse  
 Beim Erstellen eines Zielsucheszenarios werden vom Tool die folgenden drei Vorgänge ausgeführt:  
  
-   Es wird eine Data Mining-Struktur erstellt, in der wichtige Fakten zu den Daten in der Tabelle gespeichert werden.  
  
-   Es wird anhand der Daten ein Logistic Regression-Miningmodell erstellt.  
  
-   Es wird eine Vorhersage für jeden Wert erstellt, den Sie angeben.  
  
 Wenn Sie Zielsucheszenarios einzeln testen, können Sie die Ergebnisse interaktiv anzeigen. Dies ist dasselbe wie das Erstellen einer *Singleton-Vorhersageabfrage*.  
  
 Das Tool meldet, der **Ergebnisse** Bereich des Dialogfelds Feld, ob es erfolgreich beim Suchen eines Szenarios, die das gewünschte Ergebnis erzielt. Wenn eine erfolgreiche Lösung gefunden wurde, generiert das Tool auch eine Empfehlung mit der erforderlichen Änderung. Z. B. die **Zielsuche** Tool kann zeigen, dass der Arbeitsweg auf weniger als 5 Meilen werden soll.  
  
 Beispielergebnisse:  
  
 **Bei der Zielsuche für Interesse am Kauf wurde eine Lösung gefunden.**  
  
 **Nächster Treffer erreicht durch Ändern von 'Entfernung zur Arbeit' in ' 2-5 Miles.**  
  
 Da dieses Ergebnis auf einer vorhandenen Zeile in der Datentabelle beruht, bedeutet dies Folgendes: Wenn alle Werte dieses Kunden unverändert bleiben, aber sich der Arbeitsweg auf 2 – 5 km reduziert, ist es wahrscheinlich, dass der Kunde ein Fahrrad kauft.  
  
 Wenn Sie zielsuchevorhersagen für alle Zeilen in der Excel-Tabelle, durch Angabe erstellen **ganze Tabelle**, theTool gespeichert erstellt zwei neue Spalten in der ursprünglichen Datentabelle. Die erste der Tabelle hinzugefügte Spalte enthält entweder ein Häkchen in einem grünen Kreis, was bedeutet, dass das Ziel erreicht werden kann, oder ein X in einem roten Kreis, was bedeutet, dass das Ziel durch keine Änderung erreicht werden kann.  
  
 Die zweite Spalte enthält die empfohlene Änderung.  
  
> [!NOTE]  
>  Der Vertrauensgrad der Empfehlung und ihr Erfolg sind durch den Algorithmus vorbestimmt und können nicht geändert werden.  
  
## <a name="related-tools"></a>Verwandte Tools  
 Der Data Mining-Client für Excel, bei dem es sich um ein separates Add-In mit erweiterter Data Mining-Funktionalität handelt, enthält Assistenten zum Erstellen von Data Mining-Modellen, die Verhalten vorhersagen. Weitere Informationen finden Sie unter [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md).  
  
 Weitere Informationen zu den vom verwendeten Algorithmus die **Zielsuche** Szenario finden Sie unter dem Thema "Microsoft Logistic Regression-Algorithmus" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
