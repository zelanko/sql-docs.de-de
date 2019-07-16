---
title: dbo.syssessions (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35b23525dc9762d012948e6eba0b41156b45ac69
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056277"
---
# <a name="dbosyssessions-transact-sql"></a>dbo.syssessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Beim Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents wird eine neue Sitzung erstellt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent verwendet Sitzungen, um den Status von Aufträgen beizubehalten, wenn der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Dienst neu gestartet oder unerwartet beendet wird. Jede Zeile der **syssessions** -Tabelle enthält Informationen zu einer Sitzung. Mithilfe der **sysjobactivity** -Tabelle kann der Auftragsstatus am Ende einer Sitzung angezeigt werden.  
  
 Diese Tabelle wird in der **msdb** -Datenbank gespeichert.  
  
|Spaltenname|Datentyp|Beschreibung|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|ID einer Sitzung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents.|  
|**agent_start_date**|**datetime**|Datum und Uhrzeit, zu der der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Dienst für diese Sitzung gestartet wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Nur Mitglieder der festen Serverrolle **sysadmin** können auf diese Tabelle zugreifen.  
  
## <a name="see-also"></a>Siehe auch  
 [dbo.sysjobactivity &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysjobactivity-transact-sql.md)  
  
  
