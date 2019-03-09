---
title: 'Analysis Services-Tutorial – Lektion 10: Erstellen von Partitionen | Microsoft-Dokumentation'
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile"
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 705705410a69c4fa0eff507c97747f55b72b1250
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685697"
---
# <a name="create-partitions"></a>Erstellen von Partitionen

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

In dieser Lektion erstellen Sie Partitionen, um die FactInternetSales-Tabelle in kleinere logische Teile aufteilen, die verarbeitet werden können (aktualisiert) unabhängig von anderen Partitionen. Standardmäßig hat jede Tabelle in Ihrem Modell eine Partition, die alle in der Tabelle Spalten und Zeilen enthält. Wir möchten die Daten nach Jahr unterteilen, für die Tabelle "factinternetsales"; eine Partition für jedes der fünf Jahren der Tabelle. Jede Partition kann dann unabhängig verarbeitet werden. Weitere Informationen finden Sie unter [Partitionen](../tabular-models/partitions-ssas-tabular.md). 
  
Geschätzte Zeit zum Bearbeiten dieser Lektion: **15 Minuten**  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  

Dieser Artikel ist Teil einer Tutorials zur tabellenmodellierung, das in der Reihenfolge absolviert werden sollte. Bevor Sie die Aufgaben in dieser Lektion ausführen, sollten Sie die vorherige Lektion abgeschlossen haben: [Lektion 9: Erstellen von Hierarchien](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md).  
  
## <a name="create-partitions"></a>Erstellen von Partitionen  
  
#### <a name="to-create-partitions-in-the-factinternetsales-table"></a>Zum Erstellen von Partitionen in der Tabelle "factinternetsales"  
  
1.  Erweitern Sie im tabellarischen Modell-Explorer **Tabellen**, und klicken Sie dann mit der rechten Maustaste **"factinternetsales"** > **Partitionen**.  
  
2.  Klicken Sie im Partitions-Manager **Kopie**, und ändern Sie dann den Namen in **FactInternetSales2010**.
  
    Da Sie die Partition nur die Zeilen innerhalb eines bestimmten Zeitraums, für das Jahr 2010 enthalten soll, müssen Sie den Abfrageausdruck ändern.
  
4.  Klicken Sie auf **Entwurf** Abfrage-Editor öffnen, und klicken Sie auf die **FactInternetSales2010** Abfrage.

5.  Klicken Sie in der Vorschau auf den Pfeil nach unten in der **OrderDate** Spaltenüberschrift, und klicken Sie dann auf **Datums-/Zeitfilter** > **zwischen**.

    ![as-lesson10-query-editor](../tutorial-tabular-1400/media/as-lesson10-query-editor.png)

6.  Klicken Sie im Dialogfeld Filtern von Zeilen in **Zeilen anzeigen: OrderDate**, lassen Sie **ist nach oder gleich**, und geben Sie in der Date-Felds **1/1/2010**. Lassen Sie die **und** Operator ausgewählt ist, wählen Sie dann **ist, bevor Sie**, geben Sie im Datumsfeld **1/1/2011**, und klicken Sie dann auf **OK**.

    ![as-lesson10-filter-rows](../tutorial-tabular-1400/media/as-lesson10-filter-rows.png)
    
    Beachten Sie, dass im Abfrage-Editor bei ANGEWENDETE Schritte ein weiterer Schritt mit dem Namen gefilterte-Zeilen angezeigt. Diese Filter werden nur Bestelldaten aus 2010 ausgewählt.

8.  Klicken Sie auf **Importieren**.

    Beachten Sie im Partitions-Manager, dass jetzt der Abfrageausdruck eine zusätzliche gefilterte-Zeilen-Klausel verfügt.

    ![as-lesson10-query](../tutorial-tabular-1400/media/as-lesson10-query.png)
  
    Diese Anweisung gibt an, dass diese Partition nur die Daten der Zeilen beinhalten soll, in denen OrderDate im Kalenderjahr 2010 als in der gefilterte-Zeilen-Klausel angegeben.  
  
  
#### <a name="to-create-a-partition-for-the-2011-year"></a>So erstellen Sie eine Partition für das Jahr 2011  
  
1.  Klicken Sie in der Liste auf die **FactInternetSales2010** Partitionieren Sie Sie erstellt haben, und klicken Sie dann auf **Kopie**.  Ändern Sie den Partitionsnamen in **FactInternetSales2011**. 

    Sie müssen nicht mit Abfrage-Editor zum Erstellen einer neuen gefilterte-Zeilen-Klausel. Da Sie eine Kopie der Abfrage für 2010 erstellt haben, müssen Sie, lediglich eine geringfügige Änderung in der Abfrage für 2011 vornehmen.
  
2.  In **Abfrageausdruck**, in der richtigen Reihenfolge für die Partition aus, um nur die Zeilen für das Jahr 2011 enthalten, ersetzen Sie die Jahren in der gefilterte-Zeilen-Klausel mit **2011** und **2012**, jeweils wie folgt vor:  
  
    ```  
    let
        Source = #"SQL/localhost;AdventureWorksDW2014",
        dbo_FactInternetSales = Source{[Schema="dbo",Item="FactInternetSales"]}[Data],
        #"Removed Columns" = Table.RemoveColumns(dbo_FactInternetSales,{"OrderDateKey", "DueDateKey", "ShipDateKey"}),
        #"Filtered Rows" = Table.SelectRows(#"Removed Columns", each [OrderDate] >= #datetime(2011, 1, 1, 0, 0, 0) and [OrderDate] < #datetime(2012, 1, 1, 0, 0, 0))
    in
        #"Filtered Rows"
   
    ```  
  
#### <a name="to-create-partitions-for-2012-2013-and-2014"></a>Zum Erstellen von Partitionen für 2012, 2013 und 2014.  
  
- Führen Sie die vorherigen Schritte, und Erstellen von Partitionen für 2012, 2013 und 2014. ändern Sie die Jahre in der gefilterte-Zeilen-Klausel, um nur Zeilen für dieses Jahr enthält. 
  

## <a name="delete-the-factinternetsales-partition"></a>Löschen Sie die Partition "factinternetsales"

Nun, da Sie Partitionen für jedes Jahr haben, können Sie die Partition "factinternetsales" löschen; verhindert eine Überlappung bei der Auswahl alle Prozess, bei der Verarbeitung von Partitionen.

#### <a name="to-delete-the-factinternetsales-partition"></a>So löschen Sie die Partition "factinternetsales"

-  Klicken Sie auf die **"factinternetsales"** partitionieren, und klicken Sie dann auf **löschen**.



## <a name="process-partitions"></a>Partitionen verarbeiten  

Beachten Sie, dass im Partitions-Manager die **zuletzt verarbeitet** Spalte für jede der neu erstellten Partitionen wird diese Partitionen noch nicht verarbeitet wurden. Wenn Sie Partitionen erstellen, sollten Sie einen Partitionsverarbeitungs- bzw. tabellenverarbeitungsvorgang aus, um die Daten in diese Partitionen zu aktualisieren ausführen.  
  
#### <a name="to-process-the-factinternetsales-partitions"></a>So verarbeiten Sie die FactInternetSales-Partitionen  
  
1.  Klicken Sie auf **OK** Partitions-Manager zu schließen.  
  
2.  Klicken Sie auf die **"factinternetsales"** Tabelle, und klicken Sie dann die **Modell** Menü > **Prozess** > **Partitionen verarbeiten**.  
  
3.  Die Partitionen verarbeiten, überprüfen Sie im Dialogfeld **Modus** nastaven NA hodnotu **Standard verarbeiten**.  
  
4.  Aktivieren Sie das Kontrollkästchen in der Spalte **Verarbeiten** für jede der fünf von Ihnen erstellten Partitionen, und klicken Sie anschließend auf **OK**.  

    ![as-lesson10-process-partitions](../tutorial-tabular-1400/media/as-lesson10-process-partitions.png)
  
    Wenn Sie für den Identitätswechsel-Anmeldeinformationen aufgefordert werden, geben Sie den Windows-Benutzernamen und das Kennwort, die Sie in Lektion 2 angegeben.  
  
    Das Dialogfeld **Datenverarbeitung** wird daraufhin angezeigt. Es zeigt die Verarbeitungsdetails für jede Partition an. Beachten Sie, dass eine unterschiedliche Anzahl an Zeilen für jede Partition übertragen wird. Jede Partition enthält nur die Zeilen für das Jahr in der WHERE-Klausel in der SQL-Anweisung angegeben. Wenn die Verarbeitung abgeschlossen ist, fahren Sie fort und schließen Sie das Dialogfeld „Datenverarbeitung“.  
  
    ![as-lesson10-process-complete](../tutorial-tabular-1400/media/as-lesson10-process-complete.png)
  
 ## <a name="whats-next"></a>Wie geht es weiter?

Wechseln Sie zur nächsten Lektion: [Lektion 11: Erstellen von Rollen](../tutorial-tabular-1400/as-lesson-11-create-roles.md). 
