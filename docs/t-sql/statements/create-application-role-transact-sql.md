---
description: CREATE APPLICATION ROLE (Transact-SQL)
title: CREATE APPLICATION ROLE (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- APPLICATION_ROLE_TSQL
- CREATE APPLICATION ROLE
- sql13.swb.applicationrole.permissions.f1
- APPLICATION
- APPLICATION ROLE
- CREATE_APPLICATION_ROLE_TSQL
- APPLICATION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE APPLICATION ROLE statement
- application roles [SQL Server], creating
ms.assetid: 647386da-ee80-41cf-86c9-dd590f9d66b6
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: da64f4dfa4c6013a8aba2928236db09004db8f1b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88496967"
---
# <a name="create-application-role-transact-sql"></a>CREATE APPLICATION ROLE (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Fügt der aktuellen Datenbank eine Anwendungsrolle hinzu.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
  
CREATE APPLICATION ROLE application_role_name   
    WITH PASSWORD = 'password' [ , DEFAULT_SCHEMA = schema_name ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *application_role_name*  
 Gibt den Namen der Anwendungsrolle an. Dieser Name darf nicht bereits als Verweis auf einen Prinzipal in der Datenbank verwendet werden.  
  
 PASSWORD **='** _password_ **'**  
 Gibt das Kennwort an, mit dem Datenbankbenutzer die Anwendungsrolle aktivieren. Es sollten immer sichere Kennwörter verwendet werden. *password* muss den Anforderungen der Windows-Kennwortrichtlinien des Computers entsprechen, auf dem die Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgeführt wird.  
  
 DEFAULT_SCHEMA **=** _schema\_name_  
 Gibt das erste Schema an, das vom Server beim Auflösen der Objektnamen für diese Rolle durchsucht wird. Wenn DEFAULT_SCHEMA nicht definiert ist, verwendet die Anwendungsrolle DBO als Standardschema. *schema_name* kann ein Schema sein, das in der Datenbank nicht vorhanden ist.  
  
## <a name="remarks"></a>Bemerkungen  
  
> [!IMPORTANT]  
>  Beim Festlegen von Kennwörtern für Anwendungsrollen wird die Kennwortkomplexität überprüft. Anwendungen, die Anwendungsrollen aufrufen, müssen ihre Kennwörter speichern. Kennwörter für Anwendungsrollen sollten immer verschlüsselt gespeichert werden.  
  
 Anwendungsrollen werden in der [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)-Katalogsicht angezeigt.  
  
 Weitere Informationen hierzu finden Sie unter [Anwendungsrollen](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die ALTER ANY APPLICATION ROLE-Berechtigung in der Datenbank.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird eine Anwendungsrolle mit dem Namen `weekly_receipts` erstellt, die das Kennwort `987Gbv876sPYY5m23` und das Standardschema `Sales` besitzt.  
  
```sql  
CREATE APPLICATION ROLE weekly_receipts   
    WITH PASSWORD = '987G^bv876sPY)Y5m23'   
    , DEFAULT_SCHEMA = Sales;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Anwendungsrollen](../../relational-databases/security/authentication-access/application-roles.md)   
 [sp_setapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [ALTER APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-application-role-transact-sql.md)   
 [DROP APPLICATION ROLE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
