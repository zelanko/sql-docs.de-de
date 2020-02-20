---
title: 'Lektion 3: Definieren eines Datasets für den Tabellenbericht | Microsoft-Dokumentation'
description: Sobald Sie die Datenquelle für den paginierten Bericht definiert haben, müssen Sie ein Dataset definieren. In SQL Server Reporting Services sind Daten, die Sie in Berichten verwenden, in einem Dataset enthalten.
ms.date: 05/01/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 25c62e0cd615748a764937d6dc2b8e4c952e59a1
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244306"
---
# <a name="lesson-3-define-a-dataset-for-the-table-report---sql-server-reporting-services"></a>Lektion 3: Definieren eines Datasets für den Tabellenbericht: SQL Server Reporting Services

Sobald Sie die Datenquelle für den paginierten Bericht definiert haben, müssen Sie ein Dataset definieren. In [!INCLUDE[ssrsnoversion](../includes/ssrsnoversion-md.md)]sind die Daten, die Sie in Berichten verwenden, in einem *Dataset*enthalten. Ein Dataset umfasst einen Zeiger auf eine Datenquelle und eine Abfrage, die vom Bericht verwendet werden sollen, sowie berechnete Felder und Variablen.

Verwenden Sie den Abfrage-Designer im Berichts-Designer, um das Dataset zu definieren. In diesem Tutorial erstellen Sie eine Abfrage, die Auftragsinformationen aus der Datenbank „AdventureWorks2016“ abruft.

## <a name="define-a-transact-sql-query-for-report-data"></a>Definieren einer Transact-SQL-Abfrage für Berichtsdaten  

1. Klicken Sie im Bereich **Berichtsdaten** auf **Neu** > **Dataset...** . Das Dialogfeld **Dataseteigenschaften** wird geöffnet und zeigt den Abschnitt **Abfrage** an.

    ![vs-data_set_properties_dialog](media/lesson-3-defining-a-dataset-for-the-table-report-reporting-services/vs-dataset-properties-dialog.png)

2. Geben Sie in das Textfeld **Name** den Begriff „AdventureWorksDataset“ ein.

3. Aktivieren Sie darunter das Optionsfeld **Ein in den eigenen Bericht eingebettetes Dataset verwenden**.

4. Wählen Sie im Dropdownfeld **Datenquelle** die Option „AdventureWorks2016“ aus.

5. Aktivieren Sie bei **Abfragetyp** das Optionsfeld **Text**.

6. Geben Sie die folgende Transact-SQL-Abfrage entweder manuell oder durch Kopieren und Einfügen in das Textfeld **Abfrage** ein.

    ```T-SQL
    SELECT
       soh.OrderDate AS [Date],
       soh.SalesOrderNumber AS [Order],
       pps.Name AS [Subcat],
       pp.Name as [Product],
       SUM(sd.OrderQty) AS [Qty],
       SUM(sd.LineTotal) AS [LineTotal]
    FROM Sales.SalesPerson sp
    INNER JOIN Sales.SalesOrderHeader AS soh
          ON sp.BusinessEntityID = soh.SalesPersonID
       INNER JOIN Sales.SalesOrderDetail AS sd
          ON sd.SalesOrderID = soh.SalesOrderID
       INNER JOIN Production.Product AS pp
          ON sd.ProductID = pp.ProductID
       INNER JOIN Production.ProductSubcategory AS pps
          ON pp.ProductSubcategoryID = pps.ProductSubcategoryID
       INNER JOIN Production.ProductCategory AS ppc
          ON ppc.ProductCategoryID = pps.ProductCategoryID
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'
    ```

7. (Optional) Klicken Sie auf die Schaltfläche **Abfrage-Designer**. Die Abfrage wird im textbasierten *Abfrage-Designer* angezeigt. Wenn Sie die Abfrageergebnisse abrufen möchten, klicken Sie in der Symbolleiste des **Abfrage-Designers** auf die Schaltfläche ![ssrs_querydesigner_run](media/ssrs-querydesigner-run.png) **Ausführen**. Das angezeigte Dataset enthält sechs Felder aus vier Tabellen der Datenbank „AdventureWorks2016“. Diese Abfrage nutzt Transact-SQL-Funktionen wie Aliase. Beispielsweise wird die Tabelle SalesOrderHeader als *soh*bezeichnet.

8. Klicken Sie auf **OK**, um den **Abfrage-Designer** zu beenden.

9. Klicken Sie auf **OK**, um das Dialogfeld **Dataseteigenschaften** zu beenden.

Die Felder und das Dataset „AdventureWorksDataset“ werden im Bereich **Berichtsdaten** angezeigt.

   ![ssrs_adventureworksdataset](media/ssrs-adventureworksdataset.png)

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie erfolgreich eine Abfrage angegeben, mit der Sie Daten für Ihren Bericht abrufen. Als Nächstes erstellen Sie das Berichtslayout. Fahren Sie fort mit [Lektion 4: Hinzufügen einer Tabelle zum Bericht &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md).

## <a name="see-also"></a>Weitere Informationen

[Abfrageentwurfstools &#40;SSRS&#41;](../reporting-services/report-data/query-design-tools-ssrs.md)
[SQL Server-Verbindungstyp &#40;SSRS&#41;](../reporting-services/report-data/sql-server-connection-type-ssrs.md)
[Tutorial: Schreiben von Transact-SQL-Anweisungen](../t-sql/tutorial-writing-transact-sql-statements.md)
