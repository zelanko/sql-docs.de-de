---
description: sp_enum_sqlagent_subsystems (Transact-SQL)
title: sp_enum_sqlagent_subsystems (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_sqlagent_subsystems
- sp_enum_sqlagent_subsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_sqlagent_subsystems
ms.assetid: 019a3c9d-bac3-495b-a70a-2c19f1d2e20e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7ee9bf6fbb0b0567ca06635ca5d98ba9a3b98f6b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549773"
---
# <a name="sp_enum_sqlagent_subsystems-transact-sql"></a>sp_enum_sqlagent_subsystems (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Führt die Subsysteme des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents in einer Liste auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_enum_sqlagent_subsystems  
```  
  
## <a name="arguments"></a>Argumente  
 Keine  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
  
|Spaltenname|Datentyp|BESCHREIBUNG|  
|-----------------|---------------|-----------------|  
|**System**|**nvarchar(40)**|Der Name des Subsystems.|  
|**description**|**nvarchar(512)**|Beschreibung des Subsystems.|  
|**subsystem_dll**|**nvarchar (510)**|DLL-Modul, das das Subsystem enthält.|  
|**agent_exe**|**nvarchar (510)**|Ausführbares Modul, das vom Subsystem verwendet wird.|  
|**start_entry_point**|**nvarchar(30)**|Prozedur, die der SQL Server-Agent während der Ausführung der Auftragsschritte aufruft.|  
|**event_entry_point**|**nvarchar(30)**|Prozedur, die der SQL Server-Agent während der Ausführung der Auftragsschritte aufruft.|  
|**stop_entry_point**|**nvarchar(30)**|Prozedur, die der SQL Server-Agent während der Ausführung der Auftragsschritte aufruft.|  
|**max_worker_threads**|**int**|Maximale Anzahl von Threads, die der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent für dieses Subsystem startet.|  
|**subsystem_id**|**int**|Bezeichner für das Subsystem.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Prozedur listet die in der Instanz verfügbaren Subsysteme auf.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen Datenbankrolle **SQLAgentOperatorRole** in der **msdb** -Datenbank sein.  
  
 Ausführliche Informationen zu **SQLAgentOperatorRole**finden Sie unter [SQL Server-Agent fester Daten bankrollen](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Implementieren SQL Server-Agent-Sicherheit](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
  
