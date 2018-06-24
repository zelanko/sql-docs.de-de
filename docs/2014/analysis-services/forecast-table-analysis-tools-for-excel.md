---
title: Planung (Tabellenanalysetools für Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Table Analysis tools
- forecasting
- mining model, time series
- time series [data mining]
ms.assetid: 22bb0b5e-78f5-484e-883d-2b5985a12749
caps.latest.revision: 17
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 40724491e971b150fa934f8a3294509d91b99d6a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059029"
---
# <a name="forecast-table-analysis-tools-for-excel"></a>Planung (Tabellenanalysetools für Excel)
  ![Schaltfläche "Planung" auf Tabelle Analysis tools Menüband](media/tat-forecast.gif "Prognose-Schaltfläche in Tabellenanalysetools-Menüband")  
  
 Die **prognostizieren** Tool können Sie vorhersagen basierend auf Daten in einer Excel-Datentabelle oder andere Datenquellen und optional die jeden vorhergesagten Wert zugeordneten Wahrscheinlichkeiten anzeigen. Wenn Ihre Daten beispielsweise eine Datumsspalte und eine Spalte enthalten, die den Gesamtumsatz für jeden Tag des Monats anzeigt, könnten Sie den Umsatz für zukünftige Tage vorhersagen. Sie können außerdem die Anzahl der auszuführenden Vorhersagen angeben. Beispielsweise können Sie fünf Tage oder dreißig vorhersagen.  
  
 Wenn der Vorgang vom Tool abgeschlossen wird, werden die neuen Vorhersagen am Ende der Quelldatentabelle angefügt, und die neuen Werte werden hervorgehoben. Neue Zeitreihenwerte werden nicht angefügt, daher können Sie die Vorhersagen zunächst überprüfen.  
  
 Das Tool erstellt auch ein neues Arbeitsblatt mit dem Namen **Planungsbericht**. Mit diesem Arbeitsblatt wird erfasst, ob vom Assistenten erfolgreich eine Vorhersage erstellt werden konnte. Das neue Arbeitsblatt enthält zudem ein Liniendiagramm, in dem Vergangenheitstrends angezeigt werden.  
  
 Wenn Sie die Zeitreihe erweitern, um die neuen Vorhersagen einzuschließen, werden die vorhergesagten Werte dem Liniendiagramm hinzugefügt. Die Vergangenheitswerte werden als ganze Linie angezeigt, und die Vorhersagen sind als gepunktete Linie dargestellt.  
  
## <a name="using-the-forecast-tool"></a>Verwenden des Planungstools  
  
1.  Öffnen Sie eine Excel-Tabelle mit vorhersagbaren numerischen Daten.  
  
2.  Klicken Sie auf **prognostizieren** auf die **analysieren** Registerkarte.  
  
3.  Geben Sie die vorherzusagenden Spalten an. Vom Tool werden automatisch die Spalten aus den Daten ausgewählt, die einen vorhersagbaren Datentyp aufweisen, d. h. kontinuierliche numerische Daten. Es kann vorkommen, dass von dem Tool bestimmte Spalten mit kontinuierlichen numerischen Daten nicht ausgewählt werden, wenn diese zahlreiche Nullwerte oder leere Werte enthalten, da die fehlenden Daten sich auf die Ergebnisse auswirken können. In diesem Fall beheben Sie die Daten mithilfe der [neu bezeichnen &#40;SQL Server Data Mining-Add-ins&#41; ](relabel-sql-server-data-mining-add-ins.md) Tool.  
  
4.  Geben Sie die Spalte mit dem Datum, der Uhrzeit oder einem anderen Reihenbezeichner an. Wenn Sie die Option  **\<kein Zeitstempel >** das Tool erstellt eine Reihe basierend auf der Reihenfolge der Zeilen in den Quelldaten.  
  
5.  Geben Sie die Anzahl der auszuführenden Vorhersagen an.  
  
6.  Optional können Sie für den Algorithmus angeben, ob Sie erwarten, dass sich die Daten wöchentlich, monatlich oder in anderen Abständen wiederholen. Wenn Ihre Daten nicht die angegebenen Muster entspricht, oder wenn Sie keine Muster sind, wählen Sie  **\<automatisch erkennen >** das Tool an, die sich wiederholenden Zeiträume gefunden haben.  
  
7.  Vom Assistenten werden die Vorhersagen der Quelltabelle hinzugefügt, und in einem neuen Arbeitsblatt wird ein Planungsbericht erstellt.  
  
8.  Wenn Sie die neuen Werte dem Vorhersagediagramm hinzufügen möchten, erweitern Sie die Zeitreihe, sodass die geplanten Werte eingeschlossen sind.  
  
### <a name="requirements"></a>Anforderungen  
 Die von Ihnen vorhergesagten Spalten müssen kontinuierliche numerischen Daten (z. B. eine Währung oder andere Zahlen) enthalten.  
  
 Ihre Daten sollten nach Möglichkeit auch eine Spalte mit einer Zeit- oder Datumsreihe umfassen. Sie können eine numerische Reihe (1, 2, 3, ...) anstelle von Datums- oder Zeitdaten verwenden. Die Werte in der Reihenspalte müssen jedoch eindeutig sein. Ein Fehler tritt auf, wenn die **prognostizieren** Tool doppelte Werte in der reihenspalte gefunden.  
  
 Ein Datum können nicht vorhergesagt werden, mithilfe der **prognostizieren** Tool. Obwohl möglicherweise kein Fehler generiert wird, wurde der Algorithmus nicht für die Verwendung von Datumswerten als vorhersagbare Werte entwickelt.  
  
### <a name="understanding-time-stamps"></a>Grundlegendes zu Timestamps  
 Bestimmen Sie eine Spalte als eine *Zeitstempel*. Der Timestamp hat zwei Aufgaben. Zum einen identifiziert er eindeutig einen Wert in einer Zeitreihe. Wenn Sie beispielsweise täglich den Verkauf nachverfolgen, sollten Sie für jeden Tag nur einen Verkaufswert haben. Das Kalenderdatum kann als Timestamp verwendet werden. Zweitens gibt die Timestamp-Spalte die Einheit zum Treffen von Vorhersagen an. Wenn Sie den täglichen Verkauf verfolgen, werden die Vorhersagen auch in Tageseinheiten angegeben.  
  
 Falls Ihre Daten keine Datums- oder Zeitspalte enthalten, wird von dem Tool automatisch ein temporärer Reihenschlüssel namens _RowIndex erstellt. Der Schlüssel basiert auf der Reihenfolge der Zeilen im Dataset.  
  
 Geben Sie eine ganze Zahl ein, die der Anzahl der Schritte entspricht, wenn Sie die Anzahl der Vorhersagen angeben. Die für diese Schritte verwendeten Einheiten sind von den in den Datums- und Zeitreihen Ihrer Daten verwendeten Einheiten abhängig. Falls Ihre Daten beispielsweise Umsätze pro Monat auflisten, wird die Vorhersage in Monaten ausgedrückt. Sie können die Zeiteinheiten hier nur ändern, wenn Sie gleichzeitig auch die Quelldaten ändern.  
  
### <a name="understanding-periodicity"></a>Grundlegendes zu Periodizität  
 Eine Planung basiert auf Mustern, die sich über einen bestimmten Zeitraum wiederholen. Deshalb führt der Microsoft Time Series-Algorithmus Berechnungen durch, um die Zeiträume mit den aussagekräftigsten Mustern zu ermitteln. *Periodizität* bezieht sich auf diese Zeiträume.  
  
 Eine Zeitreihe kann viele potenzielle Muster enthalten. Wenn Sie sich sicher sind, dass die Daten ein bestimmtes Muster enthalten, können Sie die Qualität der Vorhersage durch einen Hinweis an den Algorithmus verbessern.  
  
 Wenn Sie beispielsweise davon ausgehen, dass die Daten sich jede Woche wiederholen, können Sie Woche auswählen, sodass vom Algorithmus nach wöchentlichen Mustern gesucht wird. Wenn jedoch keine eindeutigen Wochenmuster gefunden werden, ignoriert der Algorithmus den Hinweis.  
  
## <a name="understanding-the-forecasting-report"></a>Grundlegendes zum Planungsbericht  
 In diesem Diagramm werden die Vergangenheitswerte aus Ihrer Datentabelle als dunkle Linie angezeigt. Die vorhergesagten Werte werden als gepunktete Linien dargestellt. Sie können auf einen Punkt auf der Linie klicken, um den vorhergesagten Wert anzuzeigen.  
  
> [!NOTE]  
>  Wenn Sie Bezeichnungen auf der Zeitachse für die vorhergesagten Werte im Diagramm nicht angezeigt werden, öffnen Sie das Arbeitsblatt, die die vorhergesagten Werte enthält, und verwenden Sie die **Reihe ausfüllen** -Funktion in Excel verwenden, um die timestamp-Spalte der vorhergesagten Einbeziehung erweitern Werte.  
  
 In einigen Fällen enthält die Planung nicht so viele Zeitscheiben wie angefordert. Dies bedeutet normalerweise, dass die Daten nicht ausreichen, damit der Algorithmus so weit im Voraus planen kann. Die **prognostizieren** Tool wird nur Vorhersagen machen, die einen minimalen wahrscheinlichkeitsschwellenwert entsprechen.  
  
## <a name="related-tools"></a>Verwandte Tools  
 Der Data Mining-Client für Excel, bei dem es sich um ein separates Add-In mit erweiterter Data Mining-Funktionalität handelt, umfasst auch einen Assistenten zum Planen.  
  
 Sowohl die **prognostizieren** Tool (in den Tabellenanalysetools für Excel) und die **prognostizieren** -Assistenten (Data Mining-Client für Excel) verwenden die [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series-Algorithmus.  
  
-   Die **prognostizieren** Tool ist einfacher zu verwenden, da automatisch konfiguriert, der Algorithmus dass, um die Einstellungen zu verwenden, die für Ihre Daten am besten geeignet sind.  
  
-   Die **prognostizieren** Assistenten im Data Mining-Client für Excel Ihnen die Möglichkeit bietet, die Parameter anpassen.  
  
 Weitere Informationen zu den **prognostizieren** -Assistenten finden Sie unter [Planungs-Assistenten &#40;Data Mining-Add-ins für Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md). Weitere Informationen zum Algorithmus, der für die Planung verwendet wird, finden Sie im Thema "Microsoft Time Series-Algorithmus" in der [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Onlinedokumentation.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  