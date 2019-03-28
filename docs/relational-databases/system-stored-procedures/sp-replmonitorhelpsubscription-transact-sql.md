---
title: Sp_replmonitorhelpsubscription (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelpsubscription_TSQL
- sp_replmonitorhelpsubscription
helpviewer_keywords:
- sp_replmonitorhelpsubscription
ms.assetid: a681b2db-c82d-4624-a10c-396afb0ac42f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 92cd44dcc30a0843409c908cb3cc3a76276519aa
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528202"
---
# <a name="spreplmonitorhelpsubscription-transact-sql"></a>sp_replmonitorhelpsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Gibt die aktuellen Statusinformationen für Abonnements zurück, die zu einer oder mehreren Veröffentlichungen auf dem Verleger gehören. Dabei wird eine Zeile für jedes zurückgegebene Abonnement zurückgegeben. Diese gespeicherte Prozedur, die zur Überwachung der Replikation verwendet wird, wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorhelpsubscription [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publisher_db' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @mode = ] mode ]  
    [ , [ @topnum = ] topnum ]   
    [ , [ @exclude_anonymous = ] exclude_anonymous ]   
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Ist der Name des Verlegers, dessen Status überwacht wird. *Publisher* ist **Sysname**, hat den Standardwert NULL. Wenn **null**, Informationen zu allen Verlegern, die die Verwendung des Verteilers zurückgegeben.  
  
`[ @publisher_db = ] 'publisher_db'` Ist der Name der veröffentlichten Datenbank. *Publisher_db* ist **Sysname**, hat den Standardwert NULL. Lautet der Wert NULL, werden Informationen für alle veröffentlichten Datenbanken auf dem Verleger zurückgegeben.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, der überwacht wird. *Veröffentlichung* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @publication_type = ] publication_type` Wenn der Typ der Veröffentlichung. *Publication_type* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Transaktionsveröffentlichung.|  
|**1**|Momentaufnahmeveröffentlichung.|  
|**2**|Mergeveröffentlichung.|  
|NULL (Standard)|Die Replikation versucht, den Veröffentlichungstyp zu ermitteln.|  
  
`[ @mode = ] mode` Der Filterungsmodus, verwenden Sie bei der Rückgabe von Abonnements, die Informationen überwachen. *Modus* ist **Int**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0** (Standardwert)|Gibt alle Abonnements zurück.|  
|**1**|Gibt nur Abonnements mit Fehlern zurück.|  
|**2**|Gibt nur Abonnements zurück, die Schwellenwertwarnungen generiert haben.|  
|**3**|Gibt nur Abonnements zurück, die entweder Fehler aufweisen oder Schwellenwertwarnungen generiert haben.|  
|**4**|Die obersten 25 schlechteste Leistung Abonnements zurück.|  
|**5**|Gibt die 50 Abonnements zurück, die die schlechteste Leistung aufweisen.|  
|**6**|Gibt nur Abonnements zurück, für die zurzeit eine Synchronisierung im Gange ist.|  
|**7**|Gibt nur Abonnements zurück, für die zurzeit keine Synchronisierung im Gange ist.|  
  
`[ @topnum = ] topnum` Schränkt das Resultset auf nur die angegebene Anzahl von Abonnements am Anfang der zurückgegebenen Daten. *Topnum* ist **Int**, hat keinen Standardwert.  
  
`[ @exclude_anonymous = ] exclude_anonymous` Ist, ob anonyme Pullabonnements aus dem Resultset ausgeschlossen werden. *Exclude_anonymous* ist **Bit**, hat den Standardwert **0**; Wert **1** bedeutet, dass anonyme Abonnements ausgeschlossen werden und der Wert des **0**  bedeutet, dass sie enthalten sind.  
  
`[ @refreshpolicy = ] refreshpolicy` Nur interne Verwendung.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**status**|**int**|Überprüft den Status aller Replikations-Agents, die der Veröffentlichung zugeordnet sind, und gibt den höchsten gefundenen Status in der folgenden Reihenfolge zurück:<br /><br /> **6** = Fehler<br /><br /> **5** = wird wiederholt<br /><br /> **2** = beendet<br /><br /> **4** = im Leerlauf<br /><br /> **3** = wird ausgeführt<br /><br /> **1** = gestartet|  
|**warning**|**int**|Warnung bezüglich des maximalen Schwellenwerts, die von einem zur Veröffentlichung gehörenden Abonnement generiert wird. Dies kann das Ergebnis des logischen OR-Vorgangs mit mindestens einem der folgenden Werte sein.<br /><br /> **1** = Expiration - ein Abonnement für eine transaktionsveröffentlichung wurde nicht innerhalb der Schwellenwerts für die Beibehaltungsdauer synchronisiert.<br /><br /> **2** = Latency - die Zeitdauer für die Replikation von Daten von einem Transaktionsverleger auf den Abonnenten überschreitet den Schwellenwert in Sekunden.<br /><br /> **4** = Mergeexpiration - ein Abonnement für eine Mergeveröffentlichung wurde nicht innerhalb der Schwellenwerts für die Beibehaltungsdauer synchronisiert.<br /><br /> **8** = Mergefastrunduration - die Zeit zum Abschließen der Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert in Sekunden an, über eine schnelle Netzwerkverbindung.<br /><br /> **16** = Mergeslowrunduration – die Zeit zum Abschließen der Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert in Sekunden an, über eine langsame oder DFÜ Netzwerkverbindung.<br /><br /> **32** = Mergefastrunspeed - die Übermittlungsrate für Zeilen während der Synchronisierung eines Mergeabonnements konnte die Rate Schwellenwert in Zeilen pro Sekunde, über eine schnelle Netzwerkverbindung zu verwalten.<br /><br /> **64** = Mergeslowrunspeed - die Übermittlungsrate für Zeilen während der Synchronisierung eines Mergeabonnements konnte die Rate Schwellenwert in Zeilen pro Sekunde, über eine langsame oder DFÜ Netzwerkverbindung zu verwalten.|  
|**subscriber**|**sysname**|Der Name des Abonnenten.|  
|**subscriber_db**|**sysname**|Der Name der für das Abonnement verwendeten Datenbank.|  
|**publisher_db**|**sysname**|Der Name der Veröffentlichungsdatenbank.|  
|**publication**|**sysname**|Ist der Name einer Veröffentlichung.|  
|**publication_type**|**int**|Ist der Typ der Veröffentlichung, die der folgenden Werte sind möglich:<br /><br /> **0** = transaktionsveröffentlichung<br /><br /> **1** = momentaufnahmeveröffentlichung<br /><br /> **2** = Mergeveröffentlichung|  
|**subtype**|**int**|Der Abonnementtyp, der einen der folgenden Werte haben kann:<br /><br /> **0** = Push<br /><br /> **1** = Pull<br /><br /> **2** = anonym|  
|**latency**|**int**|Die längste Latenzzeit (in Sekunden) für Datenänderungen, die vom Protokolllese-Agent oder vom Verteilungs-Agent für eine Transaktionsveröffentlichung weitergegeben werden.|  
|**latencythreshold**|**int**|Die maximale Latenzzeit für die Transaktionsveröffentlichung, bei deren Überschreiten eine Warnung ausgegeben wird.|  
|**agentnotrunning**|**int**|Der Zeitraum (in Stunden), während dem der Agent nicht ausgeführt wird.|  
|**agentnotrunningthreshold**|**int**|Der Zeitraum (in Stunden), während dem der Agent nicht ausgeführt und bei dessen Erreichen eine Warnung ausgegeben wird.|  
|**timetoexpiration**|**int**|Der Zeitraum (in Stunden), an dessen Ende ein Abonnement abläuft, falls es nicht synchronisiert wird.|  
|**expirationthreshold**|**int**|Die Zeit (in Stunden) vor dem Ablaufen eines Abonnements, zu der eine entsprechende Warnmeldung ausgegeben wird.|  
|**last_distsync**|**datetime**|Der datetime-Wert der letzten Ausführung des Verteilungs-Agents.|  
|**distribution_agentname**|**sysname**|Der Name des Verteilungs-Agentauftrags für das Abonnement auf eine Transaktionsveröffentlichung.|  
|**mergeagentname**|**sysname**|Der Name des Merge-Agent-Auftrags für das Abonnement auf eine Mergeveröffentlichung.|  
|**mergesubscriptionfriendlyname**|**sysname**|Der für das Abonnement angegebene angezeigte Name.|  
|**mergeagentlocation**|**sysname**|Der Name des Servers, auf dem der Merge-Agent ausgeführt wird.|  
|**mergeconnectiontype**|**int**|Die beim Synchronisieren eines Abonnements auf eine Mergeveröffentlichung verwendete Verbindung, die einen der folgenden Werte haben kann:<br /><br /> **1** = des lokalen Netzwerks (LAN)<br /><br /> **2** = DFÜ-Netzwerkverbindung<br /><br /> **3** = websynchronisierung.|  
|**mergePerformance**|**int**|Die Leistung der letzten Synchronisierung im Vergleich zu allen Synchronisierungen des Abonnements. Sie ergibt sich aus der Übermittlungsrate der letzten Synchronisierung dividiert durch den Durchschnitt aller vorhergegangenen Übermittlungsraten.|  
|**mergerunspeed**|**float**|Die Übermittlungsrate der letzten Synchronisierung des Abonnements.|  
|**mergerunduration**|**int**|Der Zeitraum für den Abschluss der letzten Synchronisierung des Abonnements.|  
|**monitorranking**|**int**|Der Rangfolgenwert, der zur Sortierung der Abonnements im Resultset verwendet wird. Er kann folgende Werte haben:<br /><br /> Für eine Transaktionsveröffentlichung:<br /><br /> **60** = Fehler<br /><br /> **56** = Warnung: Leistung im kritischen Bereich<br /><br /> **52** = Warnung: läuft demnächst ab oder abgelaufen<br /><br /> **50** = Warnung: Abonnement nicht initialisiert<br /><br /> **40** = fehlerhafter Befehl wird wiederholt<br /><br /> **30** = wird nicht ausgeführt (Erfolg)<br /><br /> **20** = wird ausgeführt (wird gestartet, ausgeführt oder im Leerlauf)<br /><br /> Für eine Mergeveröffentlichung:<br /><br /> **60** = Fehler<br /><br /> **56** = Warnung: Leistung im kritischen Bereich<br /><br /> **54** = Warnung: langer Mergevorgang<br /><br /> **52** = Warnung: läuft demnächst ab<br /><br /> **50** = Warnung: Abonnement nicht initialisiert<br /><br /> **40** = fehlerhafter Befehl wird wiederholt<br /><br /> **30** = wird ausgeführt (wird gestartet, ausgeführt oder im Leerlauf)<br /><br /> **20** = wird nicht ausgeführt (Erfolg)|  
|**distributionagentjobid**|**binary(16)**|ID des Verteilungs-Agent-Auftrags für Abonnements auf eine Transaktionsveröffentlichung.|  
|**mergeagentjobid**|**binary(16)**|ID des Merge-Agent-Auftrags für Abonnements auf eine Mergeveröffentlichung.|  
|**distributionagentid**|**int**|ID des Verteilungs-Agent-Auftrags für das Abonnement.|  
|**distributionagentprofileid**|**int**|ID des vom Verteilungs-Agent verwendeten Agentprofils.|  
|**mergeagentid**|**int**|ID des Merge-Agentauftrags für das Abonnement.|  
|**mergeagentprofileid**|**int**|ID des vom Merge-Agent verwendeten Agentprofils.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **Sp_replmonitorhelpsubscription** wird für alle Replikationstypen verwendet.  
  
 **Sp_replmonitorhelpsubscription** sortiert das Resultset auf Grundlage des Schweregrads des Status des Abonnements, die durch den Wert, der bestimmt wird *Monitorranking*. So werden z. B. Zeilen für alle Abonnements, die einen Fehlerzustand aufweisen, oberhalb der Zeilen für Abonnements einsortiert, die einen Warnungsstatus aufweisen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der **Db_owner** oder **Replmonitor** -Datenbankrolle in der Verteilungsdatenbank kann ausführen **Sp_replmonitorhelpsubscription**.  
  
## <a name="see-also"></a>Siehe auch  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
