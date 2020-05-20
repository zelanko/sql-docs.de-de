---
title: sp_delete_notification (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_notification_TSQL
- sp_delete_notification
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_notification
ms.assetid: b55d3898-596d-47a5-a4f0-d65dc736223b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: eb3c5166aef24bcc9890295809b8b69a68ed4112
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830314"
---
# <a name="sp_delete_notification-transact-sql"></a>sp_delete_notification (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent-Benachrichtigungsdefinition für eine bestimmte Warnung oder einen bestimmten Operator.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_delete_notification  
     [ @alert_name = ] 'alert' ,   
     [ @operator_name = ] 'operator'   
```  
  
## <a name="arguments"></a>Argumente  
`[ @alert_name = ] 'alert'`Der Name der Warnung. *Alert* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @operator_name = ] 'operator'`Der Name des Operators. *Operator* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Durch das Entfernen einer Benachrichtigung wird nur die Benachrichtigung entfernt; die Warnung und der Operator sind weiterhin vorhanden.  
  
## <a name="permissions"></a>Berechtigungen  
 Zum Ausführen dieser gespeicherten Prozedur muss den Benutzern die festen Server Rolle **sysadmin** erteilt werden.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die Benachrichtigung entfernt, die an den `François Ajenstat`-Operator bei Auftritt der `Test Alert`-Warnung gesendet wird.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_notification  
    @alert_name = 'Test Alert',  
    @operator_name = 'François Ajenstat' ;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sp_add_alert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_add_notification &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_add_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_alert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-delete-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [sp_help_notification &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-notification-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [sp_update_notification &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-update-notification-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
