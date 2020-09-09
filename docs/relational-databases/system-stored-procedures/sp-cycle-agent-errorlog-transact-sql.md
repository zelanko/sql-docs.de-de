---
description: sp_cycle_agent_errorlog (Transact-SQL)
title: sp_cycle_agent_errorlog (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cycle_agent_errorlog
- sp_cycle_agent_errorlog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cycle_agent_errorlog
ms.assetid: 8aa96182-60b7-4d7b-b2a7-ccce70378c6e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 06e616ec3cbabb40b13783462661df91196752bc
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548201"
---
# <a name="sp_cycle_agent_errorlog-transact-sql"></a>sp_cycle_agent_errorlog (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Schließt die aktuelle Fehlerprotokolldatei des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents und nummeriert die Fehlerprotokollerweiterungen des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents wie bei einem Serverneustart durch. Das neue Fehlerprotokoll des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents enthält eine Zeile, die anzeigt, dass das neue Protokoll erstellt wurde.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cycle_agent_errorlog  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Bei jedem Starten des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents wird das aktuelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Fehlerprotokoll in **SQLAgent.1**umbenannt, **SQLAgent.1** wird in **SQLAgent.2**umbenannt, **SQLAgent.2** wird in **SQLAgent.3**umbenannt usw. Mit**sp_cycle_agent_errorlog** können die Fehlerprotokolldateien durchlaufen werden, ohne den Server neu zu starten.  
  
 Diese gespeicherte Prozedur muss von der **msdb** -Datenbank aus ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen für **sp_cycle_agent_errorlog** sind auf die Mitglieder der festen Serverrolle **sysadmin** beschränkt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das Fehlerprotokoll des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agents durchnummeriert.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_cycle_agent_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_cycle_errorlog &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md)  
  
  
