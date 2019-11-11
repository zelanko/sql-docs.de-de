---
title: DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 73f598cf-b02a-4dba-8d89-9fc0b55a12b8
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 4a701a56ba5a71037317f6c404fa394a466febba
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729883"
---
# <a name="dbcc-showresultcachespaceused-transact-sql"></a>DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Zeigt den verwendeten Speicherplatz im Resultsetcache für eine Azure [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]-Datenbank.
  
![Symbol zum Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```sql
DBCC SHOWRESULTCACHESPACEUSED  
[;]  
```  
## <a name="remarks"></a>Remarks

Der `DBCC SHOWRESULTCACHESPACEUSED`-Befehl akzeptiert keine Parameter und gibt den verwendeten Speicherplatz der Datenbank zurück, für die der Befehl ausgeführt wird.

## <a name="permissions"></a>Berechtigungen

Erfordert die VIEW SERVER STATE-Berechtigung.
  
## <a name="result-sets"></a>Resultsets  
  
|Spalte|Datentyp|und Beschreibung|  
|------------|---------------|-----------------|  
|reserved_space|BIGINT|Insgesamt durch die Datenbank belegter Speicherplatz in KB. Diese Zahl ändert sich, wenn das zwischengespeicherte Resultset größer wird.|  
|data_space|BIGINT|Durch die Daten belegter Speicherplatz in KB.|  
|index_space|BIGINT|Durch die Daten belegter Speicherplatz in KB.|  
|unused_space|BIGINT|Speicherplatz in KB, der zum reservierten Speicherplatz gehört und nicht verwendet wird.|  


## <a name="see-also"></a>Siehe auch

[Leistungsoptimierung mit Resultsetcaching](/azure/sql-data-warehouse/performance-tuning-result-set-caching)</br>
[ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options?view=azure-sqldw-latest)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)</br>
[SET RESULT SET CACHING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-result-set-caching-transact-sql)</br>
[DBCC DROPRESULTSETCACHE  &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-dropresultsetcache-transact-sql)