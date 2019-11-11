---
title: SET RESULT_SET_CACHING (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/03/2019
ms.prod: sql
ms.prod_service: sql-data-warehouse
ms.reviewer: jrasnick
ms.technology: t-sql
ms.topic: language-reference
f1_keywords: ''
dev_langs:
- TSQL
helpviewer_keywords: ''
author: XiaoyuMSFT
ms.author: xiaoyul
monikerRange: =azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: d2368cfe612831685da141f99069676ebf33cbb3
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729836"
---
# <a name="set-result-set-caching-transact-sql"></a>SET RESULT SET CACHING (Transact-SQL) 

[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-xxx-md.md)]

Steuert das Verhalten für das Zwischenspeichern von Resultsets für die aktuelle Clientsitzung.  

Gilt für Azure SQL Data Warehouse (Vorschauversion)
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Themenlink (Symbol)") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax

```
SET RESULT_SET_CACHING { ON | OFF };
```  
  
## <a name="remarks"></a>Remarks  

Führen Sie diesen Befehl aus, wenn Sie mit der Benutzerdatenbank verbunden sind, für die Sie die Einstellung result_set_caching konfigurieren möchten.

**ON**   
Aktiviert das Zwischenspeichern von Resultsets für die aktuelle Sitzung.  Das Zwischenspeichern eines Resultsets kann für eine Sitzung nicht aktiviert werden (ON), wenn es auf Datenbankebene deaktiviert (OFF) ist.

**OFF**   
Deaktivieren Sie das Zwischenspeichern von Resultsets für die aktuelle Sitzung.

## <a name="examples"></a>Beispiele

Fragen Sie die result_cache_hit-Spalte in [sys.dm_pdw_exec_requests](/sql/relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql) mit einer request_id der Abfrage ab, um zu überprüfen, ob diese Abfrage mit einem Treffer oder einem Fehler im Resultcache ausgeführt wurde.

```sql
SELECT result_cache_hit
FROM sys.dm_pdw_exec_requests
WHERE request_id = 'QID58286'
```

## <a name="permissions"></a>Berechtigungen

Erfordert die Mitgliedschaft in der „public“-Rolle.

## <a name="see-also"></a>Siehe auch
[Leistungsoptimierung mit Resultsetcaching](/azure/sql-data-warehouse/performance-tuning-result-set-caching)</br>
[ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options?view=azure-sqldw-latest)</br>
[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest)</br>
[DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-showresultcachespaceused-transact-sql)</br>
[DBCC DROPRESULTSETCACHE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-dropresultsetcache-transact-sql)