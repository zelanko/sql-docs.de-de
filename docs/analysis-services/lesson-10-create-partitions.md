---
title: 'Lektion 10: Erstellen von Partitionen | Microsoft-Dokumentation'
ms.date: 08/22/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3ce1bc8aa83b376aecdf5bd80a180a4777044bce
ms.sourcegitcommit: e8e013b4d4fbd3b25f85fd6318d3ca8ddf73f31e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42791931"
---
# <a name="lesson-10-create-partitions"></a>Lektion 10: Erstellen von Partitionen
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

In dieser Lektion erstellen Sie Partitionen, um die FactInternetSales-Tabelle in kleinere logische Teile aufteilen, die verarbeitet werden können (aktualisiert) unabhängig von anderen Partitionen. Standardmäßig verfügt jede Tabelle, die Sie ins Modell einbinden, über eine Partition. Diese beinhaltet alle Spalten und Zeilen der Tabelle. Wir möchten die Daten nach Jahr unterteilen, für die Tabelle "factinternetsales"; eine Partition für jedes der fünf Jahren der Tabelle. Jede Partition kann dann unabhängig verarbeitet werden. Weitere Informationen finden Sie unter [Partitionen](../analysis-services/tabular-models/partitions-ssas-tabular.md).  
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Vor dem Ausführen der Aufgaben in dieser Lektion an, Sie sollten die vorherige Lektion abgeschlossen haben: [Lektion 9: Erstellen von Hierarchien](../analysis-services/lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Erstellen von Partitionen  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>Zum Erstellen von Partitionen in der Tabelle "factinternetsales"  
  
1.  Erweitern Sie im tabellarischen Modell-Explorer **Tabellen**, mit der rechten Maustaste **"factinternetsales"** > **Partitionen**.  
  
2.  Klicken Sie im Dialogfeld Partitions-Manager auf **Kopie**.  
  
3.  In **Partitionsname**, ändern Sie den Namen in **FactInternetSales2010**.  
  
    > [!TIP]  
    > Beachten Sie, dass die Spaltennamen in das tabellenvorschaufenster, die in der Modelltabelle (aktiviert), durch die Spaltennamen aus der Quelle enthaltenen Spalten anzuzeigen. Das liegt daran, dass das Tabellenvorschaufenster Spalten von der Quelltabelle und nicht von der Modelltabelle anzeigt.  
  
4.  Wählen Sie die **SQL** Schaltfläche direkt über der rechten Seite des Vorschaufensters auf den SQL-Anweisung-Editor zu öffnen.  
  
    Da die Partition nur die Zeilen eines bestimmten Zeitraums beinhalten soll, ist die WHERE-Klausel einzufügen. Sie können nur anhand einer SQL-Anweisung eine WHERE-Klausel erstellen.  
  
5.  In der **SQL-Anweisung** Feld, ersetzen Sie die vorhandene Anweisung durch Kopieren und Einfügen die folgende Anweisung aus:  
  
    ```  
    SELECT   
    [dbo].[FactInternetSales].[ProductKey],  
    [dbo].[FactInternetSales].[CustomerKey],  
    [dbo].[FactInternetSales].[PromotionKey],  
    [dbo].[FactInternetSales].[CurrencyKey],  
    [dbo].[FactInternetSales].[SalesTerritoryKey],  
    [dbo].[FactInternetSales].[SalesOrderNumber],  
    [dbo].[FactInternetSales].[SalesOrderLineNumber],  
    [dbo].[FactInternetSales].[RevisionNumber],  
    [dbo].[FactInternetSales].[OrderQuantity],  
    [dbo].[FactInternetSales].[UnitPrice],  
    [dbo].[FactInternetSales].[ExtendedAmount],  
    [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
    [dbo].[FactInternetSales].[DiscountAmount],  
    [dbo].[FactInternetSales].[ProductStandardCost],  
    [dbo].[FactInternetSales].[TotalProductCost],  
    [dbo].[FactInternetSales].[SalesAmount],  
    [dbo].[FactInternetSales].[TaxAmt],  
    [dbo].[FactInternetSales].[Freight],  
    [dbo].[FactInternetSales].[CarrierTrackingNumber],  
    [dbo].[FactInternetSales].[CustomerPONumber],  
    [dbo].[FactInternetSales].[OrderDate],  
    [dbo].[FactInternetSales].[DueDate],  
    [dbo].[FactInternetSales].[ShipDate]   
    FROM [dbo].[FactInternetSales]  
    WHERE (([OrderDate] >= N'2010-01-01 00:00:00') AND ([OrderDate] < N'2011-01-01 00:00:00'))  
    ```  
  
    Diese Anweisung gibt an, dass die Partition alle Daten der Zeilen beinhalten soll, bei denen OrderDate für das Kalenderjahr 2010 gilt (wie in der WHERE-Klausel angegeben).  
  
6.  Klicken Sie auf **Überprüfen**.  
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>So erstellen Sie eine Partition für das Jahr 2011  
  
1.  Klicken Sie in der Liste auf die **FactInternetSales2010** Partitionieren Sie zuvor erstellt haben, und klicken Sie dann auf **Kopie**.  
  
2.  In **Partitionsname**, Typ **FactInternetSales2011**.  
  
3.  Ersetzen Sie in der SQL-Anweisung die WHERE-Klausel durch Folgendes, damit die Partition nur die Zeilen für das Jahr 2011 enthält:  
  
    ```  
    WHERE (([OrderDate] >= N'2011-01-01 00:00:00') AND ([OrderDate] < N'2012-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2012-year"></a>So erstellen Sie eine Partition für das Jahr 2012  
  
- Führen Sie die Schritte weiter oben, verwenden die folgende WHERE-Klausel aus. 
  
    ```  
    WHERE (([OrderDate] >= N'2012-01-01 00:00:00') AND ([OrderDate] < N'2013-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2013-year"></a>So erstellen Sie eine Partition für das Jahr 2013  
  
- Führen Sie die Schritte weiter oben, verwenden die folgende WHERE-Klausel aus. 
  
    ```  
    WHERE (([OrderDate] >= N'2013-01-01 00:00:00') AND ([OrderDate] < N'2014-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2014-year"></a>Erstellen Sie eine Partition für das Jahr 2014  
  
- Führen Sie die Schritte weiter oben, verwenden die folgende WHERE-Klausel aus. 
  
    ```  
    WHERE (([OrderDate] >= N'2014-01-01 00:00:00') AND ([OrderDate] < N'2015-01-01 00:00:00'))  
    ```  

## <a name="delete-the-factinternetsales-partition"></a>Löschen Sie die Partition "factinternetsales"
Nun, da Sie Partitionen für jedes Jahr haben, können Sie die Partition "factinternetsales" löschen. Dies verhindert die Überlappung, bei der Auswahl alle Prozess, bei der Verarbeitung von Partitionen.
#### <a name="to-delete-the-factinternetsales-partition"></a>So löschen Sie die Partition "factinternetsales"
-  Klicken Sie auf der Partition "factinternetsales", und klicken Sie dann auf **löschen**.



## <a name="process-partitions"></a>Partitionen verarbeiten  
Beachten Sie, dass im Partitions-Manager die **zuletzt verarbeitet** Spalte für jede der neuen Partitionen soeben erstellten zeigt diese Partitionen nicht verarbeitet wurden noch. Wenn Sie neue Partitionen erstellen, führen Sie einen Partitionsverarbeitungs- bzw. Tabellenverarbeitungsvorgang aus, um die Daten dieser Partitionen zu aktualisieren.  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>So verarbeiten Sie die FactInternetSales-Partitionen  
  
1.  Klicken Sie auf **OK** um das Dialogfeld Partitions-Manager zu schließen.  
  
2.  Klicken Sie auf die **"factinternetsales"** Tabelle, und klicken Sie dann die **Modell** Menü > **Prozess** > **Partitionen verarbeiten**.  
  
3.  Die Partitionen verarbeiten, überprüfen Sie im Dialogfeld **Modus** nastaven NA hodnotu **Standard verarbeiten**.  
  
4.  Aktivieren Sie das Kontrollkästchen in der Spalte **Verarbeiten** für jede der fünf von Ihnen erstellten Partitionen, und klicken Sie anschließend auf **OK**.  

    ![als-tabellarische-lesson10-Prozess-Partitionen](../analysis-services/media/as-tabular-lesson10-process-partitions.png)
  
    Wenn Sie für den Identitätswechsel-Anmeldeinformationen aufgefordert werden, geben Sie den Windows-Benutzernamen und das Kennwort, die Sie in Lektion 2 angegeben.  
  
    Das Dialogfeld **Datenverarbeitung** wird daraufhin angezeigt. Es zeigt die Verarbeitungsdetails für jede Partition an. Beachten Sie, dass eine unterschiedliche Anzahl an Zeilen für jede Partition übertragen wird. Das liegt daran, dass jede Partition nur die Zeilen für das in der WHERE-Klausel der SQL-Anweisung angegebene Jahr beinhaltet. Wenn die Verarbeitung abgeschlossen ist, fahren Sie fort und schließen Sie das Dialogfeld „Datenverarbeitung“.  
  
    ![als tabellarische-lesson10-Prozess-Vervollständigung](../analysis-services/media/as-tabular-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>Wie geht es weiter?
Wechseln Sie zur nächsten Lektion: [Lektion 11: Erstellen von Rollen](../analysis-services/lesson-11-create-roles.md). 
