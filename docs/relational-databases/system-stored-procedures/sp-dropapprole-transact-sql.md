---
title: sp_dropapprole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropapprole_TSQL
- sp_dropapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropapprole
ms.assetid: ea1aefe6-8f7d-46e9-a3cb-7b037b393e73
ms.author: vanto
author: VanMSFT
ms.openlocfilehash: 740bfcf83aca712dcaeb7189b226d880f7ae5a02
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717307"
---
# <a name="sp_dropapprole-transact-sql"></a>sp_dropapprole (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Entfernt eine Anwendungsrolle aus der aktuellen Datenbank  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Verwenden Sie stattdessen [Drop Application Role](../../t-sql/statements/drop-application-role-transact-sql.md) .  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_dropapprole [@rolename = ] 'role'  
```  
  
## <a name="arguments"></a>Argumente  
`[ @rolename = ] 'role'`Die Anwendungs Rolle, die entfernt werden soll. *role* ist vom Datentyp **sysname**und hat keinen Standardwert. *role* muss in der aktuellen Datenbank vorhanden sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Mithilfe von**sp_dropapprole** können nur Anwendungsrollen entfernt werden. Wenn eine Rolle sicherungsfähige Elemente besitzt, kann die Rolle nicht gelöscht werden. Vor dem Löschen einer Anwendungsrolle, die sicherungsfähige Elemente besitzt, müssen Sie zuerst den Besitz dieser sicherungsfähigen Elemente übertragen oder diese löschen.  
  
 **sp_dropapprole** kann nicht innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY APPLICATION ROLE-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird die `SalesApp` -Anwendungsrolle aus der aktuellen Datenbank entfernt.  
  
```sql
EXEC sp_dropapprole 'SalesApp';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addapprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [Löschen der Anwendungs Rolle &#40;Transact-SQL-&#41;](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [sp_changeobjectowner &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changeobjectowner-transact-sql.md)   
 [sp_setapprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
