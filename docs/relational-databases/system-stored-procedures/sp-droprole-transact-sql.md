---
title: Sp_droprole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprole
- sp_droprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprole
ms.assetid: 889ee074-00f8-40a9-bddb-d7d3ef0cbc19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 77c642d6b1574006122af74f0538cdb7ef607535
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47620808"
---
# <a name="spdroprole-transact-sql"></a>sp_droprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt eine Datenbankrolle aus der aktuellen Datenbank.  
  
> [!IMPORTANT]  
>  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **Sp_droprole** wurde durch die DROP ROLE-Anweisung ersetzt. **Sp_droprole** ist lediglich aus Gründen der Kompatibilität mit früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und werden in einer zukünftigen Version möglicherweise nicht unterstützt.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droprole [ @rolename= ] 'role'  
```  
  
## <a name="arguments"></a>Argumente  
 [  **@rolename =** ] **"***Rolle***"**  
 Der Name der Datenbankrolle, die aus der aktuellen Datenbank entfernt werden soll. *role* ist vom Datentyp **sysname**und hat keinen Standardwert. *role* muss in der aktuellen Datenbank bereits vorhanden sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Mit **sp_droprole**können nur Datenbankrollen entfernt werden.  
  
 Es ist nicht möglich, eine Datenbankrolle mit vorhandenen Mitgliedern zu entfernen. Vor dem Entfernen der Datenbankrolle müssen zunächst alle Mitglieder aus der Datenbankrolle entfernt werden. Entfernen Sie mithilfe von **sp_droprolemember**Benutzer aus einer Rolle. Sollten Benutzer weiterhin Mitglieder der Rolle sein, zeigen Sie diese Mitglieder mit **sp_droprole** an.  
  
 Feste Rollen und die **public** -Rolle können nicht entfernt werden.  
  
 Es ist nicht möglich, eine Rolle zu entfernen, die sicherungsfähige Elemente besitzt. Vor dem Löschen einer Anwendungsrolle, die sicherungsfähige Elemente besitzt, müssen Sie zuerst den Besitz dieser sicherungsfähigen Elemente übertragen oder diese löschen. Verwenden Sie ALTER AUTHORIZATION, um den Besitzer von Objekten zu ändern, die nicht entfernt werden dürfen.  
  
 **sp_droprole** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die CONTROL-Berechtigung für die Rolle.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die `Sales`-Anwendungsrolle entfernt.  
  
```  
EXEC sp_droprole 'Sales';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Security Stored Procedures &#40;Transact-SQL&#41; (Gespeicherte Sicherheitsprozeduren (Transact-SQL))](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [DROP ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [Sp_dropapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
