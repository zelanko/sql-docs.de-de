---
description: sp_replmonitorhelppublisher (Transact-SQL)
title: sp_replmonitorhelppublisher (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelppublisher_TSQL
- sp_replmonitorhelppublisher
helpviewer_keywords:
- sp_replmonitorhelppublisher
ms.assetid: 171501fe-4b74-4647-96c3-7691c777e01b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3bb6c758089b6089dfeb6b7a472a496931f6c929
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543128"
---
# <a name="sp_replmonitorhelppublisher-transact-sql"></a>sp_replmonitorhelppublisher (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Gibt aktuelle Statusinformationen für mindestens einen Verleger zurück, der einem Verteiler zugeordnet ist. Diese gespeicherte Prozedur, die zur Überwachung der Replikation verwendet wird, wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorhelppublisher [ [ @publisher = ] 'publisher' ]  
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name des Verlegers, dessen Status überwacht wird. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Bei NULL werden Informationen zu allen Verlegern zurückgegeben, die den Verteiler verwenden.  
  
`[ @refreshpolicy = ] refreshpolicy` Nur interne Verwendung.  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Der Name eines Verlegers.|  
|**distribution_db**|**sysname**|Der Name der Verteilungsdatenbank, die von einem bestimmten Verleger verwendet wird.|  
|**status**|**int**|Maximalstatus aller Replikations-Agents, die Veröffentlichungen auf diesem Verleger zugeordnet sind. Folgende Werte sind möglich.<br /><br /> **1** = gestartet<br /><br /> **2** = erfolgreich<br /><br /> **3** = in Bearbeitung<br /><br /> **4** = im Leerlauf<br /><br /> **5** = wird wiederholt<br /><br /> **6** = fehlgeschlagen|  
|**warning**|**int**|Warnung bezüglich des maximalen Schwellenwerts, die von einem Abonnement generiert wird, das zu einer Veröffentlichung auf diesem Verleger gehört. Dies kann das Ergebnis einer logischen OR-Operation mit mindestens einem der folgenden Werte sein.<br /><br /> **1** = Ablauf: ein Abonnement für eine Transaktions Veröffentlichung wurde nicht innerhalb des Schwellenwerts für die Beibehaltungs Dauer synchronisiert.<br /><br /> **2** = Latenz: die Zeit, die zum Replizieren von Daten von einem transaktionalen Verleger auf den Abonnenten benötigt wird, überschreitet den Schwellenwert (in Sekunden).<br /><br /> **4** = mergeablauf: ein Abonnement für eine Mergeveröffentlichung wurde nicht innerhalb des Schwellenwerts für die Beibehaltungs Dauer synchronisiert.<br /><br /> **8** = mergefastrauunduration: die Zeit, die zum Abschließen der Synchronisierung eines Mergeabonnements benötigt wird, überschreitet den Schwellenwert über eine schnelle Netzwerkverbindung (in Sekunden).<br /><br /> **16** = mergeslowrunduration: die Zeit für die Synchronisierung eines Mergeabonnements überschreitet den Schwellenwert über eine langsame oder DFÜ-Netzwerkverbindung (in Sekunden).<br /><br /> **32** = mergefastrauunspeed-die Übermittlungs Rate für Zeilen während der Synchronisierung eines Mergeabonnements konnte den Schwellenwert (in Zeilen pro Sekunde) über eine schnelle Netzwerkverbindung nicht aufrechterhalten.<br /><br /> **64** = mergeslowrunspeed-die Übermittlungs Rate für Zeilen während der Synchronisierung eines Mergeabonnements konnte den Schwellenwert (in Zeilen pro Sekunde) über eine langsame oder DFÜ-Netzwerkverbindung nicht aufrechterhalten.|  
|**publicationcount**|**int**|Die Anzahl der Veröffentlichungen, die zum Verleger gehören.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_replmonitorhelppublisher** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** auf dem Verteiler oder Mitglieder der festen Daten bankrollen **db_owner** oder **replmonitor** in der Verteilungs Datenbank können **sp_replmonitorhelppublisher**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
