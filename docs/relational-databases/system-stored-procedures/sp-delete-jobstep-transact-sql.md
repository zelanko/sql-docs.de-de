---
title: Sp_delete_jobstep (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobstep
- sp_delete_jobstep_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobstep
ms.assetid: 421ede8e-ad57-474a-9fb9-92f70a3e77e3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 84b1e2840240d0d02a3193ecc592a13331719c7a
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527822"
---
# <a name="spdeletejobstep-transact-sql"></a>sp_delete_jobstep (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt einen Auftragsschritt aus einem Auftrag.  
  
 
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_jobstep { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,   
     [ @step_id = ] step_id   
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id` Die ID des Auftrags, aus dem der Schritt entfernt werden soll. *Job_id*ist **Uniqueidentifier**, hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'` Der Name des Auftrags, aus dem der Schritt entfernt werden soll. *Job_name*ist **Sysname**, hat den Standardwert NULL.  
  
> **HINWEIS:** Entweder *Job_id* oder *Job_name* muss angegeben werden; können nicht gleichzeitig angegeben werden.  
  
`[ @step_id = ] step_id` Die ID des Schritts entfernt wird. *Step_id*ist **Int**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Durch das Entfernen eines Auftragsschritts werden die anderen Auftragsschritte, die auf den gelöschten Schritt verweisen, automatisch aktualisiert.  
  
 Führen Sie für Weitere Informationen zu den Schritten, die einem bestimmten Auftrag zugeordneten **Sp_help_jobstep**.  
  
> **HINWEIS:** Aufrufen von **Sp_delete_jobstep** mit einem *Step_id* Wert 0 (null) werden alle Auftragsschritte für den Auftrag gelöscht.  
  
 Mit Microsoft SQL Server Management Studio lassen sich Aufträge auf einfache Weise über eine grafische Oberfläche verwalten. Dies ist die empfohlene Vorgehensweise, um die Auftragsinfrastruktur zu erstellen und zu verwalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der festen Serverrolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder der **Sysadmin** können löschen ein Auftragsschritts, der von einem anderen Benutzer gehört.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird Auftragsschritt `1` aus dem Auftrag `Weekly Sales Data Backup` entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_jobstep  
    @job_name = N'Weekly Sales Data Backup',  
    @step_id = 1 ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anzeigen oder Ändern von Aufträgen](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_add_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
