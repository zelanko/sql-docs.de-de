---
title: $PARTITION (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- $partition_TSQL
- $partition
dev_langs:
- TSQL
helpviewer_keywords:
- $PARTITION function
- partitions [SQL Server], numbers
ms.assetid: abc865d0-57a8-49da-8821-29457c808d2a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b296737ecc7d9988365a9ad7abed8b2ee7abf61c
ms.sourcegitcommit: 83f061304fedbc2801d8d6a44094ccda97fdb576
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2019
ms.locfileid: "65943554"
---
# <a name="partition-transact-sql"></a>$PARTITION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Nummer der Partition zurück, der eine Gruppe von Partitionierungsspaltenwerten für eine beliebige angegebene Partitionsfunktion in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] zugeordnet würde.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlinksymbol") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
[ database_name. ] $PARTITION.partition_function_name(expression)  
```  
  
## <a name="arguments"></a>Argumente  
 *database_name*  
 Der Name der Datenbank, die die gespeicherte Partitionsfunktion enthält.  
  
 *partition_function_name*  
 Der Name einer beliebigen, vorhandenen Partitionsfunktion, für die eine Gruppe von Partitionierungsspaltenwerten angegeben wird.  
  
 *expression*  
 Ein [Ausdruck](../../t-sql/language-elements/expressions-transact-sql.md), dessen Datentyp mit der zugehörigen Partitionierungsspalte entweder übereinstimmen oder implizit in diesen konvertierbar sein muss. *expression* kann auch der Name einer Partitionierungsspalte sein, die gerade an *partition_function_name* teilnimmt.  
  
## <a name="return-types"></a>Rückgabetypen  
 **ssNoversion**  
  
## <a name="remarks"></a>Remarks  
 $PARTITION gibt einen **int**-Wert zwischen 1 und der Anzahl von der Partitionierungsfunktion betroffenen Partitionen zurück.  
  
 $PARTITION gibt die Partitionsnummer für jeden gültigen Wert zurück. Dabei spielt es keine Rolle, ob der Wert sich zurzeit in einer partitionierten Tabelle oder einem partitionierten Index befindet, die/der die Partitionsfunktion verwendet.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-getting-the-partition-number-for-a-set-of-partitioning-column-values"></a>A. Abrufen der Partitionsnummer für eine Gruppe von Partitionierungsspaltenwerten  
 Im folgenden Beispiel wird die Partitionsfunktion `RangePF1` erstellt, die eine Tabelle oder einen Index in vier Partitionen partitioniert. Mit $PARTITION wird bestimmt, dass der Wert `10`, der für die Partitionierungsspalte von `RangePF1` steht, in Partition 1 der Tabelle eingefügt wird.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE PARTITION FUNCTION RangePF1 ( int )  
AS RANGE FOR VALUES (10, 100, 1000) ;  
GO  
SELECT $PARTITION.RangePF1 (10) ;  
GO  
```  
  
### <a name="b-getting-the-number-of-rows-in-each-nonempty-partition-of-a-partitioned-table-or-index"></a>B. Abrufen der Anzahl von Zeilen in jeder nicht leeren Partition einer partitionierten Tabelle oder eines partitionierten Indexes  
 Im folgenden Beispiel wird die Anzahl von Zeilen mit Daten in jeder Partition der `TransactionHistory`-Tabelle zurückgegeben. Die `TransactionHistory`-Tabelle verwendet die Partitionsfunktion `TransactionRangePF1` und wird an der Spalte `TransactionDate` partitioniert.  
  
 Sie müssen zunächst das Skript PartitionAW.sql für die Beispieldatenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ausführen, um dieses Beispiel auszuführen. Weitere Informationen finden Sie unter [PartitioningScript](https://go.microsoft.com/fwlink/?LinkId=201015).  
  
```  
USE AdventureWorks2012;  
GO  
SELECT $PARTITION.TransactionRangePF1(TransactionDate) AS Partition,   
COUNT(*) AS [COUNT] FROM Production.TransactionHistory   
GROUP BY $PARTITION.TransactionRangePF1(TransactionDate)  
ORDER BY Partition ;  
GO  
```  
  
### <a name="c-returning-all-rows-from-one-partition-of-a-partitioned-table-or-index"></a>C. Zurückgeben aller Zeilen aus einer Partition einer partitionierten Tabelle oder eines partitionierten Indexes  
 Im folgenden Beispiel werden alle Zeilen zurückgegeben, die in der Partition `5` der Tabelle `TransactionHistory` enthalten sind.  
  
> [!NOTE]  
>  Sie müssen zunächst das Skript PartitionAW.sql für die Beispieldatenbank [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] ausführen, um dieses Beispiel auszuführen. Weitere Informationen finden Sie unter [PartitioningScript](https://go.microsoft.com/fwlink/?LinkId=201015).  
  
```  
SELECT * FROM Production.TransactionHistory  
WHERE $PARTITION.TransactionRangePF1(TransactionDate) = 5 ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE PARTITION FUNCTION &#40;Transact-SQL&#41;](../../t-sql/statements/create-partition-function-transact-sql.md)  
  
  
