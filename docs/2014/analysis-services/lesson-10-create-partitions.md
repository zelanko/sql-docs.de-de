---
title: 'Lektion 11: Erstellen von Partitionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 92eb21a8-5fc4-4999-ad37-1332ce26431d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 545c6f45339047d3a632f9e18d69108f3c8b5111
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84543582"
---
# <a name="lesson-11-create-partitions"></a>Lektion 11: Erstellen von Partitionen
  In dieser Lektion erstellen Sie Partitionen, um die Internet Sales-Tabelle in kleinere logische Teile aufzuteilen, die unabhängig von anderen Partitionen verarbeitet (aktualisiert) werden können. Standardmäßig verfügt jede Tabelle, die Sie in Ihr Modell einschließen, über eine Partition, die alle Spalten und Zeilen der Tabelle enthält. Für die Internet Sales-Tabelle sollen die Daten nach Jahr aufgeteilt werden. eine Partition für jede der fünf Jahre der Tabelle.  Jede Partition kann dann unabhängig verarbeitet werden. Weitere Informationen finden Sie unter [Partitionen &#40;SSAS – tabellarisch&#41;](tabular-models/partitions-ssas-tabular.md).  
  
 Geschätzte Zeit zum Bearbeiten dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Dieses Thema ist Teil eines Tutorials zur Tabellenmodellierung, das in der richtigen Reihenfolge absolviert werden sollte. Sie sollten vor dem Ausführen der Aufgaben in dieser Lektion die vorherige Lektion abgeschlossen haben: [Lektion 10: Erstellen von Hierarchien](lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Erstellen von Partitionen  
  
#### <a name="to-create-partitions-in-the-internet-sales-table"></a>So erstellen Sie Partitionen in der Internet Sales-Tabelle  
  
1.  Klicken Sie im Modell-Designer auf die Tabelle **Internet Sales** und dann auf das Menü **Tabelle** . Klicken Sie anschließend auf **Partitionen**.  
  
     Das Dialogfeld **Partitions-Manager** wird geöffnet.  
  
2.  Klicken Sie im Dialogfeld **Partitions-Manager** unter **Partitionen**auf die Partition **Internet Sales** .  
  
3.  Ändern Sie unter **Partitions Name**den Namen in `Internet Sales 2005` .  
  
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
  
     Beachten Sie, dass eine Warnung mit dem Hinweis angezeigt wird, dass bestimmte Spalten nicht in der Quelle vorhanden sind. Dies liegt daran, dass Sie in [Lektion 3: Umbenennen von Spalten](rename-columns.md)die Spalten in der Internet Sales-Tabelle im Modell umbenannt haben, sodass Sie sich von denselben Spalten an der Quelle unterscheiden.  
  
#### <a name="to-create-a-partition-for-the-2006-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2006 in der Internet Sales-Tabelle eine Partition  
  
1.  Klicken Sie im Dialogfeld **Partitions-Manager** unter **Partitionen**auf die Partition, die `Internet Sales 2005` Sie soeben erstellt haben, und dann auf **Kopieren**.  
  
2.  Geben Sie in **Partitions Name den Namen**ein `Internet Sales 2006` .  
  
3.  Ersetzen Sie in der SQL-Anweisung die WHERE-Klausel durch Folgendes, damit die Partition nur die Zeilen für das 2006-Jahr enthält:  
  
    ```  
    WHERE (([OrderDate] >= N'2006-01-01 00:00:00') AND ([OrderDate] < N'2007-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2007-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2007 in der Internet Sales-Tabelle eine Partition  
  
1.  Klicken Sie im Dialogfeld **Partitions-Manager** auf **Kopieren**.  
  
2.  Geben Sie in **Partitions Name den Namen**ein `Internet Sales 2007` .  
  
3.  Wählen Sie in **Wechseln zu die**Option **Abfrage-Editor**aus.  
  
4.  Ersetzen Sie in der SQL-Anweisung die WHERE-Klausel durch Folgendes, damit die Partition nur die Zeilen für das 2007-Jahr enthält:  
  
    ```  
    WHERE (([OrderDate] >= N'2007-01-01 00:00:00') AND ([OrderDate] < N'2008-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2008-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2008 in der Internet Sales-Tabelle eine Partition  
  
1.  Klicken Sie im Dialogfeld **Partitions-Manager** auf **Neu**.  
  
2.  Geben Sie in **Partitions Name den Namen**ein `Internet Sales 2008` .  
  
3.  Wählen Sie in **Wechseln zu die**Option **Abfrage-Editor**aus.  
  
4.  Ersetzen Sie in der SQL-Anweisung die WHERE-Klausel durch Folgendes, damit die Partition nur die Zeilen für das 2008-Jahr enthält:  
  
    ```  
    WHERE (([OrderDate] >= N'2008-01-01 00:00:00') AND ([OrderDate] < N'2009-01-01 00:00:00'))  
    ```  
  
#### <a name="to-create-a-partition-for-the-2009-year-in-the-internet-sales-table"></a>So erstellen Sie für das Jahr 2009 in der Internet Sales-Tabelle eine Partition  
  
1.  Klicken Sie im Dialogfeld **Partitions-Manager** auf **Neu**.  
  
2.  Geben Sie in **Partitions Name den Namen**ein `Internet Sales 2009` .  
  
3.  Wählen Sie in **Wechseln zu die**Option **Abfrage-Editor**aus.  
  
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
  
4.  Aktivieren Sie für jede der fünf Partitionen, die Sie erstellt haben, das Kontrollkästchen in der Spalte **Verarbeiten**, und klicken Sie anschließend auf **OK**.  
  
     Wenn Identitätswechsel-Anmeldeinformationen verlangt werden, geben Sie die Kombination aus Windows-Benutzername und Kennwort ein, die Sie in Lektion 2 (Schritt 6) angegeben haben.  
  
     Daraufhin wird das Dialogfeld **Daten Prozess** angezeigt, in dem die Prozessdetails für jede Partition angezeigt werden. Beachten Sie, dass eine unterschiedliche Anzahl an Zeilen für jede Partition übertragen wird. Das liegt daran, dass jede Partition nur die Zeilen für das in der WHERE-Klausel der SQL-Anweisung angegebene Jahr beinhaltet. Für das Jahr 2010 sind keine Daten vorhanden.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie mit diesem Tutorial fortfahren möchten, wechseln Sie zur nächsten Lektion: [Lektion 12: Erstellen von Rollen](lesson-11-create-roles.md).  
  
  
