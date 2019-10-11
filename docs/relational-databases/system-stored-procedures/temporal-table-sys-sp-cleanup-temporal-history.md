---
title: sys. sp_cleanup_temporal_history | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
author: CarlRabeler
ms.author: carlrab
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 6f382af39620fde58480b9fa02178901cb882dab
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72251998"
---
# <a name="syssp_cleanup_temporal_history-transact-sql"></a>sys. sp_cleanup_temporal_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

Entfernt alle Zeilen aus einer temporalen Verlaufs Tabelle, die mit dem konfigurierten HISTORY_RETENTION Zeitraum innerhalb einer einzelnen Transaktion identisch sind
  
## <a name="syntax"></a>Syntax  
```  
sp_cleanup_temporal_history [@schema_name = ] schema_name, [@table_name = ] table_name [, [@row_count=] @row_count_var [OUTPUT]]
```  
  
## <a name="arguments"></a>Argumente  

*\@table_name*

Der Name der temporalen Tabelle, für die die Beibehaltungs Bereinigung aufgerufen wird.

*schema_name*

Der Name des Schemas, zu dem die aktuelle Temporale Tabelle gehört.

*row_count_var* [Ausgabe]

Der Output-Parameter, der die Anzahl der gelöschten Zeilen zurückgibt. Wenn in der Verlaufs Tabelle ein gruppierter columnstore--Index verwendet wird, gibt dieser Parameter immer 0 zurück.
  
## <a name="remarks"></a>Hinweise
Diese gespeicherte Prozedur kann nur für temporale Tabellen verwendet werden, für die eine begrenzte Beibehaltungs Dauer festgelegt wurde.
Verwenden Sie diese gespeicherte Prozedur nur, wenn Sie alle veralteten Zeilen aus der Verlaufs Tabelle sofort bereinigen müssen. Sie sollten wissen, dass sich dies erheblich auf das Daten Bank Protokoll und das e/a-Subsystem auswirken kann, wenn alle berechtigten Zeilen innerhalb derselben Transaktion gelöscht werden. 

Es wird immer empfohlen, sich auf eine interne Hintergrundaufgabe für die Bereinigung zu verlassen, bei der veraltete Zeilen mit minimalen Auswirkungen auf die regulären Workloads und die Datenbank im allgemeinen entfernt werden.

## <a name="permissions"></a>Berechtigungen  
 Erfordert db_owner-Berechtigungen.  

## <a name="example"></a>Beispiel

```
declare @rowcnt int
EXEC sys.sp_cleanup_temporal_history 'dbo', 'Department', @rowcnt output
select @rowcnt
```

## <a name="see-also"></a>Siehe auch

[Aufbewahrungs Richtlinie für temporale Tabellen](https://docs.microsoft.com/azure/sql-database/sql-database-temporal-tables-retention-policy)
