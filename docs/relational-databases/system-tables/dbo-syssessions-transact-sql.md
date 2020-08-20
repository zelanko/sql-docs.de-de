---
description: dbo.syssessions (Transact-SQL)
title: dbo.sysSitzungen (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/30/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.syssessions_TSQL
- dbo.syssessions
- syssessions_TSQL
- syssessions
dev_langs:
- TSQL
helpviewer_keywords:
- syssessions system table
ms.assetid: 187819b6-c7f4-4a26-b74c-0a89e96695cf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 72fa9a3d55b3ed783fcbfc7c230676e7fe653eea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473292"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Beim Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents wird eine neue Sitzung erstellt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent verwendet Sitzungen, um den Status von Aufträgen beizubehalten, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst neu gestartet oder unerwartet beendet wird. Jede Zeile der **syssessions** -Tabelle enthält Informationen zu einer Sitzung. Mithilfe der **sysjobactivity** -Tabelle kann der Auftragsstatus am Ende einer Sitzung angezeigt werden.  
  
 Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID einer Sitzung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents. Diese session_id ist nicht die SPID für die Sitzung, sondern vielmehr ein Identitäts Wert in dieser Systemtabelle.|  
|**agent_start_date**|**datetime**|Datum und Uhrzeit, zu der der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst für diese Sitzung gestartet wurde.|  
  
## <a name="remarks"></a>Bemerkungen  
 Nur Mitglieder der festen Serverrolle **sysadmin** können auf diese Tabelle zugreifen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo.sysjobactivity &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
