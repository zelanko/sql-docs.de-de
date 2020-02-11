---
title: sp_dbmmonitorupdate (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitorupdate
- sp_dbmmonitorupdate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbmmonitorupdate
- database mirroring [SQL Server], monitoring
ms.assetid: 9ceb9611-4929-44ee-a406-c39ba2720fd5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 190b4f0598afa6d434b5dada8c8464cb8209dac7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061260"
---
# <a name="sp_dbmmonitorupdate-transact-sql"></a>sp_dbmmonitorupdate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Aktualisiert die Statustabelle des Datenbankspiegelungs-Monitors durch Einfügen einer neuen Tabellenzeile für jede gespiegelte Datenbank und schneidet Zeilen ab, die älter als die aktuelle Beibehaltungsdauer sind. Die Standardbeibehaltungsdauer beträgt 7 Tage (168 Stunden). Beim Aktualisieren der Tabelle wertet **sp_dbmmonitorupdate** die Leistungsmetriken aus.  
  
> [!NOTE]  
>  Bei der ersten Ausführung von **sp_dbmmonitorupdate** werden die Tabelle des Datenbankspiegelungsstatus und die feste Datenbankrolle **dbm_monitor** in der **msdb** -Datenbank erstellt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dbmmonitorupdate [ database_name ]  
```  
  
## <a name="arguments"></a>Argumente  
 *database_name*  
 Der Name der Datenbank, für die der Spiegelungsstatus aktualisiert wird. Wenn *database_name* nicht angegeben wird, aktualisiert die Prozedur die Statustabelle für jede gespiegelte Datenbank auf der Serverinstanz.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dbmmonitorupdate** können nur im Kontext der **msdb** -Datenbank ausgeführt werden.  
  
 Falls eine Spalte der Statustabelle für die Rolle eines Partners nicht gilt, ist der Wert für diesen Partner NULL. Eine Spalte hat auch den Wert NULL, wenn die relevanten Informationen nicht verfügbar sind, z. B. während eines Failovers oder eines Serverneustarts.  
  
 Nachdem **sp_dbmmonitorupdate** die **dbm_monitor** festen Daten Bank Rolle in der **msdb** -Datenbank erstellt haben, können Mitglieder der festen Server Rolle **sysadmin** jeden Benutzer der festen Daten Bank Rolle **dbm_monitor** hinzufügen. Mit der **dbm_monitor** -Rolle können die Mitglieder der Datenbank den Daten Bank Spiegelungs Status anzeigen, jedoch nicht aktualisieren, aber keine Daten Bank Spiegelungs Ereignisse anzeigen oder konfigurieren.  
  
 Beim Aktualisieren des Spiegelungs Status einer Datenbank prüft **sp_dbmmonitorupdate** den aktuellen Wert jeder Spiegelungs Leistungs Metrik, für die ein Warnungs Schwellenwert angegeben wurde. Wenn der Wert den Schwellenwert überschreitet, fügt die Prozedur dem Ereignisprotokoll ein Informationsereignis hinzu. Alle Raten sind seit dem letzten Update Durchschnittswerte. Weitere Informationen finden Sie unter [Verwenden von Warnungsschwellenwerten und Warnmeldungen für Spiegelungsleistungsmetriken &#40;SQL Server&#41;](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Spiegelungsstatus nur für die [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]-Datenbank aktualisiert.  
  
```  
USE msdb;  
EXEC sp_dbmmonitorupdate AdventureWorks2012 ;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Daten Bank Spiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangealert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangealert-transact-sql.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropalert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropalert-transact-sql.md)   
 [sp_dbmmonitorhelpalert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpalert-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
