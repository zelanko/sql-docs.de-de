---
title: Sys. dm_continuous_copy_status (Azure SQL-Datenbank) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_continuous_copy_status_TSQL
- dm_continuous_copy_status_TSQL
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
dev_langs:
- TSQL
helpviewer_keywords:
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
ms.assetid: 411b2e71-4421-4ef5-900d-5af068750899
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: cace39108f3f99d5c165f42b4337e837e1fb7c5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68121026"
---
# <a name="sysdmcontinuouscopystatus-azure-sql-database"></a>sys.dm_continuous_copy_status (Azure SQL-Datenbank)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Gibt eine Zeile für jede Benutzerdatenbank (V11), die derzeit in einer Beziehung mit kontinuierlichem kopieren Geo-Replikation beteiligt ist. Wenn für eine bestimmte primäre Datenbank mehr als eine Beziehung mit kontinuierlichem Kopieren initiiert wird, enthält diese Tabelle für jede aktive sekundäre Datenbank eine Zeile.  
  
Bei Verwendung von SQL-Datenbank V12 sollten Sie verwenden [dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) (da *Sys. dm_continuous_copy_status* gilt nur für V11).

  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**copy_guid**|**uniqueidentifier**|Eindeutige ID der Replikatdatenbank.|  
|**partner_server**|**sysname**|Der Name des SQL-Datenbankverbindungsservers.|  
|**partner_database**|**sysname**|Name der Verbindungsdatenbank auf dem SQL-Datenbankverbindungsserver.|  
|**last_replication**|**datetimeoffset**|Der Zeitstempel der zuletzt durchgeführten replizierten Transaktion.|  
|**replication_lag_sec**|**int**|Der Zeitunterschied in Sekunden zwischen der aktuellen Zeit und dem Zeitstempel der letzten Transaktion in der primären Datenbank, für die erfolgreich ein Commit ausgeführt wurde und die von der aktiven sekundären Datenbank nicht bestätigt wurde.|  
|**replication_state**|**tinyint**|Der Status der fortlaufenden kopierbeziehung für diese Datenbank. Im folgenden sind die möglichen Werte und deren Beschreibungen.<br /><br /> 1: Das Seeding. Für das Replikationsziel, das einen inkonsistenten Transaktionsstatus aufweist, wird ein Seeding durchgeführt. Solange das Seeding noch nicht abgeschlossen wurde, können Sie keine Verbindung mit der aktiven sekundären Datenbank herstellen. <br />2: Aufholend. Die aktive sekundäre Datenbank holt derzeit den Rückstand zur primären Datenbank auf und weist hinsichtlich der Transaktionen einen konsistenten Status auf.<br />3: Erneutes seeding. Für die aktive sekundäre Datenbank wird aufgrund eines nicht behebbaren Replikationsfehlers automatisch ein erneutes Seeding durchgeführt.<br />4: Unterbrochen Dies ist keine aktive Beziehung mit kontinuierlichem Kopieren. Dieser Status gibt normalerweise an, dass die Bandbreite, die für den Interlink verfügbar ist, für die Ebene der Transaktionsaktivität in der primären Datenbank nicht ausreicht. Die Beziehung mit kontinuierlichem Kopieren ist jedoch nach wie vor intakt.|  
|**replication_state_desc**|**nvarchar(256)**|Beschreibung von replication_state. Folgende Werte sind möglich:<br /><br /> SEEDING<br /><br /> CATCH_UP<br /><br /> RE_SEEDING<br /><br /> SUSPENDED|  
|**is_rpo_limit_reached**|**bit**|Wird immer auf 0 festgelegt.|  
|**is_target_role**|**bit**|0 = Quelle der Kopienbeziehung<br /><br /> 1 = Ziel der Kopienbeziehung|  
|**is_interlink_connected**|**bit**|1 = Interlink ist verbunden.<br /><br /> 0 = Interlink-Verbindung ist getrennt.|  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Abrufen von Daten, erfordert die Mitgliedschaft in der **Db_owner** -Datenbankrolle. Die Dbo-Benutzer, der Mitglied der **"DBManager"** Datenbankrolle und Anmeldenamens "sa" können alle Abfragen in dieser Ansicht auch.  
  
## <a name="remarks"></a>Hinweise  
 Die **Sys. dm_continuous_copy_status** Sicht wird erstellt, der **Ressource** -Datenbank und in allen Datenbanken, einschließlich der logischen Master sichtbar ist. Wenn aber diese Sicht in der logischen master-Datenbank abgerufen wird, wird ein leeres Set zurückgegeben.  
  
 Wenn die fortlaufende kopierbeziehung, in einer Datenbank, die Zeile für diese Datenbank in beendet wird der **Sys. dm_continuous_copy_status** -Sicht nicht mehr angezeigt.  
  
 Wie die **Sys. dm_database_copies** Ansicht **Sys. dm_continuous_copy_status** zeigt den Status der fortlaufenden kopierbeziehung in der die Datenbank entweder eine primäre oder aktive sekundäre Datenbank ist . Im Gegensatz zu **Sys. dm_database_copies**, **Sys. dm_continuous_copy_status** enthält mehrere Spalten, die Details zu Vorgängen und Leistung bereitstellen. Diese Spalten enthalten **Last_replication**, und **Replication_lag_sec**...  
  
## <a name="see-also"></a>Siehe auch  
 [Sys. dm_database_copies &#40;Azure SQL-Datenbank&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)   
 [Aktive geografische Replikation gespeicherten Prozeduren &#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)  
  
  
