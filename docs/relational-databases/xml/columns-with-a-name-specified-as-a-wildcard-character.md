---
title: Angeben einer Spalte mit einem Platzhalterzeichen (SQLXML) | Microsoft-Dokumentation
description: Finden Sie heraus, wie als Platzhalterzeichen angegebene Spaltennamen sich auf die Ergebnisse einer XQuery auswirken können.
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
ms.openlocfilehash: 915bd2824f6e3a706587769413c0f116df859f06
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85775582"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a>Spalten mit als Platzhalterzeichen angegebenen Namen

[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Wenn der angegebene Spaltenname aus einem Platzhalterzeichen (\*) besteht, wird der Inhalt der betroffenen Spalte so eingefügt, als wäre kein Spaltenname angegeben. Wenn die Spalte nicht vom Typ**xml** ist, wird der Inhalt der Spalte als Textknoten eingefügt, wie im folgenden Beispiel gezeigt:  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
       FirstName "*",   
       MiddleName "*",   
       LastName "*"  
FROM   HumanResources.Employee AS E  
  INNER JOIN Person.Person AS P  
    ON E.BusinessEntityID = P.BusinessEntityID  
WHERE E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 Dies ist das Ergebnis:  

```xml
<row EmpID="1">KenJSánchez</row>
```

 Wenn die Spalte vom Typ **xml** ist, wird die entsprechende XML-Struktur eingefügt. Die folgende Abfrage gibt beispielsweise "*" als Name der Spalte an, die den XML-Code enthält, der von der XQuery für die Instructions-Spalte zurückgegeben wurde.  
  
```sql
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
```  
  
 Dies ist das Ergebnis. Der von der XQuery zurückgegebene XML-Code wird ohne Wrapperelement eingefügt.  

```xml
<row>
  <ProductModelID>7</ProductModelID>
  <Name>HL Touring Frame</Name>
  <MI:Location LocationID="10">...</MI:Location>
  <MI:Location LocationID="20">...</MI:Location>
  ...
</row>
```

## <a name="see-also"></a>Weitere Informationen  
 [Verwenden des PATH-Modus mit FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
