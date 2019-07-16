---
title: Sp_altermessage (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_altermessage_TSQL
- sp_altermessage
dev_langs:
- TSQL
helpviewer_keywords:
- sp_altermessage
ms.assetid: 1b28f280-8ef9-48e9-bd99-ec14d79abaca
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0722bbc713804af6b2b97b5651df5b564d17a136
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68117797"
---
# <a name="spaltermessage-transact-sql"></a>sp_altermessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert den Status von benutzerdefinierten oder Systemmeldungen in einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Benutzerdefinierte Meldungen können mithilfe der **sys.messages** -Katalogsicht angezeigt werden.  

  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_altermessage [ @message_id = ] message_number   ,[ @parameter = ]'write_to_log'  
   ,[ @parameter_value = ]'value'   
```  
  
## <a name="arguments"></a>Argumente  
 [ **@message_id =** ] *Message_number*  
 Ist die Fehlernummer der Meldung zu ändernden **sys.messages**. *Message_number* ist **Int** hat keinen Standardwert.  
  
`[ @parameter = ] 'write\_to\_log_'` Wird zusammen mit **@parameter_value** , um anzugeben, dass die Nachricht an die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsprotokoll. *Write_to_log* ist **Sysname** hat keinen Standardwert. *Write_to_log* muss auf WITH_LOG oder NULL festgelegt werden. Wenn *Write_to_log* nastaven NA hodnotu WITH_LOG oder NULL, und der Wert für **@parameter_value** ist **"true"** , wird die Meldung in das Windows-Anwendungsprotokoll geschrieben. Wenn *Write_to_log* nastaven NA hodnotu WITH_LOG oder NULL, und der Wert für **@parameter_value** ist **"false"** , die Nachricht nicht immer in das Windows-Anwendungsprotokoll geschrieben, aber möglicherweise geschrieben, je nachdem wie der Fehler ausgelöst wurde. Wenn *Write_to_log* angegeben ist, den Wert für **@parameter_value** muss auch angegeben werden.  
  
> [!NOTE]  
>  Wenn eine Meldung in das Windows-Anwendungsprotokoll geschrieben wird, wird sie auch in die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Fehlerprotokolldatei geschrieben.  
  
`[ @parameter_value = ]'value_'` Wird zusammen mit **@parameter** , um anzugeben, dass der Fehler an die [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsprotokoll. *Wert* ist **varchar(5)** , hat keinen Standardwert. Wenn **"true"** , der Fehler wird immer in das Windows-Anwendungsprotokoll geschrieben. Wenn **"false"** , der Fehler nicht immer in das Windows-Anwendungsprotokoll geschrieben, sondern kann geschrieben werden, je nachdem wie der Fehler ausgelöst wurde. Wenn *Wert* angegeben wird, *Write_to_log* für **@parameter** muss auch angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Die Auswirkungen der **Sp_altermessage** mit der Option WITH_LOG aktiviert Option ähnelt der des RAISERROR WITH LOG-Parameters, außer dass **Sp_altermessage** das Protokollierverhalten einer vorhandenen Meldung ändert. Wenn eine Meldung so geändert wurde, dass für sie die Option WITH_LOG aktiviert ist, wird sie immer in das Windows-Anwendungsprotokoll geschrieben, unabhängig davon, wie ein Benutzer den Fehler auslöst. Selbst wenn RAISERROR ohne die Option WITH_LOG ausgeführt wird, wird der Fehler in das Windows-Anwendungsprotokoll geschrieben.  
  
 Systemmeldungen können geändert werden, mithilfe von **Sp_altermessage**.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **Serveradmin** -Serverrolle sein.  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die vorhandene Meldung `55001` im Windows-Anwendungsprotokoll protokolliert.  
  
```  
EXECUTE sp_altermessage 55001, 'WITH_LOG', 'true';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
