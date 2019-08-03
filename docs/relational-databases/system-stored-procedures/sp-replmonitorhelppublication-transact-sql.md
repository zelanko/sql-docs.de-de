---
title: sp_replmonitorhelppublication (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 8dc952f03ea2538412c864e1a9e9b228bf3ca877
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771212"
---
# <a name="spreplmonitorhelppublication-transact-sql"></a>sp_replmonitorhelppublication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt aktuelle Statusinformationen für mindestens eine Veröffentlichung auf dem Verleger zurück. Diese gespeicherte Prozedur, die zur Überwachung der Replikation verwendet wird, wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
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
`[ @publisher = ] 'publisher'`Der Name des Verlegers, dessen Status überwacht wird. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn der Wert **null**ist, werden Informationen für alle Verleger zurückgegeben, die den Verteiler verwenden.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der veröffentlichten Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Lautet der Wert NULL, werden Informationen für alle veröffentlichten Datenbanken auf dem Verleger zurückgegeben.  
  
`[ @publication = ] 'publication'`Der Name der zu überwachenden Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @publication_type = ] publication_type`Gibt an, ob der Typ der Veröffentlichung ist. *publication_type* ist vom Datentyp **int**und kann einen der folgenden Werte aufweisen.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Transaktionsveröffentlichung.|  
|**1**|Momentaufnahmeveröffentlichung.|  
|**2**|Mergeveröffentlichung.|  
|NULL (Standard)|Replikationsversuche zum Bestimmen des Veröffentlichungstyps.|  
  
`[ @refreshpolicy = ] refreshpolicy`Nur interne Verwendung.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**publisher_db**|**sysname**|Der Name des Verlegers.|  
|**publication**|**sysname**|Der Name einer Veröffentlichung.|  
|**publication_type**|**int**|Der Veröffentlichungstyp. Die folgenden Werte sind möglich.<br /><br /> **0** = Transaktions Veröffentlichung<br /><br /> **1** = Momentaufnahme Veröffentlichung<br /><br /> **2** = Mergeveröffentlichung|  
|**status**|**int**|Der maximale Status aller Replikations-Agents für die Veröffentlichung. Die folgenden Werte sind möglich.<br /><br /> **1** = gestartet<br /><br /> **2** = erfolgreich<br /><br /> **3** = in Bearbeitung<br /><br /> **4** = im Leerlauf<br /><br /> **5** = wird wiederholt<br /><br /> **6** = fehlgeschlagen|  
|**davor**|**int**|Warnung bezüglich des maximalen Schwellenwerts, die von einem zur Veröffentlichung gehörenden Abonnement generiert wird. Dies kann das Ergebnis des logischen OR-Vorgangs mit mindestens einem der folgenden Werte sein.<br /><br /> **1** = Ablauf: ein Abonnement für eine Transaktions Veröffentlichung wurde nicht innerhalb des Schwellenwerts für die Beibehaltungs Dauer synchronisiert.<br /><br /> **2** = Latenz: die Zeit, die zum Replizieren von Daten von einem transaktionalen Verleger auf den Abonnenten benötigt wird, überschreitet den Schwellenwert (in Sekunden).<br /><br /> **4** = mergeablauf: ein Abonnement für eine Mergeveröffentlichung wurde nicht innerhalb des Schwellenwerts für die Beibehaltungs Dauer synchronisiert.<br /><br /> **8** = mergefastrauunduration: die Zeit, die zum Abschließen der Synchronisierung eines Mergeabonnements benötigt wird, überschreitet den Schwellenwert über eine schnelle Netzwerkverbindung (in Sekunden).<br /><br /> **16** = mergeslowrunduration: die Zeit für die Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert über eine langsame oder DFÜ-Netzwerkverbindung (in Sekunden).<br /><br /> **32** = mergefastrauunspeed-die Übermittlungs Rate für Zeilen während der Synchronisierung eines Mergeabonnements konnte den Schwellenwert (in Zeilen pro Sekunde) über eine schnelle Netzwerkverbindung nicht aufrechterhalten.<br /><br /> **64** = mergeslowrunspeed-die Übermittlungs Rate für Zeilen während der Synchronisierung eines Mergeabonnements konnte den Schwellenwert (in Zeilen pro Sekunde) über eine langsame oder DFÜ-Netzwerkverbindung nicht aufrechterhalten.|  
|**worst_latency**|**int**|Die längste Latenzzeit (in Sekunden) für Datenänderungen, die vom Protokolllese-Agent oder vom Verteilungs-Agent für eine Transaktionsveröffentlichung weitergegeben werden.|  
|**best_latency**|**int**|Die kürzeste Latenzzeit (in Sekunden) für Datenänderungen, die vom Protokolllese-Agent oder vom Verteilungs-Agent für eine Transaktionsveröffentlichung weitergegeben werden.|  
|**average_latency**|**int**|Die durchschnittliche Latenzzeit (in Sekunden) für Datenänderungen, die vom Protokolllese-Agent oder vom Verteilungs-Agent für eine Transaktionsveröffentlichung weitergegeben werden.|  
|**last_distsync**|**datetime**|Der letzte mit datetime angegebene Zeitpunkt, zu dem der Verteilungs-Agent ausgeführt wurde.|  
|**retention**|**int**|Der Beibehaltungszeitraum für die Veröffentlichung.|  
|**latkocythreshold**|**int**|Der Schwellenwert für die Latenzzeit, der für die Transaktionsveröffentlichung festgelegt ist.|  
|**expirationthreshold**|**int**|Der für die Veröffentlichung festgelegte Ablaufschwellenwert, falls es sich um eine Mergeveröffentlichung handelt.|  
|**agentnotrunningthreshold**|**int**|Der festgelegte Schwellenwert für den längsten Zeitraum, für den ein Agent nicht ausgeführt wird.|  
|**subscriptioncount**|**int**|Die Anzahl von Abonnements für eine Veröffentlichung.|  
|**runningdistagentcount**|**int**|Die Anzahl der Verteilungs-Agents, die für die Veröffentlichung ausgeführt werden.|  
|**snapshot_agentname**|**sysname**|Der Name des Auftrags des Momentaufnahme-Agents für die Veröffentlichung.|  
|**logreader_agentname**|**sysname**|Der Name des Protokolllese-Agent-Auftrags für die Transaktionsveröffentlichung.|  
|**qreader_agentname**|**sysname**|Der Name des Warteschlangenlese-Agent-Auftrags für eine Transaktionsveröffentlichung, die verzögerte Updates über eine Warteschlange unterstützt.|  
|**worst_runspeedPerf**|**int**|Die längste Synchronisierungszeit für die Mergeveröffentlichung.|  
|**best_runspeedPerf**|**int**|Die kürzeste Synchronisierungszeit für die Mergeveröffentlichung.|  
|**average_runspeedPerf**|**int**|Die durchschnittliche Synchronisierungszeit für die Mergeveröffentlichung.|  
|**retention_period_unit**|**int**|Die Einheit, die zum Ausdrücken der *Beibehaltung*verwendet wird.|  
|**publisher**|**sysname**|Der Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, die zum Veröffentlichen der Veröffentlichung verwendet werden soll.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_replmonitorhelppublication** wird für alle Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Daten Bank Rolle **db_owner** oder **replmonitor** in der Verteilungs Datenbank können **sp_replmonitorhelppublication**ausführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
