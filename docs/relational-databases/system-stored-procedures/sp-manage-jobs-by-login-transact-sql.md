---
title: sp_manage_jobs_by_login (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_manage_jobs_by_login
- sp_manage_jobs_by_login_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_manage_jobs_by_login
ms.assetid: 832ec15a-6e92-4eb5-8c4a-af4dba79fbaa
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e810bf996f7dbaa8624c6a0e834011d759aa9348
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85899388"
---
# <a name="sp_manage_jobs_by_login-transact-sql"></a>sp_manage_jobs_by_login (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Löscht Aufträge des angegebenen Anmeldenamens oder weist sie neu zu.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_manage_jobs_by_login  
     [ @action = ] 'action'  
     [, [@current_owner_login_name = ] 'current_owner_login_name']  
     [, [@new_owner_login_name = ] 'new_owner_login_name']  
```  
  
## <a name="arguments"></a>Argumente  
`[ @action = ] 'action'`Die Aktion, die für den angegebenen Anmelde Namen ausgeführt werden soll. *Action* ist vom Datentyp **varchar (10)** und hat keinen Standardwert. Wenn *Action* **Delete**ist, löscht **sp_manage_jobs_by_login** alle Aufträge, die sich im Besitz *current_owner_login_name*befinden. Wenn *action* die Aktion **neu zugewiesen wird, werden**alle Aufträge *new_owner_login_name*zugewiesen.  
  
`[ @current_owner_login_name = ] 'current_owner_login_name'`Der Anmelde Name des aktuellen Auftrags Besitzers. *current_owner_login_name* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @new_owner_login_name = ] 'new_owner_login_name'`Der Anmelde Name des neuen Auftrags Besitzers. Verwenden Sie diesen Parameter nur, wenn *Aktion* erneut **zugewiesen**wird. *new_owner_login_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss den Benutzern die festen Server Rolle **sysadmin** erteilt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel erfolgt eine Neuzuweisung aller Aufträge von `danw` an `françoisa`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_manage_jobs_by_login  
    @action = N'REASSIGN',  
    @current_owner_login_name = N'danw',  
    @new_owner_login_name = N'françoisa' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_delete_job &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-job-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
