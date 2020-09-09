---
title: sp_replmonitorchangepublicationthreshold (T-SQL)
description: Beschreibt die gespeicherte Prozedur sp_replmonitorchangepublicationthreshold, mit der die Schwellenwert Metrik für die Überwachung für eine Veröffentlichung geändert wird.
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorchangepublicationthreshold_TSQL
- sp_replmonitorchangepublicationthreshold
helpviewer_keywords:
- sp_replmonitorchangepublicationthreshold
ms.assetid: 2c3615d8-4a1a-4162-b096-97aefe6ddc16
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6114d52b0db23d04c3b8cf001b0881dbc38844a6
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543150"
---
# <a name="sp_replmonitorchangepublicationthreshold-transact-sql"></a>sp_replmonitorchangepublicationthreshold (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Ändert die Schwellenwertmetrik für die Überwachung einer Veröffentlichung. Diese gespeicherte Prozedur, die zur Überwachung der Replikation verwendet wird, wird auf dem Verteiler für die Verteilungsdatenbank ausgeführt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_replmonitorchangepublicationthreshold [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
    [ , [ @publication_type = ] publication_type ]   
    [ , [ @metric_id = ] metric_id ]   
    [ , [ @thresholdmetricname = ] 'thresholdmetricname'   
    [ , [ @value = ] value ]   
    [ , [ @shouldalert = ] shouldalert ]   
    [ , [ @mode = ] mode ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @publisher = ] 'publisher'` Der Name des Verlegers. *Publisher* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publisher_db = ] 'publisher_db'` Der Name der veröffentlichten Datenbank. *publisher_db* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication = ] 'publication'` Der Name der Veröffentlichung, für die die Überwachungs Schwellenwert Attribute geändert werden. *Publication* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @publication_type = ] publication_type` Gibt an, ob der Typ der Veröffentlichung ist. *publication_type* ist vom Datentyp **int**. die folgenden Werte sind möglich:  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Transaktionsveröffentlichung.|  
|**1**|Momentaufnahmeveröffentlichung.|  
|**2**|Mergeveröffentlichung.|  
|NULL (Standard)|Replikationsversuche zum Bestimmen des Veröffentlichungstyps.|  
  
`[ @metric_id = ] metric_id` Die ID der Schwellenwert Metrik für die Veröffentlichung, die geändert wird. *metric_id* ist vom Datentyp **int**und hat den Standardwert NULL. die folgenden Werte sind möglich:  
  
|Wert|Metrikname|  
|-----------|-----------------|  
|**1**|**expiration** - überwacht den bevorstehenden Ablauf von Abonnements für Transaktionsveröffentlichungen.|  
|**2**|**latency** - überwacht die Leistung von Abonnements für Transaktionsveröffentlichungen.|  
|**4**|**mergeexpiration** - überwacht den bevorstehenden Ablauf von Abonnements für Mergeveröffentlichungen.|  
|**5**|**mergeslowrunduration** : überwacht die Dauer von Mergesynchronisierungen über Verbindungen mit niedriger Bandbreite (DFÜ-Verbindungen).|  
|**6**|**mergefastrauunduration** : überwacht die Dauer von Mergesynchronisierungen über LAN-Verbindungen (Local Area Network) mit hoher Bandbreite.|  
|**7**|**mergefastrunspeed** - Überwachung der Synchronisierungsgeschwindigkeit von Mergesynchronisierungen über Verbindungen mit hoher Bandbreite (LAN-Verbindungen).|  
|**8**|**mergeslowrunspeed** : überwacht die Synchronisierungs Geschwindigkeit von Mergesynchronisierungen über Verbindungen mit niedriger Bandbreite (DFÜ-Verbindungen).|  
  
 Sie müssen entweder *metric_id* oder " *stammoldmetricname*" angeben. Wenn " *stammoldmetricname* " angegeben ist, sollte *metric_id* NULL sein.  
  
`[ @thresholdmetricname = ] 'thresholdmetricname'` Der Name der Schwellenwert Metrik für die Veröffentlichung, die geändert wird. " *stammoldmetricname* " ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Sie müssen entweder den *Namen* "" für "" und " *metric_id*" angeben. Wenn *metric_id* angegeben wird, sollte der Wert von "der *Name* der"  
  
`[ @value = ] value` Der neue Wert der Schwellenwert Metrik für die Veröffentlichung. der *Wert* ist vom Datentyp **int**und hat den Standardwert NULL. Wenn der Wert **null**ist, wird der Metrikwert nicht aktualisiert.  
  
`[ @shouldalert = ] shouldalert` Gibt an, ob eine Warnung generiert wird, wenn eine Schwellenwert Metrik für die Veröffentlichung erreicht wird der *Wert ist* " **Bit**", der Standardwert ist NULL. Der Wert **1** bedeutet, dass eine Warnung generiert wird, und der Wert **0** bedeutet, dass keine Warnung generiert wird.  
  
`[ @mode = ] mode` Ist, wenn die Schwellenwert Metrik für die Veröffentlichung aktiviert ist. der *Modus* ist vom Datentyp **tinyint**. der Standardwert ist **1**. Der Wert **1** bedeutet, dass die Überwachung dieser Metrik aktiviert ist und der Wert **2** bedeutet, dass die Überwachung dieser Metrik deaktiviert ist.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 **sp_replmonitorchangepublicationthreshold** wird bei allen Replikations Typen verwendet.  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Daten Bank Rolle **db_owner** oder **replmonitor** in der Verteilungs Datenbank können **sp_replmonitorchangepublicationthreshold**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Programmgesteuertes Überwachen der Replikation](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  
