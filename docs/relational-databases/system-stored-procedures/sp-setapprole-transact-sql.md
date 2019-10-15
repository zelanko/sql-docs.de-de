---
title: sp_setapprole (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/12/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_setapprole
- sp_setapprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: de85505295ceff98f404b2ba4c1effe3946fdbe5
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304965"
---
# <a name="sp_setapprole-transact-sql"></a>sp_setapprole (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Aktiviert die Berechtigungen, die mit einer Anwendungsrolle in der aktuellen Datenbank verknüpft sind.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  

```sql
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```

## <a name="arguments"></a>Argumente

`[ @rolename = ] 'role'` ist der Name der in der aktuellen Datenbank definierten Anwendungs Rolle. *Role* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. *role* muss in der aktuellen Datenbank vorhanden sein.  
  
`[ @password = ] { encrypt N'password' }` ist das Kennwort, das zum Aktivieren der Anwendungs Rolle erforderlich ist. *Password* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Das *Kennwort* kann mithilfe der ODBC-Funktion " **verschlüsseln** " verdeckt werden. Wenn Sie die Funktion " **verschlüsseln** " verwenden, muss das Kennwort in eine Unicode-Zeichenfolge konvertiert werden, indem **N** vor dem ersten Anführungszeichen platziert wird.  
  
 Die Verschlüsselungsoption wird für Verbindungen, die **SqlClient**verwenden, nicht unterstützt.  
  
> [!IMPORTANT]  
> Die ODBC-Funktion zum **verschlüsseln** bietet keine Verschlüsselung. Diese Funktion ist zum Schützen von Kennwörtern, die über ein Netzwerk übertragen werden, nicht empfehlenswert. Verwenden Sie SSL oder IPSec, um diese Informationen über ein Netzwerk zu übertragen.
  
 **@encrypt = "None"**  
 Gibt an, dass keine Verbergung verwendet wird. Das Kennwort wird als Nur-Text an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] übergeben. Dies ist die Standardeinstellung.  
  
 **@encrypt = ' ODBC '**  
 Gibt an, dass ODBC das Kennwort mithilfe der ODBC- **Verschlüsselungs** Funktion verbirgt, bevor das Kennwort an den [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] gesendet wird. Dies ist nur mit einem ODBC-Client oder dem OLE DB-Anbieter für SQL Server möglich.  
  
`[ @fCreateCookie = ] true | false` gibt an, ob ein Cookie erstellt werden soll. **true** wird implizit in 1 konvertiert. **false** wird implizit in 0 konvertiert.  
  
`[ @cookie = ] @cookie OUTPUT` gibt einen Ausgabeparameter an, der das Cookie enthalten soll. Das Cookie wird nur generiert, wenn der Wert **\@fikreatecookie** **true**ist. **varbinary(8000)**  
  
> [!NOTE]  
> Der **OUTPUT** -Cookieparameter für **sp_setapprole** ist zurzeit als **varbinary(8000)** dokumentiert, was der korrekten maximalen Länge entspricht. Die aktuelle Implementierung gibt jedoch **varbinary(50)** zurück. Anwendungen müssen weiterhin **varbinary(8000)** reservieren, damit die Anwendung weiterhin ordnungsgemäß ausgeführt wird, falls die Rückgabegröße des Cookies in einer zukünftigen Version erhöht wird.
  
## <a name="return-code-values"></a>Rückgabecodewerte

 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="remarks"></a>Hinweise

 Eine durch **sp_setapprole**aktivierte Anwendungsrolle bleibt aktiv, bis der Benutzer die Serververbindung trennt oder bis er **sp_unsetapprole**ausführt. **sp_setapprole** kann nur durch direkte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungen ausgeführt werden. **sp_setapprole** kann nicht innerhalb einer anderen gespeicherten Prozedur oder innerhalb einer benutzerdefinierten Transaktion ausgeführt werden.  
  
 Eine Übersicht über Anwendungsrollen finden Sie unter [Application Roles](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!IMPORTANT]  
> Um das Kennwort der Anwendungs Rolle zu schützen, wenn es über ein Netzwerk übertragen wird, sollten Sie immer eine verschlüsselte Verbindung verwenden, wenn Sie eine Anwendungs Rolle aktivieren.
> Die Option "[!INCLUDE[msCoName](../../includes/msconame-md.md)] ODBC- **Verschlüsselung** " wird von **SqlClient**nicht unterstützt. Wenn Sie Anmeldeinformationen speichern müssen, verschlüsseln Sie sie mit den CryptoAPI-Funktionen. Das Parameter *Kennwort* wird als unidirektionaler Hash gespeichert. Um die Kompatibilität mit früheren Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beizubehalten, wird die Kenn Wort Komplexitäts Richtlinie von **sp_addapprole**nicht erzwungen. Verwenden Sie zum Erzwingen der Richtlinie für die Kenn Wort Komplexität [Create Application Role](../../t-sql/statements/create-application-role-transact-sql.md).  
  
## <a name="permissions"></a>Berechtigungen

Erfordert die Mitgliedschaft in **öffentlichem** und Kenntnis des Kennworts für die Rolle.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>A. Aktivieren einer Anwendungsrolle ohne die encrypt-Option

 Im folgenden Beispiel wird eine Anwendungsrolle namens `SalesAppRole` mit dem Nur-Text-Kennwort `AsDeF00MbXX` sowie mit den Berechtigungen aktiviert, die speziell für die vom aktuellen Benutzer verwendete Anwendung entworfen wurden.

```sql
EXEC sys.sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO
```

### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>B. Aktivieren einer Anwendungsrolle mit einem Cookie und anschließendes Zurücksetzen des ursprünglichen Kontexts

 Im folgenden Beispiel wird die `Sales11` -Anwendungsrolle mit dem Kennwort `fdsd896#gfdbfdkjgh700mM`aktiviert, und es wird ein Cookie erstellt. Im Beispiel wird der Name des aktuellen Benutzers zurückgegeben, und der Kontext wird anschließend durch Ausführen von `sp_unsetapprole` auf den ursprünglichen Kontext zurückgesetzt.  

```sql
DECLARE @cookie varbinary(8000);  
EXEC sys.sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sys.sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.
GO
```

## <a name="see-also"></a>Siehe auch

 [Gespeicherte System &#40;Prozeduren Transact&#41; -SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) - [Sicherheit gespeicherte Prozeduren &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md) [Create Application role &#40;Transact-SQL&#41; ](../../t-sql/statements/create-application-role-transact-sql.md) [Drop Application role &#40; Transact-SQL&#41; ](../../t-sql/statements/drop-application-role-transact-sql.md) [sp_unsetapprole &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)
