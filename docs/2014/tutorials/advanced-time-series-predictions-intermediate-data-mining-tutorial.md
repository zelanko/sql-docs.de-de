---
title: Erweiterte Zeitreihen Vorhersagen (Data Mining-Lernprogramm für Fortgeschrittene) | Microsoft-Dokumentation
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
ms.openlocfilehash: ca144d1d473f7df49f73d5ed170052c61ce6107d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68893693"
---
# <a name="advanced-time-series-predictions-intermediate-data-mining-tutorial"></a>Erweiterte Zeitreihenvorhersagen (Data Mining-Lernprogramm für Fortgeschrittene)
  Bei der Untersuchung des Prognosemodells wurde gezeigt, dass die Verkäufe in den meisten Regionen einem ähnlichen Muster folgen. Einige Regionen und Modelle wie das Modell M200 im Pazifischen Raum weisen jedoch deutlich abweichende Trends auf. Dies ist wenig überraschend, da bekanntermaßen häufig regionale Unterschiede auftreten und durch zahlreiche Faktoren verursacht werden können, einschließlich Marketingaktionen, fehlerhafter Berichterstellung sowie politischer Faktoren.  
  
 Ihre Benutzer benötigen jedoch ein Modell, das weltweit angewendet werden kann. Sie können daher die Auswirkungen einzelner Faktoren auf Vorhersagen minimieren, indem Sie ein Modell erstellen, das auf den aggregierten Zahlen aller Verkäufe weltweit basiert. Sie können dann dieses Modell für Vorhersagen für jede einzelne Region nutzen.  
  
 In dieser Aufgabe erstellen Sie alle Datenquellen, die für die erweiterten Vorhersagetasks erforderlich sind. Sie erstellen zwei Datenquellensichten zur Verwendung als Eingaben in die Vorhersageabfrage und eine Datenquellensicht, die beim Erstellen eines neuen Modells zum Einsatz kommt.  
  
 **Schritte**  
  
1.  [Vorbereiten der erweiterten Umsatzdaten (für die Vorhersage)](#bkmk_newExtendData)  
  
2.  [Vorbereiten der aggregierten Daten (zum Erstellen des Modells)](#bkmk_newReplaceData)  
  
3.  [Vorbereiten der Reihendaten (für Kreuzvorhersagen)](#bkmk_CrossData2)  
  
4.  [Vorhersagen mit EXTEND](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
5.  [Erstellen des Modells für Kreuzvorhersagen](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
6.  [Vorhersagen mit REPLACE](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
7.  [Überprüfen der neuen Vorhersagen](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
##  <a name="bkmk_newExtendData"></a>Erstellen der neuen erweiterten Umsatzdaten  
 Um die Umsatzdaten zu aktualisieren, müssen Sie die letzten Umsatzzahlen abrufen. Die Daten aus der Pazifikregion sind von besonderem Interesse, da dort eine regionale Werbeaktion durchgeführt wurde, um neue Niederlassungen einzuführen und ihre Produkte bekannt zu machen.  
  
 In diesem Szenario gehen wir davon aus, dass die Daten aus einer Excel-Arbeitsmappe importiert wurden, die für eine Reihe von Regionen nur drei Monate neue Daten enthält. Sie erstellen mit einem Transact-SQL-Skript eine Tabelle für die Daten und definieren dann eine Datenquellen Sicht, die für die Vorhersage verwendet werden soll.  
  
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
  
###  <a name="bkmk_newReplaceData"></a>Erstellen einer Datenquellen Sicht mit den neuen Umsatzdaten  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Datenquellensichten**und wählen Sie dann **Neue Datenquellensicht**aus.  
  
2.  Treffen Sie im Datenquellensicht-Assistenten die folgende Auswahl:  
  
     **Datenquelle**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]  
  
     **Tabellen und Sichten auswählen**: Wählen Sie die Tabelle aus, die Sie soeben erstellt haben, newsalesdata.  
  
3.  Klicken Sie auf **Fertig stellen**.  
  
4.  Klicken Sie in der Entwurfs Oberfläche der Datenquellen Sicht mit der rechten Maustaste auf newsalesdata, und wählen Sie **Daten durchsuchen** aus, um die Daten zu überprüfen.  
  
> [!WARNING]  
>  Sie verwenden diese Daten nur für Vorhersagen; daher ist es nicht wichtig, dass sie unvollständig sind.  
  
##  <a name="bkmk_CrossData2"></a>Erstellen der Daten für das Kreuz Vorhersagemodell  
 Die Daten, die im ursprünglichen Prognosemodell verwendet wurden, wurden in der Sicht vTimeSeries bereits ein wenig gruppiert, da dort mehrere Fahrradmodelle in eine kleinere Anzahl von Kategorien und die Ergebnisse einzelner Länder in Regionen zusammengeführt wurden. Sie erstellen ein Modell, das für weltweite Prognosen verwendet werden kann, indem Sie direkt im Datenquellensicht-Designer einige zusätzliche einfache Aggregationen erstellen. Die neue Datenquellensicht enthält nur die Summe und den Durchschnitt der Umsätze aller Produkte in allen Regionen.  
  
 Nachdem Sie die für das Modell verwendete Datenquelle erstellt haben, müssen Sie eine neue Datenquellensicht erstellen, die für Vorhersage verwendet werden soll. Wenn Sie z. B. die Umsätze in Europa mit dem neuen weltweite Modell vorhersagen möchten, dürfen Sie nur Daten aus der Region Europa eingeben. Daher richten Sie eine neue Datenquellensicht ein, die die ursprünglichen Daten filtert, und ändern die Filterbedingung für jeden Satz von Vorhersageabfragen.  
  
#### <a name="to-create-the-model-data-using-a-custom-data-source-view"></a>So erstellen Sie die Modelldaten mithilfe einer benutzerdefinierten Datenquellensicht  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Datenquellensichten**und wählen Sie dann **Neue Datenquellensicht**aus.  
  
2.  Klicken Sie auf der Begrüßungsseite des Assistenten auf **Weiter**.  
  
3.  Wählen Sie auf der Seite **Datenquelle auswählen**[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]aus und klicken Sie dann auf **Weiter**.  
  
4.  Wählen Sie auf der Seite **Tabellen und Sichten**, keine Tabellen hinzufügen aus. Klicken Sie einfach auf **weiter**.  
  
5.  Geben Sie auf der Seite **Assistenten abschließen**den Namen `AllRegions`ein, und klicken Sie dann auf **Fertig**stellen.  
  
6.  Klicken Sie danach mit der rechten Maustaste auf die leere Entwurfsoberfläche der Datenquellensicht und wählen Sie **Neue benannte Abfrage**aus.  
  
7.  Geben Sie im Dialogfeld **benannte Abfrage erstellen** unter **Name**den Namen `AllRegions`ein, und geben Sie für **Beschreibung**den Wert **Sum und Average of Sales für alle Modelle und Regionen**ein.  
  
8.  Geben Sie im SQL-Textbereich die folgende Anweisung ein, und klicken Sie dann auf "OK":  
  
    ```  
    SELECT ReportingDate,   
    SUM([Quantity]) as SumQty, AVG([Quantity]) as AvgQty,  
    SUM([Amount]) AS SumAmt, AVG([Amount]) AS AvgAmt,  
    'All Regions' as [Region]  
    FROM dbo.vTimeSeries   
    GROUP BY ReportingDate  
    ```  
  
9. Klicken Sie mit der `AllRegions` rechten Maustaste auf die Tabelle, und wählen Sie **Daten durchsuchen**aus.  
  
###  <a name="bkmk_CrossData"></a>So erstellen Sie die Reihen Daten für Kreuz Vorhersagen  
  
1.  Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf **Datenquellensichten**und wählen Sie dann **Neue Datenquellensicht**aus.  
  
2.  Treffen Sie im Datenquellensicht-Assistenten die folgende Auswahl:  
  
     **Datenquelle**:[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]  
  
     **Tabellen und Sichten auswählen**: keine Tabellen auswählen  
  
     **Name**:`T1000 Pacific Region`  
  
3.  Klicken Sie auf **Fertig stellen**.  
  
4.  Klicken Sie mit der rechten Maustaste auf die leere Entwurfsoberfläche für **T1000 Pacific Region.dsv**und wählen Sie dann **Neue benannte Abfrage**aus.  
  
     Das Dialogfeld **Benannte Abfrage erstellen** wird geöffnet. Geben Sie den Namen erneut ein und fügen Sie die folgende Beschreibung hinzu:  
  
     **Name**:`T1000 Pacific Region`  
  
     **Beschreibung**: **nach`vTimeSeries`Region und Modell Filtern**  
  
5.  Geben Sie im Textbereich die folgende Abfrage ein, und klicken Sie dann auf "OK":  
  
    ```  
    SELECT ReportingDate, ModelRegion, Quantity, Amount  
    FROM dbo.vTimeSeries  
    WHERE (ModelRegion = N'T1000 Pacific')  
    ```  
  
    > [!NOTE]  
    >  Da Sie Vorhersagen für jede Reihe getrennt erstellen müssen, könnten Sie den Abfragetext kopieren und als Textdatei speichern, damit Sie ihn für die andere Datenreihe erneut verwenden können.  
  
6.  Klicken Sie in der Entwurfs Oberfläche der Datenquellen Sicht mit der rechten Maustaste auf T1000 Pacific, und wählen Sie **Daten durchsuchen** , um zu überprüfen, ob die Daten ordnungsgemäß gefiltert wurden.  
  
     Sie verwenden diese Daten als Eingabe in das Modell, wenn Sie Abfragen für Kreuzvorhersagen erstellen.  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in der Lektion  
 [Zeitreihen Vorhersagen mit aktualisierten Data &#40;Data Mining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)   
 [Technische Referenz für den Microsoft Time Series-Algorithmus](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)   
 [Datenquellensichten in mehrdimensionalen Modellen](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
