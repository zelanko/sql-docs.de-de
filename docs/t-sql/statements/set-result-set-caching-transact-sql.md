---
description: SET RESULT_SET_CACHING (Transact-SQL)
title: SET RESULT_SET_CACHING (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/16/2020
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
ms.openlocfilehash: fda398df7a9b06cf50419e899c9b0c9975855478
ms.sourcegitcommit: 8f062015c2a033f5a0d805ee4adabbe15e7c8f94
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91226400"
---
# <a name="set-result-set-caching-transact-sql"></a>SET RESULT SET CACHING (Transact-SQL) 

[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

Steuert das Verhalten für das Zwischenspeichern von Resultsets für die aktuelle Clientsitzung.  

Gilt für [!INCLUDE[ssSDW](../../includes/sssdwfull-md.md)]e  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax

```syntaxsql
SET RESULT_SET_CACHING { ON | OFF };
```  
  
## <a name="remarks"></a>Bemerkungen  

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

## <a name="see-also"></a>Weitere Informationen

- [Leistungsoptimierung mit Zwischenspeichern von Resultsets](/azure/sql-data-warehouse/performance-tuning-result-set-caching)
- [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options?view=azure-sqldw-latest&preserve-view=true)
- [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql?view=azure-sqldw-latest&preserve-view=true)
- [DBCC SHOWRESULTCACHESPACEUSED (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-showresultcachespaceused-transact-sql)
- [DBCC DROPRESULTSETCACHE (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-dropresultsetcache-transact-sql)
