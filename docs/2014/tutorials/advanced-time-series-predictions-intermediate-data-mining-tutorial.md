---
title: Erweiterte Zeitreihenvorhersagen (Datamining-Lernprogramm für fortgeschrittene) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b614ebdb-07ca-44af-a0ff-893364bd4b71
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3db82b977725bdcb615ec67bd66e530b38f385c5
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56032801"
---
# <a name="advanced-time-series-predictions-intermediate-data-mining-tutorial"></a>Erweiterte Zeitreihenvorhersagen (Data Mining-Lernprogramm für Fortgeschrittene)
  Bei der Untersuchung des Prognosemodells wurde gezeigt, dass die Verkäufe in den meisten Regionen einem ähnlichen Muster folgen. Einige Regionen und Modelle wie das Modell M200 im Pazifischen Raum weisen jedoch deutlich abweichende Trends auf. Dies ist wenig überraschend, da bekanntermaßen häufig regionale Unterschiede auftreten und durch zahlreiche Faktoren verursacht werden können, einschließlich Marketingaktionen, fehlerhafter Berichterstellung sowie politischer Faktoren.  
  
 Ihre Benutzer benötigen jedoch ein Modell, das weltweit angewendet werden kann. Sie können daher die Auswirkungen einzelner Faktoren auf Vorhersagen minimieren, indem Sie ein Modell erstellen, das auf den aggregierten Zahlen aller Verkäufe weltweit basiert. Sie können dann dieses Modell für Vorhersagen für jede einzelne Region nutzen.  
  
 In dieser Aufgabe erstellen Sie alle Datenquellen, die für die erweiterten Vorhersagetasks erforderlich sind. Sie erstellen zwei Datenquellensichten zur Verwendung als Eingaben in die Vorhersageabfrage und eine Datenquellensicht, die beim Erstellen eines neuen Modells zum Einsatz kommt.  
  
 **Schritte**  
  
1.  [Vorbereiten der erweiterten Umsatzdaten (für die Vorhersage)](#bkmk_newExtendData)  
  
2.  [Vorbereiten der aggregierten Daten (für das Erstellen des Modells)](#bkmk_newReplaceData)  
  
3.  [Vorbereiten der Reihendaten (für kreuzvorhersagen)](#bkmk_CrossData2)  
  
4.  [Vorhersagen mit EXTEND](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
5.  [Erstellen des Modells für kreuzvorhersagen](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
6.  [Vorhersagen mit REPLACE](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
7.  [Überprüfen Sie die neuen Vorhersagen](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
##  <a name="bkmk_newExtendData"></a> Erstellen der neuen erweiterten Umsatzdaten  
 Um die Umsatzdaten zu aktualisieren, müssen Sie die letzten Umsatzzahlen abrufen. Die Daten aus der Pazifikregion sind von besonderem Interesse, da dort eine regionale Werbeaktion durchgeführt wurde, um neue Niederlassungen einzuführen und ihre Produkte bekannt zu machen.  
  
 In diesem Szenario gehen wir davon aus, dass die Daten aus einer Excel-Arbeitsmappe importiert wurden, die nur drei Monaten mit neuen Daten für einige Regionen enthält. Sie erstellen eine Tabelle für die Daten mithilfe von Transact-SQL-Skript, und definieren Sie dann eine Datenquellensicht für Vorhersagen verwenden.  
  
#### <a name="create-the-table-with-new-sales-data"></a>Erstellen der Tabelle mit neuen Umsatzdaten  
  
1.  Führen Sie in einem Transact-SQL-Abfragefenster die folgende Anweisung aus, um der Datenbank "AdventureWorksDW" (bzw. einer anderen Datenbank) die Umsatzdaten hinzuzufügen.  
  
    ```  
    USE [database name];  
    GO  
    IF OBJECT_ID ([dbo].[NewSalesData]) IS NOT NULL   
        DROP TABLE [dbo].[NewSalesData];  
    GO  
    CREATE TABLE [dbo].[NewSalesData]([Series] [nvarchar](255) NULL,  
    [NewDate] [datetime] NULL,  
    [NewQty] [float] NULL,  
    [NewAmount] [money] NULL) ON [PRIMARY]  
  
    GO  
    ```  
  
2.  Fügen Sie die neuen Werte mithilfe des folgenden Skripts ein.  
  
    ```  
    INSERT INTO [NewSalesData]  
    (Series,NewDate,NewQty,NewAmount)  
    VALUES('T1000 Pacific', '7/25/08', 55, '$130,170.22'),  
    ('T1000 Pacific', '8/25/08', 50, '$114,435.36 '),  
    ('T1000 Pacific', '9/25/08', 50, '$117,296.24 '),  
    ('T1000 Europe', '7/25/08', 37, '$88,210.00 '),  
    ('T1000 Europe', '8/25/08', 41, '$97,746.00 '),  
    ('T1000 Europe', '9/25/08', 37, '$88,210.00 '),  
    ('T1000 North America', '7/25/08', 69, '$164,500.00 '),  
    ('T1000 North America', '8/25/08', 66, '$157,348.00 '),  
    ('T1000 North America', '9/25/08', 58, '$138,276.00 '),  
    ('M200 Pacific', '7/25/08', 65, '$149,824.35'),  
    ('M200 Pacific', '8/25/08', 54,  '$124,619.46'),  
    ('M200 Pacific', '9/25/08', 61, '$141,143.39'),  
    ('M200 Europe', '7/25/08', 75, '$173,026.00'),  
    ('M200 Europe', '8/25/08', 76, '$175,212.00'),  
    ('M200 Europe', '9/25/08', 84, '$193,731.00'),  
    ('M200 North America', '7/25/08', 94, '$216,916.00'),  
    ('M200 North America', '8/25/08', 94, '$216,891.00'),  
    ('M200 North America', '9/25/08', 91,'$209,943.00');  
    ```  
  
    > [!WARNING]  
    >  Die Anführungszeichen werden mit Währungswerten verwendet, um Probleme mit dem Komma als Trennzeichen und dem Währungssymbol zu verhindern. Sie könnten die Währungswerte auch in diesem Format übergeben: `130170.22`  
    >   
    >  Die in der Beispieldatenbank verwendeten Datumsangaben wurden für diese Version geändert. Wenn Sie eine frühere Edition von AdventureWorks verwenden, müssen Sie die eingefügten Datumsangaben ggf. anpassen.  
  
###  <a name="bkmk_newReplaceData"></a> Erstellen Sie eine Datenquellensicht, die mit den neuen Umsatzdaten  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Datenquellensichten**und wählen Sie dann **Neue Datenquellensicht**aus.  
  
2.  Treffen Sie im Datenquellensicht-Assistenten die folgende Auswahl:  
  
     **Datenquelle**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]  
  
     **Tabellen und Sichten auswählen**: Wählen Sie die Tabelle, die Sie gerade erstellt haben, NewSalesData.  
  
3.  Klicken Sie auf **Fertig stellen**.  
  
4.  Klicken Sie in der Entwurfsoberfläche der Datenquellensicht mit der rechten Maustaste NewSalesData, und wählen Sie dann **Stichprobenoptionen** auf die Daten zu überprüfen.  
  
> [!WARNING]  
>  Sie verwenden diese Daten nur für Vorhersagen; daher ist es nicht wichtig, dass sie unvollständig sind.  
  
##  <a name="bkmk_CrossData2"></a> Erstellen die Daten für das Kreuzvorhersage-Modell  
 Die Daten, die verwendet wurde, in der ursprünglichen forecasting-Modell war bereits ein wenig durch die vTimeSeries-Sicht, die Ergebnisse einzelner Länder in Regionen zusammengeführt und mehrere Fahrradmodelle in eine kleinere Anzahl von Kategorien gruppiert werden. Sie erstellen ein Modell, das für weltweite Prognosen verwendet werden kann, indem Sie direkt im Datenquellensicht-Designer einige zusätzliche einfache Aggregationen erstellen. Die neue Datenquellensicht enthält nur die Summe und den Durchschnitt der Umsätze aller Produkte in allen Regionen.  
  
 Nachdem Sie die für das Modell verwendete Datenquelle erstellt haben, müssen Sie eine neue Datenquellensicht erstellen, die für Vorhersage verwendet werden soll. Wenn Sie z. B. die Umsätze in Europa mit dem neuen weltweite Modell vorhersagen möchten, dürfen Sie nur Daten aus der Region Europa eingeben. Daher richten Sie eine neue Datenquellensicht ein, die die ursprünglichen Daten filtert, und ändern die Filterbedingung für jeden Satz von Vorhersageabfragen.  
  
#### <a name="to-create-the-model-data-using-a-custom-data-source-view"></a>So erstellen Sie die Modelldaten mithilfe einer benutzerdefinierten Datenquellensicht  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Datenquellensichten**und wählen Sie dann **Neue Datenquellensicht**aus.  
  
2.  Klicken Sie auf der Begrüßungsseite des Assistenten auf **Weiter**.  
  
3.  Wählen Sie auf der Seite **Datenquelle auswählen** [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]aus und klicken Sie dann auf **Weiter**.  
  
4.  Auf der Seite **Tabellen und Sichten auswählen**, fügen Sie keine Tabellen – eine einfache klicken **Weiter**.  
  
5.  Auf der Seite **Abschließen des Assistenten**, geben Sie den Namen `AllRegions`, und klicken Sie dann auf **Fertig stellen**.  
  
6.  Klicken Sie danach mit der rechten Maustaste auf die leere Entwurfsoberfläche der Datenquellensicht und wählen Sie **Neue benannte Abfrage**aus.  
  
7.  In der **benannte Abfrage erstellen** im Dialogfeld für **Namen**, Typ `AllRegions`, und für **Beschreibung**, Typ **Summen- und Durchschnittswerte der Verkäufe für alle Modelle und Regionen**.  
  
8.  Geben Sie im SQL-Textbereich die folgende Anweisung ein, und klicken Sie dann auf "OK":  
  
    ```  
    SELECT ReportingDate,   
    SUM([Quantity]) as SumQty, AVG([Quantity]) as AvgQty,  
    SUM([Amount]) AS SumAmt, AVG([Amount]) AS AvgAmt,  
    'All Regions' as [Region]  
    FROM dbo.vTimeSeries   
    GROUP BY ReportingDate  
    ```  
  
9. Mit der rechten Maustaste die `AllRegions` Tabelle, und wählen Sie dann **Stichprobenoptionen**.  
  
###  <a name="bkmk_CrossData"></a> Erstellen Sie die Reihendaten für kreuzvorhersagen  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Datenquellensichten**und wählen Sie dann **Neue Datenquellensicht**aus.  
  
2.  Treffen Sie im Datenquellensicht-Assistenten die folgende Auswahl:  
  
     **Datenquelle**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]  
  
     **Tabellen und Sichten auswählen**: Aktivieren Sie keine Tabellen  
  
     **Name**: `T1000 Pacific Region`  
  
3.  Klicken Sie auf **Fertig stellen**.  
  
4.  Klicken Sie mit der rechten Maustaste auf die leere Entwurfsoberfläche für **T1000 Pacific Region.dsv**und wählen Sie dann **Neue benannte Abfrage**aus.  
  
     Das Dialogfeld **Benannte Abfrage erstellen** wird geöffnet. Geben Sie den Namen erneut ein und fügen Sie die folgende Beschreibung hinzu:  
  
     **Name**: `T1000 Pacific Region`  
  
     **Beschreibung**: **Filter`vTimeSeries`nach Region und Modell**  
  
5.  Geben Sie im Textbereich die folgende Abfrage ein, und klicken Sie dann auf "OK":  
  
    ```  
    SELECT ReportingDate, ModelRegion, Quantity, Amount  
    FROM dbo.vTimeSeries  
    WHERE (ModelRegion = N'T1000 Pacific')  
    ```  
  
    > [!NOTE]  
    >  Da Sie Vorhersagen für jede Reihe getrennt erstellen müssen, könnten Sie den Abfragetext kopieren und als Textdatei speichern, damit Sie ihn für die andere Datenreihe erneut verwenden können.  
  
6.  Klicken Sie in der Entwurfsoberfläche der Datenquellensicht mit der rechten Maustaste T1000 Pacific, und wählen Sie dann **Stichprobenoptionen** um sicherzustellen, dass die Daten ordnungsgemäß gefiltert wurden.  
  
     Sie verwenden diese Daten als Eingabe in das Modell, wenn Sie Abfragen für Kreuzvorhersagen erstellen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Zeitreihenvorhersagen mit aktualisierten Daten &#40;fortgeschrittene Data Mining-Lernprogramm&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Technische Referenz für den Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Datenquellsichten in mehrdimensionalen Modellen](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
  
  
