---
title: Erstellen von Sichten über XML-Spalten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- views [XML in SQL Server]
ms.assetid: eb5f0439-1f69-49c2-8759-e59bda1633b7
author: rothja
ms.author: jroth
ms.openlocfilehash: d2c4a0cd87d42db9e17097932b6530936a2b83eb
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059481"
---
# <a name="create-views-over-xml-columns"></a>Erstellen von Sichten über XML-Spalten
  Sie können eine Spalte vom Typ `xml` zum Erstellen von Sichten verwenden. Im folgenden Beispiel wird eine Sicht erstellt, in der mithilfe der `value()`-Methode des `xml`-Datentyps der Wert aus einer Spalte vom Typ `xml` abgerufen wird.  
  
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
  
 Beachten Sie die folgenden Punkte in Bezug auf das Erstellen von Sichten mit dem `xml`-Datentyp:  
  
-   Der XML-Datentyp kann in einer materialisierten Sicht erstellt werden. Die materialisierte Sicht kann nicht auf einer xml-Datentypmethode basieren. Er kann jedoch in eine XML-Schemaauflistung umgewandelt werden, die sich von der XML-Typspalte der Basistabelle unterscheidet.  
  
-   Der `xml`-Datentyp kann nicht in verteilten partitionierten Sichten verwendet werden.  
  
-   SQL-Prädikate, die für die Sicht ausgeführt werden, werden nicht in die XQuery der Sichtdefinition verschoben.  
  
-   XML-Datentypmethoden in einer Sicht sind nicht aktualisierbar.  
  
  
