---
title: 'Analysis Services-Tutorial – Lektion 6: Erstellen von Measures | Microsoft-Dokumentation'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f9b466a703dd04a53c6ebf7c6fac624476abcc52
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43093963"
---
# <a name="create-measures"></a>Erstellen von Measures

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion erstellen Sie Measures, die im Modell eingeschlossen werden. Ähnlich wie die berechneten Spalten, die Sie erstellt haben, ist ein Measure eine Berechnung, die mithilfe einer DAX-Formel erstellt. Im Gegensatz zu berechneten Spalten werden Measures werden jedoch ausgewertet anhand eines vom Benutzer ausgewählten *Filter*. Z. B. eine bestimmte Spalte oder ein Slicer, die das Feld für Zeilenbezeichnungen in einer PivotTable hinzugefügt. Ein Wert für jede Zelle im Filter wird dann vom übernommenen Measure berechnet. Measures sind leistungsstarke, flexible Berechnungen, die in fast allen tabellenmodellen für dynamische Berechnungen von numerischen Daten eingeschlossen werden sollen. Weitere Informationen finden Sie unter [Measures](../tabular-models/measures-ssas-tabular.md).
  
Um Measures zu erstellen, verwenden Sie die *Measureraster*. Standardmäßig verfügt jede Tabelle ein leeres measureraster; Allerdings wird für jede Tabelle Measures in der Regel nicht erstellen. Das Measureraster wird in der Datensicht unter einer Tabelle im Modell-Designer angezeigt. Um das Measureraster für eine Tabelle auszublenden oder anzuzeigen, klicken Sie auf das Menü **Tabelle** und anschließend auf **Measureraster anzeigen**.  
  
Sie können ein Measure erstellen, indem Sie auf eine leere Zelle im measureraster angezeigt und dann eine DAX-Formel in der Bearbeitungsleiste eingeben. Wenn Sie drücken die EINGABETASTE zum Abschließen der Formel das Measure dann in der Zelle angezeigt. Sie können auch Measures mithilfe einer standardaggregationsfunktion durch Klicken auf eine Spalte aus, und klicken Sie dann auf die Schaltfläche AutoSumme erstellen (**∑**) auf der Symbolleiste. Measures, die mithilfe der Funktion AutoSumme erstellt wurden, werden im measureraster direkt unterhalb der Spalte angezeigt, aber verschoben werden können.  
  
In dieser Lektion erstellen Sie Measures sowohl durch Eingabe einer DAX-Formel in der Bearbeitungsleiste, und klicken Sie mit der AutoSumme-Funktion.  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **30 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion an, Sie sollten die vorherige Lektion abgeschlossen haben: [Lektion 5: Erstellen von berechneten Spalten](../tutorial-tabular-1400/as-lesson-5-create-calculated-columns.md).  
  
## <a name="create-measures"></a>Erstellen von Measures  
  
#### <a name="to-create-a-dayscurrentquartertodate-measure-in-the-dimdate-table"></a>Erstellen Sie ein DaysCurrentQuarterToDate-Measure in der DimDate-Tabelle  
  
1.  Klicken Sie im Modell-Designer auf die **DimDate** Tabelle.  
  
2.  Klicken Sie im Measureraster auf die linke obere leere Zelle.  
  
3.  Geben Sie in der Bearbeitungsleiste folgende Formel ein:  
  
    ```
    DaysCurrentQuarterToDate:=COUNTROWS( DATESQTD( 'DimDate'[Date])) 
    ```
  
    Beachten Sie, dass die linke obere Zelle jetzt einen Measurenamen enthält, **DaysCurrentQuarterToDate**, gefolgt von dem Ergebnis **92**. Das Ergebnis ist an diesem Punkt nicht relevant, da kein Benutzerfilter angewendet wurde.
    
      ![als lesson6 newmeasure](../tutorial-tabular-1400/media/as-lesson6-newmeasure.png) 
    
    Im Gegensatz zu berechneten Spalten können Sie mit measureformeln den Measurenamen gefolgt von einem Doppelpunkt, gefolgt vom Formelausdruck eingeben.

  
#### <a name="to-create-a-daysincurrentquarter-measure-in-the-dimdate-table"></a>Erstellen Sie ein DaysInCurrentQuarter-Measure in der DimDate-Tabelle  
  
1.  Mit der **DimDate** -Tabelle noch im Modell-Designer, im measureraster aktiv ist, klicken Sie auf die leere Zelle unterhalb des Measures, die Sie erstellt haben.  
  
2.  Geben Sie in der Bearbeitungsleiste folgende Formel ein:  
  
    ```
    DaysInCurrentQuarter:=COUNTROWS( DATESBETWEEN( 'DimDate'[Date], STARTOFQUARTER( LASTDATE('DimDate'[Date])), ENDOFQUARTER('DimDate'[Date])))
    ```
  
    Erstellung eines vergleichsverhältnisses zwischen einem unvollständigen Zeitraum und dem vorherigen Zeitraum auf. Die Formel muss der Anteil des Zeitraums berechnen, die abgelaufen ist und mit dem gleichen Anteil des vorherigen Zeitraums vergleichen. In diesem Fall [gibt DaysCurrentQuarterToDate] / [DaysInCurrentQuarter] Gibt den Anteil des aktuellen Zeitraums vergangen.  
  
#### <a name="to-create-an-internetdistinctcountsalesorder-measure-in-the-factinternetsales-table"></a>Erstellen Sie eine InternetDistinctCountSalesOrder-Measure in der Tabelle "factinternetsales"  
  
1.  Klicken Sie auf die **"factinternetsales"** Tabelle.   
  
2.  Klicken Sie auf die **SalesOrderNumber** Spaltenüberschrift.  
  
3.  Klicken Sie in der Symbolleiste neben der AutoSumme-Schaltfläche (**∑**) auf den Pfeil nach unten, und wählen Sie **DistinctCount**aus.  
  
    Die AutoSumme-Funktion erstellt mit der DistinctCount-Standardaggregationsformel automatisch ein Measure für die ausgewählte Spalte.  
    
       ![als lesson6 newmeasure2](../tutorial-tabular-1400/media/as-lesson6-newmeasure2.png)
  
4.  Klicken Sie im measureraster auf das neue Measure, und klicken Sie dann in der **Eigenschaften** Fenster im **Measurename**, benennen Sie das Measure in **InternetDistinctCountSalesOrder**. 
 
  
#### <a name="to-create-additional-measures-in-the-factinternetsales-table"></a>Erstellen Sie zusätzliche Measures in der Tabelle "factinternetsales"  
  
1.  Erstellen Sie unter Verwendung der AutoSumme-Funktion die folgenden Measures, und benennen Sie diese um:  

    |Spalte|Measurename|AutoSumme (∑)|Formel|  
    |----------------|----------|-----------------|-----------|  
    |SalesOrderLineNumber|InternetOrderLinesCount|Count|=COUNTA([SalesOrderLineNumber])|  
    |OrderQuantity|InternetTotalUnits|SUM|=SUM([OrderQuantity])|  
    |DiscountAmount|InternetTotalDiscountAmount|SUM|=SUM([DiscountAmount])|  
    |TotalProductCost|InternetTotalProductCost|SUM|=SUM([TotalProductCost])|  
    |SalesAmount|"Internettotalsales" an|SUM|=SUM([SalesAmount])|  
    |Margin|InternetTotalMargin|SUM|=SUM([Margin])|  
    |TaxAmt|InternetTotalTaxAmt|SUM|=SUM([TaxAmt])|  
    |Freight|InternetTotalFreight|SUM|=SUM([Freight])|  
  
2.  Erstellen Sie durch Klicken auf eine leere Zelle im measureraster, und mithilfe der Bearbeitungsleiste, die folgenden benutzerdefinierten Measures in der Reihenfolge:  
  
      ```
      InternetPreviousQuarterMargin:=CALCULATE([InternetTotalMargin],PREVIOUSQUARTER('DimDate'[Date]))
      ```
      
      ```
      InternetCurrentQuarterMargin:=TOTALQTD([InternetTotalMargin],'DimDate'[Date])
      ```
  
      ```
      InternetPreviousQuarterMarginProportionToQTD:=[InternetPreviousQuarterMargin]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
      ```
      InternetPreviousQuarterSales:=CALCULATE([InternetTotalSales],PREVIOUSQUARTER('DimDate'[Date]))
      ```
  
      ```
      InternetCurrentQuarterSales:=TOTALQTD([InternetTotalSales],'DimDate'[Date])
      ```
      
      ```
      InternetPreviousQuarterSalesProportionToQTD:=[InternetPreviousQuarterSales]*([DaysCurrentQuarterToDate]/[DaysInCurrentQuarter])
      ```
  
Für die FactInternetSales-Tabelle erstellten Measures können verwendet werden, analysieren Sie wichtige Finanzdaten wie Verkäufe, Kosten und Gewinnspanne für Elemente, die durch vom Benutzer gewählte Filter definiert.  
  
## <a name="whats-next"></a>Wie geht es weiter?

[Lektion 7: Erstellen von Key Performance Indicators](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md).  

  
