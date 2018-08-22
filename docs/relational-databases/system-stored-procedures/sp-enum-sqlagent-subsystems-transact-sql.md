---
title: Sp_enum_sqlagent_subsystems (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enum_sqlagent_subsystems
- sp_enum_sqlagent_subsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_sqlagent_subsystems
ms.assetid: 019a3c9d-bac3-495b-a70a-2c19f1d2e20e
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e2a816ae764e7348e85a4ae405fe3e57d268cb01
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40393678"
---
# <a name="spenumsqlagentsubsystems-transact-sql"></a>sp_enum_sqlagent_subsystems (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Listet die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent-Subsysteme.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_enum_sqlagent_subsystems  
```  
  
## <a name="arguments"></a>Argumente  
 None  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|Description|  
|-----------------|---------------|-----------------|  
|**subsystem**|**nvarchar(40)**|Der Name des Subsystems.|  
|**description**|**nvarchar(512)**|Beschreibung des Subsystems.|  
|**subsystem_dll**|**nvarchar(510)**|DLL-Modul, das das Subsystem enthält.|  
|**agent_exe**|**nvarchar(510)**|Ausführbares Modul, das vom Subsystem verwendet wird.|  
|**start_entry_point**|**nvarchar(30)**|Prozedur, die der SQL Server-Agent während der Ausführung der Auftragsschritte aufruft.|  
|**event_entry_point**|**nvarchar(30)**|Prozedur, die der SQL Server-Agent während der Ausführung der Auftragsschritte aufruft.|  
|**stop_entry_point**|**nvarchar(30)**|Prozedur, die der SQL Server-Agent während der Ausführung der Auftragsschritte aufruft.|  
|**max_worker_threads**|**int**|Maximale Anzahl von Threads [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent wird für dieses Subsystem startet.|  
|**subsystem_id**|**int**|Bezeichner für das Subsystem.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Prozedur listet die in der Instanz verfügbaren Subsysteme auf.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
 Weitere Informationen zu **SQLAgentOperatorRole**, finden Sie unter [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren von SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
  
