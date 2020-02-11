---
title: Zielsuchszenario (Tabellenanalyse Tools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- scenario analysis
- goal seek scenario
ms.assetid: efe50306-cf7c-46b3-9cc4-e7f0b6968b0c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d547c52bc5d4cb02870fc647469b5f63af9ab7cb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66080740"
---
# <a name="goal-seek-scenario-table-analysis-tools-for-excel"></a>Zielsucheszenario (Tabellenanalysetools für Excel)
  ![Zielsuche (Schaltfläche in Tabellenanalysetools)](media/tat-goalseek.gif "Zielsuche (Schaltfläche in Tabellenanalysetools)")  
  
 Das Tool " **zielsuchszenario** " ist eine Ergänzung zum [What if](what-if-scenario-table-analysis-tools-for-excel.md) Scenario-Tool. Das **Was-wäre-wenn-** Tool informiert Sie über die Auswirkungen einer Änderung, während das Tool " **Zielsuche** " die zugrunde liegenden Faktoren anzeigt, die geändert werden müssen, um ein gewünschtes Ergebnis zu erzielen.  
  
 Nehmen wir beispielsweise an, Sie möchten die Kundenzufriedenheit steigern. Mithilfe der **Zielsuche** können Sie feststellen, welche Faktoren die Kundenzufriedenheit am wahrscheinlichsten steigern und entscheiden, ob diese Änderungen kostengünstig sind.  
  
 Nach Abschluss der Analyse durch das Tool werden zwei neue Spalten in der Quelldatentabelle erstellt. Diese Spalten zeigen die *Wahrscheinlichkeit* , dass das Zielergebnis erreicht werden kann, und ggf. die empfohlene Änderung an.  
  
 Das Tool kann ein Dataset analysieren und Voraussagen für den gesamten Satz treffen, oder Sie können die Analyse erstellen und dann Szenarios einzeln testen.  
  
## <a name="using-the-goal-seek-scenario-tool"></a>Verwenden des Zielsucheszenario-Tools  
  
1.  Öffnen Sie eine Excel-Tabelle.  
  
2.  Klicken Sie auf **Szenarien**, und wählen Sie **Zielsuche**aus.  
  
3.  Wählen Sie im Dialogfeld **Szenarienanalyse: Zielsuche** in der Liste die Spalte aus, die den Zielwert enthält.  
  
4.  Geben Sie den Wert an, den Sie erzielen möchten.  
  
     Wenn das Spaltenziel fortlaufende numerische Werte enthält, können Sie auch eine gewünschte Zunahme oder Abnahme des Werts angeben. Beispielsweise können Sie **Sales** als Spalte auswählen und angeben, dass das Ziel eine Erhöhung von 120% ist.  
  
     Sie können das Ziel auch als Wertebereich angeben, indem Sie eine Unter- und Obergrenze angeben.  
  
5.  Geben Sie die Spalte an, die die Werte enthält, die Sie ändern möchten. Wählen Sie mit anderen Worten die Spalte aus, die bearbeitet werden muss, um das gewünschte Ergebnis zu erzielen.  
  
6.  Klicken Sie optional auf **Spalten auswählen, die für die Analyse verwendet werden**sollen, und wählen Sie Spalten aus, die nützliche Informationen enthalten. Heben Sie die Auswahl der Spalten auf, die nicht zur Analyse beitragen.  
  
    > [!NOTE]  
    >  Heben Sie die Auswahl nicht für Spalten auf, die Sie entweder für das Ziel oder die Änderung verwenden. Diese Spalten sind erforderlich.  
  
7.  Geben Sie an, ob Sie Vorhersagen für die gesamte Tabelle oder nur für die ausgewählten Ziele erstellen möchten.  
  
8.  Wenn Sie die **gesamte Tabellen** Option ausgewählt haben, fügt das Tool die Vorhersagen der Quell Tabelle in zwei neue Spalten hinzu.  
  
9. Wenn Sie die Option **in dieser Zeile**ausgewählt haben, werden die Ergebnisse der Analyse im Dialogfeld zur Überprüfung ausgegeben. Das Dialogfeld bleibt geöffnet, damit Sie damit fortfahren können, andere Werte und Ziele auszuprobieren.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Für dieses Tool wird der Microsoft Logistic Regression-Algorithmus verwendet, der numerische oder diskrete Werte verarbeiten kann.  
  
 Sie können die Vorhersage mehrere Male ausführen und zu einem späteren Zeitpunkt andere Spalten auswählen. Es muss jedoch jede Kombination aus Ziel und Änderung separat berechnet werden.  
  
 Sie erzielen bessere Ergebnisse, wenn Sie Spalten zur Analyse auswählen, die nützliche Informationen enthalten. Wenn Sie jedoch zu wenige Spalten einbeziehen, ist es u. U. schwierig, ein Ergebnis zu erzielen.  
  
 Stellen Sie beim Erstellen von Vorhersagen sicher, dass Sie eine Zeile auswählen, die nicht bereits das gewünschte Ergebnis enthält, andernfalls erhalten Sie einen Fehler. Mit anderen Worten: Wenn der Zweck einer Zielsuche ist, begünstigende Faktoren für einen Fahrradkauf zu ermitteln, sollten nur Kunden einbezogen werden, die noch kein Fahrrad gekauft haben.  
  
## <a name="understanding-the-results-of-goal-seek-analysis"></a>Grundlegendes zu den Ergebnissen der Zielsucheanalyse  
 Beim Erstellen eines Zielsucheszenarios werden vom Tool die folgenden drei Vorgänge ausgeführt:  
  
-   Es wird eine Data Mining-Struktur erstellt, in der wichtige Fakten zu den Daten in der Tabelle gespeichert werden.  
  
-   Es wird anhand der Daten ein Logistic Regression-Miningmodell erstellt.  
  
-   Es wird eine Vorhersage für jeden Wert erstellt, den Sie angeben.  
  
 Wenn Sie Zielsucheszenarios einzeln testen, können Sie die Ergebnisse interaktiv anzeigen. Dies entspricht dem Erstellen einer *SINGLETON-Vorhersage Abfrage*.  
  
 Das Tool meldet im **Ergebnis** Bereich des Dialog Felds, ob es erfolgreich ein Szenario gefunden hat, das das gewünschte Ziel erreicht. Wenn eine erfolgreiche Lösung gefunden wurde, generiert das Tool auch eine Empfehlung mit der erforderlichen Änderung. Das Tool zur **Zielsuche** könnte z. b. Aufschluss darüber geben, dass die Verbindungs Distanz weniger als 5 Kilometer betragen sollte.  
  
 Beispielergebnisse:  
  
 **Bei der Zielsuche für Interesse am Kauf wurde eine Lösung gefunden.**  
  
 **Nächster Treffer erreicht durch Ändern von 'Entfernung zur Arbeit' in '2-5 km'.**  
  
 Da dieses Ergebnis auf einer vorhandenen Zeile in der Datentabelle beruht, bedeutet dies Folgendes: Wenn alle Werte dieses Kunden unverändert bleiben, aber sich der Arbeitsweg auf 2 – 5 km reduziert, ist es wahrscheinlich, dass der Kunde ein Fahrrad kauft.  
  
 Wenn Sie Ziel basierte Vorhersagen für alle Zeilen in der Excel-Tabelle erstellen, indem Sie die **gesamte Tabelle**angeben, erstellt das Tool zwei neue Spalten in der ursprünglichen Datentabelle. Die erste der Tabelle hinzugefügte Spalte enthält entweder ein Häkchen in einem grünen Kreis, was bedeutet, dass das Ziel erreicht werden kann, oder ein X in einem roten Kreis, was bedeutet, dass das Ziel durch keine Änderung erreicht werden kann.  
  
 Die zweite Spalte enthält die empfohlene Änderung.  
  
> [!NOTE]  
>  Der Vertrauensgrad der Empfehlung und ihr Erfolg sind durch den Algorithmus vorbestimmt und können nicht geändert werden.  
  
## <a name="related-tools"></a>Verwandte Tools  
 Der Data Mining-Client für Excel, bei dem es sich um ein separates Add-In mit erweiterter Data Mining-Funktionalität handelt, enthält Assistenten zum Erstellen von Data Mining-Modellen, die Verhalten vorhersagen. Weitere Informationen finden Sie unter [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md).  
  
 Weitere Informationen zum Algorithmus, der vom Tool für das Tool zur **Zielsuche** verwendet wird, finden Sie im Thema "Microsoft Logistic [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Regression-Algorithmus" in der-Online Dokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
