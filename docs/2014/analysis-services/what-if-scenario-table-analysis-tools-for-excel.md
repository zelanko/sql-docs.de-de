---
title: Was-wäre-wenn-Szenario (Tabellenanalyse Tools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- what if scenario
- scenario analysis
ms.assetid: 4df5a5c5-1983-4009-a7c5-cd340649fd2f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 49b642d60da57192bc0c6bf842a16b0d12d529d5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175549"
---
# <a name="what-if-scenario-table-analysis-tools-for-excel"></a>Was-wäre-wenn-Szenario (Tabellenanalysetools für Excel)
  ![Schaltfläche für Was-wäre-wenn-Szenario in der Leiste "Tabellenanalysetools"](media/tat-whatif.gif "Schaltfläche für Was-wäre-wenn-Szenario in der Leiste "Tabellenanalysetools"")

 Das **Was-wäre-wenn-** szenariotool analysiert Muster in vorhandenen Daten und ermöglicht es Ihnen, die Auswirkung zu bewerten, die Änderungen in einer Spalte auf den Wert einer anderen Spalte haben.

 Beispielsweise können Sie die Auswirkung einer Preiserhöhung für einen Artikel auf dessen Gesamtumsatz prüfen.

 Das Tool lässt beliebig viele Vorhersagen zu. Nachdem die erste Analyse abgeschlossen wurde, können Sie Änderungen für alle Daten in der Tabelle vorhersagen oder Testwerte nacheinander eingeben.

## <a name="using-the-what-if-scenario-tool"></a>Verwenden des Tools für das Was-wäre-wenn-Szenario

1.  Öffnen Sie eine Excel-Datentabelle.

2.  Klicken Sie auf **Szenarios**und dann auf **Was-wäre-wenn**.

3.  Wählen Sie im Feld **Szenario** die Spalte aus, die den Wert enthält, den Sie ändern möchten, und geben Sie die Änderung entweder als einen bestimmten Wert oder als Prozentsatz der Änderung (entweder erweitert oder verkleinert) für die aktuellen Werte an.

4.  Geben Sie im Feld **Was geschieht mit** die Spalte an, für die Sie den Effekt bewerten möchten.

5.  Klicken Sie optional auf **Spalten auswählen, die für die Analyse verwendet werden** sollen, um Spalten auszuwählen, die bei der Vorhersage wahrscheinlich nützlich sind. Sie können die Auswahl von Spalten aufheben, die beim Erkennen von Mustern wahrscheinlich wenig nützlich sein werden, z. B. Zeilen-IDs oder Namen.

6.  Wählen Sie im Feld **Zeile oder Tabelle angeben** aus, ob die Auswirkung nur für die aktuell ausgewählte Zeile oder für den gesamten Satz von Daten in der Tabelle ausgewertet werden soll.

7.  Wenn Sie in **dieser Zeile**auswählen, zeigt das Tool das Ergebnis im Dialogfeld an. Sie können Ihre Auswahl ändern, um andere Szenarien zu testen, während das Dialogfeld geöffnet ist.

8.  Wenn Sie die **gesamte Tabelle**auswählen, zeigt das Tool eine Statusmeldung im Dialogfeld an und fügt der ursprünglichen Datentabelle zwei neue Spalten hinzu. Klicken Sie auf **Schließen** , um die gesamten Ergebnisse im Arbeitsblatt anzuzeigen.

### <a name="requirements"></a>Anforderungen
 Für dieses Tool wird der Microsoft Logistic Regression-Algorithmus verwendet, der Vorhersagen für numerische oder diskrete Werte unterstützt. Um aber die besten Ergebnisse zu erzielen, sollten Sie die folgenden bewährten Methoden anwenden:

-   Wählen Sie Spalten für die Analyse aus, die nützliche Informationen enthalten.

-   Wenn Sie zu wenige Spalten einschließen, kann das Erzielen von Ergebnissen erschwert werden.

-   Wenn Sie die Option **mit Wert** verwenden, müssen Sie einen Wert in das Feld eingeben oder einen Wert aus der Liste auswählen.

-   Wenn Sie die Option **Prozentsatz** verwenden, legen Sie die Änderung als prozentuale Erhöhung oder Verringerung fest. Der Standardwert ist 120 Prozent, das bedeutet eine Erhöhung von 20 Prozent über den aktuellen Wert.

> [!NOTE]
>  Wenn Sie keinen Wert festlegen, wird möglicherweise ein Fehler angezeigt.

## <a name="understanding-the-results-of-what-if-analysis"></a>Grundlegendes zu den Ergebnissen der Was-wäre-wenn-Analyse
 Wenn Sie ein **Was-wäre-wenn-** Szenario erstellen, erledigt das Tool drei Dinge:

-   Es wird eine Data Mining-Struktur erstellt, in der wichtige Fakten zu den Daten in der Tabelle gespeichert werden.

-   Es wird anhand der Daten ein Logistic Regression-Miningmodell erstellt.

-   Es wird eine Vorhersageabfrage für alle von Ihnen angegebenen Werte erstellt.

 Sie können alle Vorhersagen gleichzeitig ausgeben, indem Sie die **gesamte Tabelle**angeben. Vom Tool werden daraufhin in der ursprünglichen Datentabelle zwei neue Spalten erstellt.

 Die der Tabelle hinzugefügten Spalten enthalten zwei Informationstypen: den geänderten vorhergesagten Wert sowie das Vertrauen in den Wert. Mit Vertrauen ist die Wahrscheinlichkeit gemeint, dass die Vorhersage zutrifft.

 Sie können Änderungswerte auch nacheinander im Dialogfeld eingeben und die Vorhersagen anschließend interaktiv anzeigen. Dies entspricht dem Erstellen einer *SINGLETON-Vorhersage Abfrage*. Die Ergebnisse der Vorhersageabfrage werden zusammen mit den folgenden Informationen ausgegeben: dem Erfolg oder Fehler der Vorhersage, dem vorhergesagten Wert sowie dem Vertrauensgrad. Der Vertrauensgrad wird als Leiste mit einer gepunkteten Linie angezeigt. Je länger die gepunktete Linie ist, desto höher ist das Vertrauen in das Ergebnis.

 Wenn Sie z. b. versuchen, die Auswirkung der Erhöhung des Alters des Kunden auf den Kauf zu ermitteln und das Alter des Kunden auf 25 zu erhöhen, fragt das **Was-wäre-wenn-** Tool das Data Mining Modell ab und gibt das folgende Ergebnis zurück:

 **Bei der Was-wäre-wenn-Analyse für Fahrradverkäufe wurde eine Lösung gefunden.**

 **'Fahrradverkäufe' = ja**

 **Vertrauen: Durchschnittlich**

 Da dieses Ergebnis auf einer vorhandenen Zeile in der Datentabelle beruht, bedeutet das bei einem bestimmten Kunden Folgendes: Wenn alle anderen Werte zum Kunden unverändert bleiben, das Alter des Kunden jedoch auf 25 erhöht wird, kauft der Kunde wahrscheinlich ein Fahrrad.

 Die Ausgabe der Vorhersagen in die ursprüngliche Datentabelle vereinfacht möglicherweise die Überprüfung, ob die Vorhersagen nützlich sind.

## <a name="related-tools"></a>Verwandte Tools
 Der Data Mining-Client für Excel, bei dem es sich um ein separates Add-In mit erweiterter Data Mining-Funktionalität handelt, enthält Assistenten zum Erstellen von Data Mining-Modellen, die Verhalten vorhersagen. Weitere Informationen finden Sie unter [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md).

 Weitere Informationen zum Algorithmus, der vom **Was-wäre-wenn-Szenario-** Tool verwendet wird, finden Sie im Thema "Microsoft Logistic Regression-Algorithmus" in SQL Server-Onlinedokumentation.

## <a name="see-also"></a>Weitere Informationen
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)


