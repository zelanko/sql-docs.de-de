---
title: Geben Sie in Beispiel (Tabellenanalysetools für Excel) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: d1e09e439469f23412c84ea7bab65c0aa748f286
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66081318"
---
# <a name="fill-from-example-table-analysis-tools-for-excel"></a>Aus Beispiel füllen (Tabellenanalysetools für Excel)
  ![Aus Beispiel füllen-Schaltfläche in Tabellenanalysetools](media/tat-fillex.gif "aus Beispiel füllen-Schaltfläche in Tabellenanalysetools")  
  
 Die **aus Beispiel füllen** Tool können Sie auf der Grundlage vorhandener Werte neue Datenspalten erstellen.  
  
 Nehmen wir beispielsweise an, die Daten enthalten ein **Kaufbetrag** Spalte eine **Bestellmenge** Spalte und eine **Premier-Kunde** Spalte, die basierend auf eine Formel mit der andere Spalten. Wenn die **Premier-Kunde** Spalte enthält viele leere Zeilen, könnten Sie mit der **Kaufbetrag** und **Bestellmenge** Spalten als Eingaben, um die fehlenden Werte abzuleiten. Das Tool analysiert die vorhandenen Datenmuster in Kombination mit den von Ihnen eingegebenen Beispielen und trifft eine Vorhersage dazu, welche Kategorie den einzelnen Kunden zugewiesen werden soll.  
  
 Wenn Sie mit den Ergebnissen nicht zufrieden sind, können Sie sie optimieren, indem Sie weitere Beispiele bereitstellen.  
  
## <a name="using-the-fill-from-example-tool"></a>Verwenden des Tools 'Aus Beispiel füllen'  
  
1.  In der **analysieren** des Menübands, klicken Sie auf **aus Beispiel füllen**.  
  
2.  Basierend auf der Analyse der Daten wird die auszufüllende Spalte automatisch vom Tool ausgefüllt. Diese Empfehlung können Sie dann übernehmen oder überschreiben.  
  
3.  Erstellen Sie eine Spalte für die neuen Daten, und geben Sie Beispiele für die Daten ein, für die Sie eine Vorhersage treffen möchten. Stellen Sie sicher, dass für jeden vorherzusagenden Wert mindestens ein Beispiel vorhanden ist. Wenn Daten in eine bereits vorhandene Spalte eingetragen werden sollen, wählen Sie die Spalte mit den fehlenden Werten aus.  
  
4.  Klicken Sie optional auf **wählen Sie Spalten in der Analyse zu verwendende**. In der **erweiterte Spaltenauswahl** Dialogfeld geben die Spalten, die am ehesten nützlich sein, beim Ausfüllen der fehlenden Daten.  
  
     Sie wissen beispielsweise aus Erfahrung, dass zwischen einer bestimmten Spalte und der Spalte mit den fehlenden Werten ein kausaler Zusammenhang besteht. In diesem Fall können Sie die Auswahl anderer Spalten aufheben, um bessere Ergebnisse zu erzielen.  
  
     Klicken Sie auf **OK**.  
  
5.  Klicken Sie auf **Ausführen**.  
  
     Wenn die Analyse abgeschlossen ist, erstellt das Tool eine neue **Muster** Arbeitsblatt, das die Ergebnisse der Analyse enthält. Der Bericht zeigt an, welche Regeln oder wichtigen Einflussfaktoren gefunden wurden und wie hoch die Wahrscheinlichkeit für die einzelnen Regeln ist.  
  
     Durch das Tool wird der ursprünglichen Datentabelle außerdem automatisch eine Spalte hinzugefügt, die die neuen Werte enthält. Sie können diese Werte überprüfen und mit den ursprünglichen Werten vergleichen.  
  
### <a name="requirements"></a>Anforderungen  
 Sie können nur Daten verwenden, die sich in Spalten befinden. Verwenden Sie die Einfügen/Transponieren-Funktion in Excel, um aufzufüllende Datenreihen, die in einer Zeile gespeichert sind, in das Spaltenformat umzuwandeln.  
  
## <a name="understanding-the-pattern-report"></a>Grundlegendes zum Musterbericht  
 Beim Ausführen der **aus Beispiel füllen** Tool ein Bericht erstellt, die Weitere Informationen zu den Mustern bereitstellt, die erkannt wurden. Diese Muster werden zum Extrapolieren der neuen Datenwerte verwendet.  
  
 Im Musterbericht werden die wichtigen Einflussfaktoren für jeden vorhergesagten Wert angezeigt. Jeder Einflussfaktor bzw. jede Regel wird als eine Kombination aus einer Spalte, des Werts in dieser Spalte und der relativen Auswirkung der Regel auf die Vorhersage beschrieben.  
  
 Wenn Sie beispielsweise ein Arbeitsblatt mit den Entfernungen zu Lieferadressen für Bestellungen ausfüllen möchten, dann nehmen Sie logischerweise an, dass die Lieferadresse einen großen Einfluss auf die Entfernung hat. In diesem Fall enthält der Bericht möglicherweise folgende Zeile:  
  
|Spalte|Wert|Begünstigt|Relative Auswirkung|  
|------------|-----------|------------|---------------------|  
|Bundesland/Kanton/PLZ|AB|> 500 Kilometer|80%|  
  
 Dies bedeutet, dass den Wert AB, in der **StateProvinceCode** Spalte vorhergesagt eine Protokollversand Entfernung > 500 Kilometer.  
  
 In der Regel beruhen die Vorhersagen auf weit komplexeren Mustern als in diesem Beispiel, und der Bericht enthält möglicherweise zahlreiche Regelzeilen für jede Vorhersage. Die Auswirkungen der einzelnen Regeln werden kombiniert, um den vorhergesagten Wert abzuleiten.  
  
> [!NOTE]  
>  **Relative Auswirkung** wird als schattierter Balken angezeigt. Je länger der Balken, desto größer ist die Wahrscheinlichkeit, dass die Regel für den ausgefüllten Wert zutrifft.  
  
 Das Tool fügt auch eine neue Spalte, mit dem Namen der ursprünglichen Datentabelle \<Spaltenname > erweitert.  
  
 Wenn die ursprüngliche Datenspalte einen Wert enthält, wird dieser Wert in die neue Spalte kopiert. Wenn die ursprüngliche Spalte jedoch eine leere Zelle enthält, enthält die neue Spalte den durch den Assistenten vorhergesagten Wert.  
  
## <a name="related-tools-and-information"></a>Verwandte Tools und Informationen  
 Sie können auch die [Daten durchsuchen](explore-data-sql-server-data-mining-add-ins.md) Assistenten im Data Mining-Client für Excel verwenden, um die Verteilung der Werte in einer Excel-Spalte zu untersuchen. Weitere Informationen finden Sie unter [Exploring und Bereinigen von Daten](exploring-and-cleaning-data.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenanalysetools für Excel](table-analysis-tools-for-excel.md)  
  
  
