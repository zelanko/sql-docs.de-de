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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9f8a5cd825aba164796ec394709c8188367572cf
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540997"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)

[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

Beim Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents wird eine neue Sitzung erstellt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent verwendet Sitzungen, um den Status von Aufträgen beizubehalten, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst neu gestartet oder unerwartet beendet wird. Jede Zeile der **syssessions** -Tabelle enthält Informationen zu einer Sitzung. Mithilfe der **sysjobactivity** -Tabelle kann der Auftragsstatus am Ende einer Sitzung angezeigt werden.  
  
 Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID einer Sitzung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents. Diese session_id ist nicht die SPID für die Sitzung, sondern vielmehr ein Identitäts Wert in dieser Systemtabelle.|  
|**agent_start_date**|**datetime**|Datum und Uhrzeit, zu der der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst für diese Sitzung gestartet wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Nur Mitglieder der festen Serverrolle **sysadmin** können auf diese Tabelle zugreifen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [dbo.sysjobactivity &#40;Transact-SQL-&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
