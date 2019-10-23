---
title: sp_altermessage (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 4949307cdaf2cc712e56525e872381c2af8256fd
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304796"
---
# <a name="sp_altermessage-transact-sql"></a>sp_altermessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ändert den Status von benutzerdefinierten oder Systemmeldungen in einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Benutzerdefinierte Meldungen können mithilfe der **sys.messages** -Katalogsicht angezeigt werden.  

  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_altermessage [ @message_id = ] message_number   ,[ @parameter = ]'write_to_log'  
   ,[ @parameter_value = ]'value'   
```  
  
## <a name="arguments"></a>Argumente  
 [ **@message_id =** ] *message_number*  
 Die Fehlernummer der Meldung, die von **sys. Messages**geändert werden soll. *message_number* ist vom Datentyp **int** und hat keinen Standardwert.  
  
`[ @parameter = ] 'write\_to\_log_'` wird mit **\@parameter_value** verwendet, um anzugeben, dass die Meldung in das Windows-Anwendungsprotokoll "[!INCLUDE[msCoName](../../includes/msconame-md.md)]" geschrieben werden soll. *write_to_log* ist vom **Datentyp vom Datentyp sysname** und hat keinen Standardwert. *write_to_log* muss auf WITH_LOG oder NULL festgelegt werden. Wenn *write_to_log* auf WITH_LOG oder NULL festgelegt ist und der Wert für **\@parameter_value** auf **true**festgelegt ist, wird die Meldung in das Windows-Anwendungsprotokoll geschrieben. Wenn *write_to_log* auf WITH_LOG oder NULL festgelegt ist und der Wert für **\@parameter_value** auf **false**festgelegt ist, wird die Nachricht nicht immer in das Windows-Anwendungsprotokoll geschrieben, kann jedoch abhängig von der Art des Fehlers geschrieben werden. Wenn *write_to_log* angegeben wird, muss auch der Wert für **\@parameter_value** angegeben werden.  
  
> [!NOTE]  
>  Wenn eine Meldung in das Windows-Anwendungsprotokoll geschrieben wird, wird sie auch in die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Fehlerprotokolldatei geschrieben.  
  
`[ @parameter_value = ]'value_'` wird mit **\@Parameter** verwendet, um anzugeben, dass der Fehler in das Windows-Anwendungsprotokoll "[!INCLUDE[msCoName](../../includes/msconame-md.md)]" geschrieben werden soll. der *Wert* ist vom Datentyp **varchar (5)** und hat keinen Standardwert. Wenn der Wert **true**ist, wird der Fehler immer in das Windows-Anwendungsprotokoll geschrieben. Wenn der Wert **false**ist, wird der Fehler nicht immer in das Windows-Anwendungsprotokoll geschrieben, kann jedoch abhängig von der Art des Fehlers geschrieben werden. Wenn *value* angegeben ist, muss auch *write_to_log* für **\@parameter** angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 None  
  
## <a name="remarks"></a>Hinweise  
 Die Wirkung von **sp_altermessage** mit der WITH_LOG-Option ähnelt der des RAISERROR WITH LOG-Parameters, mit dem Unterschied, dass **sp_altermessage** das Protokollierungs Verhalten einer vorhandenen Nachricht ändert. Wenn eine Meldung so geändert wurde, dass für sie die Option WITH_LOG aktiviert ist, wird sie immer in das Windows-Anwendungsprotokoll geschrieben, unabhängig davon, wie ein Benutzer den Fehler auslöst. Selbst wenn RAISERROR ohne die Option WITH_LOG ausgeführt wird, wird der Fehler in das Windows-Anwendungsprotokoll geschrieben.  
  
 System Meldungen können mithilfe von **sp_altermessage**geändert werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Server Rolle **serveradmin** .  
  
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
  
  
