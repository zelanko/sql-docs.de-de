---
title: 'Lektion 11: Erstellen von Partitionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 06ffe60802e52bd0ae141435628fc3812dc2c7c6
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66079201"
---
# <a name="lesson-11-create-partitions"></a>Lektion 11: Erstellen von Partitionen
  In dieser Lektion erstellen Sie Partitionen, um die Internet Sales-Tabelle in kleinere logische Teile aufzuteilen, die unabhängig von anderen Partitionen verarbeitet (aktualisiert) werden können. Standardmäßig verfügt jede Tabelle im Modell über eine Partition, die Spalten und Zeilen der Tabelle enthält. Der Internet Sales-Tabelle möchten wir die Daten nach Jahr unterteilen; eine Partition für jedes der fünf Jahren der Tabelle.  Jede Partition kann dann unabhängig verarbeitet werden. Weitere Informationen finden Sie unter [Partitionen &#40;SSAS – tabellarisch&#41;](tabular-models/partitions-ssas-tabular.md).  
  
 Geschätzte Zeit zum Abschließen dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 10: Erstellen von Hierarchien](lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Erstellen von Partitionen  
  
#### <a name="to-create-partitions-in-the-internet-sales-table"></a>So erstellen Sie Partitionen in der Internet Sales-Tabelle  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle **Internet Sales** und dann auf das Menü **Tabelle** . Klicken Sie anschließend auf **Partitionen**.  
  
     Das Dialogfeld **Partitions-Manager** wird geöffnet.  
  
2.  In der **Partitions-Manager** Dialogfeld **Partitionen**, klicken Sie auf die **Internetverkäufe** Partition.  
  
3.  In **Partitionsname**, ändern Sie den Namen in `Internet Sales 2005`.  
  
    > [!TIP]  
    >  Vor dem Fortfahren mit dem nächsten Schritt ist zu beachten, dass die Spaltennamen für diese in der Modelltabelle enthaltenen (aktivierten) Spalten im Tabellenvorschaufenster den Spaltennamen der Quelle entsprechen. Das liegt daran, dass das Tabellenvorschaufenster Spalten von der Quelltabelle und nicht von der Modelltabelle anzeigt.  
  
4.  Klicken Sie direkt rechts oberhalb des Vorschaufensters auf die Schaltfläche **Abfrage-Editor** .  
  
     Da die Partition nur die Zeilen eines bestimmten Zeitraums beinhalten soll, ist die WHERE-Klausel einzufügen. Sie können nur anhand einer SQL-Anweisung eine WHERE-Klausel erstellen.  
  
5.  Ersetzen Sie im Feld **SQL-Anweisung** die vorhandene Anweisung durch die folgende Anweisung:  
  
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
    WHERE (([OrderDate] >= N'2005-01-01 00:00:00') AND ([OrderDate] < N'2006-01-01 00:00:00'))  
    ```  
  
     Diese Anweisung gibt an, dass die Partition alle Daten der Zeilen beinhalten soll, bei denen OrderDate für das Kalenderjahr 2005 gilt (wie in der WHERE-Klausel angegeben).  
  
6.  Klicken Sie auf **Überprüfen**.  
  
     Beachten Sie, dass eine Warnung mit dem Hinweis angezeigt wird, dass bestimmte Spalten nicht in der Quelle vorhanden sind. Grund hierfür ist, im [Lektion 3: Umbenennen von Spalten](rename-columns.md), Sie diese Spalten in der Internet Sales-Tabelle in das Modell, das aus der Quelle abweichen umbenannt.  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2006 in der Internet Sales-Tabelle eine Partition  
  
1.  In der **Partitions-Manager** Dialogfeld **Partitionen**, klicken Sie auf die `Internet Sales 2005` Partition, die Sie gerade erstellt haben, und klicken Sie dann **Kopie**.  
  
2.  In **Partitionsname**, Typ `Internet Sales 2006`.  
  
3.  Ersetzen Sie in der SQL-Anweisung in der richtigen Reihenfolge für die Partition nur die Zeilen für das Jahr 2006 enthält die WHERE-Klausel durch Folgendes:  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2007 in der Internet Sales-Tabelle eine Partition  
  
1.  Klicken Sie im Dialogfeld **Partitions-Manager** auf **Kopieren**.  
  
2.  In **Partitionsname**, Typ `Internet Sales 2007`.  
  
3.  In **wechseln zu**Option **Abfrage-Editor**.  
  
4.  Ersetzen Sie in der SQL-Anweisung in der richtigen Reihenfolge für die Partition nur die Zeilen für das Jahr 2007 enthält die WHERE-Klausel durch Folgendes:  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2008 in der Internet Sales-Tabelle eine Partition  
  
1.  Klicken Sie im Dialogfeld **Partitions-Manager** auf **Neu**.  
  
2.  In **Partitionsname**, Typ `Internet Sales 2008`.  
  
3.  In **wechseln zu**Option **Abfrage-Editor**.  
  
4.  Ersetzen Sie in der SQL-Anweisung in der richtigen Reihenfolge für die Partition nur die Zeilen für das Jahr 2008, enthält die WHERE-Klausel durch Folgendes:  
  
    ```  
    WHERE (([OrderDate] >= N'2008-01-01 00:00:00') AND ([OrderDate] < N'2009-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2009-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2009 in der Internet Sales-Tabelle eine Partition  
  
1.  Klicken Sie im Dialogfeld **Partitions-Manager** auf **Neu**.  
  
2.  In **Partitionsname**, Typ `Internet Sales 2009`.  
  
3.  In **wechseln zu**Option **Abfrage-Editor**.  
  
4.  Ersetzen Sie in der SQL-Anweisung die WHERE-Klausel durch Folgendes, damit die Partition nur die Zeilen für das Jahr 2009 enthält:  
  
    ```  
    WHERE (([OrderDate] >= N'2009-01-01 00:00:00') AND ([OrderDate] < N'2010-01-01 00:00:00'))  
    ```  
  
## <a name="process-partitions"></a>Partitionen verarbeiten  
 Achten Sie im Dialogfeld **Partitions-Manager** auf das Sternchen (**\***) neben den Partitionsnamen für jede der gerade neu erstellten Partitionen. Dies gibt an, dass die Partition noch nicht verarbeitet (aktualisiert) wurde. Wenn Sie neue Partitionen erstellen, führen Sie einen Partitionsverarbeitungs- bzw. Tabellenverarbeitungsvorgang aus, um die Daten dieser Partitionen zu aktualisieren.  
  
#### <a name="to-process-internet-sales-partitions"></a>So verarbeiten Sie die Internet Sales-Partitionen  
  
1.  Klicken Sie auf **OK** , um das Dialogfeld **Partitions-Manager** zu schließen.  
  
2.  Klicken Sie im Modell-Designer auf die Tabelle **Internet Sales** . Klicken Sie anschließend auf das Menü **Modell** , zeigen Sie auf **Verarbeiten** (Aktualisieren), und klicken Sie auf **Partitionen verarbeiten**.  
  
3.  Überprüfen Sie im Dialogfeld **Partitionen verarbeiten** , ob der Wert für **Modus** auf **Standard verarbeiten**festgelegt ist.  
  
4.  Aktivieren Sie das Kontrollkästchen in der Spalte **Verarbeiten** für jede der fünf von Ihnen erstellten Partitionen, und klicken Sie anschließend auf **OK**.  
  
     Wenn Identitätswechsel-Anmeldeinformationen verlangt werden, geben Sie die Kombination aus Windows-Benutzername und Kennwort ein, die Sie in Lektion 2 (Schritt 6) angegeben haben.  
  
     Die **Datenverarbeitung** dann erscheint und zeigt die Verarbeitungsdetails für jede Partition. Beachten Sie, dass eine unterschiedliche Anzahl an Zeilen für jede Partition übertragen wird. Das liegt daran, dass jede Partition nur die Zeilen für das in der WHERE-Klausel der SQL-Anweisung angegebene Jahr beinhaltet. Für das Jahr 2010 sind keine Daten vorhanden.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Um dieses Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: Lektion: [Lektion 12: Erstellen von Rollen](lesson-11-create-roles.md).  
  
  
