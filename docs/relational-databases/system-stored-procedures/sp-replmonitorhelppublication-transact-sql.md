---
title: Sp_replmonitorhelppublication (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelppublication_TSQL
- sp_replmonitorhelppublication
helpviewer_keywords:
- sp_replmonitorhelppublication
ms.assetid: 7928c50c-617f-41c5-9e0f-4e42e8be55dc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 84fa72ff11ffb97d736dcd5ed194064367c3a5ba
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/03/2018
ms.locfileid: "52748333"
---
# <a name="spreplmonitorhelppublication-transact-sql"></a>sp_replmonitorhelppublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt aktuelle Statusinformationen für mindestens eine Veröffentlichung auf dem Verleger zurück. Diese gespeicherte Prozedur, die zum Überwachen der Replikation verwendet wird, wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorhelppublication [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db'   
    [ , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@publisher** = ] **'***publisher***'**  
 Der Name des Verlegers, dessen Status überwacht wird. *Publisher* ist **Sysname**, hat den Standardwert NULL. Wenn **null**, werden Informationen zu allen Verlegern, die die Verwendung des Verteilers zurückgegeben.  
  
 [ **@publisher_db** = ] **'***publisher_db***'**  
 Der Name der veröffentlichten Datenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL. Lautet der Wert NULL, werden Informationen für alle veröffentlichten Datenbanken auf dem Verleger zurückgegeben.  
  
 [ **@publication** =] **"***Veröffentlichung***"**  
 Der Name der Veröffentlichung, die überwacht wird. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL.  
  
 [ **@publication_type** =] *Publication_type*  
 Der Typ der Veröffentlichung. *Publication_type* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Transaktionsveröffentlichung.|  
|**1**|Momentaufnahmeveröffentlichung.|  
|**2**|Mergeveröffentlichung.|  
|NULL (Standard)|Replikationsversuche zum Bestimmen des Veröffentlichungstyps.|  
  
 [  **@refreshpolicy=** ] *Refreshpolicy*  
 Nur interne Verwendung.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**publisher_db**|**sysname**|Der Name des Verlegers.|  
|**Veröffentlichung**|**sysname**|Ist der Name einer Veröffentlichung.|  
|**publication_type**|**int**|Der Veröffentlichungstyp. Die folgenden Werte sind möglich.<br /><br /> **0** = transaktionsveröffentlichung<br /><br /> **1** = momentaufnahmeveröffentlichung<br /><br /> **2** = Mergeveröffentlichung|  
|**status**|**int**|Der maximale Status aller Replikations-Agents für die Veröffentlichung. Die folgenden Werte sind möglich.<br /><br /> **1** = gestartet<br /><br /> **2** = war erfolgreich<br /><br /> **3** = wird ausgeführt<br /><br /> **4** = im Leerlauf<br /><br /> **5** = wird wiederholt<br /><br /> **6** = Fehler|  
|**Warnung**|**int**|Warnung bezüglich des maximalen Schwellenwerts, die von einem zur Veröffentlichung gehörenden Abonnement generiert wird. Dies kann das Ergebnis des logischen OR-Vorgangs mit mindestens einem der folgenden Werte sein.<br /><br /> **1** = Expiration - ein Abonnement für eine transaktionsveröffentlichung wurde nicht innerhalb der Schwellenwerts für die Beibehaltungsdauer synchronisiert.<br /><br /> **2** = Latency - die Zeitdauer für die Replikation von Daten von einem Transaktionsverleger auf den Abonnenten überschreitet den Schwellenwert in Sekunden.<br /><br /> **4** = Mergeexpiration - ein Abonnement für eine Mergeveröffentlichung wurde nicht innerhalb der Schwellenwerts für die Beibehaltungsdauer synchronisiert.<br /><br /> **8** = Mergefastrunduration - die Zeit zum Abschließen der Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert in Sekunden an, über eine schnelle Netzwerkverbindung.<br /><br /> **16** = Mergeslowrunduration – die Zeit zum Abschließen der Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert in Sekunden an, über eine langsame oder DFÜ Netzwerkverbindung.<br /><br /> **32** = Mergefastrunspeed - die Übermittlungsrate für Zeilen während der Synchronisierung eines Mergeabonnements konnte die Rate Schwellenwert in Zeilen pro Sekunde, über eine schnelle Netzwerkverbindung zu verwalten.<br /><br /> **64** = Mergeslowrunspeed - die Übermittlungsrate für Zeilen während der Synchronisierung eines Mergeabonnements konnte die Rate Schwellenwert in Zeilen pro Sekunde, über eine langsame oder DFÜ Netzwerkverbindung zu verwalten.|  
|**worst_latency**|**int**|Die längste Latenzzeit (in Sekunden) für Datenänderungen, die vom Protokolllese-Agent oder vom Verteilungs-Agent für eine Transaktionsveröffentlichung weitergegeben werden.|  
|**best_latency**|**int**|Die kürzeste Latenzzeit (in Sekunden) für Datenänderungen, die vom Protokolllese-Agent oder vom Verteilungs-Agent für eine Transaktionsveröffentlichung weitergegeben werden.|  
|**average_latency**|**int**|Die durchschnittliche Latenzzeit (in Sekunden) für Datenänderungen, die vom Protokolllese-Agent oder vom Verteilungs-Agent für eine Transaktionsveröffentlichung weitergegeben werden.|  
|**last_distsync**|**datetime**|Der letzte mit datetime angegebene Zeitpunkt, zu dem der Verteilungs-Agent ausgeführt wurde.|  
|**Beibehaltungsdauer**|**int**|Der Beibehaltungszeitraum für die Veröffentlichung.|  
|**"LatencyThreshold"**|**int**|Der Schwellenwert für die Latenzzeit, der für die Transaktionsveröffentlichung festgelegt ist.|  
|**expirationthreshold**|**int**|Der für die Veröffentlichung festgelegte Ablaufschwellenwert, falls es sich um eine Mergeveröffentlichung handelt.|  
|**agentnotrunningthreshold**|**int**|Der festgelegte Schwellenwert für den längsten Zeitraum, für den ein Agent nicht ausgeführt wird.|  
|**subscriptioncount**|**int**|Die Anzahl von Abonnements für eine Veröffentlichung.|  
|**runningdistagentcount**|**int**|Die Anzahl der Verteilungs-Agents wird für die Veröffentlichung ausgeführt werden|  
|**snapshot_agentname**|**sysname**|Der Name des Auftrags des Momentaufnahme-Agents für die Veröffentlichung.|  
|**logreader_agentname**|**sysname**|Der Name des Protokolllese-Agent-Auftrags für die Transaktionsveröffentlichung.|  
|**qreader_agentname**|**sysname**|Der Name des Warteschlangenlese-Agent-Auftrags für eine Transaktionsveröffentlichung, die verzögerte Updates über eine Warteschlange unterstützt.|  
|**worst_runspeedPerf**|**int**|Die längste Synchronisierungszeit für die Mergeveröffentlichung.|  
|**best_runspeedPerf**|**int**|Die kürzeste Synchronisierungszeit für die Mergeveröffentlichung.|  
|**average_runspeedPerf**|**int**|Die durchschnittliche Synchronisierungszeit für die Mergeveröffentlichung.|  
|**retention_period_unit**|**int**|Ist die Einheit, die zum Ausdrücken von *Aufbewahrung*.|  
|**publisher**|**sysname**|Der Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, die zum Veröffentlichen der Veröffentlichung verwendet werden soll.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replmonitorhelppublication** wird für alle Replikationstypen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Db_owner** oder **Replmonitor** -Datenbankrolle in der Verteilungsdatenbank kann ausführen **Sp_replmonitorhelppublication**.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
