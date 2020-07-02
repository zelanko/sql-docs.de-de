---
title: sp_helppublication_snapshot (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppublication_snapshot
- sp_helppublication_snapshot_TSQL
helpviewer_keywords:
- sp_helppublication_snapshot
ms.assetid: 97b4a7ae-40a5-4328-88f1-ff5d105bbb34
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a1dc48a88bd9a180b7cb0ce65a24c607b80cd6a9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725759"
---
# <a name="sp_helppublication_snapshot-transact-sql"></a>sp_helppublication_snapshot (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt Informationen zum Momentaufnahme-Agent einer gegebenen Veröffentlichung zurück. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungs Datenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_helppublication_snapshot [ @publication = ] 'publication'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher = ] 'publisher'`Gibt einen nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Verleger an. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  der *Verleger* sollte nicht verwendet werden, wenn einem Verleger ein Artikel hinzugefügt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ID des Momentaufnahme-Agents|  
|**name**|**nvarchar (100)**|Name des Momentaufnahme-Agents|  
|**publisher_security_mode**|**smallint**|Sicherheitsmodus, der vom Agent für die Verbindung mit dem Verleger verwendet wird. Folgende Werte sind möglich:<br /><br /> **0** -  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentifizierung<br /><br /> **1** = Windows-Authentifizierung.|  
|**publisher_login**|**sysname**|Anmeldename, der für die Verbindung mit dem Verleger verwendet wird.|  
|**publisher_password**|**nvarchar (524)**|Aus Sicherheitsgründen wird immer der Wert **\*\*\*\*\*\*\*\*\*\*** zurückgegeben.|  
|**job_id**|**uniqueidentifier**|Eindeutige ID des Agentauftrags.|  
|**job_login**|**nvarchar(512)**|Das Windows-Konto, unter dem der Momentaufnahme-Agent ausgeführt wird, der im Format *Domäne* \\ *Benutzername*zurückgegeben wird.|  
|**job_password**|**sysname**|Aus Sicherheitsgründen wird immer der Wert **\*\*\*\*\*\*\*\*\*\*** zurückgegeben.|  
|**schedule_name**|**sysname**|Name des für diesen Agentauftrag verwendeten Zeitplans|  
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
  
## <a name="remarks"></a>Hinweise  
 **sp_help_publication_snapshot** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verleger oder Mitglieder der festen Daten Bank Rolle **db_owner** in der Veröffentlichungs Datenbank können **sp_help_publication_snapshot**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen und Ändern von Veröffentlichungseigenschaften](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [sp_addpublication_snapshot &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [sp_changepublication_snapshot &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)  
  
  
