---
description: sp_addmessage (Transact-SQL)
title: sp_addmessage (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addmessage
- sp_addmessage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addmessage
ms.assetid: 54746d30-f944-40e5-a707-f2d9be0fb9eb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 86a7c1c41cf9b745efea8b2368d5120f0b03d3ff
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88489567"
---
# <a name="sp_addmessage-transact-sql"></a>sp_addmessage (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Speichert eine neue benutzerdefinierte Fehlermeldung in einer [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]-Instanz. Mithilfe von **sp_addmessage** gespeicherte Nachrichten können mithilfe der **sys. Messages** -Katalog Sicht angezeigt werden.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_addmessage [ @msgnum= ] msg_id , [ @severity= ] severity , [ @msgtext= ] 'msg'   
     [ , [ @lang= ] 'language' ]   
     [ , [ @with_log= ] { 'TRUE' | 'FALSE' } ]   
     [ , [ @replace= ] 'replace' ]   
```  
  
## <a name="arguments"></a>Argumente  
`[ @msgnum = ] msg_id` Die ID der Nachricht. *msg_id* ist vom Datentyp **int** und hat den Standardwert NULL. *msg_id* für benutzerdefinierte Fehlermeldungen kann eine ganze Zahl zwischen 50.001 und 2.147.483.647 sein. Die Kombination aus *msg_id* und *Sprache* muss eindeutig sein. Wenn die ID für die angegebene Sprache bereits vorhanden ist, wird ein Fehler zurückgegeben.  
  
`[ @severity = ]severity` Der Schweregrad des Fehlers. *Schweregrad* ist vom Datentyp **smallint** . der Standardwert ist NULL. Die gültigen Werte reichen von 1 bis 25. Weitere Informationen zu den Schweregraden finden Sie unter [Schweregrade von Datenbank-Engine-Fehlern](../../relational-databases/errors-events/database-engine-error-severities.md).  
  
`[ @msgtext = ] 'msg'` Der Text der Fehlermeldung. *msg* ist vom Datentyp **nvarchar (255)** und hat den Standardwert NULL.  
  
`[ @lang = ] 'language'` Die Sprache für diese Nachricht. *Language* ist vom **Datentyp vom Datentyp sysname** und hat den Standardwert NULL. Da mehrere Sprachen auf demselben Server installiert werden können, gibt *Sprache* die Sprache an, in der die einzelnen Nachrichten geschrieben werden. Wenn *Language* weggelassen wird, ist die Sprache die Standardsprache für die Sitzung.  
  
`[ @with_log = ] { 'TRUE' | 'FALSE' }` Gibt an, ob die Nachricht bei Auftreten in das Windows-Anwendungsprotokoll geschrieben werden soll. ** \@ WITH_LOG** ist vom Datentyp **varchar (5)** und hat den Standardwert false. Bei TRUE wird der Fehler immer in das Windows-Anwendungsprotokoll geschrieben. Bei FALSE wird der Fehler nicht immer in das Windows-Anwendungsprotokoll geschrieben, sondern in Abhängigkeit davon, wie er ausgelöst wurde. Nur Mitglieder der **sysadmin** -Server Rolle können diese Option verwenden.  
  
> [!NOTE]  
>  Wenn eine Meldung in das Windows-Anwendungsprotokoll geschrieben wird, wird sie auch in die [!INCLUDE[ssDE](../../includes/ssde-md.md)]-Fehlerprotokolldatei geschrieben.  
  
`[ @replace = ] 'replace'` Bei Angabe als Zeichenfolge *ersetzen*wird eine vorhandene Fehlermeldung mit neuem Meldungs Text und Schweregrad überschrieben. *Replace* ist vom Datentyp **varchar (7)** und hat den Standardwert NULL. Diese Option muss angegeben werden, wenn *msg_id* bereits vorhanden ist. Wenn Sie eine US-englische Nachricht ersetzen, wird der Schweregrad für alle Nachrichten in allen anderen Sprachen ersetzt, die denselben *msg_id*haben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Keine  
  
## <a name="remarks"></a>Bemerkungen  
 Handelt es sich nicht um eine englischsprachige Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], muss die US-englische Version einer Meldung bereits vorhanden sein, bevor die Meldung mithilfe einer anderen Sprache hinzugefügt werden kann. Der Schweregrad der beiden Versionen der Meldung muss übereinstimmen.  
  
 Verwenden Sie bei der Lokalisierung von Meldungen mit Parametern Parameternummern, die den Parametern der Originalmeldung entsprechen. Fügen Sie nach jeder Parameternummer ein Ausrufezeichen (!) ein.  
  
|Originalmeldung|Lokalisierte Meldung|  
|----------------------|-----------------------|  
|'Originalmeldung Parameter 1: %s,<br /><br /> Parameter 2: %d'|'Lokalisierte Meldung Parameter 1:<br /><br /> param 2: %2! "|  
  
 Wegen Unterschieden in der Sprachsyntax weisen die Parameternummern in der lokalisierten Meldung möglicherweise eine andere Reihenfolge als in der Originalmeldung auf.  
  
## <a name="permissions"></a>Berechtigungen  
Erfordert die Mitgliedschaft in den festen Server Rollen **sysadmin** oder **serveradmin** .  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-defining-a-custom-message"></a>A. Definieren einer benutzerdefinierten Meldung  
 Im folgenden Beispiel wird **sys. Messages**eine benutzerdefinierte Meldung hinzugefügt.  
  
```  
USE master;  
GO  
EXEC sp_addmessage 50001, 16,   
   N'Percentage expects a value between 20 and 100.   
   Please reexecute with a more appropriate value.';  
GO  
```  
  
### <a name="b-adding-a-message-in-two-languages"></a>B. Hinzufügen einer Meldung in zwei Sprachen  
 Im folgenden Beispiel wird zunächst eine Meldung auf US-Englisch und anschließend dieselbe Meldung auf Französisch hinzugefügt`.`  
  
```  
USE master;  
GO  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'The item named %s already exists in %s.',   
   @lang = 'us_english';  
  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'L''élément nommé %1! existe déjà dans %2!',   
   @lang = 'French';  
GO  
```  
  
### <a name="c-changing-the-order-of-parameters"></a>C. Ändern der Reihenfolge von Parametern  
 Im folgenden Beispiel wird zunächst eine Meldung auf US-Englisch und anschließend eine lokalisierte Meldung hinzugefügt, in der die Reihenfolge der Parameter geändert ist.  
  
```  
USE master;  
GO  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        N'This is a test message with one numeric  
        parameter (%d), one string parameter (%s),   
        and another string parameter (%s).',  
    @lang = 'us_english';  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        -- In the localized version of the message,  
        -- the parameter order has changed. The   
        -- string parameters are first and second  
        -- place in the message, and the numeric   
        -- parameter is third place.  
        N'Dies ist eine Testmeldung mit einem   
        Zeichenfolgenparameter (%3!),  
        einem weiteren Zeichenfolgenparameter (%2!),   
        und einem numerischen Parameter (%1!).',  
    @lang = 'German';  
GO    
  
-- Changing the session language to use the U.S. English  
-- version of the error message.  
SET LANGUAGE us_english;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2') -- error, severity, state,  
GO                                       -- parameters.  
  
-- Changing the session language to use the German  
-- version of the error message.  
SET LANGUAGE German;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2'); -- error, severity, state,   
GO                                       -- parameters.  
```  
  
## <a name="see-also"></a>Siehe auch  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_dropmessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
