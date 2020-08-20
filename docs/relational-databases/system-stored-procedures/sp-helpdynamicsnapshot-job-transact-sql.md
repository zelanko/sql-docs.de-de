---
description: sp_helpdynamicsnapshot_job (Transact-SQL)
title: sp_helpdynamicsnapshot_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdynamicsnapshot_TSQL
- sp_helpdynamicsnapshot_job_TSQL
- job_TSQL
- helpdynamicsnapshot
- job
- sp_helpdynamicsnapshot
- sp_helpdynamicsnapshot_job
- helpdynamicsnapshot_TSQL
helpviewer_keywords:
- sp_helpdynamicsnapshot_job
ms.assetid: d6dfdf26-f874-495f-a8a6-8780699646d7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 61e72b03e3bc6adff3a9e3d0858a8a2bdb4b5805
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88469292"
---
# <a name="sp_helpdynamicsnapshot_job-transact-sql"></a>sp_helpdynamicsnapshot_job (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt Informationen zu Agent-Aufträgen zurück, die gefilterte Datenmomentaufnahmen generieren. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helpdynamicsnapshot_job [ [ @publication = ] 'publication' ]   
    [ , [ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname' ]  
    [ , [ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname** **%** und hat den Standardwert, der Informationen zu allen gefilterten Daten Momentaufnahme-Aufträgen zurückgibt, die dem angegebenen *dynamic_snapshot_jobid*und *dynamic_snapshot_jobname*für alle Veröffentlichungen entsprechen.  
  
`[ @dynamic_snapshot_jobname = ] 'dynamic_snapshot_jobname'` Der Name eines Auftrags für eine Momentaufnahme gefilterter Daten. *dynamic_snapshot_jobname*ist vom **Datentyp vom Datentyp sysname**. der Standardwert ist **%** ", wodurch alle dynamischen Aufträge für eine Veröffentlichung mit dem angegebenen *dynamic_snapshot_jobid*zurückgegeben werden. Wenn beim Erstellen des Auftrags kein expliziter Auftragsname angegeben wurde, hat der Auftragsname folgendes Format:  
  
```  
'dyn_' + <name of the standard snapshot job> + <GUID>  
```  
  
`[ @dynamic_snapshot_jobid = ] 'dynamic_snapshot_jobid'` Ein Bezeichner für einen Auftrag für eine Momentaufnahme gefilterter Daten. *dynamic_snapshot_jobid*ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL, der alle Momentaufnahme Aufträge zurückgibt, die mit dem angegebenen *dynamic_snapshot_jobname*identisch sind.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|Identifiziert den Auftrag für eine Momentaufnahme gefilterter Daten.|  
|**job_name**|**sysname**|Name des Auftrags für eine Momentaufnahme gefilterter Daten.|  
|**job_id**|**uniqueidentifier**|Identifiziert den [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Auftrag auf dem Verteiler.|  
|**dynamic_filter_login**|**sysname**|Der Wert, der zum Auswerten der [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) Funktion in einem parametrisierten, für die Veröffentlichung definierten Zeilen Filter verwendet wird.|  
|**dynamic_filter_hostname**|**sysname**|Der Wert, der zum Auswerten der [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) Funktion in einem parametrisierten, für die Veröffentlichung definierten Zeilen Filter verwendet wird.|  
|**dynamic_snapshot_location**|**nvarchar(255)**|Der Pfad zu dem Ordner, aus dem die Momentaufnahmedateien gelesen werden, wenn ein parametrisierter Zeilenfilter verwendet wird.|  
|**frequency_type**|**int**|Die Häufigkeit, mit der der Agent planmäßig ausgeführt wird. Die folgenden Werte sind möglich:<br /><br /> **1** = einmal<br /><br /> **2** = Bedarfs gesteuert<br /><br /> **4** = täglich<br /><br /> **8** = wöchentlich<br /><br /> **16** = monatlich<br /><br /> **32** = monatlich, relativ<br /><br /> **64** = Autostart<br /><br /> **128** = wiederholt|  
|**frequency_interval**|**int**|Die Tage, an denen der Agent ausgeführt wird. Die folgenden Werte sind möglich.<br /><br /> **1** = Sonntag<br /><br /> **2** = Montag<br /><br /> **3** = Dienstag<br /><br /> **4** = Mittwoch<br /><br /> **5** = Donnerstag<br /><br /> **6** = Freitag<br /><br /> **7** = Samstag<br /><br /> **8** = Tag<br /><br /> **9** = Wochentage<br /><br /> **10** = Wochenende (Tage)|  
|**frequency_subday_type**|**int**|Der Typ, der definiert, wie oft der Agent ausgeführt wird, wenn *frequency_type* **4** (täglich) ist und einen der folgenden Werte aufweisen kann.<br /><br /> **1** = zum angegebenen Zeitpunkt<br /><br /> **2** = Sekunden<br /><br /> **4** = Minuten<br /><br /> **8** = Stunden|  
|**frequency_subday_interval**|**int**|Anzahl der Intervalle von *frequency_subday_type* , die zwischen der geplanten Ausführung des Agents auftreten.|  
|**frequency_relative_interval**|**int**|Die Woche, in der der Agent in einem bestimmten Monat ausgeführt wird, wenn *frequency_type* **32** (monatlich, relativ) ist und einen der folgenden Werte aufweisen kann.<br /><br /> **1** = zuerst<br /><br /> **2** = Sekunde<br /><br /> **4** = dritte<br /><br /> **8** = Fourth<br /><br /> **16** = zuletzt|  
|**frequency_recurrence_factor**|**int**|Anzahl der Wochen oder Monate zwischen der geplanten Ausführung der Momentaufnahme.|  
|**active_start_date**|**int**|Datum, an dem die Ausführung der Momentaufnahme zum ersten Mal geplant ist (Format: YYYYMMDD).|  
|**active_end_date**|**int**|Datum, an dem die Ausführung der Momentaufnahme zum letzten Mal geplant ist (Format: YYYYMMDD).|  
|**active_start_time**|**int**|Uhrzeit, zu der die Ausführung der Momentaufnahme zum ersten Mal geplant ist (Format: HHMMSS).|  
|**active_end_time**|**int**|Uhrzeit, zu der die Ausführung der Momentaufnahme zum letzten Mal geplant ist (Format: HHMMSS).|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_helpdynamicsnapshot_job** wird bei der Mergereplikation verwendet.  
  
 Werden alle Standardparameterwerte verwendet, werden Informationen zu allen Aufträgen für eine Momentaufnahme partitionierter Daten für die gesamte Veröffentlichungsdatenbank zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** , der festen Daten Bank Rolle **db_owner** und der Veröffentlichungs Zugriffsliste für die Veröffentlichung können **sp_helpdynamicsnapshot_job**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
