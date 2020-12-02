---
description: Formatieren einer geschachtelten JSON-Ausgabe im PATH-Modus (SQL Server)
title: Formatieren einer geschachtelten JSON-Ausgabe im PATH-Modus
ms.date: 06/03/2020
ms.prod: sql
ms.technology: ''
ms.topic: conceptual
ms.assetid: 032761b0-6358-42e4-b05c-dbfd663ac881
author: jovanpop-msft
ms.author: jovanpop
ms.reviewer: jroth
ms.custom: seo-dt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8c091618be5e414faa15e200fc8b30230f793eaf
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "96130241"
---
# <a name="format-nested-json-output-with-path-mode-sql-server"></a>Formatieren einer geschachtelten JSON-Ausgabe im PATH-Modus (SQL Server)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Wenn Sie die vollständige Kontrolle über die Ausgabe der **FOR JSON**-Klausel behalten möchten, geben Sie die Option **PATH** an.  
  
Im **PATH**-Modus können Sie Wrapper-Objekte erstellen und komplexe Eigenschaften schachteln. Die Ergebnisse werden wie ein JSON-Objekt-Array formatiert.  
  
Alternativ können Sie die Option **AUTO** verwenden, um die Ausgabe automatisch entsprechend der Struktur der **SELECT**-Anweisung zu formatieren.
 -   Weitere Informationen zur Option **AUTO** finden Sie unter [Format JSON Output Automatically with AUTO Mode (Automatisches Formatieren der JSON-Ausgabe im AUTO-Modus)](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).
 -   Einen Überblick über die beiden Optionen finden Sie unter [Format Query Results as JSON with FOR JSON (Formatieren von Abfrageergebnissen als JSON mit FOR JSON)](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).
 
Hier sind einige Beispiele für die **FOR JSON** -Klausel mit der Option **PATH** . Geschachtelte Ergebnisse formatieren Sie, wie nachfolgend gezeigt, mit durch Punkte getrennten Spaltennamen oder mit verschachtelten Abfragen. Nullwerte sind standardmäßig nicht in der **FOR JSON**-Ausgabe enthalten.  [Azure Data Studio](../../azure-data-studio/download-azure-data-studio.md) ist der empfohlene Abfrage-Editor für JSON-Abfragen, da hierbei die JSON-Ergebnisse (wie in diesem Artikel gezeigt) automatisch formatiert werden, anstatt dass eine flache Zeichenfolge angezeigt wird.

## <a name="example---dot-separated-column-names"></a>Beispiel – Durch Punkte getrennte Spaltennamen  
Die ersten fünf Zeilen der AdventureWorks-Tabelle `Person` werden durch die Abfrage als JSON formatiert.  

Die Klausel **FOR JSON PATH** verwendet den Spaltenalias oder einen Spaltennamen, um den Schlüsselnamen in der JSON-Ausgabe zu bestimmen. Wenn ein Alias Punkte enthält, erstellt die Option PATH geschachtelte Objekte.  

 **Abfrage**  
  
```sql  
SELECT TOP 5   
       BusinessEntityID As Id,  
       FirstName, LastName,  
       Title As 'Info.Title',  
       MiddleName As 'Info.MiddleName'  
   FROM Person.Person  
   FOR JSON PATH   
```  
  
 **Ergebnis**  
  
```json  
[{
    "Id": 1,
    "FirstName": "Ken",
    "LastName": "Sanchez",
    "Info": {
        "MiddleName": "J"
    }
}, {
    "Id": 2,
    "FirstName": "Terri",
    "LastName": "Duffy",
    "Info": {
        "MiddleName": "Lee"
    }
}, {
    "Id": 3,
    "FirstName": "Roberto",
    "LastName": "Tamburello"
}, {
    "Id": 4,
    "FirstName": "Rob",
    "LastName": "Walters"
}, {
    "Id": 5,
    "FirstName": "Gail",
    "LastName": "Erickson",
    "Info": {
        "Title": "Ms.",
        "MiddleName": "A"
    }
}]
```  
   
## <a name="example---multiple-tables"></a>Beispiel – Mehrere Tabellen  
Wenn Sie in einer Abfrage auf mehr als eine Tabelle verweisen, schachtelt **FOR JSON PATH** jede Spalte mithilfe des Alias. Die folgende Abfrage erstellt ein JSON-Objekt pro (OrderHeader, OrderDetails) Paar, das in der Abfrage verknüpft ist. 
  
 **Abfrage**  
  
```sql  
SELECT TOP 2 H.SalesOrderNumber AS 'Order.Number',  
        H.OrderDate AS 'Order.Date',  
        D.UnitPrice AS 'Product.Price',  
        D.OrderQty AS 'Product.Quantity'  
FROM Sales.SalesOrderHeader H  
   INNER JOIN Sales.SalesOrderDetail D  
     ON H.SalesOrderID = D.SalesOrderID  
FOR JSON PATH   
```  
  
 **Ergebnis**  
  
```json  
[{
    "Order": {
        "Number": "SO43659",
        "Date": "2011-05-31T00:00:00"
    },
    "Product": {
        "Price": 2024.9940,
        "Quantity": 1
    }
}, {
    "Order": {
        "Number": "SO43659"
    },
    "Product": {
        "Price": 2024.9940
    }
}]
```  

## <a name="learn-more-about-json-in-sql-server-and-azure-sql-database"></a>Weitere Informationen zu JSON in SQL Server und Azure SQL-Datenbank  
  
### <a name="microsoft-videos"></a>Microsoft-Videos

Eine visuelle Einführung in die JSON-Unterstützung, die in SQL Server und Azure SQL-Datenbank integriert ist, finden Sie in den folgenden Videos:

-   [SQL Server 2016 and JSON Support](https://channel9.msdn.com/Shows/Data-Exposed/SQL-Server-2016-and-JSON-Support)

-   [Using JSON in SQL Server 2016 and Azure SQL Database](https://channel9.msdn.com/Shows/Data-Exposed/Using-JSON-in-SQL-Server-2016-and-Azure-SQL-Database)

-   [JSON as a bridge between NoSQL and relational worlds](https://channel9.msdn.com/events/DataDriven/SQLServer2016/JSON-as-a-bridge-betwen-NoSQL-and-relational-worlds)

## <a name="see-also"></a>Weitere Informationen  
 [FOR-Klausel &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)  
