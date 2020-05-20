---
title: sp_helpdistributiondb (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributiondb_TSQL
- sp_helpdistributiondb
helpviewer_keywords:
- sp_helpdistributiondb
ms.assetid: a2917020-26d1-4011-99f8-9212d120fd2d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e0efc86400b0858e387a83e8ea765f0058e30459
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824495"
---
# <a name="sp_helpdistributiondb-transact-sql"></a>sp_helpdistributiondb (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt die Eigenschaften der angegebenen Verteilungsdatenbank zurück. Diese gespeicherte Prozedur wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdistributiondb [ [ @database= ] 'database_name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @database = ] 'database_name'`Der Name der Datenbank, für die Eigenschaften zurückgegeben werden. *database_name* ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **%** für alle Datenbanken, die dem Verteiler zugeordnet sind und für die der Benutzer über Berechtigungen verfügt.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Der Name der Verteilungsdatenbank.|  
|**min_distretention**|**int**|Die Mindestbeibehaltungsdauer in Stunden, bevor Transaktionen gelöscht werden.|  
|**max_distretention**|**int**|Die Höchstbeibehaltungsdauer in Stunden, bevor Transaktionen gelöscht werden.|  
|**history retention**|**int**|Die Anzahl von Stunden, für die der Verlauf erhalten bleibt.|  
|**history_cleanup_agent**|**sysname**|Der Name des Verlaufscleanup-Agents.|  
|**distribution_cleanup_agent**|**sysname**|Der Name des Verteilungscleanup-Agents.|  
|**status**|**int**|Nur zur internen Verwendung.|  
|**data_folder**|**nvarchar(255)**|Der Name des Verzeichnisses zum Speichern der Datenbankdateien.|  
|**data_file**|**nvarchar(255)**|Der Name der Datenbankdatei.|  
|**data_file_size**|**int**|Die Anfangsgröße der Datendatei in Megabyte.|  
|**log_folder**|**nvarchar(255)**|Der Name des Verzeichnisses für die Datenbankprotokolldatei.|  
|**log_file**|**nvarchar(255)**|Der Name der Protokolldatei.|  
|**log_file_size**|**int**|Die Anfangsgröße der Protokolldatei in Megabyte.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helpdistributiondb** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Mitglieder der festen Daten Bank Rolle **db_owner** oder der Rolle **replmonitor** in einer Verteilungs Datenbank und Benutzer in der Veröffentlichungs Zugriffsliste einer Veröffentlichung, die die Verteilungs Datenbank verwendet, können **sp_helpdistributiondb** ausführen, um Datei bezogene Informationen zurückzugeben. Mitglieder der **Public** -Rolle können **sp_helpdistributiondb** ausführen, um nicht Datei bezogene Informationen für Verteilungs Datenbanken zurückzugeben, auf die Sie Zugriff haben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern der Verteiler-und Verleger Eigenschaften](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributiondb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_changedistributiondb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
