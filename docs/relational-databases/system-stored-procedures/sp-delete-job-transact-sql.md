---
description: sp_delete_job (Transact-SQL)
title: sp_delete_job (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_job
- sp_delete_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_job
ms.assetid: b85db6e4-623c-41f1-9643-07e5ea38db09
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f11bf53f9663893c2d678e7a7af904b70b4fc1cc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493340"
---
# <a name="sp_delete_job-transact-sql"></a>sp_delete_job (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht einen Auftrag.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_job { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,  
     [ , [ @originating_server = ] 'server' ]   
     [ , [ @delete_history = ] delete_history ]  
     [ , [ @delete_unused_schedule = ] delete_unused_schedule ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` Die ID des Auftrags, der gelöscht werden soll. *job_id* ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags, der gelöscht werden soll. *job_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> [!NOTE]  
>  Es muss entweder *job_id* oder *job_name*angegeben werden. Beide können nicht angegeben werden.  
  
`[ @originating_server = ] 'server'` Zur internen Verwendung.  
  
`[ @delete_history = ] delete_history` Gibt an, ob der Verlauf für den Auftrag gelöscht werden soll. *delete_history* ist vom Typ **Bit**und hat den Standardwert **1**. Wenn *delete_history* **1**ist, wird der Auftrags Verlauf für den Auftrag gelöscht. Wenn *delete_history* **0**ist, wird der Auftrags Verlauf nicht gelöscht.  
  
 Beachten Sie Folgendes: Wenn ein Auftrag gelöscht und der Verlauf nicht gelöscht wird, werden die Verlaufs Informationen für den Auftrag nicht in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] grafischen Benutzeroberfläche des Agent-Auftragsverlaufs angezeigt. die Informationen befinden sich jedoch weiterhin in der **sysjobhistory** -Tabelle der **msdb** -Datenbank.  
  
`[ @delete_unused_schedule = ] delete_unused_schedule` Gibt an, ob die an diesen Auftrag angefügten Zeitpläne gelöscht werden sollen, wenn Sie nicht an einen anderen Auftrag angefügt sind. *delete_unused_schedule* ist vom Typ **Bit**und hat den Standardwert **1**. Wenn *delete_unused_schedule* **1**ist, werden die an diesen Auftrag angefügten Zeitpläne gelöscht, wenn keine anderen Aufträge auf den Zeitplan verweisen. Wenn *delete_unused_schedule* **0**ist, werden die Zeitpläne nicht gelöscht.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Das ** \@ originating_server** -Argument ist für die interne Verwendung reserviert.  
  
 Das ** \@ delete_unused_schedule** -Argument bietet Abwärtskompatibilität mit früheren Versionen von SQL Server durch automatisches Entfernen von Zeitplänen, die nicht an einen Auftrag angefügt sind. Beachten Sie, dass dieser Parameter standardmäßig das Verhalten der Abwärtskompatibilität bietet. Wenn Sie Zeitpläne beibehalten möchten, die nicht an einen Auftrag angefügt sind, müssen Sie den Wert **0** als ** \@ delete_unused_schedule** Argument angeben.  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] können Aufträge problemlos mithilfe einer grafischen Oberfläche verwaltet werden. Dies ist die empfohlene Vorgehensweise für die Erstellung und Verwaltung der Auftragsinfrastruktur.  
  
 Mit dieser gespeicherten Prozedur können keine Wartungspläne oder Aufträge, die Teil von Wartungsplänen sind, gelöscht werden. Zum Löschen von Wartungsplänen müssen Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] verwenden.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der festen Serverrolle **sysadmin** können **sp_delete_job** ausführen, um einen beliebigen Auftrag zu löschen. Ein Benutzer, der kein Mitglied der festen Serverrolle **sysadmin** ist, kann nur Aufträge löschen, deren Besitzer er ist.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Auftrag `NightlyBackups` gelöscht.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_job  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_add_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-job-transact-sql.md)   
 [sp_help_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_update_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
