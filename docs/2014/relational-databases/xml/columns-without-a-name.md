---
title: Spalten ohne Namen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns without
ms.assetid: 440de44e-3a56-4531-b4e4-1533ca933cac
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d36934be00b7d4be6b28a6ed1748f99ded2d310e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226993"
---
# <a name="columns-without-a-name"></a>Spalten ohne Namen
  Spalten ohne Namen werden als Inlinespalten betrachtet. Beispielsweise werden namenlose Spalten für berechnete Spalten oder geschachtelte skalare Abfragen, die keinen Spaltenalias angeben, generiert. Wenn die Spalte `xml` Typ, den Inhalt dieser Datentypinstanz eingefügt wird. Anderenfalls wird der Inhalt der Spalte als Textknoten eingefügt.  
  
```  
SELECT 2+2  
FOR XML PATH  
```  
  
 Erstellen Sie diesen XML-Code. Standardmäßig wird im XML-Ergebnis für jede Zeile des Rowsets ein <`row`>-Element generiert. Dies entspricht dem RAW-Modus.  
  
 `<row>4</row>`  
  
 Die folgende Abfrage gibt ein Rowset mit drei Spalten zurück. Die dritte, namenlose Spalte enthält XML-Daten. Der PATH-Modus fügt eine Instanz des XML-Typs ein.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID,  
       Name,  
       Instructions.query('declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
                /MI:root/MI:Location   
              ')   
FROM Production.ProductModel  
WHERE ProductModelID=7  
FOR XML PATH ;  
GO  
```  
  
 Dies ist das Teilergebnis:  
  
 `<row>`  
  
 `<ProductModelID>7</ProductModelID>`  
  
 `<Name>HL Touring Frame</Name>`  
  
 `<MI:Location ...LocationID="10" ...></MI:Location>`  
  
 `<MI:Location ...LocationID="20" ...></MI:Location>`  
  
 `...`  
  
 `</row>`  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden des PATH-Modus mit FOR XML](use-path-mode-with-for-xml.md)  
  
  
