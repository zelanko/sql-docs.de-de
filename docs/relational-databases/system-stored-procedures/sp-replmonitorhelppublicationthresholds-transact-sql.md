---
title: sp_replmonitorhelppublicationthresholds (T-SQL)
description: Beschreibt die gespeicherte Prozedur sp_replmonitorhelppublicationthresholds, die die für eine überwachte Veröffentlichung festgelegten Schwellenwert Metriken zurückgibt.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelppublicationthresholds
- sp_replmonitorhelppublicationthresholds_TSQL
helpviewer_keywords:
- sp_replmonitorhelppublicationthresholds
ms.assetid: d6b1aa4b-3369-4255-a892-c0e5cc9cb693
author: stevestein
ms.author: sstein
ms.openlocfilehash: d351db8ca696263f294f5a52f364d42ac48bad24
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "75320777"
---
# <a name="sp_replmonitorhelppublicationthresholds-transact-sql"></a>sp_replmonitorhelppublicationthresholds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Gibt die für eine überwachte Veröffentlichung festgelegten Schwellenwertmetriken zurück. Diese gespeicherte Prozedur, die zur Überwachung der Replikation verwendet wird, wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorhelppublicationthresholds [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'`Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'`Der Name der veröffentlichten Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'`Der Name der Veröffentlichung. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication_type = ] publication_type`Gibt an, ob der Typ der Veröffentlichung ist. *publication_type* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Transaktionsveröffentlichung.|  
|**1**|Momentaufnahmeveröffentlichung.|  
|**2**|Mergeveröffentlichung.|  
|NULL (Standard)|Die Replikation versucht, den Veröffentlichungstyp zu ermitteln.|  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**metric_id**|**int**|ID der Replikationsleistungsmetrik. Folgende Werte sind möglich.<br /><br /> **1ablauf** -überwacht den bevorstehenden Ablauf von Abonnements für Transaktions Veröffentlichungen.<br /><br /> **2latency** : überwacht die Leistung von Abonnements für Transaktions Veröffentlichungen.<br /><br /> **4mergeablauf** -überwacht den bevorstehenden Ablauf von Abonnements für Mergeveröffentlichungen.<br /><br /> **5mergeslowrunduration** : überwacht die Dauer von Mergesynchronisierungen über Verbindungen mit niedriger Bandbreite (DFÜ-Verbindungen).<br /><br /> **6mergefastrauunduration** : überwacht die Dauer von Mergesynchronisierungen über Verbindungen mit hoher Bandbreite (LAN-Verbindungen).<br /><br /> **7mergefastrauunspeed** : überwacht die Synchronisierungs Geschwindigkeit von Mergesynchronisierungen über Verbindungen mit hoher Bandbreite (LAN-Verbindungen).<br /><br /> **8mergeslowrunspeed** : überwacht die Synchronisierungs Geschwindigkeit von Mergesynchronisierungen über Verbindungen mit niedriger Bandbreite (DFÜ-Verbindungen).|  
|**title**|**sysname**|Der Name der Replikationsleistungsmetrik.|  
|**value**|**int**|Der Schwellenwert der Leistungsmetrik.|  
|**shouldalert**|**bit**|Gibt an, ob eine Warnung generiert werden soll, wenn die Metrik den definierten Schwellenwert für diese Veröffentlichung überschreitet. der Wert **1** gibt an, dass eine Warnung ausgelöst werden soll.|  
|**IsEnabled**|**bit**|Gibt an, ob die Überwachung für diese Replikations Leistungs Metrik für diese Veröffentlichung aktiviert ist. der Wert **1** gibt an, dass die Überwachung aktiviert ist.|  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_replmonitorhelppublicationthresholds** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Daten Bank Rolle **db_owner** oder **replmonitor** in der Verteilungs Datenbank können **sp_replmonitorhelppublicationthresholds**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmgesteuerte Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
