---
title: Implementieren von MERGE-Funktionalität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: d4bcdc36-3302-4abc-9b35-64ec2b920986
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: faf6112fa3f8ec588d00480d09ff072a71051a02
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52508158"
---
# <a name="implementing-merge-functionality"></a>Implementieren von MERGE-Funktionalität
  Eine Datenbank muss u. U. einen Einfüge- oder einen Updatevorgang ausführen, je nachdem, ob eine bestimmte Zeile in der Datenbank bereits vorhanden ist.  
  
 Ohne Verwendung der `MERGE`-Anweisung kann der folgende Ansatz in [!INCLUDE[tsql](../../includes/tsql-md.md)] verwendet werden:  
  
```tsql  
UPDATE mytable SET col=@somevalue WHERE myPK = @parm  
IF @@ROWCOUNT = 0  
    INSERT mytable (columns) VALUES (@parm, @other values)  
```  
  
 Eine weitere [!INCLUDE[tsql](../../includes/tsql-md.md)] -Methode zum Implementieren eines Merge:  
  
```tsql  
IF EXISTS (SELECT 1 FROM mytable WHERE myPK = @parm)  
    UPDATE....  
ELSE  
    INSERT  
```  
  
 Für eine systemintern kompilierte gespeicherte Prozedur  
  
```tsql  
DECLARE @i  int  = 0  -- or whatever your PK data type is  
UPDATE mytable SET @i=myPK, othercolums = other values WHERE myPK = @parm  
IF @i = 0  
   INSERT....  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Migrationsprobleme bei nativ kompilierten gespeicherten Prozeduren](migration-issues-for-natively-compiled-stored-procedures.md)   
 [Von In-Memory OLTP nicht unterstützte Transact-SQL-Konstrukte](transact-sql-constructs-not-supported-by-in-memory-oltp.md)  
  
  
