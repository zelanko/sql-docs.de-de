---
title: sp_droprole (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2573019948a326c9171fc83d62428e7e2f888eb5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933811"
---
# <a name="sp_droprole-transact-sql"></a>sp_droprole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Entfernt eine Datenbankrolle aus der aktuellen Datenbank.  
  
> [!IMPORTANT]  
>  In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]wurde **sp_droprole** durch die DROP ROLE-Anweisung ersetzt. **sp_droprole** wird lediglich aus Gründen der Kompatibilität mit früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bereitgestellt und wird in künftigen Versionen möglicherweise nicht mehr unterstützt.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_droprole [ @rolename= ] 'role'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'`Der Name der Daten Bank Rolle, die aus der aktuellen Datenbank entfernt werden soll. *role* ist vom Datentyp **sysname**und hat keinen Standardwert. *role* muss in der aktuellen Datenbank bereits vorhanden sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [Drop Role &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [Alter Authorization &#40;Transact-SQL-&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sp_dropapprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropapprole-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
