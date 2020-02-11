---
title: dbo. sysjobzeitpläne (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobschedules
- dbo.sysjobschedules
- dbo.sysjobschedules_TSQL
- sysjobschedules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobschedules system table
ms.assetid: ccdafec7-2a9b-4356-bffb-1caa3a12db59
author: stevestein
ms.author: sstein
ms.openlocfilehash: a7f2dfc6196bfba6c274eb45a45745159447cc39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061181"
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enthält Zeitplaninformationen für Aufträge, die vom [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent ausgeführt werden sollen. Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
> **Hinweis:** Die **sysjobzeitpläne** -Tabelle wird alle 20 Minuten aktualisiert, was sich auf die Werte auswirken kann, die von der gespeicherten Prozedur **sp_help_jobschedule** zurückgegeben werden.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|ID des Zeitplans.|  
|**job_id**|**uniqueidentifier**|ID des Auftrags.|  
|**next_run_date**|**int**|Das nächste Datum, an dem eine Ausführung des Auftrags geplant ist. Für das Datum wird das Format YYYYMMDD verwendet.|  
|**next_run_time**|**int**|Uhrzeit, an der eine Ausführung des Auftrags geplant ist. Für die Uhrzeit wird das Format HHMMSS und eine 24-Stunden-Schreibweise verwendet.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo. syszeitpläne &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
