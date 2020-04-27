---
title: Vorhersage (Tabellenanalyse Tools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- forecasting
- mining model, time series
- time series [data mining]
ms.assetid: 22bb0b5e-78f5-484e-883d-2b5985a12749
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dc620811209d854af5a9c874956847236819f462
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66081045"
---
# <a name="forecast-table-analysis-tools-for-excel"></a>Planung (Tabellenanalysetools für Excel)
  ![Planung (Schaltfläche auf Tabellenanalysetools-Menüband)](media/tat-forecast.gif "Planung (Schaltfläche auf Tabellenanalysetools-Menüband)")  
  
 Mit dem Tool für die **Vorhersage** können Sie Vorhersagen auf Grundlage von Daten in einer Excel-Datentabelle oder einer anderen Datenquelle treffen und optional die Wahrscheinlichkeiten anzeigen, die jedem vorhergesagten Wert zugeordnet sind. Wenn Ihre Daten beispielsweise eine Datumsspalte und eine Spalte enthalten, die den Gesamtumsatz für jeden Tag des Monats anzeigt, könnten Sie den Umsatz für zukünftige Tage vorhersagen. Sie können außerdem die Anzahl der auszuführenden Vorhersagen angeben. Beispielsweise können Sie fünf Tage oder dreißig vorhersagen.  
  
 Wenn der Vorgang vom Tool abgeschlossen wird, werden die neuen Vorhersagen am Ende der Quelldatentabelle angefügt, und die neuen Werte werden hervorgehoben. Neue Zeitreihenwerte werden nicht angefügt, daher können Sie die Vorhersagen zunächst überprüfen.  
  
 Das Tool erstellt auch ein neues Arbeitsblatt mit dem Namen **Prognosebericht**. Mit diesem Arbeitsblatt wird erfasst, ob vom Assistenten erfolgreich eine Vorhersage erstellt werden konnte. Das neue Arbeitsblatt enthält zudem ein Liniendiagramm, in dem Vergangenheitstrends angezeigt werden.  
  
 Wenn Sie die Zeitreihe erweitern, um die neuen Vorhersagen einzuschließen, werden die vorhergesagten Werte dem Liniendiagramm hinzugefügt. Die Vergangenheitswerte werden als ganze Linie angezeigt, und die Vorhersagen sind als gepunktete Linie dargestellt.  
  
## <a name="using-the-forecast-tool"></a>Verwenden des Planungstools  
  
1.  Öffnen Sie eine Excel-Tabelle mit vorhersagbaren numerischen Daten.  
  
2.  Klicken Sie auf der Registerkarte **analysieren** auf **Vorhersagen** .  
  
3.  Geben Sie die vorherzusagenden Spalten an. Das Tool wählt automatisch Spalten in den Daten aus, die einen vorhersagbaren Datentyp aufweisen, d. h. kontinuierliche numerische Daten. Es kann vorkommen, dass von dem Tool bestimmte Spalten mit kontinuierlichen numerischen Daten nicht ausgewählt werden, wenn diese zahlreiche Nullwerte oder leere Werte enthalten, da die fehlenden Daten sich auf die Ergebnisse auswirken können. Wenn dies der Fall ist, können Sie die Daten mit dem [&#41;Tool "Relabel &#40;SQL Server Data Mining-Add-ins](relabel-sql-server-data-mining-add-ins.md) " korrigieren.  
  
4.  Geben Sie die Spalte mit dem Datum, der Uhrzeit oder einem anderen Reihenbezeichner an. Wenn Sie die Option ** \<kein Zeitstempel>** auswählen, erstellt das Tool eine Reihe basierend auf der Zeilen Sequenz in den Quelldaten.  
  
5.  Geben Sie die Anzahl der auszuführenden Vorhersagen an.  
  
6.  Optional können Sie für den Algorithmus angeben, ob Sie erwarten, dass sich die Daten wöchentlich, monatlich oder in anderen Abständen wiederholen. Wenn Ihre Daten keinem der angegebenen Muster entsprechen, oder wenn Sie keine Muster haben, wählen Sie ** \<automatisch>erkennen** aus, damit das Tool die sich wiederholenden Zeiträume findet.  
  
7.  Vom Assistenten werden die Vorhersagen der Quelltabelle hinzugefügt, und in einem neuen Arbeitsblatt wird ein Planungsbericht erstellt.  
  
8.  Wenn Sie die neuen Werte dem Vorhersagediagramm hinzufügen möchten, erweitern Sie die Zeitreihe, sodass die geplanten Werte eingeschlossen sind.  
  
### <a name="requirements"></a>Anforderungen  
 Die von Ihnen vorhergesagten Spalten müssen kontinuierliche numerischen Daten (z. B. eine Währung oder andere Zahlen) enthalten.  
  
 Ihre Daten sollten nach Möglichkeit auch eine Spalte mit einer Zeit- oder Datumsreihe umfassen. Anstelle von Datums-und Uhrzeitdaten können Sie eine numerische Reihe (1, 2, 3...) verwenden. Die Werte in der Reihenspalte müssen jedoch eindeutig sein. Ein Fehler tritt auf, wenn das Tool für die **Vorhersage** doppelte Werte in der Reihen Spalte findet.  
  
 Sie können mit dem Tool für die **Vorhersage** kein Datum Vorhersagen. Obwohl möglicherweise kein Fehler generiert wird, wurde der Algorithmus nicht für die Verwendung von Datumswerten als vorhersagbare Werte entwickelt.  
  
### <a name="understanding-time-stamps"></a>Grundlegendes zu Timestamps  
 Sie müssen eine Spalte identifizieren, die als *Zeitstempel*verwendet werden soll. Der Timestamp hat zwei Aufgaben. Zum einen identifiziert er eindeutig einen Wert in einer Zeitreihe. Wenn Sie beispielsweise täglich den Verkauf nachverfolgen, sollten Sie für jeden Tag nur einen Verkaufswert haben. Das Kalenderdatum kann als Timestamp verwendet werden. Zweitens gibt die Timestamp-Spalte die Einheit zum Treffen von Vorhersagen an. Wenn Sie den täglichen Verkauf verfolgen, werden die Vorhersagen auch in Tageseinheiten angegeben.  
  
 Falls Ihre Daten keine Datums- oder Zeitspalte enthalten, wird von dem Tool automatisch ein temporärer Reihenschlüssel namens _RowIndex erstellt. Der Schlüssel basiert auf der Reihenfolge der Zeilen im Dataset.  
  
 Geben Sie eine ganze Zahl ein, die der Anzahl der Schritte entspricht, wenn Sie die Anzahl der Vorhersagen angeben. Die für diese Schritte verwendeten Einheiten sind von den in den Datums- und Zeitreihen Ihrer Daten verwendeten Einheiten abhängig. Falls Ihre Daten beispielsweise Umsätze pro Monat auflisten, wird die Vorhersage in Monaten ausgedrückt. Sie können die Zeiteinheiten hier nur ändern, wenn Sie gleichzeitig auch die Quelldaten ändern.  
  
### <a name="understanding-periodicity"></a>Grundlegendes zu Periodizität  
 Eine Planung basiert auf Mustern, die sich über einen bestimmten Zeitraum wiederholen. Deshalb führt der Microsoft Time Series-Algorithmus Berechnungen durch, um die Zeiträume mit den aussagekräftigsten Mustern zu ermitteln. *Periodizität* bezieht sich auf diese Zeiträume.  
  
 Eine Zeitreihe kann viele potenzielle Muster enthalten. Wenn Sie sich sicher sind, dass die Daten ein bestimmtes Muster enthalten, können Sie die Qualität der Vorhersage durch einen Hinweis an den Algorithmus verbessern.  
  
 Wenn Sie beispielsweise davon ausgehen, dass die Daten sich jede Woche wiederholen, können Sie Woche auswählen, sodass vom Algorithmus nach wöchentlichen Mustern gesucht wird. Wenn jedoch keine eindeutigen Wochenmuster gefunden werden, ignoriert der Algorithmus den Hinweis.  
  
## <a name="understanding-the-forecasting-report"></a>Grundlegendes zum Planungsbericht  
 In diesem Diagramm werden die Vergangenheitswerte aus Ihrer Datentabelle als dunkle Linie angezeigt. Die vorhergesagten Werte werden als gepunktete Linien dargestellt. Sie können auf einen Punkt auf der Linie klicken, um den vorhergesagten Wert anzuzeigen.  
  
> [!NOTE]  
>  Wenn für die vorhergesagten Werte im Diagramm keine Bezeichnungen auf der Zeitachse angezeigt werden, öffnen Sie das Arbeitsblatt, das die vorhergesagten Werte enthält, und verwenden Sie die **Fill-, Series** -Funktion in Excel, um die Zeitstempel Spalte um die vorhergesagten Werte zu erweitern.  
  
 In einigen Fällen enthält die Planung nicht so viele Zeitscheiben wie angefordert. Dies bedeutet normalerweise, dass die Daten nicht ausreichen, damit der Algorithmus so weit im Voraus planen kann. Das Tool **Vorhersage** führt nur Vorhersagen aus, die einen minimalen Wahrscheinlichkeits Schwellenwert erfüllen.  
  
## <a name="related-tools"></a>Verwandte Tools  
 Der Data Mining-Client für Excel, bei dem es sich um ein separates Add-In mit erweiterter Data Mining-Funktionalität handelt, umfasst auch einen Assistenten zum Planen.  
  
 Sowohl das Tool für die **Vorhersage** (in den Tabellenanalyse Tools für Excel) als auch der Planungs **-Assistent (** im Data Mining-Client [!INCLUDE[msCoName](../includes/msconame-md.md)] für Excel) verwenden den Time Series-Algorithmus.  
  
-   Das Tool für die **Vorhersage** ist einfacher zu verwenden, da der Algorithmus automatisch so konfiguriert wird, dass er die Einstellungen verwendet, die für Ihre Daten am besten geeignet sind.  
  
-   Der Planungs-Assistent im Data Mining-Client für Excel bietet **Ihnen die Möglichkeit** , die Parameter anzupassen.  
  
 Weitere Informationen zum Planungs- **Assistenten finden** Sie unter [Assistent zum Prognostizieren von &#40;Data Mining-Add-Ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md). Weitere Informationen zum Algorithmus, der für die Planung verwendet wird, finden Sie im Thema "Microsoft Time Series-Algorithmus" in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
