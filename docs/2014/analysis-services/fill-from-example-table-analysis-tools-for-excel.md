---
title: Aus Beispiel füllen (Tabellenanalyse Tools für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- fill from example
ms.assetid: dac57d8f-1c65-4878-8ea0-9c680df5e4fb
author: minewiskan
ms.author: owend
ms.openlocfilehash: f3894f8ea42c0c5c91c3b6a5c5e7a6677b763b02
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528346"
---
# <a name="fill-from-example-table-analysis-tools-for-excel"></a>Aus Beispiel füllen (Tabellenanalysetools für Excel)
  ![Aus Beispiel füllen (Schaltfläche in Tabellenanalysetools)](media/tat-fillex.gif "Aus Beispiel füllen (Schaltfläche in Tabellenanalysetools)")  
  
 Das Tool **aus Beispiel füllen** unterstützt Sie beim Erstellen neuer Datenspalten auf der Grundlage vorhandener Werte.  
  
 Nehmen Sie beispielsweise an, dass Ihre Daten eine Spalte " **Purchase Amount** ", eine Spalte "Bestell **Menge** " und eine Spalte " **Premier Customer** " enthalten, die auf einer Formel basiert, die die anderen Spalten verwendet. Wenn die Spalte **Premier Customer** viele leere Zeilen enthält, können Sie die Spalten **Purchase Amount** und **Order** Amount als Eingaben verwenden, um die fehlenden Werte abzuleiten. Das Tool analysiert die vorhandenen Datenmuster in Kombination mit den von Ihnen eingegebenen Beispielen und trifft eine Vorhersage dazu, welche Kategorie den einzelnen Kunden zugewiesen werden soll.  
  
 Wenn Sie mit den Ergebnissen nicht zufrieden sind, können Sie sie optimieren, indem Sie weitere Beispiele bereitstellen.  
  
## <a name="using-the-fill-from-example-tool"></a>Verwenden des Tools 'Aus Beispiel füllen'  
  
1.  Klicken Sie im Menüband **analysieren** auf **aus Beispiel füllen**.  
  
2.  Basierend auf der Analyse der Daten wird die auszufüllende Spalte automatisch vom Tool ausgefüllt. Diese Empfehlung können Sie dann übernehmen oder überschreiben.  
  
3.  Erstellen Sie eine Spalte für die neuen Daten, und geben Sie Beispiele für die Daten ein, für die Sie eine Vorhersage treffen möchten. Stellen Sie sicher, dass für jeden vorherzusagenden Wert mindestens ein Beispiel vorhanden ist. Wenn Daten in eine bereits vorhandene Spalte eingetragen werden sollen, wählen Sie die Spalte mit den fehlenden Werten aus.  
  
4.  Klicken Sie optional auf **Spalten auswählen, die in der Analyse verwendet werden sollen**. Geben Sie im Dialogfeld **Erweiterte Spaltenauswahl** die Spalten an, die am wahrscheinlichsten beim Ausfüllen der fehlenden Daten nützlich sein werden.  
  
     Sie wissen beispielsweise aus Erfahrung, dass zwischen einer bestimmten Spalte und der Spalte mit den fehlenden Werten ein kausaler Zusammenhang besteht. In diesem Fall können Sie die Auswahl anderer Spalten aufheben, um bessere Ergebnisse zu erzielen.  
  
     Klicken Sie auf **OK**.  
  
5.  Klicken Sie auf **Ausführen**.  
  
     Wenn die Analyse fertiggestellt ist, erstellt das Tool ein neues **Muster** Arbeitsblatt, das die Ergebnisse der Analyse enthält. Der Bericht zeigt an, welche Regeln oder wichtigen Einflussfaktoren gefunden wurden und wie hoch die Wahrscheinlichkeit für die einzelnen Regeln ist.  
  
     Durch das Tool wird der ursprünglichen Datentabelle außerdem automatisch eine Spalte hinzugefügt, die die neuen Werte enthält. Sie können diese Werte überprüfen und mit den ursprünglichen Werten vergleichen.  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
 Sie können nur Daten verwenden, die sich in Spalten befinden. Verwenden Sie die Einfügen/Transponieren-Funktion in Excel, um aufzufüllende Datenreihen, die in einer Zeile gespeichert sind, in das Spaltenformat umzuwandeln.  
  
## <a name="understanding-the-pattern-report"></a>Grundlegendes zum Musterbericht  
 Wenn Sie das Tool " **aus Beispiel füllen** " ausführen, wird ein Bericht erstellt, der weitere Informationen zu den erkannten Mustern bereitstellt. Diese Muster werden zum Extrapolieren der neuen Datenwerte verwendet.  
  
 Im Musterbericht werden die wichtigen Einflussfaktoren für jeden vorhergesagten Wert angezeigt. Jeder Einflussfaktor bzw. jede Regel wird als eine Kombination aus einer Spalte, des Werts in dieser Spalte und der relativen Auswirkung der Regel auf die Vorhersage beschrieben.  
  
 Wenn Sie beispielsweise ein Arbeitsblatt mit den Entfernungen zu Lieferadressen für Bestellungen ausfüllen möchten, dann nehmen Sie logischerweise an, dass die Lieferadresse einen großen Einfluss auf die Entfernung hat. In diesem Fall enthält der Bericht möglicherweise folgende Zeile:  
  
|Column|Wert|Begünstigt|Relative Auswirkung|  
|------------|-----------|------------|---------------------|  
|Bundesland/Kanton/PLZ|AB|>500-Kilometer|80 %|  
  
 Dies bedeutet, dass der Wert ab in der Spalte **StateProvinceCode** stark eine Versand Entfernung von >500 Kilometer vorhersagt.  
  
 In der Regel beruhen die Vorhersagen auf weit komplexeren Mustern als in diesem Beispiel, und der Bericht enthält möglicherweise zahlreiche Regelzeilen für jede Vorhersage. Die Auswirkungen der einzelnen Regeln werden kombiniert, um den vorhergesagten Wert abzuleiten.  
  
> [!NOTE]  
>  Die **relative Auswirkung** wird als schattierter Balken angezeigt. Je länger der Balken, desto größer ist die Wahrscheinlichkeit, dass die Regel für den ausgefüllten Wert zutrifft.  
  
 Das Tool fügt der ursprünglichen Datentabelle mit dem Namen erweitert auch eine neue Spalte hinzu \<column name> .  
  
 Wenn die ursprüngliche Datenspalte einen Wert enthält, wird dieser Wert in die neue Spalte kopiert. Wenn die ursprüngliche Spalte jedoch eine leere Zelle enthält, enthält die neue Spalte den durch den Assistenten vorhergesagten Wert.  
  
## <a name="related-tools-and-information"></a>Verwandte Tools und Informationen  
 Sie können auch den Assistenten zum durch [Suchen von Daten](explore-data-sql-server-data-mining-add-ins.md) verwenden, der im Data Mining-Client für Excel verfügbar ist, um die Verteilung von Werten in einer Excel-Spalte zu überprüfen. Weitere Informationen finden Sie unter durch [Suchen und Bereinigen von Daten](exploring-and-cleaning-data.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
