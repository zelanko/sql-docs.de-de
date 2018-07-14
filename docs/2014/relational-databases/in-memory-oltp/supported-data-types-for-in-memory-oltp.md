---
title: Unterstützte Datentypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine-imoltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f967b7cf4c20492f7e7d46ad9b8f9a2556042e7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37195310"
---
# <a name="supported-data-types"></a>Unterstützte Datentypen
  Die folgenden Datentypen sind **unterstützt** in speicheroptimierten Tabellen und systemintern kompilierten gespeicherten Prozeduren:  
  
 **Numerische Datentypen**  
  
|Datentyp|Weitere Informationen finden Sie unter|  
|---------------|--------------------------|  
|ssNoversion|[int, bigint, smallint und tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|BIGINT|[int, bigint, smallint und tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|SMALLINT|[int, bigint, smallint und tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|TINYINT|[int, bigint, smallint und tinyint &#40;Transact-SQL&#41;](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|Decimal|[decimal und numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|NUMERIC|[decimal und numeric &#40;Transact-SQL&#41;](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|FLOAT|[float und real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|REAL|[float und real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|money|[money und smallmoney &#40;Transact-SQL&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|SMALLMONEY|[money und smallmoney &#40;Transact-SQL&#41;](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 **Zeichenfolgen-Datentypen**  
  
|Datentyp|Weitere Informationen finden Sie unter|  
|---------------|--------------------------|  
|char(n)|[char und varchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|varchar (n) <sup>1</sup>|[char und varchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|nchar(n)|[nchar und nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|nvarchar (n) <sup>1</sup>|[nchar und nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|sysname|[nchar und nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <sup>1</sup> Einschränkung beträgt 8060 Bytes pro Zeilensumme, Zählung (n) in Typen variabler Länge.  
  
 Weitere Informationen zu unterstützten Sortierungen finden Sie unter [Sortierungen und Codepages](../../database-engine/collations-and-code-pages.md).  
  
 **Datums- und Uhrzeitdatentypen:**  
  
|Datentyp|Weitere Informationen finden Sie unter|  
|---------------|--------------------------|  
|date|[Datum &#40;Transact-SQL&#41;](/sql/t-sql/data-types/date-transact-sql)|  
|Uhrzeit|[time &#40;Transact-SQL&#41;](/sql/t-sql/data-types/time-transact-sql)|  
|DATETIME|[datetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)|  
|datetime2|[datetime2 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/datetime2-transact-sql)|  
|smalldatetime|[smalldatetime &#40;Transact-SQL&#41;](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 **Binäre Datentypen**  
  
|Datentyp|Weitere Informationen finden Sie unter|  
|---------------|--------------------------|  
|bit|[bit &#40;Transact-SQL&#41;](/sql/t-sql/data-types/bit-transact-sql)|  
|binary(n)|[binary und varbinary &#40;Transact-SQL&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|varbinary <sup>1</sup>|[binary und varbinary &#40;Transact-SQL&#41;](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <sup>1</sup> Einschränkung beträgt 8060 Bytes pro Zeilensumme, Zählung (n) in Typen variabler Länge.  
  
 **Andere Datentypen**  
  
|Datentyp|Weitere Informationen finden Sie unter|  
|---------------|--------------------------|  
|UNIQUEIDENTIFIER|[uniqueidentifier &#40;Transact-SQL&#41;](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 **Nicht unterstützte Datentypen**  
  
 Die folgenden Datentypen werden nicht unterstützt:  
  
||||  
|-|-|-|  
|DATETIMEOFFSET|GEOGRAPHY|GEOMETRY|  
|HIERARCHYID|Large Objects (LOBs, große Objekte). Beispielsweise varchar(max), nvarchar(max), varbinary(max), image, xml, text oder ntext.|ROWVERSION|  
|sql_variant|CLR-Funktionen|Benutzerdefinierte Typen (User-defined types, UDTs)|  
  
## <a name="see-also"></a>Siehe auch  
 [Transact-SQL-Unterstützung für In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md)   
 [Implementieren von LOB-Spalten in einer speicheroptimierten Tabelle](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md)   
 [Implementieren von SQL_VARIANT in einer speicheroptimierten Tabelle](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  
