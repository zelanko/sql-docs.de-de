---
title: sp_replmonitorhelpmergesession (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 305b7a0e2c9d83fe33a6d571198b205f7452ba44
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725689"
---
# <a name="sp_replmonitorhelpmergesession-transact-sql"></a>sp_replmonitorhelpmergesession (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt Informationen zu vergangenen Sitzungen für einen angegebenen Replikationsmerge-Agent zurück. Für jede Sitzung, die den Filterkriterien entspricht, wird dabei eine Zeile zurückgegeben. Diese gespeicherte Prozedur dient zum Überwachen der Mergereplikation. Sie wird beim Verteiler auf der Verteilungsbank oder beim Abonnenten auf der Abonnementdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @agent_name = ] 'agent_name'`Der Name des Agents. *agent_name* ist vom Datentyp **nvarchar (100)** und hat keinen Standardwert.  
  
`[ @hours = ] hours`Der Zeitraum (in Stunden), für den historische agentsitzungsinformationen zurückgegeben werden. *Hours* ist vom Datentyp **int**. die folgenden Bereiche sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|< **1,0**|Gibt Informationen zu vergangenen Agentausführungen (bis zu maximal 100 Ausführungen) zurück.|  
|**0** (Standardwert)|Gibt Informationen zu allen vergangenen Agentausführungen zurück.|  
|> **1,0**|Gibt Informationen zu Agent-Ausführungen zurück, die in der Anzahl der letzten *Stunden* aufgetreten sind.|  
  
`[ @session_type = ] session_type`Filtert das Resultset basierend auf dem Endzeit Ergebnis der Sitzung. *session_type* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**1** (Standard)|Agentsitzungen mit einem Neuversuch oder erfolgreichem Abschluss.|  
|**0**|Agentsitzungen mit einem Fehlerergebnis.|  
  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter wird verwendet, wenn **sp_replmonitorhelpmergesession** auf dem Abonnenten ausgeführt wird.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der Veröffentlichungs Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter wird verwendet, wenn **sp_replmonitorhelpmergesession** auf dem Abonnenten ausgeführt wird.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Dieser Parameter wird verwendet, wenn **sp_replmonitorhelpmergesession** auf dem Abonnenten ausgeführt wird.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**Session_id**|**int**|ID der Agentauftragssitzung.|  
|**Status**|**int**|Agenttestlauf-Status:<br /><br /> **1** = Start<br /><br /> **2** = erfolgreich<br /><br /> **3** = in Bearbeitung<br /><br /> **4** = im Leerlauf<br /><br /> **5** = Wiederholung<br /><br /> **6** = Fehler|  
|**StartTime**|**datetime**|Zeit-Agent-Auftrags Sitzung wurde gestartet.|  
|**EndTime**|**datetime**|Die Zeit-Agent-Auftrags Sitzung wurde abgeschlossen.|  
|**Dauer**|**int**|Kumulierte Dauer dieser Auftragssitzung in Sekunden.|  
|**UploadedCommands**|**int**|Anzahl von Befehlen, die während der Agentsitzung hochgeladen wurden.|  
|**DownloadedCommands**|**int**|Anzahl von Befehlen, die während der Agentsitzung heruntergeladen wurden.|  
|**ErrorMessages**|**int**|Anzahl von Fehlermeldungen, die während der Agentsitzung generiert wurden.|  
|**ErrorID**|**int**|ID des aufgetretenen Fehlers.|  
|**PercentageDone**|**decimal**|Geschätzter prozentualer Anteil an der Gesamtzahl von Änderungen, die bereits in einer aktiven Sitzung zugestellt wurden.|  
|**TimeRemaining**|**int**|Geschätzte verbleibende Zeit (in Sekunden) in einer aktiven Sitzung.|  
|**CurrentPhase**|**int**|Die aktuelle Phase einer aktiven Sitzung, die Folgendes sein kann:<br /><br /> **1** = hochladen<br /><br /> **2** = herunterladen|  
|**Last Message**|**nvarchar (500)**|Die letzte protokollierte Meldung des Merge-Agents während der Sitzung.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_replmonitorhelpmergesession** wird zum Überwachen der Mergereplikation verwendet.  
  
 Bei der Ausführung auf dem Abonnenten werden von **sp_replmonitorhelpmergesession** nur Informationen zu den letzten fünf Merge-Agent Sitzungen zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Daten Bank Rolle **db_owner** oder **replmonitor** in der Verteilungs Datenbank auf dem Verteiler oder der Abonnement Datenbank auf dem Abonnenten können **sp_replmonitorhelpmergesession**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmgesteuerte Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
