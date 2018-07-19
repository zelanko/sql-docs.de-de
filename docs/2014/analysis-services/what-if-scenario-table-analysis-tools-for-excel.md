---
title: Was-Wenn-Szenario (Tabellenanalysetools für Excel) | Microsoft-Dokumentation
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
- what if scenario
- scenario analysis
ms.assetid: 4df5a5c5-1983-4009-a7c5-cd340649fd2f
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1edfd62ab4938970a2da22c71724d63953a507c8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37249070"
---
# <a name="what-if-scenario-table-analysis-tools-for-excel"></a>Was-wäre-wenn-Szenario (Tabellenanalysetools für Excel)
  ![Welche Wenn-Szenario-Schaltfläche in Tabellenanalysetools](media/tat-whatif.gif "wäre-wenn-Szenario-Schaltfläche in Tabellenanalysetools")  
  
 Die **What-If** Szenario Tool analysiert Muster in vorhandenen Daten und anschließend können Sie die Auswirkungen zu bewerten, die Änderungen in einer Spalte auf den Wert einer anderen Spalte hätten.  
  
 Beispielsweise können Sie die Auswirkung einer Preiserhöhung für einen Artikel auf dessen Gesamtumsatz prüfen.  
  
 Das Tool lässt beliebig viele Vorhersagen zu. Nachdem die erste Analyse abgeschlossen wurde, können Sie Änderungen für alle Daten in der Tabelle vorhersagen oder Testwerte nacheinander eingeben.  
  
## <a name="using-the-what-if-scenario-tool"></a>Verwenden des Tools für das Was-wäre-wenn-Szenario  
  
1.  Öffnen Sie eine Excel-Datentabelle.  
  
2.  Klicken Sie auf **Szenarien**, und wählen Sie dann **What-If**.  
  
3.  In der **Szenario** wählen die Spalte, die den Wert ändern, und geben Sie die Änderung als spezifischen Wert oder als Prozentsatz der Änderung (vergrößert oder verringert) für die aktuellen Werte enthält.  
  
4.  In der **was geschieht mit** geben die Spalte, die für die Sie die Auswirkung überprüfen möchten.  
  
5.  Klicken Sie optional auf **Spalten für die Analyse auswählen** um Spalten auszuwählen, die wahrscheinlich in der Vorhersage nützlich sind. Sie können die Auswahl von Spalten aufheben, die beim Erkennen von Mustern wahrscheinlich wenig nützlich sein werden, z. B. Zeilen-IDs oder Namen.  
  
6.  In der **Zeile oder Tabelle angeben** wählen, ob die Auswirkungen, die bewertet werden, für die nur die aktuell ausgewählte Zeile oder den vollständigen Satz von Daten in der Tabelle werden soll.  
  
7.  Bei Auswahl von **in dieser Zeile**, das Tool zeigt das Ergebnis in das Dialogfeld. Sie können Ihre Auswahl ändern, um andere Szenarien zu testen, während das Dialogfeld geöffnet ist.  
  
8.  Bei Auswahl von **ganze Tabelle**, das Tool zeigt eine Statusmeldung in das Dialogfeld, und der ursprünglichen Datentabelle zwei neue Spalten hinzugefügt. Klicken Sie auf **schließen** zum Anzeigen der vollständigen Ergebnisse im Arbeitsblatt.  
  
### <a name="requirements"></a>Anforderungen  
 Für dieses Tool wird der Microsoft Logistic Regression-Algorithmus verwendet, der Vorhersagen für numerische oder diskrete Werte unterstützt. Um aber die besten Ergebnisse zu erzielen, sollten Sie die folgenden bewährten Methoden anwenden:  
  
-   Wählen Sie Spalten für die Analyse aus, die nützliche Informationen enthalten.  
  
-   Wenn Sie zu wenige Spalten einschließen, kann das Erzielen von Ergebnissen erschwert werden.  
  
-   Bei Verwendung der **Wert** Option, Sie müssen einen Wert in das Feld eingeben oder wählen Sie einen Wert aus der Liste.  
  
-   Bei Verwendung der **Prozentsatz** aus, legen Sie die Änderung als prozentuale Erhöhung oder Verringerung der. Der Standardwert ist 120 Prozent, das bedeutet eine Erhöhung von 20 Prozent über den aktuellen Wert.  
  
> [!NOTE]  
>  Wenn Sie keinen Wert festlegen, wird möglicherweise ein Fehler angezeigt.  
  
## <a name="understanding-the-results-of-what-if-analysis"></a>Grundlegendes zu den Ergebnissen der Was-wäre-wenn-Analyse  
 Bei der Erstellung einer **What-If** Szenario, das Tool führt drei Aufgaben:  
  
-   Es wird eine Data Mining-Struktur erstellt, in der wichtige Fakten zu den Daten in der Tabelle gespeichert werden.  
  
-   Es wird anhand der Daten ein Logistic Regression-Miningmodell erstellt.  
  
-   Es wird eine Vorhersageabfrage für alle von Ihnen angegebenen Werte erstellt.  
  
 Sie können alle Vorhersagen gleichzeitig ausgeben, dazu **ganze Tabelle**. Vom Tool werden daraufhin in der ursprünglichen Datentabelle zwei neue Spalten erstellt.  
  
 Die der Tabelle hinzugefügten Spalten enthalten zwei Informationstypen: den geänderten vorhergesagten Wert sowie das Vertrauen in den Wert. Mit Vertrauen ist die Wahrscheinlichkeit gemeint, dass die Vorhersage zutrifft.  
  
 Sie können Änderungswerte auch nacheinander im Dialogfeld eingeben und die Vorhersagen anschließend interaktiv anzeigen. Dies ist dasselbe wie das Erstellen einer *Singleton-Vorhersageabfrage*. Die Ergebnisse der Vorhersageabfrage werden zusammen mit den folgenden Informationen ausgegeben: dem Erfolg oder Fehler der Vorhersage, dem vorhergesagten Wert sowie dem Vertrauensgrad. Der Vertrauensgrad wird als Leiste mit einer gepunkteten Linie angezeigt. Je länger die gepunktete Linie ist, desto höher ist das Vertrauen in das Ergebnis.  
  
 Wenn Sie feststellen möchten, die Auswirkungen des Alters Ihrer Kunden auf der Ihr Kaufverhalten kaufen, und erhöhen Sie das kundenalter auf 25, z. B. die **What-If** Tool Abfragen von Datamining-Modells und gibt die Folgendes Ergebnis:  
  
 **Was-wenn-Analyse für Fahrradverkäufe wurde eine Lösung gefunden.**  
  
 **'Fahrradverkäufe' = Ja**  
  
 **Zuverlässigkeit: Fair**  
  
 Da dieses Ergebnis auf einer vorhandenen Zeile in der Datentabelle beruht, bedeutet das bei einem bestimmten Kunden Folgendes: Wenn alle anderen Werte zum Kunden unverändert bleiben, das Alter des Kunden jedoch auf 25 erhöht wird, kauft der Kunde wahrscheinlich ein Fahrrad.  
  
 Die Ausgabe der Vorhersagen in die ursprüngliche Datentabelle vereinfacht möglicherweise die Überprüfung, ob die Vorhersagen nützlich sind.  
  
## <a name="related-tools"></a>Verwandte Tools  
 Der Data Mining-Client für Excel, bei dem es sich um ein separates Add-In mit erweiterter Data Mining-Funktionalität handelt, enthält Assistenten zum Erstellen von Data Mining-Modellen, die Verhalten vorhersagen. Weitere Informationen finden Sie unter [Erstellen eines Data Mining-Modells](creating-a-data-mining-model.md).  
  
 Weitere Informationen zu den vom verwendeten Algorithmus die **What-If** Szenario finden Sie unter dem Thema "Microsoft Logistic Regression-Algorithmus" in SQL Server-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
