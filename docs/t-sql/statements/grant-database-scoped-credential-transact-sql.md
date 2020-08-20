---
description: GRANT (Berechtigungen für datenbankweit gültige Anmeldeinformationen) (Transact-SQL)
title: GRANT (Datenbankweit gültige Anmeldeinformationen) (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/19/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- GRANT DATABASE SCOPED CREDENTIAL
- GRANT_DATABASE_SCOPED_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], database scoped credential
- permissions [SQL Server], database scoped credential
- database scoped credential [SQL Server], permissions
- GRANT statement, database scoped credentials
ms.assetid: 501f2c8a-6aeb-41af-bf0b-974d17af33c0
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f65bf32fb857b5039f6a48e26d48a8f49eca5a04
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472229"
---
# <a name="grant-database-scoped-credential-permissions-transact-sql"></a>GRANT (Berechtigungen für datenbankweit gültige Anmeldeinformationen) (Transact-SQL)
[!INCLUDE[sqlserver2017-asdb](../../includes/applies-to-version/sqlserver2017-asdb.md)]

  Erteilt Berechtigungen für datenbankweit gültige Anmeldeinformationen. 
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
GRANT permission  [ ,...n ]    
    ON DATABASE SCOPED CREDENTIAL :: credential_name   
    TO principal [ ,...n ] [ WITH GRANT OPTION ]   
    [ AS granting_principal ]   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Argumente
 *permission*  
 Gibt eine Berechtigung an, die für die datenbankweit gültige Anmeldeinformationen erteilt werden kann. Unten aufgeführt.  
  
 ON DATABASE SCOPED CREDENTIAL **::** _credential_name_  
 Gibt die datenbankweit gültigen Anmeldeinformationen an, für die die Berechtigung erteilt wird. Der Bereichsqualifizierer "::" ist erforderlich.  
  
 *database_principal*  
 Gibt den Prinzipal an, für den die Berechtigung erteilt wird. Einer der folgenden:  
  
-   Datenbankbenutzer  
-   Datenbankrolle (database role)  
-   Anwendungsrolle  
-   Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer  
-   Einer Windows-Gruppe zugeordneter Datenbankbenutzer  
-   Einem Zertifikat zugeordneter Datenbankbenutzer  
-   Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer  
-   Keinem Serverprinzipal zugeordneter Datenbankbenutzer.  
  
GRANT OPTION  
 Gibt an, dass der Prinzipal die angegebene Berechtigung auch anderen Prinzipalen erteilen kann.  
  
AS *granting_principal*  
 Gibt einen Prinzipal an, von dem der Prinzipal, der diese Abfrage ausführt, sein Recht zum Erteilen der Berechtigung ableitet. Einer der folgenden:  
  
-   Datenbankbenutzer  
-   Datenbankrolle (database role)  
-   Anwendungsrolle  
-   Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer  
-   Einer Windows-Gruppe zugeordneter Datenbankbenutzer  
-   Einem Zertifikat zugeordneter Datenbankbenutzer  
-   Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer  
-   Keinem Serverprinzipal zugeordneter Datenbankbenutzer.  
  
## <a name="remarks"></a>Hinweise  
 Datenbankweit gültige Anmeldeinformationen sind ein sicherungsfähiges Element auf Datenbankebene in der Datenbank, die das übergeordnete Element in der Berechtigungshierarchie ist. Die spezifischsten und restriktivsten Berechtigungen, die für datenbankweit gültige Anmeldeinformationen erteilt werden können, sind im Folgenden aufgeführt, zusammen mit den allgemeineren Berechtigungen, die sie implizit enthalten.  
  
|Berechtigung für datenbankweit gültige Anmeldeinformationen|Impliziert durch die Berechtigung für datenbankweit gültige Anmeldeinformationen|Impliziert durch Datenbankberechtigung|  
|----------------------------|---------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Berechtigungen  
 Der Berechtigende (oder der mit der AS-Option angegebene Prinzipal) benötigt entweder die Berechtigung selbst mit GRANT OPTION oder eine höhere Berechtigung, die die erteilte Berechtigung impliziert.  
  
 Wenn Sie die Option AS verwenden, gelten die folgenden zusätzlichen Anforderungen.  
  
|AS *granting_principal*|Zusätzliche Berechtigung erforderlich|  
|------------------------------|------------------------------------|  
|Datenbankbenutzer|IMPERSONATE-Berechtigung für den Benutzer, die Mitgliedschaft in der festen Datenbankrolle **db_securityadmin** und **db_owner** oder die Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einem Windows-Anmeldenamen zugeordneter Datenbankbenutzer|IMPERSONATE-Berechtigung für den Benutzer, die Mitgliedschaft in der festen Datenbankrolle **db_securityadmin** und **db_owner** oder die Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einer Windows-Gruppe zugeordneter Datenbankbenutzer|Mitgliedschaft in der Windows-Gruppe, Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einem Zertifikat zugeordneter Datenbankbenutzer|Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einem asymmetrischen Schlüssel zugeordneter Datenbankbenutzer|Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Einem Serverprinzipal zugeordneter Datenbankbenutzer|IMPERSONATE-Berechtigung für den Benutzer, die Mitgliedschaft in der festen Datenbankrolle **db_securityadmin** und **db_owner** oder die Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Datenbankrolle|ALTER-Berechtigung für die Rolle, Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
|Anwendungsrolle|ALTER-Berechtigung für die Rolle, Mitgliedschaft in der festen Datenbankrolle **db_securityadmin**, Mitgliedschaft in der festen Datenbankrolle **db_owner** oder Mitgliedschaft in der festen Serverrolle **sysadmin**.|  
  
 Objektbesitzer können Berechtigungen für die Objekte erteilen, die sie besitzen. Prinzipale mit CONTROL-Berechtigung für ein sicherungsfähiges Element können die Berechtigung für dieses sicherungsfähige Element erteilen.  
  
 Empfänger der CONTROL SERVER-Berechtigung, wie z.B. Mitglieder der festen Serverrolle **sysadmin**, können jede beliebige Berechtigung für jedes beliebige sicherungsfähige Element auf dem Server erteilen. Empfänger der CONTROL-Berechtigung für eine Datenbank, wie z.B. Mitglieder der festen Datenbankrolle **db_owner**, können jede beliebige Berechtigung für jedes beliebige sicherungsfähige Element in der Datenbank erteilen. Empfänger der CONTROL-Berechtigung für ein Schema können jede beliebige Berechtigung für jedes Objekt innerhalb des Schemas erteilen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE (Datenbankweit gültige Anmeldeinformationen) (Transact-SQL)](../../t-sql/statements/revoke-database-scoped-credential-transact-sql.md)   
 [DENY (Datenbankweit gültige Anmeldeinformationen) (Transact-SQL)](../../t-sql/statements/deny-database-scoped-credential-transact-sql.md)   
 [Berechtigungen &#40;Datenbank-Engine&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Prinzipale &#40;Datenbank-Engine&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Verschlüsselungshierarchie](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
