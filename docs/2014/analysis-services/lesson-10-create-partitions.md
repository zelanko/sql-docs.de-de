---
title: 'Lektion 11: Erstellen von Partitionen | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: c480583da42aee4f73e6053d20e7bf8b6542547c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050424"
---
# <a name="lesson-11-create-partitions"></a>Lektion 11: Erstellen von Partitionen
  In dieser Lektion erstellen Sie Partitionen, um die Internet Sales-Tabelle in kleinere logische Teile aufzuteilen, die unabhängig von anderen Partitionen verarbeitet (aktualisiert) werden können. Standardmäßig verfügt jede Tabelle, die Sie ins Modell einbinden, über eine Partition. Diese beinhaltet alle Spalten und Zeilen der Tabelle. Für die Internet Sales-Tabelle sollen die Daten nach Jahr aufgeteilt werden, wobei jede Partition jeweils ein Jahr von den fünf Jahren der Tabelle umfasst.  Jede Partition kann dann unabhängig verarbeitet werden. Weitere Informationen finden Sie unter [Partitionen &#40;SSAS – tabellarisch&#41;](tabular-models/partitions-ssas-tabular.md).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Dieses Thema ist Teil eines Lernprogramms zur Tabellenmodellierung, das in der entsprechenden Reihenfolge bearbeitet werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 10: Erstellen von Hierarchien](lesson-9-create-hierarchies.md).  
  
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
  
     Beachten Sie, dass eine Warnung mit dem Hinweis angezeigt wird, dass bestimmte Spalten nicht in der Quelle vorhanden sind. Grund hierfür ist, in [Lektion 3: Umbenennen von Spalten](rename-columns.md), Sie umbenannt haben die Spalten in der Internet Sales-Tabelle im Modell, die von den Namen der Quelle des unterschiedlich sein.  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2006 in der Internet Sales-Tabelle eine Partition  
  
1.  In der **Partitions-Manager** Dialogfeld **Partitionen**, klicken Sie auf die `Internet Sales 2005` Partition, die Sie gerade erstellt haben, und klicken Sie dann **Kopie**.  
  
2.  In **Partitionsname**, Typ `Internet Sales 2006`.  
  
3.  Ersetzen Sie in der SQL-Anweisung in Ordnung für die Partition nur die Zeilen für das Jahr 2006 enthalten die WHERE-Klausel durch Folgendes:  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2007 in der Internet Sales-Tabelle eine Partition  
  
1.  Klicken Sie im Dialogfeld **Partitions-Manager** auf **Kopieren**.  
  
2.  In **Partitionsname**, Typ `Internet Sales 2007`.  
  
3.  In **wechseln zu**Option **Abfrage-Editor**.  
  
4.  Ersetzen Sie in der SQL-Anweisung in Ordnung für die Partition nur die Zeilen für das Jahr 2007 enthalten die WHERE-Klausel durch Folgendes:  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2008 in der Internet Sales-Tabelle eine Partition  
  
1.  Klicken Sie im Dialogfeld **Partitions-Manager** auf **Neu**.  
  
2.  In **Partitionsname**, Typ `Internet Sales 2008`.  
  
3.  In **wechseln zu**Option **Abfrage-Editor**.  
  
4.  Ersetzen Sie in der SQL-Anweisung in Ordnung für die Partition nur die Zeilen für das Jahr 2008 enthalten die WHERE-Klausel durch Folgendes:  
  
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
  
     Die **Datenverarbeitung** Dialogfeld wird angezeigt, und zeigt die Verarbeitungsdetails für jede Partition. Beachten Sie, dass eine unterschiedliche Anzahl an Zeilen für jede Partition übertragen wird. Das liegt daran, dass jede Partition nur die Zeilen für das in der WHERE-Klausel der SQL-Anweisung angegebene Jahr beinhaltet. Für das Jahr 2010 sind keine Daten vorhanden.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 12: Erstellen von Rollen](lesson-11-create-roles.md).  
  
  