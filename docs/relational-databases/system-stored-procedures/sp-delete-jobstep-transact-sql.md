---
title: sp_delete_jobstep (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 77557dee97475ef713c88c969de98a241d955eea
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85863905"
---
# <a name="sp_delete_jobstep-transact-sql"></a>sp_delete_jobstep (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Entfernt einen Auftragsschritt aus einem Auftrag.  
  
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_jobstep { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,   
     [ @step_id = ] step_id   
```  
  
## <a name="arguments"></a>Argumente  
`[ @job_id = ] job_id`Die ID des Auftrags, von dem der Schritt entfernt wird. *job_id*ist vom Datentyp **uniqueidentifier**und hat den Standardwert NULL.  
  
`[ @job_name = ] 'job_name'`Der Name des Auftrags, von dem aus der Schritt entfernt wird. *job_name*ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
> **Hinweis:** Es muss entweder *job_id* oder *job_name* angegeben werden. Beide können nicht angegeben werden.  
  
`[ @step_id = ] step_id`Die ID des Schrittes, der entfernt wird. *step_id*ist vom Datentyp **int**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Durch das Entfernen eines Auftragsschritts werden die anderen Auftragsschritte, die auf den gelöschten Schritt verweisen, automatisch aktualisiert.  
  
 Führen Sie **sp_help_jobstep**aus, um weitere Informationen zu den Schritten zu erhalten, die mit einem bestimmten Auftrag verknüpft sind.  
  
> **Hinweis:** Wenn Sie **sp_delete_jobstep** mit dem *step_id* Wert NULL aufrufen, werden alle Auftrags Schritte für den Auftrag gelöscht.  
  
 Mit Microsoft SQL Server Management Studio lassen sich Aufträge auf einfache Weise über eine grafische Oberfläche verwalten. Dies ist die empfohlene Vorgehensweise, um die Auftragsinfrastruktur zu erstellen und zu verwalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
 Nur Mitglieder von **sysadmin** können einen Auftrags Schritt löschen, dessen Besitzer ein anderer Benutzer ist.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Anzeigen oder Ändern von Aufträgen](../../ssms/agent/view-or-modify-jobs.md)   
 [sp_add_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)   
 [sp_update_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md)   
 [sp_help_jobstep &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
