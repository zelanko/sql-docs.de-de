---
title: sp_unsetapprole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_unsetapprole_TSQL
- sp_unsetapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_unsetapprole
ms.assetid: 4c4033d3-1a34-4dfb-835d-e3293d1a442d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 18fe415653a912bda012e786b0a65e5f5b30dd3c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85891362"
---
# <a name="sp_unsetapprole-transact-sql"></a>sp_unsetapprole (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Deaktiviert eine Anwendungsrolle und setzt den Sicherheitskontext auf den vorherigen Kontext zurück.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_unsetapprole @cookie   
```  
  
## <a name="arguments"></a>Argumente  
 **\@KS**  
 Gibt das Cookie an, das beim Aktivieren der Anwendungsrolle erstellt wurde. Das Cookie wird von [sp_setapprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)erstellt. **varbinary (8000)**.  
  
> [!NOTE]  
>  Der **OUTPUT** -Cookieparameter für **sp_setapprole** ist zurzeit als **varbinary(8000)** dokumentiert, was der korrekten maximalen Länge entspricht. Die aktuelle Implementierung gibt jedoch **varbinary(50)** zurück. Anwendungen müssen weiterhin **varbinary(8000)** reservieren, damit die Anwendung weiterhin ordnungsgemäß ausgeführt wird, falls die Rückgabegröße des Cookies in einer zukünftigen Version erhöht wird.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 Eine durch **sp_setapprole**aktivierte Anwendungsrolle bleibt aktiv, bis der Benutzer die Serververbindung trennt oder bis er **sp_unsetapprole**ausführt.  
  
 Eine Übersicht über Anwendungsrollen finden Sie unter [Application Roles](../../relational-databases/security/authentication-access/application-roles.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in **public** und die Kenntnis des Cookies, das beim Aktivieren der Anwendungsrolle erstellt wurde.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="activating-an-application-role-with-a-cookie-then-reverting-to-the-previous-context"></a>Aktivieren einer Anwendungsrolle mit einem Cookie und anschließendes Zurücksetzen auf den vorherigen Kontext  
 Im folgenden Beispiel wird die `Sales11` -Anwendungsrolle mit dem Kennwort `fdsd896#gfdbfdkjgh700mM`aktiviert, und es wird ein Cookie erstellt. Der Name des aktuellen Benutzers wird zurückgegeben, und der Kontext wird anschließend durch Ausführen von **sp_unsetapprole**auf den ursprünglichen Kontext zurückgesetzt.  
  
```  
DECLARE @cookie varbinary(8000);  
EXEC sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.   
GO   
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sp_setapprole &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Gespeicherte Sicherheits Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Erstellen einer Anwendungs Rolle &#40;Transact-SQL-&#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-application-role-transact-sql.md)  
  
  
