---
title: sysdbmaintplan_history (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdbmaintplan_history_TSQL
- sysdbmaintplan_history
dev_langs:
- TSQL
helpviewer_keywords:
- sysdbmaintplan_history system table
ms.assetid: 02d36f08-ac93-4463-bb59-284c5cd6ed04
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4470b6b5d1b30f5698bf588a04066c50bb4c7197
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68130453"
---
# <a name="sysdbmaintplan_history-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|Von den Datenbankwartungsplänen erstellte Verlaufssequenz.|  
|**plan_id**|**uniqueidentifier**|ID des Datenbankwartungsplans.|  
|**plan_name**|**sysname**|Name des Datenbankwartungsplans.|  
|**database_name**|**sysname**|Der Name der Datenbank, die dem Datenbank-Wartungsplan zugeordnet ist.|  
|**server_name**|**sysname**|Systemname.|  
|**aktiv**|**nvarchar(128)**|Die vom Datenbankwartungsplan durchgeführte Aktivität (z. B. Transaktionsprotokoll sichern usw.).|  
|**succeeded**|**bit**|**0** = erfolgreich **1** = Fehler|  
|**end_time**|**datetime**|Zeitpunkt, an dem die Aktion abgeschlossen wurde.|  
|**auf**|**int**|Erforderliche Zeitspanne, um die Aktion im Rahmen des Datenbankwartungsplans abzuschließen.|  
|**start_time**|**datetime**|Zeitpunkt, an dem die Aktion gestartet wurde.|  
|**error_number**|**int**|Fehlernummer, die bei einem Fehler gemeldet wird.|  
|**Nachricht**|**nvarchar(512)**|Von **sqlmaint**generierte Meldung.|  
  
  
