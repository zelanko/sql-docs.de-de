---
description: sp_notify_operator (Transact-SQL)
title: sp_notify_operator (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_notify_operator_TSQL
- sp_notify_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_notify_operator
ms.assetid: c440f5c9-9884-4196-b07c-55d87afb17c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c6a1c623ec7172a7cab48c49491619184d618ebf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481105"
---
# <a name="sp_notify_operator-transact-sql"></a>sp_notify_operator (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Sendet mithilfe der Datenbank-E-Mail eine E-Mail-Nachricht an den Operator.  
  
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_notify_operator  
    [ @profile_name = ] 'profilename' ,  
    [ @id = ] id ,  
    [ @name = ] 'name' ,  
    [ @subject = ] 'subject' ,  
    [ @body = ] 'message' ,  
    [ @file_attachments = ] 'attachment'  
    [ @mail_database = ] 'mail_host_database'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @profile_name = ] 'profilename'` Der Name des Datenbank-E-Mail Profils, das zum Senden der Nachricht verwendet werden soll. Profile Name ist vom *Datentyp* **nvarchar (128)**. Wenn Profile Name nicht *angegeben wird,* wird das Standard Datenbank-E-Mail Profil verwendet.  
  
`[ @id = ] id` Der Bezeichner für den Operator, an den die Nachricht gesendet werden soll. *ID* ist vom Datentyp **int**und hat den Standardwert NULL. Eine *ID* oder ein *Name* muss angegeben werden.  
  
`[ @name = ] 'name'` Der Name des Operators, an den die Nachricht gesendet werden soll. *Name ist vom Datentyp* **nvarchar (128)** und hat den Standardwert NULL. Eine *ID* oder ein *Name* muss angegeben werden.  
  
> **Hinweis:** Eine e-Mail-Adresse muss für den Operator definiert werden, bevor Nachrichten empfangen werden können.  
  
`[ @subject = ] 'subject'` Der Betreff der e-Mail-Nachricht. *Subject* ist vom Datentyp **nvarchar (256)** und hat keinen Standardwert.  
  
`[ @body = ] 'message'` Der Text der e-Mail-Nachricht. die Nachricht ist vom *Datentyp* **nvarchar (max)** und hat keinen Standardwert.  
  
`[ @file_attachments = ] 'attachment'` Der Name einer Datei, die an die e-Mail-Nachricht angefügt werden soll. *Anlage* ist vom Datentyp **nvarchar (512)** und hat keinen Standardwert.  
  
`[ @mail_database = ] 'mail_host_database'` Gibt den Namen der Mail Host Datenbank an. *mail_host_database* ist vom Datentyp **nvarchar (128)**. Wenn keine *mail_host_database* angegeben ist, wird standardmäßig die **msdb** -Datenbank verwendet.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="remarks"></a>Bemerkungen  
 Sendet die Nachricht an die angegebene E-Mail-Adresse des angegebenen Operators. Falls für den Operator keine E-Mail-Adresse konfiguriert ist, wird ein Fehler zurückgegeben.  
  
 Die Datenbank-E-Mail und eine Mailhostdatenbank müssen konfiguriert werden, bevor eine Benachrichtigung an einen Operator gesendet werden kann.  
  
## <a name="permissions"></a>Berechtigungen  
 Standardmäßig können Mitglieder der festen Server Rolle **sysadmin** diese gespeicherte Prozedur ausführen. Andere Benutzer müssen Mitglieder der festen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent-Datenbankrollen in der **msdb** -Datenbank sein:  
  
-   **SQLAgentUserRole**  
  
-   **SQLAgentReaderRole**  
  
-   **SQLAgentOperatorRole**  
  
 Weitere Informationen zu den Berechtigungen dieser Rollen finden Sie unter [Feste Datenbankrollen des SQL Server-Agents](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Benachrichtigungs-E-Mail an den Operator `François Ajenstat` mit dem Datenbank-E-Mail-Profil `AdventureWorks Administrator` gesendet. Der Betreff der E-Mail lautet `Test Notification`. Die E-Mail-Nachricht enthält den Satz "This is a test of notification via e-mail".  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_notify_operator  
   @profile_name = N'AdventureWorks Administrator',  
   @name = N'François Ajenstat',  
   @subject = N'Test Notification',  
   @body = N'This is a test of notification via e-mail.' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server-Agent gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_delete_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)  
  
  
