---
title: sp_dropuser (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropuser
- sp_dropuser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropuser
ms.assetid: e28f18f9-7ecf-4568-89f4-fe5c520df386
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42628ab49e30a4c6dada2eafb505435b8b389de6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124721"
---
# <a name="sp_dropuser-transact-sql"></a>sp_dropuser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt einen Datenbankbenutzer aus der aktuellen Datenbank. **sp_dropuser** bietet Kompatibilität mit früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Drop User](../../t-sql/statements/drop-user-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_dropuser [ @name_in_db = ] 'user'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @name_in_db = ] 'user'`Der Name des zu entfernenden Benutzers. *User* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. der *Benutzer* muss in der aktuellen Datenbank vorhanden sein. Wenn Sie einen Windows-Anmeldenamen angeben, verwenden Sie den Namen, mit dem der Anmeldename von der Datenbank identifiziert wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_dropuser** führt **sp_revokedbaccess** aus, um den Benutzer aus der aktuellen Datenbank zu entfernen.  
  
 Verwenden Sie **sp_helpuser** , um eine Liste der Benutzernamen anzuzeigen, die aus der aktuellen Datenbank entfernt werden können.  
  
 Wenn ein Datenbankbenutzer entfernt wird, werden auch alle Aliase für diesen Benutzer entfernt. Wenn der Benutzer ein leeres Schema mit dem gleichen Namen wie der Benutzer besitzt, wird das Schema gelöscht. Wenn der Benutzer andere sicherungsfähige Elemente in der Datenbank besitzt, wird der Benutzer nicht gelöscht. Der Besitz der Objekte muss zuerst auf einen anderen Prinzipal übertragen werden. Weitere Informationen finden Sie unter [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md). Beim Entfernen eines Datenbankbenutzers werden automatisch die Berechtigungen dieses Benutzers entfernt, und der Benutzer wird aus allen Datenbankrollen entfernt, in denen er Mitglied ist.  
  
 **sp_dropuser** können nicht verwendet werden, um den Datenbankbesitzer (**dbo**) **INFORMATION_SCHEMA** Benutzer oder den **Gast** Benutzer aus den Datenbanken **Master** oder **tempdb** zu entfernen. In nicht-System Datenbanken `EXEC sp_dropuser 'guest'` wird die CONNECT-Berechtigung vom Benutzer **Gast**widerrufen. Der Benutzer selbst wird jedoch nicht gelöscht.  
  
 **sp_dropuser** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY USER-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Benutzer `Albert` aus der aktuellen Datenbank entfernt.  
  
```  
EXEC sp_dropuser 'Albert';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [Drop User &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
