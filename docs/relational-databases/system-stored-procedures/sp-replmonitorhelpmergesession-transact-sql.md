---
title: Sp_replmonitorhelpmergesession (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpmergesession_TSQL
- sp_replmonitorhelpmergesession
helpviewer_keywords:
- sp_replmonitorhelpmergesession
ms.assetid: a0400ba8-9609-4901-917e-925e119103a1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 224d304a44c3e66eb8f2c18f4c581bf271f926f9
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58538502"
---
# <a name="spreplmonitorhelpmergesession-transact-sql"></a>sp_replmonitorhelpmergesession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt Informationen zu vergangenen Sitzungen für einen angegebenen Replikationsmerge-Agent zurück. Für jede Sitzung, die den Filterkriterien entspricht, wird dabei eine Zeile zurückgegeben. Diese gespeicherte Prozedur dient zum Überwachen der Mergereplikation. Sie wird beim Verteiler auf der Verteilungsbank oder beim Abonnenten auf der Abonnementdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorhelpmergesession [ [ @agent_name = ] 'agent_name' ]  
    [ , [ @hours = ] hours ]  
    [ , [ @session_type = ] session_type ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @agent_name = ] 'agent_name'` Ist der Name des Agents. *Agent_name* ist **nvarchar(100)** hat keinen Standardwert.  
  
`[ @hours = ] hours` Ist der Zeitbereich, in Stunden, für die historische agentsitzungsinformationen zurückgegeben wird. *Stunden* ist **Int**, die kann eine der folgenden Bereiche.  
  
|Wert|Description|  
|-----------|-----------------|  
|< **0**|Gibt Informationen zu vergangenen Agentausführungen (bis zu maximal 100 Ausführungen) zurück.|  
|**0** (Standardwert)|Gibt Informationen zu allen vergangenen Agentausführungen zurück.|  
|> **0**|Gibt Informationen zu Agent ausgeführt wird, die aufgetreten sind in den letzten *Stunden* Anzahl von Stunden.|  
  
`[ @session_type = ] session_type` Filtert das Resultset auf Grundlage des sitzungsendergebnisses. *SQLDMO_SESSION_TYPE* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**1** (Standard)|Agentsitzungen mit einem Neuversuch oder erfolgreichem Abschluss.|  
|**0**|Agentsitzungen mit einem Fehlerergebnis.|  
  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers. *Publisher* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter wird verwendet, bei der Ausführung **Sp_replmonitorhelpmergesession** auf dem Abonnenten.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der Veröffentlichungsdatenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter wird verwendet, bei der Ausführung **Sp_replmonitorhelpmergesession** auf dem Abonnenten.  
  
`[ @publication = ] 'publication'` Ist der Name der Veröffentlichung. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL. Dieser Parameter wird verwendet, bei der Ausführung **Sp_replmonitorhelpmergesession** auf dem Abonnenten.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**Session_id**|**int**|ID der Agentauftragssitzung.|  
|**Status**|**int**|-Agent-Status der Ausführung:<br /><br /> **1** = Start<br /><br /> **2** = Erfolg<br /><br /> **3** = wird ausgeführt<br /><br /> **4** = im Leerlauf<br /><br /> **5** = wiederholen<br /><br /> **6** = Fehler|  
|**StartTime**|**datetime**|Zeit der agentauftragssitzung wurde gestartet.|  
|**EndTime**|**datetime**|Zeit der agentauftragssitzung wurde abgeschlossen.|  
|**Dauer**|**int**|Kumulierte Dauer dieser Auftragssitzung in Sekunden.|  
|**UploadedCommands**|**int**|Anzahl von Befehlen, die während der Agentsitzung hochgeladen wurden.|  
|**DownloadedCommands**|**int**|Anzahl von Befehlen, die während der Agentsitzung heruntergeladen wurden.|  
|**ErrorMessages**|**int**|Anzahl von Fehlermeldungen, die während der Agentsitzung generiert wurden.|  
|**ErrorID**|**int**|ID des aufgetretenen Fehlers.|  
|**PercentageDone**|**decimal**|Geschätzter prozentualer Anteil an der Gesamtzahl von Änderungen, die bereits in einer aktiven Sitzung zugestellt wurden.|  
|**TimeRemaining**|**int**|Geschätzte verbleibende Zeit (in Sekunden) in einer aktiven Sitzung.|  
|**CurrentPhase**|**int**|Die aktuelle Phase einer aktiven Sitzung, die Folgendes sein kann:<br /><br /> **1** = Upload<br /><br /> **2** = herunterladen|  
|**LastMessage**|**nvarchar(500)**|Die letzte protokollierte Meldung des Merge-Agents während der Sitzung.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replmonitorhelpmergesession** wird zum Überwachen der Mergereplikation verwendet.  
  
 Bei der Ausführung auf dem Abonnenten **Sp_replmonitorhelpmergesession** gibt nur Informationen zu den letzten fünf Merge-agentsitzungen zurück.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Db_owner** oder **Replmonitor** festen Datenbankrolle, die für die Verteilungsdatenbank auf dem Verteiler oder für die Abonnementdatenbank auf dem Abonnenten ausführen kann **Sp_ Replmonitorhelpmergesession**.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
