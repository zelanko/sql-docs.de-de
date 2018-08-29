---
title: Sp_helpdistributiondb (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpdistributiondb_TSQL
- sp_helpdistributiondb
helpviewer_keywords:
- sp_helpdistributiondb
ms.assetid: a2917020-26d1-4011-99f8-9212d120fd2d
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: df4a44be4ef3271e6af8e7148bfee50f40c71617
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43018296"
---
# <a name="sphelpdistributiondb-transact-sql"></a>sp_helpdistributiondb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die Eigenschaften der angegebenen Verteilungsdatenbank zurück. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdistributiondb [ [ @database= ] 'database_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@database=**] **"***Database_name***"**  
 Der Datenbankname, für den Eigenschaften zurückgegeben werden. *Database_name* ist **Sysname**, hat den Standardwert **%** für alle Datenbanken verbunden sind, mit dem Verteiler und für die der Benutzer über Berechtigungen verfügt.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Verteilungsdatenbank.|  
|**min_distretention**|**int**|Die Mindestbeibehaltungsdauer in Stunden, bevor Transaktionen gelöscht werden.|  
|**max_distretention**|**int**|Die Höchstbeibehaltungsdauer in Stunden, bevor Transaktionen gelöscht werden.|  
|**verlaufsbeibehaltung**|**int**|Die Anzahl von Stunden, für die der Verlauf erhalten bleibt.|  
|**history_cleanup_agent**|**sysname**|Der Name des Verlaufscleanup-Agents.|  
|**distribution_cleanup_agent**|**sysname**|Der Name des Verteilungscleanup-Agents.|  
|**status**|**int**|Nur interne Verwendung.|  
|**data_folder**|**nvarchar(255)**|Der Name des Verzeichnisses zum Speichern der Datenbankdateien.|  
|**data_file**|**nvarchar(255)**|Der Name der Datenbankdatei.|  
|**data_file_size**|**int**|Die Anfangsgröße der Datendatei in Megabyte.|  
|**log_folder**|**nvarchar(255)**|Der Name des Verzeichnisses für die Datenbankprotokolldatei.|  
|**Log_file**|**nvarchar(255)**|Der Name der Protokolldatei.|  
|**log_file_size**|**int**|Die Anfangsgröße der Protokolldatei in Megabyte.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_helpdistributiondb** wird in allen Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der **Db_owner** festen Datenbankrolle oder der **Replmonitor** -Rolle in eine Verteilungsdatenbank und Benutzer in der veröffentlichungszugriffsliste einer Veröffentlichung mit der Distribution-Datenbank ausführen können **Sp_helpdistributiondb** um dateibezogene Informationen zurückzugeben. Mitglieder der **öffentliche** Rolle ausführen kann **Sp_helpdistributiondb** um nicht dateibezogene Daten für Verteilungsdatenbanken zurückzugeben, auf die sie Zugriff haben.  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen und Ändern der Verteiler- und Verlegereigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Sp_adddistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [Sp_changedistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [Sp_dropdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
