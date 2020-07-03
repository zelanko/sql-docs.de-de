---
title: sysabonnements (System Sicht) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- syssubscriptions_TSQL
- syssubscriptions
dev_langs:
- TSQL
helpviewer_keywords:
- syssubscriptions view
ms.assetid: c9613858-9512-43a9-aa53-7ee8064f064c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 043624acfb2eab1ea7c959c8c9221c9f252935dc
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881234"
---
# <a name="syssubscriptions-system-view-transact-sql"></a>syssubscriptions (Systemsicht) (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Die **sysabonnements** -Sicht macht Abonnement Informationen verfügbar. Diese Sicht wird in der distribution-Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Die eindeutige ID eines abonnierten Artikels.|  
|**srvid**|**smallint**|Die Server-ID des Abonnenten.|  
|**dest_db**|**sysname**|Der Name der Abonnement Datenbank.|  
|**status**|**tinyint**|Status des Abonnements:<br /><br /> **0** = inaktiv.<br /><br /> **1** = abonniert.<br /><br /> **2** = aktiv.|  
|**sync_type**|**tinyint**|Der Typ der Erstsynchronisierung:<br /><br /> **1** = automatisch.<br /><br /> **2** = keine.|  
|**login_name**|**sysname**|Der Anmeldename, der für die Verbindung mit dem Verleger zum Hinzufügen des Abonnements verwendet wird.|  
|**subscription_type**|**int**|Der Typ des Abonnements:<br /><br /> **0** = Push-der Verteilungs-Agent wird auf dem Verteiler ausgeführt.<br /><br /> **1** = Pull-der Verteilungs-Agent wird auf dem Abonnenten ausgeführt.|  
|**distribution_jobid**|**Binary (16)**|Gibt den zum Synchronisieren des Abonnements verwendeten Verteilungs-Agent-Auftrag an.|  
|**timestmap**|**timestamp**|Datum und Uhrzeit der Erstellung des Abonnements.|  
|**update_mode**|**tinyint**|Updatemodus:<br /><br /> **0** = schreibgeschützt.<br /><br /> **1** = sofortige Aktualisierung.|  
|**loopback_detection**|**bit**|Gilt für Abonnements, die Teil einer bidirektionalen Transaktionsreplikationstopologie sind. Bestimmt, ob der Verteilungs-Agent Transaktionen des Abonnenten zurück an den Abonnenten sendet:<br /><br /> **0** = sendet zurück.<br /><br /> **1** = sendet nicht zurück.|  
|**queued_reinit**|**bit**|Gibt an, ob der Artikel für die Initialisierung oder erneute Initialisierung markiert ist. Der Wert **1** gibt an, dass der abonnierte Artikel für die Initialisierung oder erneute Initialisierung markiert ist.|  
|**nosync_type**|**tinyint**|Der Typ der Abonnementinitialisierung:<br /><br /> **0** = automatisch (Momentaufnahme)<br /><br /> **1** = nur Replikations Unterstützung<br /><br /> **2** = mit Sicherung initialisieren<br /><br /> **3** = Initialisieren von der Protokoll Folge Nummer (Log Sequence Number, LSN)<br /><br /> Weitere Informationen finden Sie unter dem ** \@ sync_type** -Parameter von [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md).<br /><br /> **€** = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**srvname**|**sysname**|Den Namen des Abonnenten.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Replikations Tabellen &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Replikations Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [syssubscriptions &#40;Transact-SQL&#41;](../../relational-databases/system-tables/syssubscriptions-transact-sql.md)  
  
  
