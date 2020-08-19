---
description: sp_cycle_errorlog (Transact-SQL)
title: sp_cycle_errorlog (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cycle_errorlog_TSQL
- sp_cycle_errorlog
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cycle_errorlog
ms.assetid: 61a12cbf-78a3-4052-8604-3b29d07573fd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5f950b15772f30e914f425261f84591deb0f822d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88447340"
---
# <a name="sp_cycle_errorlog-transact-sql"></a>sp_cycle_errorlog (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Schließt die aktuelle Fehlerprotokolldatei und nummeriert die Fehlerprotokollerweiterungen wie bei einem Serverneustart durch. Das neue Fehlerprotokoll enthält Informationen zur Version und urheberrechtliche Informationen sowie eine Zeile, die anzeigt, dass das neue Protokoll erstellt wurde.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_cycle_errorlog  
```  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Bei jedem Starten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird das aktuelle Fehlerprotokoll in **errorlog.1**umbenannt, **errorlog.1** wird in **errorlog.2**umbenannt, **errorlog.2** wird in **errorlog.3**umbenannt usw. Mit**sp_cycle_errorlog** können die Fehlerprotokolldateien durchlaufen werden, ohne den Server neu zu starten.  
  
## <a name="permissions"></a>Berechtigungen  
 Die Ausführungsberechtigungen für **sp_cycle_errorlog** sind auf die Mitglieder der festen Serverrolle **sysadmin** beschränkt.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird das [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Fehlerprotokoll durchlaufen.  
  
```  
EXEC sp_cycle_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cycle_agent_errorlog &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-cycle-agent-errorlog-transact-sql.md)  
  
  
