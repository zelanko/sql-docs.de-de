---
title: Sp_revokedbaccess (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokedbaccess_TSQL
- sp_revokedbaccess
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokedbaccess
ms.assetid: c997cfa1-539d-485c-a664-9c6f76bfe0c2
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 98e962d5600064194ef4aff4a8f514e39a8f71a4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806774"
---
# <a name="sprevokedbaccess-transact-sql"></a>sp_revokedbaccess (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt einen Datenbankbenutzer aus der aktuellen Datenbank.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Verwendung [DROP USER](../../t-sql/statements/drop-user-transact-sql.md) stattdessen.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_revokedbaccess [ @name_in_db = ] 'name'  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@name_in_db =** ] **'***name***'**  
 Der Name des zu entfernenden Datenbankbenutzers. *Namen* ist eine **Sysname** hat keinen Standardwert. *Namen* kann der Name einer serveranmeldung, einer Windows-Anmeldung oder eine Windows-Gruppe sein, und in der aktuellen Datenbank vorhanden sein. Wenn Sie einen Windows-Anmeldenamen oder eine Windows-Gruppe angeben, verwenden Sie den in der Datenbank bekannten Namen.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Beim Entfernen des Datenbankbenutzers werden auch die Berechtigungen und Aliase entfernt, die von diesem Benutzer abhängen.  
  
 **Sp_revokedbaccess** können nur Datenbankbenutzer aus der aktuellen Datenbank entfernen. Vor dem Entfernen eines Datenbankbenutzers, der Objekte in der aktuellen Datenbank besitzt, müssen Sie entweder den Besitz der Objekte übertragen oder die Objekte aus der Datenbank löschen. Weitere Informationen finden Sie unter [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
 **Sp_revokedbaccess** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY USER-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird der Datenbankbenutzer, der `Edmonds\LolanSo` zugeordnet ist, aus der aktuellen Datenbank entfernt.  
  
```  
EXEC sp_revokedbaccess 'Edmonds\LolanSo';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [DROP USER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-user-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)  
  
  
