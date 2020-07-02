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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b84eb615704799d0e63aa139b28356203512ea28
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85716283"
---
# <a name="sp_altermessage-transact-sql"></a>sp_altermessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Ändert den Status von benutzerdefinierten oder Systemmeldungen in einer Instanz von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Benutzerdefinierte Meldungen können mithilfe der **sys.messages** -Katalogsicht angezeigt werden.  

  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_altermessage [ @message_id = ] message_number   ,[ @parameter = ]'write_to_log'  
   ,[ @parameter_value = ]'value'   
```  
  
## <a name="arguments"></a>Argumente  
 [** @message_id =** ] *message_number*  
 Die Fehlernummer der Meldung, die von **sys. Messages**geändert werden soll. *message_number* ist vom Datentyp **int** und hat keinen Standardwert.  
  
`[ @parameter = ] 'write\_to\_log_'`Wird mit ** \@ parameter_value** verwendet, um anzugeben, dass die Meldung in das Windows- [!INCLUDE[msCoName](../../includes/msconame-md.md)] Anwendungsprotokoll geschrieben werden soll. *write_to_log* ist vom **Datentyp vom Datentyp sysname** und hat keinen Standardwert. *write_to_log* muss auf WITH_LOG oder NULL festgelegt werden. Wenn *write_to_log* auf WITH_LOG oder NULL festgelegt ist und der Wert für ** \@ parameter_value** auf **true**festgelegt ist, wird die Meldung in das Windows-Anwendungsprotokoll geschrieben. Wenn *write_to_log* auf WITH_LOG oder NULL festgelegt ist und der Wert für ** \@ parameter_value** auf **false**festgelegt ist, wird die Nachricht nicht immer in das Windows-Anwendungsprotokoll geschrieben, kann jedoch abhängig von der Art des Fehlers geschrieben werden. Wenn *write_to_log* angegeben wird, muss auch der Wert für ** \@ parameter_value** angegeben werden.  
  
> [!NOTE]  
>  Wenn eine Meldung in das Windows-Anwendungsprotokoll geschrieben wird, wird sie auch in die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Fehlerprotokolldatei geschrieben.  
  
`[ @parameter_value = ]'value_'`Wird mit dem- ** \@ Parameter** verwendet, um anzugeben, dass der Fehler in das [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows-Anwendungsprotokoll geschrieben werden soll. der *Wert* ist vom Datentyp **varchar (5)** und hat keinen Standardwert. Wenn der Wert **true**ist, wird der Fehler immer in das Windows-Anwendungsprotokoll geschrieben. Wenn der Wert **false**ist, wird der Fehler nicht immer in das Windows-Anwendungsprotokoll geschrieben, kann jedoch abhängig von der Art des Fehlers geschrieben werden. Wenn *value* angegeben wird, müssen auch *write_to_log* für ** \@ Parameter** angegeben werden.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Die Auswirkung der **sp_altermessage** mit der WITH_LOG-Option ähnelt der des RAISERROR WITH LOG-Parameters, mit dem Unterschied, dass **sp_altermessage** das Protokollierungs Verhalten einer vorhandenen Nachricht ändert. Wenn eine Meldung so geändert wurde, dass für sie die Option WITH_LOG aktiviert ist, wird sie immer in das Windows-Anwendungsprotokoll geschrieben, unabhängig davon, wie ein Benutzer den Fehler auslöst. Selbst wenn RAISERROR ohne die Option WITH_LOG ausgeführt wird, wird der Fehler in das Windows-Anwendungsprotokoll geschrieben.  
  
 System Meldungen können mithilfe von **sp_altermessage**geändert werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der Server Rolle **serveradmin** .  
  
## <a name="examples"></a>Beispiele  
 In diesem Beispiel wird die vorhandene Meldung `55001` im Windows-Anwendungsprotokoll protokolliert.  
  
```  
EXECUTE sp_altermessage 55001, 'WITH_LOG', 'true';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_addmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
