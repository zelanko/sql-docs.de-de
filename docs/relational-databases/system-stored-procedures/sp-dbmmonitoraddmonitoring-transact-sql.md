---
title: sp_dbmmonitoraddmonitoring (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbmmonitoraddmonitoring
- sp_dbmmonitoraddmonitoring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database mirroring [SQL Server], monitoring
- sp_dbmmonitoraddmonitoring
ms.assetid: 9489dc30-af29-4363-a172-4645947fc95e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7869fed1b04a16a57750fcfd91d18e1b0c0d18a7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85738531"
---
# <a name="sp_dbmmonitoraddmonitoring-transact-sql"></a>sp_dbmmonitoraddmonitoring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Erstellt einen Auftrag für den Datenbankspiegelungs-Monitor, der in regelmäßigen Abständen den Spiegelungsstatus für jede gespiegelte Datenbank in der Serverinstanz aktualisiert.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dbmmonitoraddmonitoring [ update_period ]  
```  
  
## <a name="arguments"></a>Argumente  
 *update_period*  
 Gibt das Intervall zwischen den Updates in Minuten an. Dieser Wert kann zwischen 1 und 120 Minuten betragen. Der Standardwert beträgt 1&#160;Minute.  
  
> [!NOTE]  
>  Bei einem zu kurz festgelegten Updatezeitraum kann die Antwortzeit für Clients zunehmen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Keine  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Prozedur erfordert, dass die Ausführung des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agents in der Serverinstanz zugelassen wird. Damit der Auftrag für den Datenbankspiegelungs-Monitor ausgeführt wird, muss der Agent ausgeführt werden.  
  
 Wenn die Daten Bank Spiegelung von gestartet wird [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , wird die **sp_dbmmonitoraddmonitoring** Prozedur automatisch ausgeführt. Wenn Sie die Spiegelung manuell mithilfe von ALTER DATABASE-Anweisungen starten, müssen Sie **sp_dbmmonitoraddmonitoring** manuell ausführen, um eine gespiegelte Datenbank auf der Serverinstanz zu überwachen.  
  
> [!NOTE]  
>  Wenn Sie **sp_dbmmonitoraddmonitoring** vor dem Einrichten der Daten Bank Spiegelung ausführen, wird der Überwachungs Auftrag ausgeführt, aber die Statustabelle, in der der Daten Bank Spiegelungs Monitor-Verlauf gespeichert ist, wird nicht aktualisiert.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Überwachung mit einem Updatezeitraum von `3` Minuten gestartet.  
  
```  
EXEC sp_dbmmonitoraddmonitoring 3;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überwachen der Daten Bank Spiegelung &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [sp_dbmmonitorchangemonitoring &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorchangemonitoring-transact-sql.md)   
 [sp_dbmmonitordropmonitoring &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitordropmonitoring-transact-sql.md)   
 [sp_dbmmonitorhelpmonitoring &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorhelpmonitoring-transact-sql.md)   
 [sp_dbmmonitorresults &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dbmmonitorresults-transact-sql.md)  
  
  
