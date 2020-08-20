---
description: sp_update_jobschedule (Transact-SQL)
title: sp_update_jobschedule (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_jobschedule_TSQL
- sp_update_jobschedule
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_jobschedule
ms.assetid: 4df02594-4cd1-49a9-8d97-37c44e4d5423
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 92aa7a001a365ed9d24c0e856b304b723e57c9c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473528"
---
# <a name="sp_update_jobschedule-transact-sql"></a>sp_update_jobschedule (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ändert die Zeitplaneinstellungen für den angegebenen Auftrag.  
  
 **sp_update_jobschedule** wird nur aus Gründen der Abwärtskompatibilität bereitgestellt.  
  
> [!IMPORTANT]
>  Weitere Informationen zur Syntax, die in früheren Versionen von Microsoft SQL Server verwendet wurde, finden Sie unter Transact-SQL referencefor Microsoft SQL Server 2000 *.*  
  
## <a name="remarks"></a>Bemerkungen  
 Auftragszeitpläne können jetzt unabhängig von Aufträgen verwaltet werden. Verwenden Sie **sp_update_schedule**, um einen Zeitplan zu aktualisieren.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder von **sysadmin** können diese gespeicherte Prozedur verwenden, um Auftrags Zeitpläne zu aktualisieren, die sich im Besitz anderer Benutzer befinden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_update_schedule &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-schedule-transact-sql.md)  
  
  
