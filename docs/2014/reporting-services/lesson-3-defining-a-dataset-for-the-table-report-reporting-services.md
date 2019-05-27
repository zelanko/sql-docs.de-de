---
title: 'Lektion 3: Definieren eines Datasets für den Tabellenbericht (Reporting Services) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f4c78328e02215520b8d33213e01871f010f62d6
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66108458"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a>Lektion 3: Definieren eines Datasets für den Tabellenbericht (Reporting Services)
  Nachdem Sie die Datenquelle festgelegt haben, müssen Sie ein Dataset definieren. In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]sind die Daten, die Sie in Berichten verwenden, in einem *Dataset*enthalten. Ein Dataset umfasst einen Zeiger auf eine Datenquelle sowie eine Abfrage, die vom Bericht verwendet werden, sowie berechnete Felder und Variablen.  
  
 Sie können den Abfrage-Designer im Berichts-Designer verwenden, um die Abfrage zu entwerfen. In diesem Lernprogramm erstellen Sie eine Abfrage, die Bestellinformationen aus der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]**2008** -Datenbank abruft.  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a>So definieren Sie eine Transact-SQL-Abfrage für Berichtsdaten  
  
1.  Klicken Sie im **Berichtsdatenbereich** auf **Neu** und anschließend auf **Dataset...**. Das Dialogfeld **Dataseteigenschaften** wird angezeigt.  
  
2.  Geben Sie in das Feld **Name** den Namen **AdventureWorksDataset**ein.  
  
3.  Klicken Sie auf **Verwenden Sie ein in den eigenen Bericht eingebettetes Dataset**.  
  
4.  Der Name der Datenquelle, "AdventureWorks2012", muss im Feld **Datenquelle** eingetragen sein, und als **Abfragetyp** muss **Text**verwendet werden.  
  
5.  Geben Sie die folgende Transact-SQL-Abfrage entweder manuell oder durch Kopieren und Einfügen in das Feld **Abfrage** ein.  
  
    ```  
    SELECT   
       soh.OrderDate AS [Date],   
       soh.SalesOrderNumber AS [Order],   
       pps.Name AS Subcat, pp.Name as Product,    
       SUM(sd.OrderQty) AS Qty,  
       SUM(sd.LineTotal) AS LineTotal  
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
    GROUP BY ppc.Name, soh.OrderDate, soh.SalesOrderNumber, pps.Name, pp.Name,   
       soh.SalesPersonID  
    HAVING ppc.Name = 'Clothing'  
    ```  
  
6.  (Optional) klicken Sie auf die Schaltfläche **Abfrage-Designer** . Die Abfrage wird im textbasierten Abfrage-Designer angezeigt. Sie können zum grafischen Abfrage-Designer wechseln, indem Sie auf **Als Text bearbeiten**klicken. Die Ergebnisse der Abfrage anzeigen, indem Sie auf die Ausführung **(!)**  Schaltfläche auf der Symbolleiste des Abfrage-Designers.  
  
     Daraufhin werden die Daten von sechs Feldern aus vier verschiedenen Tabellen in der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Datenbank angezeigt. Diese Abfrage nutzt Transact-SQL-Funktionen wie Aliase. Beispielsweise wird die Tabelle SalesOrderHeader als "soh" bezeichnet.  
  
     Klicken Sie auf **OK** , um den Abfrage-Designer zu schließen.  
  
7.  Klicken Sie auf **OK** , um das Dialogfeld **Dataseteigenschaften** zu beenden.  
  
     Die Felder des **AdventureWorksDataset** -Datasets werden im Berichtsdatenbereich angezeigt.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Damit haben Sie erfolgreich eine Abfrage angegeben, die Daten für Ihren Bericht abruft. Als Nächstes erstellen Sie das Berichtslayout. Siehe [Lektion 4: Hinzufügen einer Tabelle zum Bericht &#40;Reporting Services&#41;](lesson-4-adding-a-table-to-the-report-reporting-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Abfrageentwurfstools im Berichts-Designer SQL-Server-Datatools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md)   
 [SQL Server-Verbindungstyp &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md)   
 [Tutorial: Schreiben von Transact-SQL-Anweisungen](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  
