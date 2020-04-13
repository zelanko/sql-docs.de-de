---
title: Erstellen von Sichten über XML-Spalten | Microsoft-Dokumentation
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 40c91548b4bf106f938f4bce8298a162937e7ffc
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664598"
---
# <a name="create-views-over-xml-columns"></a>Erstellen von Sichten über XML-Spalten
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Sie können eine Spalte vom Typ **xml** zum Erstellen von Sichten verwenden. Im folgenden Beispiel wird eine Sicht erstellt, in der mithilfe der `xml` value() **-Methode des** xml **-Datentyps der Wert aus einer Spalte vom Typ** abgerufen wird.  
  
```  
-- Create the table.  
CREATE TABLE T (  
    ProductID          int primary key,   
    CatalogDescription xml)  
GO  
-- Insert sample data.  
INSERT INTO T values(1,'<ProductDescription ProductID="1" ProductName="SomeName" />')  
GO  
-- Create view (note the value() method used to retrieve ProductName   
-- attribute value from the XML).  
CREATE VIEW MyView AS   
  SELECT ProductID,  
         CatalogDescription.value('(/ProductDescription/@ProductName)[1]', 'varchar(40)') AS PName  
  FROM T  
GO   
```  
  
 Führen Sie die folgende Abfrage für die Sicht aus:  
  
```  
SELECT *   
FROM   MyView  
```  
  
 Dies ist das Ergebnis:  
  
```  
ProductID   PName        
----------- ------------  
1           SomeName   
```  
  
 Beachten Sie die folgenden Punkte in Bezug auf das Erstellen von Sichten mit dem **xml** -Datentyp:  
  
-   Der XML-Datentyp kann in einer materialisierten Sicht erstellt werden. Die materialisierte Sicht kann nicht auf einer xml-Datentypmethode basieren. Er kann jedoch in eine XML-Schemaauflistung umgewandelt werden, die sich von der XML-Typspalte der Basistabelle unterscheidet.  
  
-   Der **xml** -Datentyp kann nicht in verteilten partitionierten Sichten verwendet werden.  
  
-   SQL-Prädikate, die für die Sicht ausgeführt werden, werden nicht in die XQuery der Sichtdefinition verschoben.  
  
-   XML-Datentypmethoden in einer Sicht sind nicht aktualisierbar.  
  
  
