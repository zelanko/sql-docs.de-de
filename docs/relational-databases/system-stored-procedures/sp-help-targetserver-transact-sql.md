---
title: sp_help_targetserver (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_targetserver_TSQL
- sp_help_targetserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_targetserver
ms.assetid: f841d3bd-901a-4980-ad0b-1c6eeba3f717
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ed310262b4f233a8642bbbab382a6d0b30a311e4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85752788"
---
# <a name="sp_help_targetserver-transact-sql"></a>sp_help_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Listet alle Zielserver auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help_targetserver   
     [ [ @server_name = ] 'server_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server_name = ] 'server_name'`Der Name des Servers, für den Informationen zurückgegeben werden sollen. *server_name* ist vom Datentyp **nvarchar (30)** und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Wenn *server_name* nicht angegeben ist, gibt **sp_help_targetserver** dieses Resultset zurück.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Die Server-ID.|  
|**server_name**|**nvarchar(30)**|Servername.|  
|**location**|**nvarchar(200)**|Standort des angegebenen Servers.|  
|**time_zone_adjustment**|**int**|Zeitzonenanpassung ausgehend von der GMT (Greenwich Mean Time) in Stunden.|  
|**enlist_date**|**datetime**|Datum der Eintragung des angegebenen Servers.|  
|**last_poll_date**|**datetime**|Datum, an dem der Server zuletzt nach Aufträgen abgefragt wurde.|  
|**status**|**int**|Status des angegebenen Servers.|  
|**unread_instructions**|**int**|Gibt an, ob auf dem Server ungelesene Anweisungen vorhanden sind. Wenn alle Zeilen heruntergeladen wurden, ist diese Spalte **0**.|  
|**local_time**|**datetime**|Lokales Datum und lokale Uhrzeit auf dem Zielserver. Diese basieren auf der lokalen Zeit des Zielservers zum Zeitpunkt des letzten Abrufs des Masterservers.|  
|**enlisted_by_nt_user**|**nvarchar (100)**|Microsoft Windows-Benutzer, der den Zielserver eingetragen hat.|  
|**poll_interval**|**int**|Häufigkeit in Sekunden, mit der der Zielserver den Master-SQLServerAgent-Dienst abruft, um Aufträge herunterzuladen und den Auftragsstatus hochzuladen.|  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss ein Benutzer Mitglied der festen Serverrolle **sysadmin** sein.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-listing-information-for-all-registered-target-servers"></a>A. Auflisten von Informationen für alle registrierten Zielserver  
 Das folgende Beispiel listet Informationen für alle registrierten Zielserver auf.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-target-server"></a>B. Auflisten von Informationen für einen bestimmten Zielserver  
 Das folgende Beispiel listet Informationen für den Zielserver `SEATTLE2` auf.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_targetservergroup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_delete_targetservergroup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [dbo.sysdownloadlist &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-sysdownloadlist-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
