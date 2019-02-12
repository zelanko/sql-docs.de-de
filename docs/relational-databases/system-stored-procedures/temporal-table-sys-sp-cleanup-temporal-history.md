---
title: Sys. sp_cleanup_temporal_history | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d74211c9c5052adc9fa49f47b55b9c379c33f01c
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56026441"
---
# <a name="sysspcleanuptemporalhistory-transact-sql"></a>sys.sp_cleanup_temporal_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

Entfernt alle Zeilen aus der temporalen Verlaufstabelle, die konfigurierten HISTORY_RETENTION-Zeitraum innerhalb einer einzelnen Transaktion zu entsprechen.
  
## <a name="syntax"></a>Syntax  
```  
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```  
  
## <a name="arguments"></a>Argumente  

*@table_name*

Der Name der temporalen Tabelle für die Aufbewahrung Cleanup aufgerufen wird.

*schema_name*

Der Name des Schemas, zu der aktuellen temporalen Tabelle gehört

*Row_count_var* [Ausgabe]

Die Output-Parameter, der Anzahl der gelöschten Zeilen zurückgibt. Dieser Parameter gibt zurück, wenn die Verlaufstabelle einen gruppierten columnstore-Index hat, immer 0.
  
## <a name="remarks"></a>Hinweise
Diese gespeicherte Prozedur kann nur mit temporalen Tabellen verwendet werden, begrenzte Beibehaltungsdauer angegeben haben.
Verwenden Sie diese gespeicherte Prozedur nur, wenn Sie sofort alle veraltete Zeilen aus der Verlaufstabelle bereinigen möchten. Sie sollten wissen, dass es erhebliche Auswirkungen auf das Datenbankprotokoll und die e/a-Subsystem kann wie alle geeignete Zeilen innerhalb derselben Transaktion gelöscht. 

Es wird immer empfohlen, dass veraltete von entfernt Zeilen mit der minimalen Auswirkungen auf die normale arbeitsauslastungen und die Datenbank im Allgemeinen von einer internen Hintergrundtask zur Bereinigung abhängig zu sein.

## <a name="permissions"></a>Berechtigungen  
 Benötigen Sie Db_owner-Berechtigungen.  

## <a name="example"></a>Beispiel

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>Siehe auch

[Temporale Tabellen mit Aufbewahrungsrichtlinie](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
