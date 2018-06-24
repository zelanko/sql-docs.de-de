---
title: 'Lektion 3: Definieren eines Datasets für den Tabellenbericht (Reporting Services) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee93dfcb-8f52-4d63-b4f6-0d38e00fd350
caps.latest.revision: 50
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 34595ca07e370bb0a66512c839a6843f8c38f5d1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059301"
---
# <a name="lesson-3-defining-a-dataset-for-the-table-report-reporting-services"></a>Lektion 3: Definieren eines Datasets für den Tabellenbericht (Reporting Services)
  Nachdem Sie die Datenquelle festgelegt haben, müssen Sie ein Dataset definieren. In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]sind die Daten, die Sie in Berichten verwenden, in einem *Dataset*enthalten. Ein Dataset umfasst einen Zeiger auf eine Datenquelle sowie eine Abfrage, die vom Bericht verwendet werden, sowie berechnete Felder und Variablen.  
  
 Sie können den Abfrage-Designer im Berichts-Designer verwenden, um die Abfrage zu entwerfen. In diesem Lernprogramm erstellen Sie eine Abfrage, die Bestellinformationen aus Ruft die [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] **2008** Datenbank.  
  
### <a name="to-define-a-transact-sql-query-for-report-data"></a>So definieren Sie eine Transact-SQL-Abfrage für Berichtsdaten  
  
1.  Klicken Sie im **Berichtsdatenbereich** auf **Neu**und anschließend auf **Dataset...**. Das Dialogfeld **Dataseteigenschaften** wird angezeigt.  
  
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
  
     Daraufhin werden die Daten von sechs Feldern aus vier verschiedenen Tabellen in der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] Datenbank. Diese Abfrage nutzt Transact-SQL-Funktionen wie Aliase. Beispielsweise wird die Tabelle SalesOrderHeader als "soh" bezeichnet.  
  
     Klicken Sie auf **OK** , um den Abfrage-Designer zu schließen.  
  
7.  Klicken Sie auf **OK** , um das Dialogfeld **Dataseteigenschaften** zu beenden.  
  
     Die Felder des **AdventureWorksDataset** -Datasets werden im Berichtsdatenbereich angezeigt.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Damit haben Sie erfolgreich eine Abfrage angegeben, die Daten für Ihren Bericht abruft. Als Nächstes erstellen Sie das Berichtslayout. Weitere Informationen finden Sie unter [Lektion 4: Hinzufügen einer Tabelle zum Bericht (Reporting Services)](lesson-4-adding-a-table-to-the-report-reporting-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Abfragen von Entwurfstools in Berichts-Designers von SQL Server Datatools &#40;SSRS&#41;](report-data/query-design-tools-ssrs.md)   
 [SQL Server-Verbindungstyp &#40;SSRS&#41;](report-data/sql-server-connection-type-ssrs.md)   
 [Lernprogramm: Schreiben von Transact-SQL-Anweisungen](../t-sql/tutorial-writing-transact-sql-statements.md)  
  
  