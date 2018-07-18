---
title: Sys. sp_cleanup_temporal_history | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: ''
ms.prod_service: sql-database
ms.service: sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6eff30b4-b261-4f1f-b93c-1f69d754298d
caps.latest.revision: 4
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 6216ca6584c2bf6d78bb66096145cd49428398dc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38051195"
---
# <a name="sysspcleanuptemporalhistory-transact-sql"></a>Sys. sp_cleanup_temporal_history (Transact-SQL)
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
