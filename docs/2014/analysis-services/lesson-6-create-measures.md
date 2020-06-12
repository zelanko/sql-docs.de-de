---
title: 'Lektion 7: Erstellen von Measures | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: ef487927098e63c7fc870aa65e55f57faa26767d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542562"
---
# <a name="lesson-7-create-measures"></a>Lektion 7: Erstellen von Measures
  In dieser Lektion erstellen Sie in das Modell einzufügende Measures. Ähnlich wie die berechneten Spalten, die Sie in der vorherigen Lektion erstellt haben, ist ein Measure im Wesentlichen eine mit einer DAX-Formel erstellte Berechnung. Im Gegensatz zu berechneten Spalten werden Measures jedoch auf Basis eines vom Benutzer ausgewählten *Filters*ausgewertet; z.B. eine bestimmte Spalte oder ein Slicer, die bzw. der dem Feld für Zeilenbezeichnungen in einer PivotTable hinzugefügt wurde.   Anschließend wird vom angewendeten Measure ein Wert für jede Zelle im Filter berechnet. Measures sind leistungsstarke, flexible Berechnungen, die Sie in fast alle Tabellenmodelle einbinden können, um dynamische Berechnungen für numerische Daten auszuführen. Weitere Informationen finden Sie unter [Measures &#40;SSAS – tabellarisch&#41;](tabular-models/measures-ssas-tabular.md).  
  
 Um Measures zu erstellen, verwenden Sie das Measureraster. Standardmäßig hat jede Tabelle ein leeres Measureraster. Sie erstellen jedoch in der Regel keine Measures für jede Tabelle. Das Measureraster wird in der Datensicht unter einer Tabelle im Modell-Designer angezeigt. Klicken Sie auf das Menü **Tabelle**, und klicken Sie dann auf **Measureraster anzeigen**, um das Measureraster für eine Tabelle anzuzeigen oder auszublenden.  
  
 Sie können ein Measure erstellen, indem Sie auf eine leere Zelle im Measureraster klicken und dann eine DAX-Formel in die Bearbeitungsleiste eingeben. Nach dem Abschließen der Formelerstellung mit der EINGABETASTE wird das Measure in der Zelle angezeigt. Sie können auch Measures mithilfe einer Standardaggregationsfunktion erstellen, indem Sie auf eine Spalte und anschließend auf die Schaltfläche AutoSumme (**∑**) auf der Symbolleiste klicken. Measures, die mithilfe der AutoSumme-Funktion erstellt wurden, werden im Measureraster direkt unterhalb der Spalte angezeigt, können bei Bedarf jedoch verschoben werden.  
  
 In dieser Lektion erstellen Sie Measures sowohl durch Eingabe einer DAX-Formel in der Bearbeitungsleiste als auch mithilfe der AutoSumme-Funktion.  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **30 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema ist Teil eines Tutorials zur Tabellenmodellierung, das in der richtigen Reihenfolge absolviert werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 6: Erstellen von berechneten Spalten](lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Erstellen von Measures  
  
#### <a name="to-create-a-days-current-quarter-to-date-measure-in-the-date-table"></a>So erstellen Sie ein Measure vom Typ "Days Current Quarter to Date" in der Date-Tabelle.  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle **Date** .  
  
2.  Wenn nicht bereits ein leeres Measureraster nicht unter der Tabelle angezeigt wird, klicken Sie auf das Menü **Tabelle** und anschließend auf **Measureraster anzeigen**.  
  
3.  Klicken Sie im Measureraster auf die leere Zelle links oben.  
  
4.  Geben Sie in der Bearbeitungsleiste über der Tabelle folgende Formel ein:  
  
     `=COUNTROWS( DATESQTD( 'Date'[Date]))`  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
     Beachten Sie, dass die linke obere Zelle jetzt einen Measurenamen, **Measure 1**, gefolgt vom Ergebnis **30**enthält. Der Measurename geht auch der Formel in der Bearbeitungsleiste voraus.  
  
5.  Um das Measure umzubenennen, markieren Sie den Namen **Measure 1**in der Bearbeitungs Leiste, geben `Days Current Quarter to Date` Sie ein, und drücken Sie dann die EINGABETASTE.  
  
    > [!TIP]  
    >  Wenn Sie in der Bearbeitungsleiste eine Formel eingeben, können Sie auch zuerst den Measurenamen eingeben, dem ein Doppelpunkt (:) mit anschließender Leerstelle und Formel folgt. Bei dieser Methode müssen Sie das Measure nicht umbenennen.  
  
#### <a name="to-create-a-days-in-current-quarter-measure-in-the-date-table"></a>So erstellen Sie ein Measure vom Typ "Days in Current Quarter" in der Date-Tabelle.  
  
1.  Klicken Sie mit der im Modell-Designer nach wie vor aktiven Tabelle **Date** auf die leere Zelle unterhalb des Measures, das Sie gerade erstellt haben.  
  
2.  Geben Sie in der Bearbeitungsleiste folgende Formel ein:  
  
     `Days in Current Quarter :=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))`  
  
     Hinweis: In dieser zuerst einbezogenen Formel folgt ein Doppelpunkt (:) auf den Rasternamen.  
  
     Drücken Sie nach dem Erstellen der Formel die EINGABETASTE.  
  
 Bei der Erstellung eines Vergleichsverhältnisses zwischen einem unvollständigen Zeitraum und dem vorherigen Zeitraum muss in der Formel der Anteil des verstrichenen Zeitraums berücksichtigt und mit dem gleichen Anteil des vorherigen Zeitraums verglichen werden. In diesem Fall gibt [Days Current Quarter to Date]/[Days in Current Quarter] den verstrichenen Anteil des aktuellen Zeitraums zurück.  
  
#### <a name="to-create-an-internet-distinct-count-sales-order-measure-in-the-internet-sales-table"></a>So erstellen Sie eine Measure vom Typ "Internet Distinct Count Sales Order" in der Internet Sales-Tabelle  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle (Registerkarte) **Internet Sales** .  
  
     Wenn das Measureraster nicht bereits angezeigt wird, klicken Sie mit der rechten Maustaste auf die Tabelle (Registerkarte) **Internet Sales** und anschließend auf **Measureraster anzeigen**.  
  
2.  Klicken Sie auf die Spaltenüberschrift **Sales Order Number** .  
  
3.  Klicken Sie in der Symbolleiste auf den Dropdownpfeil neben der Schaltfläche AutoSumme (**∑**), und wählen Sie dann **DistinctCount** aus.  
  
     Die Funktion AutoSumme erstellt mithilfe der Standardaggregationsformel „DistinctCount“ automatisch ein Measure für die ausgewählte Spalte.  
  
     Beachten Sie die oberste Zelle unter der Spalte im Measureraster. Sie enthält jetzt einen Measurenamen, **Distinct Count Sales Order Number**. Mit der AutoSumme-Funktion erstellte Measures werden automatisch unter der zugeordneten Spalte in der obersten Zelle im Measureraster eingefügt.  
  
4.  Klicken Sie im Measureraster auf das neue Measure, und benennen Sie anschließend im Fenster **Eigenschaften** im Feld **Measurename**das Measure in **Internet Distinct Count Sales Order**um.  
  
#### <a name="to-create-additional-measures-in-the-internet-sales-table"></a>So erstellen Sie zusätzliche Measures in der Internet Sales-Tabelle  
  
1.  Erstellen Sie mithilfe der Funktion AutoSumme die folgenden Measures und benennen Sie sie:  
  
    |Measurename|Column|AutoSumme (∑)|Formel|  
    |------------------|------------|-------------------|-------------|  
    |Internet Order Lines Count|Sales Order Line Number|Anzahl|=COUNT([Sales Order Line Number])|  
    |Internet Total Units|Order Quantity|SUM|=SUM([Order Quantity])|  
    |Internet Total Discount Amount|Discount Amount|SUM|=SUM([Discount Amount])|  
    |Internet Total Product Cost|Total Product Cost|SUM|=SUM([Total Product Cost])|  
    |Internet Total Sales|Sales Amount|SUM|=SUM([Sales Amount])|  
    |Internet Total Margin|Margin|SUM|=SUM([Margin])|  
    |Internet Total Tax Amt|Tax Amt|SUM|=SUM([Tax Amt])|  
    |Internet Total Freight|Freight (Fracht)|SUM|=SUM([Freight])|  
  
2.  Erstellen Sie durch Klicken auf eine leere Zelle im Measureraster und durch Verwenden der Bearbeitungsleiste die folgenden Measures, und benennen Sie diese um:  
  
    > [!IMPORTANT]  
    >  Sie müssen die folgenden Measures in entsprechender Reihenfolge erstellen. Formeln in späteren Measures verweisen auf vorherige Measures.  
  
    |Measurename|Formel|  
    |------------------|-------------|  
    |Internet Previous Quarter Margin|=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))|  
    |Internet Current Quarter Margin|=TOTALQTD([Internet Total Margin],'Date'[Date])|  
    |Internet Previous Quarter Margin Proportion to QTD|=[Internet Previous Quarter Margin]*([Days Current Quarter to Date]/[Days In Current Quarter])|  
    |Internet Previous Quarter Sales|=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))|  
    |Internet Current Quarter Sales|=TOTALQTD([Internet Total Sales],'Date'[Date])|  
    |Internet Previous Quarter Sales Proportion to QTD|=[Internet Previous Quarter Sales]*([Days Current Quarter to Date]/[Days In Current Quarter])|  
  
 Mit den für die Internet Sales-Tabelle erstellten Measures lassen sich wichtige Finanzdaten wie Verkäufe, Kosten und Gewinnspanne für Elemente analysieren, die durch vom Benutzer gewählte Filter definiert sind.  
  
## <a name="next-step"></a>Nächster Schritt  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 8: Erstellen von Leistungskennzahlen](lesson-7-create-key-performance-indicators.md).  
  
  
