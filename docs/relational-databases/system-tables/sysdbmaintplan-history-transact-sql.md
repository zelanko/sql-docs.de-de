---
description: sysdbmaintplan_history (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 473e98da465aa9952261ae3c57d77ab9b5d2629e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89517707"
---
# <a name="sysdbmaintplan_history-transact-sql"></a>sysdbmaintplan_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
 [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**sequence_id**|**int**|Von den Datenbankwartungsplänen erstellte Verlaufssequenz.|  
|**plan_id**|**uniqueidentifier**|ID des Datenbankwartungsplans.|  
|**plan_name**|**sysname**|Name des Datenbankwartungsplans.|  
|**database_name**|**sysname**|Der Name der Datenbank, die dem Datenbank-Wartungsplan zugeordnet ist.|  
|**server_name**|**sysname**|Systemname.|  
|**activity**|**nvarchar(128)**|Die vom Datenbankwartungsplan durchgeführte Aktivität (z. B. Transaktionsprotokoll sichern usw.).|  
|**succeeded**|**bit**|**0** = Erfolgreich **1** = Fehler|  
|**end_time**|**datetime**|Zeitpunkt, an dem die Aktion abgeschlossen wurde.|  
|**duration**|**int**|Erforderliche Zeitspanne, um die Aktion im Rahmen des Datenbankwartungsplans abzuschließen.|  
|**start_time**|**datetime**|Zeitpunkt, an dem die Aktion gestartet wurde.|  
|**error_number**|**int**|Fehlernummer, die bei einem Fehler gemeldet wird.|  
|**Nachricht**|**nvarchar(512)**|Von **sqlmaint**generierte Meldung.|  
  
  
