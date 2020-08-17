---
description: dbo.sysjobstepslogs (Transact-SQL)
title: dbo.sysjobstepslogs (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysjobstepslogs_TSQL
- sysjobstepslogs_TSQL
- sysjobstepslogs
- dbo.sysjobstepslogs
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobstepslogs system table
ms.assetid: 128c25db-0b71-449d-bfb2-38b8abcf24a0
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f32042c01db8a35f9ce44fe938b19e4ae8e6118b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88373827"
---
# <a name="dbosysjobstepslogs-transact-sql"></a>dbo.sysjobstepslogs (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enthält das Auftragsschrittprotokoll für alle Auftragsschritte des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents, die konfiguriert werden, um die Ausgabe der Auftragsschritte in eine Tabelle zu schreiben. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**log_id**|**int**|ID des Auftragsschrittprotokolls.|  
|**angezeigt**|**nvarchar(max)**|Inhalt des Auftragsschrittprotokolls.|  
|**date_created**|**datetime**|Datum und Uhrzeit der Erstellung des Auftragsschrittprotokolls.|  
|**date_modified**|**datetime**|Datum und Uhrzeit der letzten Änderung des Auftragsschrittprotokolls.|  
|**log_size**|**int**|Größe des Auftragsschrittprotokolls in Bytes.|  
|**step_uid**|**uniqueidentifier**|Eindeutiger Bezeichner des Auftragsschrittes.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_help_jobsteplog &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-jobsteplog-transact-sql.md)   
 [sp_delete_jobsteplog &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-jobsteplog-transact-sql.md)  
  
  
