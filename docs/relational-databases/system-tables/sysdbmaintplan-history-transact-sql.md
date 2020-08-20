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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f5871f6acc8e4df58223e1568b0a253a7e62c42d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473150"
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
  
  
