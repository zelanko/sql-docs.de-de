---
description: sp_updatestats (Transact-SQL)
title: sp_updatestats (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_updatestats_TSQL
- sp_updatestats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatestats
ms.assetid: 01184651-6e61-45d9-a502-366fecca0ee4
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: dee5ef30ca260855c9df6a7823e7dce605c3ff72
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534798"
---
# <a name="sp_updatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Wird `UPDATE STATISTICS` für alle benutzerdefinierten und internen Tabellen in der aktuellen Datenbank ausgeführt.  
  
Weitere Informationen zu `UPDATE STATISTICS` finden Sie unter [Aktualisieren von Statistiken &#40;Transact-SQL-&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Weitere Informationen zu Statistiken finden Sie unter [Statistik](../../relational-databases/statistics/statistics.md).  
    
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="arguments"></a>Argumente  
`[ @resample = ] 'resample'` Gibt an, dass **sp_updatestats** die RESAMPLE-Option der [Update Statistics](../../t-sql/statements/update-statistics-transact-sql.md) -Anweisung verwendet. Wird **'resample'** nicht angegeben, aktualisiert **sp_updatestats** Statistiken mithilfe der Standardstichprobe. **resample** ist vom Datentyp **varchar(8)** . Der Standardwert ist NO.  
  
## <a name="remarks"></a>Hinweise  
 **sp_updatestats** `UPDATE STATISTICS` wird durch Angabe des- `ALL` Schlüssel Worts für alle benutzerdefinierten und internen Tabellen in der Datenbank ausgeführt. sp_updatestats zeigt Meldungen an, die auf den Fortschritt hinweisen. Nach Abschluss des Updates wird gemeldet, dass die Statistiken für alle Tabellen aktualisiert wurden.  
  
**sp_updatestats** aktualisiert Statistiken für deaktivierte nicht gruppierte Indizes und aktualisiert keine Statistiken für deaktivierte gruppierte Indizes.  
  
Bei Datenträger basierten Tabellen aktualisiert **sp_updatestats** Statistiken basierend auf den **modification_counter** Informationen in der **sys. dm_db_stats_properties** -Katalog Sicht und aktualisiert die Statistiken, wenn mindestens eine Zeile geändert wurde. Statistiken für speicheroptimierte Tabellen werden immer aktualisiert, wenn **sp_updatestats**ausgeführt wird. Deshalb sollte **sp_updatestats** nicht häufiger als nötig ausgeführt werden.  
  
**sp_updatestats** kann die Neukompilierung von gespeicherten Prozeduren oder anderem kompilierten Code auslösen. Allerdings kann **sp_updatestats** unter Umständen keine Neukompilierung verursachen, wenn nur ein Abfrageplan für die Tabellen, auf die verwiesen wird, und die Indizes möglich ist. Eine Neukompilierung wäre in diesen Fällen nicht erforderlich, selbst wenn die Statistiken aktualisiert werden.  
  
Bei Datenbanken mit einem Kompatibilitätsgrad unter 90 wird beim Ausführen von **sp_updatestats** die letzte NORECOMPUTE-Einstellung für bestimmte Statistiken nicht beibehalten. Bei Datenbanken mit einem Kompatibilitäts Grad von 90 oder höher behält sp_updatestats die letzte NORECOMPUTE-Option für bestimmte Statistiken bei. Weitere Informationen zum Deaktivieren und erneuten Aktivieren von Statistikupdates finden Sie unter [Statistiken](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Berechtigungen  

Um **sp_updatestats**auszuführen, muss der Benutzer der Besitzer der Datenbank ( `dbo` nicht nur Mitglied der Rolle `db_owner` ) oder Mitglied der festen Server Rolle sysadmin sein.

## <a name="examples"></a>Beispiele  
Im folgenden Beispiel werden die Statistiken für Tabellen in der [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] -Datenbank aktualisiert.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  

## <a name="automatic-index-and-statistics-management"></a>Automatische Verwaltung von Index und Statistiken
Nutzen Sie Lösungen wie [Adaptive Index Defrag](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag), um die Indexdefragmentierung und das Aktualisieren der Statistiken für eine oder mehrere Datenbanken automatisch zu verwalten. Dieser Vorgang entscheidet unter anderem anhand des Fragmentierungsgrads automatisch, ob ein Index neu organisiert oder neu erstellt wird und aktualisiert Statistiken mit einem linearen Schwellenwert.

## <a name="see-also"></a>Weitere Informationen  
 [ALTER DATABASE SET-Optionen &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Gespeicherte System Prozeduren](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
 
