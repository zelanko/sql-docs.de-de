---
title: Sp_purge_jobhistory (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_purge_jobhistory_TSQL
- sp_purge_jobhistory
dev_langs:
- TSQL
helpviewer_keywords:
- sp_purge_jobhistory
ms.assetid: 237f9bad-636d-4262-9bfb-66c034a43e88
caps.latest.revision: 33
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 1807fb797b7bd3d53f83cae60c4b876fcb91b74f
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395504"
---
# <a name="sppurgejobhistory-transact-sql"></a>sp_purge_jobhistory (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Entfernt die Verlaufsdatensätze für einen Auftrag.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_purge_jobhistory   
   {   [ @job_name = ] 'job_name' |   
     | [ @job_id = ] job_id }  
   [ , [ @oldest_date = ] oldest_date ]  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@job_name=** ] **"***Job_name***"**  
 Der Name des Auftrags, für den die Verlaufsdatensätze gelöscht werden sollen. *Job_name*ist **Sysname**, hat den Standardwert NULL. Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich.  
  
> [!NOTE]  
>  Mitglied der **Sysadmin** -Serverrolle oder Mitglied der **SQLAgentOperatorRole** festen Datenbankrolle ausführen kann **Sp_purge_jobhistory** ohne Angabe einer *Job_name* oder *Job_id*. Wenn **Sysadmin** -Benutzer diese Argumente nicht angeben, wird der Auftragsverlauf für alle lokalen und Multiserveraufträge innerhalb der angegebenen Zeit gelöscht *Oldest_date*. Wenn **SQLAgentOperatorRole** -Benutzer diese Argumente nicht angeben, wird der Auftragsverlauf für alle lokalen Aufträge innerhalb der angegebenen Zeit gelöscht *Oldest_date*.  
  
 [ **@job_id=** ] *job_id*  
 Die ID des Auftrags für die zu löschenden Datensätze. *Job_id*ist **Uniqueidentifier**, hat den Standardwert NULL. Entweder *Job_id* oder *Job_name* muss angegeben werden, aber beide Angaben sind nicht möglich. Siehe Hinweis in der Beschreibung des **@job_name** Informationen **Sysadmin** oder **SQLAgentOperatorRole** Benutzer können dieses Argument verwenden.  
  
 [ **@oldest_date** =] *Oldest_date*  
 Der älteste Datensatz, der im Verlauf beibehalten werden soll. *Oldest_date* ist **"DateTime"**, hat den Standardwert NULL. Wenn *Oldest_date* angegeben wird, **Sp_purge_jobhistory** entfernt nur die Datensätze, die älter als der angegebene Wert sind.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Wenn **Sp_purge_jobhistory** wird erfolgreich abgeschlossen, es wird eine Meldung zurückgegeben.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können nur Mitglieder der der **Sysadmin** -Serverrolle sein oder die **SQLAgentOperatorRole** -Datenbankrolle diese gespeicherte Prozedur ausführen. Mitglieder der **Sysadmin** können den Auftragsverlauf für alle lokalen und Multiserveraufträge leeren. Mitglieder der **SQLAgentOperatorRole** können den Auftragsverlauf für alle lokalen Aufträge nur.  
  
 Anderen Benutzern, einschließlich Elementen der **SQLAgentUserRole** und Mitglieder der **SQLAgentReaderRole**, müssen ausdrücklich erteilt werden die EXECUTE-Berechtigung auf **Sp_purge_jobhistory**. Nachdem die EXECUTE-Berechtigung für diese gespeicherte Prozedur erteilt wurde, können dieses Benutzer nur den Verlauf für Aufträge leeren, deren Besitzer sie sind.  
  
 Die **SQLAgentUserRole**, **SQLAgentReaderRole**, und **SQLAgentOperatorRole** feste Datenbankrollen sind der **Msdb** Datenbank. Weitere Informationen zu deren Berechtigungen finden Sie unter [SQL Server Agent Fixed Database Roles](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-remove-history-for-a-specific-job"></a>A. Entfernen des Verlaufs für einen bestimmten Auftrag  
 Im folgenden Beispiel wird der Verlauf eines Auftrags mit dem Namen `NightlyBackups` entfernt.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory  
    @job_name = N'NightlyBackups' ;  
GO  
```  
  
### <a name="b-remove-history-for-all-jobs"></a>B. Entfernen des Verlaufs für alle Aufträge  
  
> [!NOTE]  
>  Nur Mitglieder der der **Sysadmin** festen Serverrolle und Mitglieder der **SQLAgentOperatorRole** können Verlaufsdatensätze für alle Aufträge entfernen. Wenn **Sysadmin** -Benutzer diese gespeicherte Prozedur ohne Parameter ausführen, wird der Auftragsverlauf für alle lokalen und Multiserveraufträge geleert. Wenn **SQLAgentOperatorRole** -Benutzer diese gespeicherte Prozedur ohne Parameter ausführen, wird nur der Auftragsverlauf für alle lokalen Aufträge geleert.  
  
 Im folgenden Beispiel wird die Prozedur ohne Parameter ausgeführt, um alle Verlaufsdatensätze zu entfernen.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_purge_jobhistory ;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [sp_help_job &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-job-transact-sql.md)   
 [sp_help_jobhistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobhistory-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [GRANT (Objektberechtigungen) &#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
  
