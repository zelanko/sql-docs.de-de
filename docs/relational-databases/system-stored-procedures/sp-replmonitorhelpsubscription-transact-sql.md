---
title: sp_replmonitorhelpsubscription (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 845b9bc59b2232dfa6760087c4a18af84a3c65b7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68764351"
---
# <a name="sp_replmonitorhelpsubscription-transact-sql"></a>sp_replmonitorhelpsubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt die aktuellen Statusinformationen für Abonnements zurück, die zu einer oder mehreren Veröffentlichungen auf dem Verleger gehören. Dabei wird eine Zeile für jedes zurückgegebene Abonnement zurückgegeben. Diese gespeicherte Prozedur, die zur Überwachung der Replikation verwendet wird, wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @publisher = ] 'publisher'`Der Name des Verlegers, dessen Status überwacht wird. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Wenn der Wert **null**ist, werden Informationen für alle Verleger zurückgegeben, die den Verteiler verwenden.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der veröffentlichten Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Lautet der Wert NULL, werden Informationen für alle veröffentlichten Datenbanken auf dem Verleger zurückgegeben.  
  
`[ @publication = ] 'publication'`Der Name der zu überwachenden Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @publication_type = ] publication_type`Gibt an, ob der Typ der Veröffentlichung ist. *publication_type* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|**0**|Transaktionsveröffentlichung.|  
|**1**|Momentaufnahmeveröffentlichung.|  
|**2**|Mergeveröffentlichung.|  
|NULL (Standard)|Die Replikation versucht, den Veröffentlichungstyp zu ermitteln.|  
  
`[ @mode = ] mode`Der Filter Modus, der beim Zurückgeben von Abonnement Überwachungsinformationen verwendet werden soll. der *Modus* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0** (Standardwert)|Gibt alle Abonnements zurück.|  
|**1**|Gibt nur Abonnements mit Fehlern zurück.|  
|**2**|Gibt nur Abonnements zurück, die Schwellenwertwarnungen generiert haben.|  
|**3**|Gibt nur Abonnements zurück, die entweder Fehler aufweisen oder Schwellenwertwarnungen generiert haben.|  
|**4**|Gibt die 25 häufigsten Abonnements zurück.|  
|**5**|Gibt die 50 Abonnements zurück, die die schlechteste Leistung aufweisen.|  
|**6**|Gibt nur Abonnements zurück, für die zurzeit eine Synchronisierung im Gange ist.|  
|**7**|Gibt nur Abonnements zurück, für die zurzeit keine Synchronisierung im Gange ist.|  
  
`[ @topnum = ] topnum`Beschränkt das Resultset auf die angegebene Anzahl von Abonnements am Anfang der zurückgegebenen Daten. *topnum* ist vom Datentyp **int**und hat keinen Standardwert.  
  
`[ @exclude_anonymous = ] exclude_anonymous`Gibt an, ob anonyme Pullabonnements aus dem Resultset ausgeschlossen werden. *exclude_anonymous* ist vom Typ **Bit**. der Standardwert ist **0**. der Wert **1** bedeutet, dass anonyme Abonnements ausgeschlossen werden und der Wert **0** bedeutet, dass Sie eingeschlossen werden.  
  
`[ @refreshpolicy = ] refreshpolicy`Nur interne Verwendung.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**status**|**int**|Überprüft den Status aller Replikations-Agents, die der Veröffentlichung zugeordnet sind, und gibt den höchsten gefundenen Status in der folgenden Reihenfolge zurück:<br /><br /> **6** = fehlgeschlagen<br /><br /> **5** = wird wiederholt<br /><br /> **2** = beendet<br /><br /> **4** = im Leerlauf<br /><br /> **3** = in Bearbeitung<br /><br /> **1** = gestartet|  
|**davor**|**int**|Warnung bezüglich des maximalen Schwellenwerts, die von einem zur Veröffentlichung gehörenden Abonnement generiert wird. Dies kann das Ergebnis des logischen OR-Vorgangs mit mindestens einem der folgenden Werte sein.<br /><br /> **1** = Ablauf: ein Abonnement für eine Transaktions Veröffentlichung wurde nicht innerhalb des Schwellenwerts für die Beibehaltungs Dauer synchronisiert.<br /><br /> **2** = Latenz: die Zeit, die zum Replizieren von Daten von einem transaktionalen Verleger auf den Abonnenten benötigt wird, überschreitet den Schwellenwert (in Sekunden).<br /><br /> **4** = mergeablauf: ein Abonnement für eine Mergeveröffentlichung wurde nicht innerhalb des Schwellenwerts für die Beibehaltungs Dauer synchronisiert.<br /><br /> **8** = mergefastrauunduration: die Zeit, die zum Abschließen der Synchronisierung eines Mergeabonnements benötigt wird, überschreitet den Schwellenwert über eine schnelle Netzwerkverbindung (in Sekunden).<br /><br /> **16** = mergeslowrunduration: die Zeit für die Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert über eine langsame oder DFÜ-Netzwerkverbindung (in Sekunden).<br /><br /> **32** = mergefastrauunspeed-die Übermittlungs Rate für Zeilen während der Synchronisierung eines Mergeabonnements konnte den Schwellenwert (in Zeilen pro Sekunde) über eine schnelle Netzwerkverbindung nicht aufrechterhalten.<br /><br /> **64** = mergeslowrunspeed-die Übermittlungs Rate für Zeilen während der Synchronisierung eines Mergeabonnements konnte den Schwellenwert (in Zeilen pro Sekunde) über eine langsame oder DFÜ-Netzwerkverbindung nicht aufrechterhalten.|  
|**Abonnenten**|**sysname**|Der Name des Abonnenten.|  
|**subscriber_db**|**sysname**|Der Name der für das Abonnement verwendeten Datenbank.|  
|**publisher_db**|**sysname**|Der Name der Veröffentlichungsdatenbank.|  
|**ung**|**sysname**|Der Name einer Veröffentlichung.|  
|**publication_type**|**int**|Der Veröffentlichungstyp. die folgenden Werte sind möglich:<br /><br /> **0** = Transaktions Veröffentlichung<br /><br /> **1** = Momentaufnahme Veröffentlichung<br /><br /> **2** = Mergeveröffentlichung|  
|**Untertyp**|**int**|Der Abonnementtyp, der einen der folgenden Werte haben kann:<br /><br /> **0** = Push<br /><br /> **1** = Pull<br /><br /> **2** = anonym|  
|**Schleifen**|**int**|Die längste Latenzzeit (in Sekunden) für Datenänderungen, die vom Protokolllese-Agent oder vom Verteilungs-Agent für eine Transaktionsveröffentlichung weitergegeben werden.|  
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
|**mergeconnectiontype**|**int**|Die beim Synchronisieren eines Abonnements auf eine Mergeveröffentlichung verwendete Verbindung, die einen der folgenden Werte haben kann:<br /><br /> **1** = LAN (Local Area Network)<br /><br /> **2** = DFÜ-Netzwerkverbindung<br /><br /> **3** = Websynchronisierung.|  
|**mergePerformance**|**int**|Die Leistung der letzten Synchronisierung im Vergleich zu allen Synchronisierungen des Abonnements. Sie ergibt sich aus der Übermittlungsrate der letzten Synchronisierung dividiert durch den Durchschnitt aller vorhergegangenen Übermittlungsraten.|  
|**mergerunspeed**|**float**|Die Übermittlungsrate der letzten Synchronisierung des Abonnements.|  
|**mergerunduration**|**int**|Der Zeitraum für den Abschluss der letzten Synchronisierung des Abonnements.|  
|**monitorranking**|**int**|Der Rangfolgenwert, der zur Sortierung der Abonnements im Resultset verwendet wird. Er kann folgende Werte haben:<br /><br /> Für eine Transaktionsveröffentlichung:<br /><br /> **60** = Fehler<br /><br /> **56** = Warnung: Leistungs kritisch<br /><br /> **52** = Warnung: läuft demnächst ab oder abgelaufen<br /><br /> **50** = Warnung: Abonnement nicht initialisiert<br /><br /> **40** = fehlerhafter Befehl wird wiederholt<br /><br /> **30** = wird nicht ausgeführt (Erfolg)<br /><br /> **20** = wird ausgeführt (wird gestartet, wird ausgeführt oder im Leerlauf)<br /><br /> Für eine Mergeveröffentlichung:<br /><br /> **60** = Fehler<br /><br /> **56** = Warnung: Leistungs kritisch<br /><br /> **54** = Warnung: langer Merge<br /><br /> **52** = Warnung: läuft demnächst ab<br /><br /> **50** = Warnung: Abonnement nicht initialisiert<br /><br /> **40** = fehlerhafter Befehl wird wiederholt<br /><br /> **30** = wird ausgeführt (wird gestartet, wird ausgeführt oder im Leerlauf)<br /><br /> **20** = wird nicht ausgeführt (Erfolg)|  
|**distributionagentjobid**|**Binary (16)**|ID des Verteilungs-Agent-Auftrags für Abonnements auf eine Transaktionsveröffentlichung.|  
|**mergeagentjobid**|**Binary (16)**|ID des Merge-Agent-Auftrags für Abonnements auf eine Mergeveröffentlichung.|  
|**distributionagentid**|**int**|ID des Verteilungs-Agent-Auftrags für das Abonnement.|  
|**distributionagentprofileid**|**int**|ID des vom Verteilungs-Agent verwendeten Agentprofils.|  
|**mergeagentid**|**int**|ID des Merge-Agentauftrags für das Abonnement.|  
|**mergeagentprofileid**|**int**|ID des vom Merge-Agent verwendeten Agentprofils.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_replmonitorhelpsubscription** wird bei allen Replikations Typen verwendet.  
  
 **sp_replmonitorhelpsubscription** ordnet das Resultset auf Grundlage des schwere Grads des Status des Abonnements an, das durch den Wert von *monitorrang*bestimmt wird. So werden z. B. Zeilen für alle Abonnements, die einen Fehlerzustand aufweisen, oberhalb der Zeilen für Abonnements einsortiert, die einen Warnungsstatus aufweisen.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Daten Bank Rolle **db_owner** oder **replmonitor** in der Verteilungs Datenbank können **sp_replmonitorhelpsubscription**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmgesteuerte Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
