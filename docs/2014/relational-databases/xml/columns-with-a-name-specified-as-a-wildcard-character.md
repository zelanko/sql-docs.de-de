---
title: Spalten mit als Platzhalterzeichen angegebenen Namen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: d9551df1-5bb4-4c0b-880a-5bb049834884
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4ff6bcd9379e6e20351dacee75cb92e56b79d374
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48056150"
---
# <a name="columns-with-a-name-specified-as-a-wildcard-character"></a>Spalten mit als Platzhalterzeichen angegebenen Namen
  Wenn der angegebene Spaltenname aus einem Platzhalterzeichen (\*) besteht, wird der Inhalt der betroffenen Spalte so eingefügt, als wäre kein Spaltenname angegeben. Wenn diese Spalte nicht`xml` Spalte vom Typ, der Inhalt der Spalte wird als Textknoten eingefügt, wie im folgenden Beispiel gezeigt:  
  
```  
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
  
 `<row EmpID="1">KenJSánchez</row>`  
  
 Wenn die Spalte vom Typ `xml` ist, wird die entsprechende XML-Struktur eingefügt. Die folgende Abfrage gibt beispielsweise "*" als Name der Spalte an, die den XML-Code enthält, der von der XQuery für die Instructions-Spalte zurückgegeben wurde.  
  
```  
SELECT   
       ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
                /MI:root/MI:Location   
              ') as "*"  
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH;   
GO  
```  
  
 Dies ist das Ergebnis. Der von der XQuery zurückgegebene XML-Code wird ohne Wrapperelement eingefügt.  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location LocationID="10">...</MI:Location>`  
  
 `<MI:Location LocationID="20">...</MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des PATH-Modus mit FOR XML](use-path-mode-with-for-xml.md)  
  
  
