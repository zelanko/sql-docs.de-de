---
title: Erstellen von und Zugreifen auf Tabellen in tempdb aus nativ kompilierten gespeicherten Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 12be8011-b76c-45c1-8f55-7f46e0e374e9
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c66b43d4bad56724817a4d38a810fd150b2b3fd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050245"
---
# <a name="creating-and-accessing-tables-in-tempdb-from-natively-compiled-stored-procedures"></a>Erstellen von und Zugreifen auf Tabellen in TempDB aus systemintern kompilierten gespeicherten Prozeduren
  Das Erstellen von und Zugreifen auf Tabellen in TempDB aus systemintern kompilierten gespeicherten Prozeduren wird nicht unterstützt. Verwenden Sie stattdessen Tabellentypen und Tabellenvariablen. Beispiel:  
  
```sql  
CREATE TYPE dbo.OrderQuantityByProduct   
  AS TABLE   
   (id INT NOT NULL PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT=100000),   
    ProductID INT NOT NULL,   
    Quantity INT NOT NULL) WITH (MEMORY_OPTIMIZED=ON)  
GO  
CREATE PROCEDURE dbo.usp_OrderQuantityByProduct   
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH   
(  
    TRANSACTION ISOLATION LEVEL = SNAPSHOT,  
    LANGUAGE = 'english'  
)  
  -- declare table variables for the list of orders   
  DECLARE @Input dbo.OrderQuantityByProduct  
  
  -- populate input  
  INSERT @Input SELECT ProductID, Quantity FROM dbo.[Order Details]  
  end  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Von in-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
