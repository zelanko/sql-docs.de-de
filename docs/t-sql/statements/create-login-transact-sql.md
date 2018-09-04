---
title: CREATE LOGIN (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/10/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_LOGIN_TSQL
- CREATE LOGIN
- LOGIN_TSQL
- LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], logins
- mapping logins [SQL Server]
- logins [SQL Server], creating
- CREATE LOGIN statement
- permissions [SQL Server], logins
- Windows domain accounts [SQL Server]
- re-hashing passwords
- certificates [SQL Server], logins
ms.assetid: eb737149-7c92-4552-946b-91085d8b1b01
caps.latest.revision: 101
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6a5f2edc15c171a80c16ccc77f11bf7673571d53
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074473"
---
# <a name="create-login-transact-sql"></a>CREATE LOGIN (Transact-SQL)

Erstellt einen Anmeldenamen für SQL Server, SQL-Datenbank, SQL Data Warehouse oder Parallel Data Warehouse-Datenbanken. Klicken Sie auf eine der folgenden Registerkarten, um Syntax, Argumente, Hinweise, Berechtigungen und Beispiele für eine bestimmte Version anzuzeigen.

Weitere Informationen zu Syntaxkonventionen finden Sie unter [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md). 

## <a name="click-a-product"></a>Wählen Sie ein Produkt.

Klicken Sie in der folgenden Zeile auf den Namen des Produkts, das Sie am meisten interessiert. Mit nur einem Klick erhalten Sie auf dieser Webseite unterschiedliche Inhalte, die zu dem Produkt passen, das Sie ausgewählt haben.

::: moniker range=">=sql-server-2016||>=sql-server-linux-2017||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> ||||||
> |-|-|-|-|-|
> |**_\* SQL Server \*_**|[SQL-Datenbank<br />logischer Server](create-login-transact-sql.md?view=azuresqldb-current)|[SQL-Datenbank<br />Verwaltete Instanz](create-login-transact-sql.md?view=azuresqldb-mi-current)|[SQL Data<br />Warehouse](create-login-transact-sql.md?view=azure-sqldw-latest)|[SQL Parallel<br />Data Warehouse](create-login-transact-sql.md?view=aps-pdw-2016)

&nbsp;

# <a name="sql-server"></a>SQL Server

## <a name="syntax"></a>Syntax 
  
```  
-- Syntax for SQL Server  
CREATE LOGIN login_name { WITH <option_list1> | FROM <sources> }  
  
<option_list1> ::=   
    PASSWORD = { 'password' | hashed_password HASHED } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
    SID = sid  
    | DEFAULT_DATABASE = database      
    | DEFAULT_LANGUAGE = language  
    | CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
    | CREDENTIAL = credential_name   
  
<sources> ::=  
    WINDOWS [ WITH <windows_options>[ ,... ] ]  
    | CERTIFICATE certname  
    | ASYMMETRIC KEY asym_key_name  
  
<windows_options> ::=        
    DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
```  
  
## <a name="arguments"></a>Argumente  
*login_name*  
Gibt den Anmeldenamen an, der erstellt wird. Es gibt vier Arten von Anmeldenamen: SQL Server-Anmeldenamen, Windows-Anmeldenamen, Anmeldenamen mit zugeordneten Zertifikaten sowie Anmeldenamen mit zugeordneten asymmetrischen Schlüsseln. Wenn Sie Anmeldenamen erstellen, die von einem Windows-Domänenkonto zugeordnet werden, müssen Sie den Benutzeranmeldenamen einer Version vor Windows 2000 im Format [\<domainName>\\<login_name>] verwenden. Sie können keine UPN im Format login_name@DomainName verwenden. Ein Beispiel hierzu finden Sie unter „Beispiel D“ weiter unten in diesem Artikel. Anmeldenamen für die Authentifizierung sind vom Typ **sysname**. Sie müssen den Regeln für [Bezeichner](../../relational-databases/databases/database-identifiers.md) entsprechen und dürfen keinen „**\\**“ enthalten. Windows-Anmeldenamen können '**\\**'-Zeichen enthalten. Auf Active Directory-Benutzer basierende Anmeldenamen sind auf Namen mit weniger als 21 Zeichen beschränkt. 

PASSWORD **='***Kennwort***'* Gilt nur für SQL Server-Anmeldenamen. Gibt das Kennwort für den Anmeldenamen an, der erstellt wird. Sie sollten ein sicheres Kennwort verwenden. Weitere Informationen finden Sie unter [Sichere Kennwörter](../../relational-databases/security/strong-passwords.md) und [Kennwortrichtlinie](../../relational-databases/security/password-policy.md). Ab SQL Server 2012 (11.x) werden gespeicherte Kennwortinformationen mithilfe der SHA-512-Komponente des mit Salt verschlüsselten Kennworts berechnet. 
  
Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Kennwörter sollten immer mindestens 8 Zeichen lang sein und dürfen 128 Zeichen nicht überschreiten. Kennwörter dürfen a-z, A-Z, 0-9 und die meisten nicht alphanumerischen Zeichen einschließen. Kennwörter dürfen keine einfachen Anführungszeichen oder *login_name* enthalten. 
  
PASSWORD **=***hashed_password*  
Gilt nur für das HASHED-Schlüsselwort. Gibt den Hashwert des Kennworts für den Anmeldenamen an, der erstellt wird. 
  
HASHED Gilt nur für SQL Server-Anmeldenamen. Gibt an, dass das nach dem PASSWORD-Argument eingegebene Kennwort bereits einen Hashwert darstellt. Wenn diese Option nicht ausgewählt wird, wird aus der als Kennwort eingegebenen Zeichenfolge vor dem Speichern in der Datenbank ein Hashwert erstellt. Diese Option sollte nur verwendet werden, um Datenbanken von einem Server auf einen anderen zu migrieren. Verwenden Sie die HASHED-Option nicht, um neue Anmeldenamen zu erstellen. Die HASHED-Option kann nicht mit Hashes verwendet werden, die in SQL 7 oder einer früheren Version erstellt wurden.

MUST_CHANGE Gilt nur für SQL Server-Anmeldenamen. Wenn diese Option angegeben wird, wird der Benutzer von SQL Server zur Eingabe eines neuen Kennworts aufgefordert, wenn der neue Anmeldename zum ersten Mal verwendet wird. 
  
CREDENTIAL **=***credential_name*  
Die Anmeldeinformationen, die dem neuen SQL Server-Anmeldenamen zugeordnet werden sollen. Die Anmeldeinformationen müssen bereits auf dem Server vorhanden sein. Momentan verknüpft diese Option nur die Anmeldeeinformationen mit einem Anmeldenamen. Der Anmeldung eines Systemadministrators können keine Anmeldeinformationen zugeordnet werden. 
  
SID = *sid*  
Wird verwendet, um eine Anmeldung neu zu erstellen. Gilt nur für Anmeldenamen für die SQL Server-Authentifizierung, nicht für Anmeldenamen für die Windows-Authentifizierung. Gibt die SID des neuen Anmeldenamens für die SQL Server-Authentifizierung an. Wenn diese Option nicht verwendet wird, weist SQL Server automatisch eine SID zu. Die SID-Struktur hängt von der SQL Server-Version ab. SID des Anmeldenamens für SQL Server: ein 16-Byte-Literalwert (**binary(16)**) basierend auf einer GUID. Beispiel: `SID = 0x14585E90117152449347750164BA00A7`. 
  
DEFAULT_DATABASE **=***database*  
Gibt die Standarddatenbank an, die dem Anmeldenamen zugewiesen werden soll. Wenn diese Option nicht enthalten ist, wird die Standarddatenbank als „master“ festgelegt. 
  
DEFAULT_LANGUAGE **=***language*  
Gibt die Standardsprache an, die dem Anmeldenamen zugewiesen werden soll. Wenn diese Option nicht enthalten ist, wird die aktuelle Standardsprache des Servers als Standardsprache festgelegt. Wenn die Standardsprache des Servers zu einem späteren Zeitpunkt geändert wird, wird die Standardsprache des Anmeldenamens nicht geändert. 
  
CHECK_EXPIRATION **=** { ON | **OFF** }  
Gilt nur für SQL Server-Anmeldenamen. Gibt an, ob die Richtlinie für das Ablaufen von Kennwörtern für diesen Anmeldenamen erzwungen werden soll. Der Standardwert ist OFF. 
  
CHECK_POLICY **=** { **ON** | OFF }  
Gilt nur für SQL Server-Anmeldenamen. Gibt an, dass die Windows-Kennwortrichtlinien des Computers, auf dem SQL Server ausgeführt wird, für diesen Anmeldenamen erzwungen werden sollen. Der Standardwert ist ON. 
  
Wenn die Windows-Richtlinie sichere Kennwörter erfordert, müssen Kennwörter mindestens drei der folgenden vier Eigenschaften aufweisen:  
  
- Ein Großbuchstabe (A-Z). 
- Ein Kleinbuchstabe (a-z). 
- Eine Ziffer (0-9). 
- Ein nicht alphanumerisches Zeichen, z. B. ein Leerzeichen, _, @, *, ^,%, !, $, # oder &. 
  
WINDOWS  
Gibt an, dass der Anmeldename einem Windows-Anmeldenamen zugeordnet wird. 
  
CERTIFICATE *certname*  
Gibt den Namen eines Zertifikats an, das diesem Anmeldenamen zugeordnet werden soll. Dieses Zertifikat muss bereits in der Masterdatenbank vorhanden sein. 
  
ASYMMETRIC KEY *asym_key_name*  
Gibt den Namen eines asymmetrischen Schlüssels an, der diesem Anmeldenamen zugeordnet werden soll. Dieser Schlüssel muss bereits in der Masterdatenbank vorhanden sein. 
  
## <a name="remarks"></a>Remarks  
- Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.
- Das vorherige Erstellen von Hashwerten für Kennwörter wird nur unterstützt, wenn Sie SQL Server-Anmeldenamen erstellen.
- Falls MUST_CHANGE angegeben wird, müssen CHECK_EXPIRATION und CHECK_POLICY auf ON festgelegt werden. Andernfalls erzeugt die Anweisung einen Fehler.
- Die Kombination aus CHECK_POLICY = OFF und CHECK_EXPIRATION = ON wird nicht unterstützt.
- Wenn CHECK_POLICY auf OFF festgelegt ist, wird *lockout_time* zurückgesetzt, und CHECK_EXPIRATION wird auf OFF festgelegt. 
  
> [!IMPORTANT]  
>  CHECK_EXPIRATION und CHECK_POLICY werden nur unter Windows Server 2003 und höher erzwungen. Weitere Informationen finden Sie unter [Password Policy](../../relational-databases/security/password-policy.md). 
  
- Aus Zertifikaten oder asymmetrischen Schlüsseln erstellte Anmeldenamen werden nur zum Signieren von Code verwendet. Sie können nicht verwendet werden, um eine Verbindung mit SQL Server herzustellen. Sie können einen Anmeldenamen anhand eines Zertifikats oder eines asymmetrischen Schlüssels nur erstellen, wenn das Zertifikat oder der asymmetrische Schlüssel bereits in der Masterdatenbank vorhanden ist. 
- Ein Skript zum Übertragen von Anmeldenamen finden unter [Übertragen von Benutzernamen und Kennwörtern zwischen Instanzen von SQL Server](http://support.microsoft.com/kb/918992).
- Durch das Erstellen eines Anmeldenamens wird der neue Anmeldename automatisch aktiviert, und diesem Anmeldenamen wird die **CONNECT SQL**-Berechtigung auf Serverebene gewährt. 
- Der [Authentifizierungsmodus](../../relational-databases/security/choose-an-authentication-mode.md) muss mit dem Anmeldetyp übereinstimmen, damit der Zugriff gewährt wird.
- Informationen zum Entwerfen eines Berechtigungssystems finden Sie unter [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).

## <a name="permissions"></a>Berechtigungen  
- Nur Benutzer mit **ALTER ANY LOGIN**-Berechtigung auf dem Server oder einer Mitgliedschaft bei der festen Serverrolle **securityadmin** können Anmeldenamen erstellen. Weitere Informationen finden Sie unter [Rollen auf Serverebene](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) und unter [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles.
- Falls die Option **CREDENTIAL** verwendet wird, ist auch die **ALTER ANY CREDENTIAL**-Berechtigung auf dem Server erforderlich. 
  
## <a name="after-creating-a-login"></a>Nach dem Erstellen eines Anmeldenamens  
Nach dem Erstellen eines Anmeldenamens kann mit dem Namen eine Verbindung mit SQL Server hergestellt werden, er verfügt jedoch nur über die der Rolle **public** gewährten Berechtigungen. Ziehen Sie die Ausführung einiger der folgenden Aktivitäten in Betracht. 
  
 - Erstellen Sie zum Herstellen einer Verbindung mit einer Datenbank einen Datenbankbenutzer für den Anmeldenamen. Weitere Informationen finden Sie unter [CREATE USER](../../t-sql/statements/create-user-transact-sql.md). 
  
 - Erstellen sie eine benutzerdefinierte Serverrolle mit [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md). Verwenden Sie **ALTER SERVER ROLE** ... **ADD MEMBER**, um der benutzerdefinierten Serverrolle den neuen Anmeldenamen hinzuzufügen. Weitere Informationen finden Sie unter [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md) und unter [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). 
  
 - Fügen Sie den Anmeldenamen mit **sp_addsrvrolemember** einer festen Serverrolle hinzu. Weitere Informationen finden Sie unter [Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md) und unter [sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md). 
  
 - Gewähren Sie mit der **GRANT**-Anweisung Berechtigungen auf Serverebene für den neuen Anmeldenamen oder für eine Rolle, die den Anmeldenamen enthält. Weitere Informationen finden Sie unter [GRANT](../../t-sql/statements/grant-transact-sql.md). 
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-a-login-with-a-password"></a>A. Erstellen einer Anmeldung mit einem Kennwort  
 Im folgenden Beispiel wird ein Anmeldename für einen bestimmten Benutzer erstellt, und es wird ein Kennwort zugewiesen. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-with-a-password-that-must-be-changed"></a>B. Erstellen einer Anmeldung mit einem zu ändernden Kennwort
 Im folgenden Beispiel wird ein Anmeldename für einen bestimmten Benutzer erstellt, und es wird ein Kennwort zugewiesen. Die Option `MUST_CHANGE` erfordert, dass Benutzer dieses Kennwort ändern, wenn sie das erste Mal eine Verbindung mit dem Server herstellen. 
  
**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>' 
    MUST_CHANGE,  CHECK_EXPIRATION = ON;
GO  
``` 

> [!NOTE]
> Die Option MUST_CHANGE kann nicht verwendet werden, wenn CHECK_EXPIRATION auf OFF festgelegt ist.
  
### <a name="c-creating-a-login-mapped-to-a-credential"></a>C. Erstellen eines Anmeldenamens, der Anmeldeinformationen zugeordnet ist  
 Im folgenden Beispiel wird unter Verwendung des Benutzers der Anmeldename für einen bestimmten Benutzer erstellt. Dieser Anmeldename wird den Anmeldeinformationen zugeordnet. 
  
**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>',   
    CREDENTIAL = <credentialName>;  
GO  
```  
  
### <a name="d-creating-a-login-from-a-certificate"></a>D. Erstellen eines Anmeldenamens aus einem Zertifikat  
 Im folgenden Beispiel wird der Anmeldename für eine bestimmte Benutzer-ID von einem Zertifikat in der Masterdatenbank erstellt. 
  
**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
```sql
USE MASTER;  
CREATE CERTIFICATE <certificateName>  
    WITH SUBJECT = '<login_name> certificate in master database',  
    EXPIRY_DATE = '12/05/2025';  
GO  
CREATE LOGIN <login_name> FROM CERTIFICATE <certificateName>;  
GO  
```  
  
### <a name="e-creating-a-login-from-a-windows-domain-account"></a>E. Erstellen eines Anmeldenamens von einem Windows-Domänenkonto  
 Im folgenden Beispiel wird ein Anmeldename von einem Windows-Domänenkonto erstellt. 
  
**Gilt für**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] bis [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
```sql  
CREATE LOGIN [<domainName>\<login_name>] FROM WINDOWS;  
GO  
```  
  
### <a name="f-creating-a-login-from-a-sid"></a>F. Erstellen eines Anmeldenamens aus einer SID  
 Im folgenden Beispiel wird ein Anmeldename für die SQL Server-Authentifizierung erstellt und die SID des Anmeldenamens festgelegt. 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 Die Abfrage hier gibt 0x241C11948AEEB749B0D22646DB1A19F2 als SID zurück. Die Abfrage gibt einen anderen Wert zurück. Die folgenden Anweisungen löschen den Anmeldenamen und erstellen dann erneut die Anmeldung. Verwenden Sie die SID aus der vorherigen Abfrage. 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
- [Erste Schritte mit Berechtigungen für die Datenbank-Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
- [Prinzipale &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
- [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)   
- [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
- [Erstellen eines Anmeldenamens](../../relational-databases/security/authentication-access/create-a-login.md)  
  
::: moniker-end
::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="create-login-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><strong><em>* SQL-Datenbank<br />SQL-Datenbank-Server *</em></strong></th>
>   <th><a href="create-login-transact-sql.md?view=azuresqldb-mi-current">SQL-Datenbank<br />SQL-Datenbank-Instanz</a></th>
>   <th><a href="create-login-transact-sql.md?view=azure-sqldw-latest">SQL Data<br />Warehouse</a></th>
>   <th><a href="create-login-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="azure-sql-database-logical-server"></a>Logischer Azure SQL-Datenbank-Server
  
## <a name="syntax"></a>Syntax 
  
```
-- Syntax for Azure SQL Database  
CREATE LOGIN login_name  
 { WITH <option_list> }  
  
<option_list> ::=   
    PASSWORD = { 'password' }  
    [ , SID = sid ]  
```  

## <a name="arguments"></a>Argumente  
*login_name*  
Gibt den Anmeldenamen an, der erstellt wird. Azure SQL-Datenbank (logischer Server) unterstützt nur SQL-Anmeldenamen. 

PASSWORD **='** Kennwort**'*  
Gibt das Kennwort für den SQL-Anmeldenamen an, der erstellt wird. Sie sollten ein sicheres Kennwort verwenden. Weitere Informationen finden Sie unter [Sichere Kennwörter](../../relational-databases/security/strong-passwords.md) und [Kennwortrichtlinie](../../relational-databases/security/password-policy.md). Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden gespeicherte Kennwortinformationen mithilfe der SHA-512-Komponente des mit Salt verschlüsselten Kennworts berechnet. 
  
Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Kennwörter sollten immer mindestens 8 Zeichen lang sein und dürfen 128 Zeichen nicht überschreiten. Kennwörter dürfen a-z, A-Z, 0-9 und die meisten nicht alphanumerischen Zeichen einschließen. Kennwörter dürfen keine einfachen Anführungszeichen oder *login_name* enthalten. 

SID = *sid*  
Wird verwendet, um eine Anmeldung neu zu erstellen. Gilt nur für Anmeldenamen für die SQL Server-Authentifizierung, nicht für Anmeldenamen für die Windows-Authentifizierung. Gibt die SID des neuen Anmeldenamens für die SQL Server-Authentifizierung an. Wenn diese Option nicht verwendet wird, weist SQL Server automatisch eine SID zu. Die SID-Struktur hängt von der SQL Server-Version ab. Bei SQL-Datenbank ist dies normalerweise ein 32-Byte-Literalwert (**binary(32)**) bestehend aus `0x01060000000000640000000000000000` plus 16 Byte, die eine GUID darstellen. Beispiel: `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`. 
  
## <a name="remarks"></a>Remarks  
- Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.
- Ein Skript zum Übertragen von Anmeldenamen finden unter [Übertragen von Benutzernamen und Kennwörtern zwischen Instanzen von SQL Server](http://support.microsoft.com/kb/918992).
- Durch das Erstellen eines Anmeldenamens wird der neue Anmeldename automatisch aktiviert, und diesem Anmeldenamen wird die **CONNECT SQL**-Berechtigung auf Serverebene gewährt. 
- Der [Authentifizierungsmodus](../../relational-databases/security/choose-an-authentication-mode.md) muss mit dem Anmeldetyp übereinstimmen, damit der Zugriff gewährt wird.
    - Informationen zum Entwerfen eines Berechtigungssystems finden Sie unter [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).
  
## <a name="login"></a>Anmeldename

### <a name="sql-database-logins"></a>Anmeldenamen für SQL-Datenbanken
Die **CREATE LOGIN**-Anweisung muss die einzige Anweisung in einem Batch sein. 
  
In einigen Methoden zum Herstellen einer Verbindung mit SQL-Datenbank, z.B. **sqlcmd**, müssen Sie den Servernamen von SQL-Datenbank mit der *\<login>*@*\<server>*-Notation an den Anmeldenamen in der Verbindungszeichenfolge anfügen. Wenn Ihr Anmeldename beispielsweise `login1` und der vollqualifizierte Name des Servers von SQL-Datenbank `servername.database.windows.net` lautet, sollte der Parameter *username* der Verbindungszeichenfolge `login1@servername` lauten. Da die Gesamtlänge des *username*-Parameters 128 Zeichen beträgt, ist *login_name* auf 127 Zeichen abzüglich der Länge des Servernamens beschränkt. Im Beispiel darf `login_name` nur 117 Zeichen lang sein, da `servername` 10 Zeichen enthält. 
  
In SQL-Datenbank muss eine Verbindung mit der Masterdatenbank bestehen, um einen Anmeldenamen erstellen zu können. 
  
 Mithilfe von SQL Server-Regeln können Sie einen Anmeldenamen für die SQL Server-Authentifizierung im Format \<loginname>@\<servername> erstellen. Wenn der [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Servername **myazureserver** und der Anmeldename **myemail@live.com** lauten, müssen Sie den Anmeldenamen als **myemail@live.com@myazureserver** bereitstellen. 
  
In SQL-Datenbank werden Anmeldedaten, die für die Authentifizierung einer Verbindung und für Firewallregeln auf Serverebene erforderlich sind, über einen gewissen Zeitraum in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um eine Aktualisierung des Authentifizierungscache zu erzwingen und sicherzustellen, dass eine Datenbank über die aktuelle Version der Tabelle mit Anmeldenamen verfügt. 
  
 Weitere Informationen zu Anmeldenamen für SQL-Datenbank finden Sie unter [Verwalten von Datenbanken und Anmeldenamen in der Windows Azure SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins). 
 
## <a name="permissions"></a>Berechtigungen

Neue Anmeldenamen können nur mit den Anmeldenamen des Serverebenenprinzipals (im Bereitstellungsprozess erstellt) oder von Mitgliedern der `loginmanager`-Datenbankrolle in der Masterdatenbank erstellt werden. Weitere Informationen finden Sie unter [Rollen auf Serverebene](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) und unter [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles.

## <a name="logins"></a>Anmeldungen
- Erfordert eine **ALTER ANY LOGIN**-Berechtigung auf dem Server oder eine Mitgliedschaft bei der festen Serverrolle**securityadmin**. Dieser Befehl kann nur auf dem Azure AD-Konto (Azure Active Directory) mit der **ALTER ANY LOGIN**-Berechtigung auf dem Server oder mit einer Mitgliedschaft bei der Serverrolle „securityadmin“ ausgeführt werden
- Muss in dem gleichen Verzeichnis, das auch für den logischen Azure SQL-Server verwendet wird, ein Azure AD-Mitglied sein
  
## <a name="after-creating-a-login"></a>Nach dem Erstellen eines Anmeldenamens  
Nach dem Erstellen eines Anmeldenamens kann mit diesem Namen eine Verbindung mit der SQL-Datenbank hergestellt werden. Er verfügt jedoch nur über die der Rolle **public** erteilten Berechtigungen. Ziehen Sie die Ausführung einiger der folgenden Aktivitäten in Betracht. 
  
- Erstellen Sie zum Herstellen einer Verbindung mit einer Datenbank einen Datenbankbenutzer für den Anmeldenamen in dieser Datenbank. Weitere Informationen finden Sie unter [CREATE USER](../../t-sql/statements/create-user-transact-sql.md). 
- Verwenden Sie für die Erteilung von Berechtigungen für einen Benutzer in einer Datenbank die Anweisung **ALTER SERVER ROLE**... **ADD MEMBER**-Anweisung, um die Verwendung zu einer der integrierten Datenbankrollen oder einer benutzerdefinierten Rolle hinzuzufügen oder um Berechtigungen für den Benutzer zu erteilen, indem Sie die Anweisung [GRANT]((../../t-sql/statements/grant-transact-sql.md) direkt verwenden. Weitere Informationen finden Sie unter [Nichtadministratorrollen](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#non-administrator-users) und bei den Anweisungen [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles und [GRANT](grant-transact-sql.md).
- Wenn Sie serverweite Berechtigungen erteilen möchten, erstellen Sie in der Masterdatenbank einen Datenbankbenutzer, und verwenden Sie die Anweisung **ALTER SERVER ROLE**... **ADD MEMBER**-Anweisung, um die Verwendung zu einer der administrativen Serverrollen hinzuzufügen. Weitere Informationen finden Sie unter [Rollen auf Serverebene](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) und unter [Serverrollen](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles).
- Gewähren Sie mit der **GRANT**-Anweisung Berechtigungen auf Serverebene für den neuen Anmeldenamen oder für eine Rolle, die den Anmeldenamen enthält. Weitere Informationen finden Sie unter [GRANT](../../t-sql/statements/grant-transact-sql.md).
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-a-login-with-a-password"></a>A. Erstellen einer Anmeldung mit einem Kennwort  
 Im folgenden Beispiel wird ein Anmeldename für einen bestimmten Benutzer erstellt, und es wird ein Kennwort zugewiesen. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-from-a-sid"></a>B. Erstellen eines Anmeldenamens aus einer SID  
 Im folgenden Beispiel wird ein Anmeldename für die SQL Server-Authentifizierung erstellt und die SID des Anmeldenamens festgelegt. 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 Die Abfrage hier gibt 0x241C11948AEEB749B0D22646DB1A19F2 als SID zurück. Die Abfrage gibt einen anderen Wert zurück. Die folgenden Anweisungen löschen den Anmeldenamen und erstellen dann erneut die Anmeldung. Verwenden Sie die SID aus der vorherigen Abfrage. 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erste Schritte mit Berechtigungen für die Datenbank-Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Prinzipale &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [Erstellen eines Anmeldenamens](../../relational-databases/security/authentication-access/create-a-login.md)  

::: moniker-end
::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="create-login-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><a href="create-login-transact-sql.md?view=azuresqldb-current">SQL-Datenbank<br />SQL-Datenbank-Server</a></th>
>   <th><strong><em>* SQL-Datenbank<br />Verwaltete Instanz *</em></strong></th>
>   <th><a href="create-login-transact-sql.md?view=azure-sqldw-latest">SQL Data<br />Warehouse</a></th>
>   <th><a href="create-login-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="azure-sql-database-managed-instance"></a>Verwaltete Azure SQL-Datenbank-Instanz.

## <a name="overview"></a>Übersicht

## <a name="syntax"></a>Syntax 
  
```sql
-- Syntax for Azure SQL Database  
CREATE LOGIN login_name  
 { WITH <option_list> }  
  
<option_list> ::=   
    PASSWORD = { 'password' }  
    [ , SID = sid ]  
```  

## <a name="arguments"></a>Argumente  
*login_name*  
Gibt den Anmeldenamen an, der erstellt wird. Azure SQL-Datenbank (Verwaltete Instanz) unterstützt nur SQL-Anmeldenamen. 

PASSWORD **='** Kennwort**'*  
Gibt das Kennwort für den SQL-Anmeldenamen an, der erstellt wird. Sie sollten ein sicheres Kennwort verwenden. Weitere Informationen finden Sie unter [Sichere Kennwörter](../../relational-databases/security/strong-passwords.md) und [Kennwortrichtlinie](../../relational-databases/security/password-policy.md). Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden gespeicherte Kennwortinformationen mithilfe der SHA-512-Komponente des mit Salt verschlüsselten Kennworts berechnet. 
  
Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Kennwörter sollten immer mindestens 8 Zeichen lang sein und dürfen 128 Zeichen nicht überschreiten. Kennwörter dürfen a-z, A-Z, 0-9 und die meisten nicht alphanumerischen Zeichen einschließen. Kennwörter dürfen keine einfachen Anführungszeichen oder *login_name* enthalten. 

SID = *sid*  
Wird verwendet, um eine Anmeldung neu zu erstellen. Gilt nur für Anmeldenamen für die SQL Server-Authentifizierung, nicht für Anmeldenamen für die Windows-Authentifizierung. Gibt die SID des neuen Anmeldenamens für die SQL Server-Authentifizierung an. Wenn diese Option nicht verwendet wird, weist SQL Server automatisch eine SID zu. Die SID-Struktur hängt von der SQL Server-Version ab. Bei SQL-Datenbank ist dies normalerweise ein 32-Byte-Literalwert (**binary(32)**) bestehend aus `0x01060000000000640000000000000000` plus 16 Byte, die eine GUID darstellen. Beispiel: `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`. 
  
## <a name="remarks"></a>Remarks  
- Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.
- Ein Skript zum Übertragen von Anmeldenamen finden unter [Übertragen von Benutzernamen und Kennwörtern zwischen Instanzen von SQL Server](http://support.microsoft.com/kb/918992).
- Durch das Erstellen eines Anmeldenamens wird der neue Anmeldename automatisch aktiviert, und diesem Anmeldenamen wird die **CONNECT SQL**-Berechtigung auf Serverebene gewährt. 
- Der [Authentifizierungsmodus](../../relational-databases/security/choose-an-authentication-mode.md) muss mit dem Anmeldetyp übereinstimmen, damit der Zugriff gewährt wird.
    - Informationen zum Entwerfen eines Berechtigungssystems finden Sie unter [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).
  
## <a name="login"></a>Anmeldename

### <a name="sql-database-logins"></a>Anmeldenamen für SQL-Datenbanken
Die **CREATE LOGIN**-Anweisung muss die einzige Anweisung in einem Batch sein. 
  
In einigen Methoden zum Herstellen einer Verbindung mit SQL-Datenbank, z.B. **sqlcmd**, müssen Sie den Servernamen von SQL-Datenbank mit der *\<login>*@*\<server>*-Notation an den Anmeldenamen in der Verbindungszeichenfolge anfügen. Wenn Ihr Anmeldename beispielsweise `login1` und der vollqualifizierte Name des Servers von SQL-Datenbank `servername.database.windows.net` lautet, sollte der Parameter *username* der Verbindungszeichenfolge `login1@servername` lauten. Da die Gesamtlänge des *username*-Parameters 128 Zeichen beträgt, ist *login_name* auf 127 Zeichen abzüglich der Länge des Servernamens beschränkt. Im Beispiel darf `login_name` nur 117 Zeichen lang sein, da `servername` 10 Zeichen enthält. 
  
In SQL-Datenbank muss eine Verbindung mit der Masterdatenbank bestehen, um einen Anmeldenamen erstellen zu können. 
  
 Mithilfe von SQL Server-Regeln können Sie einen Anmeldenamen für die SQL Server-Authentifizierung im Format \<loginname>@\<servername> erstellen. Wenn der [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Servername **myazureserver** und der Anmeldename **myemail@live.com** lauten, müssen Sie den Anmeldenamen als **myemail@live.com@myazureserver** bereitstellen. 
  
In SQL-Datenbank werden Anmeldedaten, die für die Authentifizierung einer Verbindung und für Firewallregeln auf Serverebene erforderlich sind, über einen gewissen Zeitraum in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um eine Aktualisierung des Authentifizierungscache zu erzwingen und sicherzustellen, dass eine Datenbank über die aktuelle Version der Tabelle mit Anmeldenamen verfügt. 
  
 Weitere Informationen zu Anmeldenamen für SQL-Datenbank finden Sie unter [Verwalten von Datenbanken und Anmeldenamen in der Windows Azure SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins). 
 
## <a name="permissions"></a>Berechtigungen

Neue Anmeldenamen können nur mit den Anmeldenamen des Serverebenenprinzipals (im Bereitstellungsprozess erstellt) oder von Mitgliedern der `loginmanager`-Datenbankrolle in der Masterdatenbank erstellt werden. Weitere Informationen finden Sie unter [Rollen auf Serverebene](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) und unter [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles.

## <a name="logins"></a>Anmeldungen
- Erfordert eine **ALTER ANY LOGIN**-Berechtigung auf dem Server oder eine Mitgliedschaft bei der festen Serverrolle**securityadmin**. Dieser Befehl kann nur auf dem Azure AD-Konto (Azure Active Directory) mit der **ALTER ANY LOGIN**-Berechtigung auf dem Server oder mit einer Mitgliedschaft bei der Serverrolle „securityadmin“ ausgeführt werden
- Muss in dem gleichen Verzeichnis, das auch für den logischen Azure SQL-Server verwendet wird, ein Azure AD-Mitglied sein
  
## <a name="after-creating-a-login"></a>Nach dem Erstellen eines Anmeldenamens  
Nach dem Erstellen eines Anmeldenamens kann mit diesem Namen eine Verbindung mit der SQL-Datenbank hergestellt werden. Er verfügt jedoch nur über die der Rolle **public** erteilten Berechtigungen. Ziehen Sie die Ausführung einiger der folgenden Aktivitäten in Betracht. 
  
- Erstellen Sie zum Herstellen einer Verbindung mit einer Datenbank einen Datenbankbenutzer für den Anmeldenamen in dieser Datenbank. Weitere Informationen finden Sie unter [CREATE USER](../../t-sql/statements/create-user-transact-sql.md). 
- Verwenden Sie für die Erteilung von Berechtigungen für einen Benutzer in einer Datenbank die Anweisung **ALTER SERVER ROLE**... **ADD MEMBER**-Anweisung, um die Verwendung zu einer der integrierten Datenbankrollen oder einer benutzerdefinierten Rolle hinzuzufügen oder um Berechtigungen für den Benutzer zu erteilen, indem Sie die Anweisung [GRANT]((../../t-sql/statements/grant-transact-sql.md) direkt verwenden. Weitere Informationen finden Sie unter [Nichtadministratorrollen](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#non-administrator-users) und bei den Anweisungen [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles und [GRANT](grant-transact-sql.md).
- Wenn Sie serverweite Berechtigungen erteilen möchten, erstellen Sie in der Masterdatenbank einen Datenbankbenutzer, und verwenden Sie die Anweisung **ALTER SERVER ROLE**... **ADD MEMBER**-Anweisung, um die Verwendung zu einer der administrativen Serverrollen hinzuzufügen. Weitere Informationen finden Sie unter [Rollen auf Serverebene](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) und unter [Serverrollen](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles).
- Gewähren Sie mit der **GRANT**-Anweisung Berechtigungen auf Serverebene für den neuen Anmeldenamen oder für eine Rolle, die den Anmeldenamen enthält. Weitere Informationen finden Sie unter [GRANT](../../t-sql/statements/grant-transact-sql.md).
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-a-login-with-a-password"></a>A. Erstellen einer Anmeldung mit einem Kennwort  
 Im folgenden Beispiel wird ein Anmeldename für einen bestimmten Benutzer erstellt, und es wird ein Kennwort zugewiesen. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-from-a-sid"></a>B. Erstellen eines Anmeldenamens aus einer SID  
 Im folgenden Beispiel wird ein Anmeldename für die SQL Server-Authentifizierung erstellt und die SID des Anmeldenamens festgelegt. 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 Die Abfrage hier gibt 0x241C11948AEEB749B0D22646DB1A19F2 als SID zurück. Die Abfrage gibt einen anderen Wert zurück. Die folgenden Anweisungen löschen den Anmeldenamen und erstellen dann erneut die Anmeldung. Verwenden Sie die SID aus der vorherigen Abfrage. 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erste Schritte mit Berechtigungen für die Datenbank-Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Prinzipale &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [Erstellen eines Anmeldenamens](../../relational-databases/security/authentication-access/create-a-login.md)  


  
::: moniker-end
::: moniker range="=azure-sqldw-latest||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="create-login-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><a href="create-login-transact-sql.md?view=azuresqldb-current">SQL-Datenbank<br />SQL-Datenbank-Server</a></th>>   <th><strong><em>* SQL Data<br />Warehouse *</em></strong></th>
>   <th><a href="create-login-transact-sql.md?view=aps-pdw-2016">SQL Parallel<br />Data Warehouse</a></th>
> </tr>
> </table>

&nbsp;

# <a name="azure-sql-data-warehouse"></a>Azure SQL Data Warehouse
  
## <a name="syntax"></a>Syntax 
  
```
-- Syntax for Azure SQL Data Warehouse  
CREATE LOGIN login_name  
 { WITH <option_list> }  
  
<option_list> ::=   
    PASSWORD = { 'password' }  
    [ , SID = sid ]  
```  
  
## <a name="arguments"></a>Argumente  
*login_name*  
Gibt den Anmeldenamen an, der erstellt wird. Die Azure SQL-Datenbank unterstützt nur SQL-Anmeldenamen. 

PASSWORD **='** Kennwort**'*  
Gibt das Kennwort für den SQL-Anmeldenamen an, der erstellt wird. Sie sollten ein sicheres Kennwort verwenden. Weitere Informationen finden Sie unter [Sichere Kennwörter](../../relational-databases/security/strong-passwords.md) und [Kennwortrichtlinie](../../relational-databases/security/password-policy.md). Ab [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] werden gespeicherte Kennwortinformationen mithilfe der SHA-512-Komponente des mit Salt verschlüsselten Kennworts berechnet. 
  
Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Kennwörter sollten immer mindestens 8 Zeichen lang sein und dürfen 128 Zeichen nicht überschreiten. Kennwörter dürfen a-z, A-Z, 0-9 und die meisten nicht alphanumerischen Zeichen einschließen. Kennwörter dürfen keine einfachen Anführungszeichen oder *login_name* enthalten. 

 SID = *sid*  
 Wird verwendet, um eine Anmeldung neu zu erstellen. Gilt nur für Anmeldenamen für die SQL Server-Authentifizierung, nicht für Anmeldenamen für die Windows-Authentifizierung. Gibt die SID des neuen Anmeldenamens für die SQL Server-Authentifizierung an. Wenn diese Option nicht verwendet wird, weist SQL Server automatisch eine SID zu. Die SID-Struktur hängt von der SQL Server-Version ab. Bei SQL Data Warehouse ist dies normalerweise ein 32-Byte-Literalwert (**binary(32)**) bestehend aus `0x01060000000000640000000000000000` plus 16 Byte, die eine GUID darstellen. Beispiel: `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`. 
  
## <a name="remarks"></a>Remarks  
- Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.
- Ein Skript zum Übertragen von Anmeldenamen finden unter [Übertragen von Benutzernamen und Kennwörtern zwischen Instanzen von SQL Server](http://support.microsoft.com/kb/918992).
- Durch das Erstellen eines Anmeldenamens wird der neue Anmeldename automatisch aktiviert, und diesem Anmeldenamen wird die **CONNECT SQL**-Berechtigung auf Serverebene gewährt. 
- Der [Authentifizierungsmodus](../../relational-databases/security/choose-an-authentication-mode.md) muss mit dem Anmeldetyp übereinstimmen, damit der Zugriff gewährt wird.
    - Informationen zum Entwerfen eines Berechtigungssystems finden Sie unter [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).
  
## <a name="logins"></a>Anmeldungen

Die **CREATE LOGIN**-Anweisung muss die einzige Anweisung in einem Batch sein. 
  
Bei einigen Methoden zum Herstellen einer Verbindung mit SQL Data Warehouse, z.B. **sqlcmd**, müssen Sie den Servernamen von SQL Data Warehouse mit der *\<login>*@*\<server>*-Notation an den Anmeldenamen in der Verbindungszeichenfolge anfügen. Wenn Ihr Anmeldenamen beispielsweise `login1` und der vollqualifizierte Name des SQL Data Warehouse-Servers `servername.database.windows.net` lautet, sollte der Parameter *username* der Verbindungszeichenfolge `login1@servername` lauten. Da die Gesamtlänge des *username*-Parameters 128 Zeichen beträgt, ist *login_name* auf 127 Zeichen abzüglich der Länge des Servernamens beschränkt. Im Beispiel darf `login_name` nur 117 Zeichen lang sein, da `servername` 10 Zeichen enthält. 
  
In SQL Data Warehouse muss eine Verbindung mit der Masterdatenbank bestehen, um einen Anmeldenamen erstellen zu können. 
  
 Mithilfe von SQL Server-Regeln können Sie einen Anmeldenamen für die SQL Server-Authentifizierung im Format \<loginname>@\<servername> erstellen. Wenn der [!INCLUDE[ssSDS](../../includes/sssds-md.md)]-Servername **myazureserver** und der Anmeldename **myemail@live.com** lauten, müssen Sie den Anmeldenamen als **myemail@live.com@myazureserver** bereitstellen. 
  
In SQL Data Warehouse werden Anmeldedaten, die für die Authentifizierung einer Verbindung und für Firewallregeln auf Serverebene erforderlich sind, temporär in jeder Datenbank gespeichert. Dieser Cache wird regelmäßig aktualisiert. Führen Sie [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md) aus, um eine Aktualisierung des Authentifizierungscache zu erzwingen und sicherzustellen, dass eine Datenbank über die aktuelle Version der Tabelle mit Anmeldenamen verfügt. 
  
 Weitere Informationen zu Anmeldenamen für SQL Data Warehouse finden Sie unter [Verwalten von Datenbanken und Anmeldenamen in Windows Azure SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins). 
 
## <a name="permissions"></a>Berechtigungen

Neue Anmeldenamen können nur mit den Anmeldenamen des Serverebenenprinzipals (im Bereitstellungsprozess erstellt) oder von Mitgliedern der `loginmanager`-Datenbankrolle in der Masterdatenbank erstellt werden. Weitere Informationen finden Sie unter [Rollen auf Serverebene](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) und unter [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles.

## <a name="after-creating-a-login"></a>Nach dem Erstellen eines Anmeldenamens  
Nach dem Erstellen eines Anmeldenamens kann mit diesem Namen eine Verbindung mit SQL Data Warehouse hergestellt werden, er verfügt jedoch nur über die der Rolle **public** gewährten Berechtigungen. Ziehen Sie die Ausführung einiger der folgenden Aktivitäten in Betracht. 
  
- Erstellen Sie zum Herstellen einer Verbindung mit einer Datenbank einen Datenbankbenutzer für den Anmeldenamen. Weitere Informationen finden Sie unter [CREATE USER](../../t-sql/statements/create-user-transact-sql.md).
- Verwenden Sie für die Erteilung von Berechtigungen für einen Benutzer in einer Datenbank die Anweisung **ALTER SERVER ROLE**... **ADD MEMBER**-Anweisung, um die Verwendung zu einer der integrierten Datenbankrollen oder einer benutzerdefinierten Rolle hinzuzufügen oder um Berechtigungen für den Benutzer zu erteilen, indem Sie die Anweisung [GRANT](grant-transact-sql.md) direkt verwenden. Weitere Informationen finden Sie unter [Nichtadministratorrollen](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#non-administrator-users) und bei den Anweisungen [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles und [GRANT](grant-transact-sql.md).
- Wenn Sie serverweite Berechtigungen erteilen möchten, erstellen Sie in der Masterdatenbank einen Datenbankbenutzer, und verwenden Sie die Anweisung **ALTER SERVER ROLE**... **ADD MEMBER**-Anweisung, um die Verwendung zu einer der administrativen Serverrollen hinzuzufügen. Weitere Informationen finden Sie unter [Rollen auf Serverebene](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) und unter [Serverrollen](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles).

- Gewähren Sie mit der **GRANT**-Anweisung Berechtigungen auf Serverebene für den neuen Anmeldenamen oder für eine Rolle, die den Anmeldenamen enthält. Weitere Informationen finden Sie unter [GRANT](../../t-sql/statements/grant-transact-sql.md). 
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-creating-a-login-with-a-password"></a>A. Erstellen einer Anmeldung mit einem Kennwort  
Im folgenden Beispiel wird ein Anmeldename für einen bestimmten Benutzer erstellt, und es wird ein Kennwort zugewiesen. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  

### <a name="b-creating-a-login-from-a-sid"></a>B. Erstellen eines Anmeldenamens aus einer SID  
 Im folgenden Beispiel wird ein Anmeldename für die SQL Server-Authentifizierung erstellt und die SID des Anmeldenamens festgelegt. 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 Die Abfrage hier gibt 0x241C11948AEEB749B0D22646DB1A19F2 als SID zurück. Die Abfrage gibt einen anderen Wert zurück. Die folgenden Anweisungen löschen den Anmeldenamen und erstellen dann erneut die Anmeldung. Verwenden Sie die SID aus der vorherigen Abfrage. 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erste Schritte mit Berechtigungen für die Datenbank-Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Prinzipale &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [Erstellen eines Anmeldenamens](../../relational-databases/security/authentication-access/create-a-login.md)  
  
::: moniker-end
::: moniker range="=aps-pdw-2016||=sqlallproducts-allversions"

> [!div class="mx-tdCol2BreakAll"]
> <table>
> <tr>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
>   <th> &nbsp; </th>
> </tr>
> <tr>
>   <th><a href="create-login-transact-sql.md?view=sql-server-2016">SQL Server</a></th>
>   <th><a href="create-login-transact-sql.md?view=azuresqldb-current">SQL-Datenbank<br />SQL-Datenbank-Server</a></th>
>   <th><a href="create-login-transact-sql.md?view=azure-sqldw-latest">SQL Data<br />Warehouse</a></th>
>   <th><strong><em>* SQL Parallel<br />Data Warehouse *</em></strong></th>
> </tr>
> </table>

&nbsp;

# <a name="sql-parallel-data-warehouse"></a>SQL Parallel Data Warehouse

  
## <a name="syntax"></a>Syntax 
  
```
-- Syntax for Parallel Data Warehouse  
CREATE LOGIN loginName { WITH <option_list1> | FROM WINDOWS }  
  
<option_list1> ::=   
    PASSWORD = { 'password' } [ MUST_CHANGE ]  
    [ , <option_list> [ ,... ] ]  
  
<option_list> ::=    
      CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
```  

## <a name="arguments"></a>Argumente  
*login_name*  
Gibt den Anmeldenamen an, der erstellt wird. Es gibt vier Arten von Anmeldenamen: SQL Server-Anmeldenamen, Windows-Anmeldenamen, Anmeldenamen mit zugeordneten Zertifikaten sowie Anmeldenamen mit zugeordneten asymmetrischen Schlüsseln. Wenn Sie Anmeldenamen erstellen, die von einem Windows-Domänenkonto zugeordnet werden, müssen Sie den Benutzeranmeldenamen einer Version vor Windows 2000 im Format [\<domainName>\\<login_name>] verwenden. Sie können keine UPN im Format login_name@DomainName verwenden. Ein Beispiel hierzu finden Sie unter „Beispiel D“ weiter unten in diesem Artikel. Anmeldenamen für die Authentifizierung sind vom Typ **sysname**. Sie müssen den Regeln für [Bezeichner](../../relational-databases/databases/database-identifiers.md) entsprechen und dürfen keinen „**\\**“ enthalten. Windows-Anmeldenamen können '**\\**'-Zeichen enthalten. Auf Active Directory-Benutzer basierende Anmeldenamen sind auf Namen mit weniger als 21 Zeichen beschränkt. 

PASSWORD **='***Kennwort***'* Gilt nur für SQL Server-Anmeldenamen. Gibt das Kennwort für den Anmeldenamen an, der erstellt wird. Sie sollten ein sicheres Kennwort verwenden. Weitere Informationen finden Sie unter [Sichere Kennwörter](../../relational-databases/security/strong-passwords.md) und [Kennwortrichtlinie](../../relational-databases/security/password-policy.md). Ab SQL Server 2012 (11.x) werden gespeicherte Kennwortinformationen mithilfe der SHA-512-Komponente des mit Salt verschlüsselten Kennworts berechnet. 
  
Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden. Kennwörter sollten immer mindestens 8 Zeichen lang sein und dürfen 128 Zeichen nicht überschreiten. Kennwörter dürfen a-z, A-Z, 0-9 und die meisten nicht alphanumerischen Zeichen einschließen. Kennwörter dürfen keine einfachen Anführungszeichen oder *login_name* enthalten. 
  
MUST_CHANGE Gilt nur für SQL Server-Anmeldenamen. Wenn diese Option angegeben wird, wird der Benutzer von SQL Server zur Eingabe eines neuen Kennworts aufgefordert, wenn der neue Anmeldename zum ersten Mal verwendet wird. 
  
CHECK_EXPIRATION **=** { ON | **OFF** }  
Gilt nur für SQL Server-Anmeldenamen. Gibt an, ob die Richtlinie für das Ablaufen von Kennwörtern für diesen Anmeldenamen erzwungen werden soll. Der Standardwert ist OFF. 
  
CHECK_POLICY **=** { **ON** | OFF }  
Gilt nur für SQL Server-Anmeldenamen. Gibt an, dass die Windows-Kennwortrichtlinien des Computers, auf dem SQL Server ausgeführt wird, für diesen Anmeldenamen erzwungen werden sollen. Der Standardwert ist ON. 
  
Wenn die Windows-Richtlinie sichere Kennwörter erfordert, müssen Kennwörter mindestens drei der folgenden vier Eigenschaften aufweisen:  
  
- Ein Großbuchstabe (A-Z). 
- Ein Kleinbuchstabe (a-z). 
- Eine Ziffer (0-9). 
- Ein nicht alphanumerisches Zeichen, z. B. ein Leerzeichen, _, @, *, ^,%, !, $, # oder &. 
  
WINDOWS  
Gibt an, dass der Anmeldename einem Windows-Anmeldenamen zugeordnet wird. 
  
## <a name="remarks"></a>Remarks  
- Bei Kennwörtern wird nach Groß- und Kleinschreibung unterschieden.
- Falls MUST_CHANGE angegeben wird, müssen CHECK_EXPIRATION und CHECK_POLICY auf ON festgelegt werden. Andernfalls erzeugt die Anweisung einen Fehler.
- Die Kombination aus CHECK_POLICY = OFF und CHECK_EXPIRATION = ON wird nicht unterstützt.
- Wenn CHECK_POLICY auf OFF festgelegt ist, wird *lockout_time* zurückgesetzt, und CHECK_EXPIRATION wird auf OFF festgelegt. 
  
> [!IMPORTANT]  
>  CHECK_EXPIRATION und CHECK_POLICY werden nur unter Windows Server 2003 und höher erzwungen. Weitere Informationen finden Sie unter [Password Policy](../../relational-databases/security/password-policy.md). 
  
- Ein Skript zum Übertragen von Anmeldenamen finden unter [Übertragen von Benutzernamen und Kennwörtern zwischen Instanzen von SQL Server](http://support.microsoft.com/kb/918992).
- Durch das Erstellen eines Anmeldenamens wird der neue Anmeldename automatisch aktiviert, und diesem Anmeldenamen wird die **CONNECT SQL**-Berechtigung auf Serverebene gewährt. 
- Informationen zum Entwerfen eines Berechtigungssystems finden Sie unter [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).

## <a name="permissions"></a>Berechtigungen  
Nur Benutzer mit **ALTER ANY LOGIN**-Berechtigung auf dem Server oder einer Mitgliedschaft bei der festen Serverrolle **securityadmin** können Anmeldenamen erstellen. Weitere Informationen finden Sie unter [Rollen auf Serverebene](https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#groups-and-roles) und unter [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). https://docs.microsoft.com/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles.
  
## <a name="after-creating-a-login"></a>Nach dem Erstellen eines Anmeldenamens  
Nach dem Erstellen eines Anmeldenamens kann mit diesem Namen eine Verbindung mit SQL Data Warehouse hergestellt werden, er verfügt jedoch nur über die der Rolle **public** gewährten Berechtigungen. Ziehen Sie die Ausführung einiger der folgenden Aktivitäten in Betracht. 
  
 - Erstellen Sie zum Herstellen einer Verbindung mit einer Datenbank einen Datenbankbenutzer für den Anmeldenamen. Weitere Informationen finden Sie unter [CREATE USER](../../t-sql/statements/create-user-transact-sql.md). 
  
 - Erstellen sie eine benutzerdefinierte Serverrolle mit [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md). Verwenden Sie **ALTER SERVER ROLE** ... **ADD MEMBER**, um der benutzerdefinierten Serverrolle den neuen Anmeldenamen hinzuzufügen. Weitere Informationen finden Sie unter [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md) und unter [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). 
  
 - Fügen Sie den Anmeldenamen mit **sp_addsrvrolemember** einer festen Serverrolle hinzu. Weitere Informationen finden Sie unter [Rollen auf Serverebene](../../relational-databases/security/authentication-access/server-level-roles.md) und unter [sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md). 
  
 - Gewähren Sie mit der **GRANT**-Anweisung Berechtigungen auf Serverebene für den neuen Anmeldenamen oder für eine Rolle, die den Anmeldenamen enthält. Weitere Informationen finden Sie unter [GRANT](../../t-sql/statements/grant-transact-sql.md). 
  
## <a name="examples"></a>Beispiele  
  
### <a name="g-creating-a-sql-server-authentication-login-with-a-password"></a>G. Erstellen einer SQL Server-Authentifizierungsanmeldung mit einem Kennwort  
 Im folgenden Beispiel wird der Anmeldename `Mary7` mit dem Kennwort `A2c3456` erstellt. 
  
```sql  
CREATE LOGIN Mary7 WITH PASSWORD = 'A2c3456$#' ;  
```  
  
### <a name="h-using-options"></a>H. Using-Optionen  
 Im folgenden Beispiel wird der Anmeldename `Mary8` mit Kennwörtern und einigen optionalen Argumenten erstellt. 
  
```sql  
CREATE LOGIN Mary8 WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
```  
  
### <a name="i-creating-a-login-from-a-windows-domain-account"></a>I. Erstellen eines Anmeldenamens von einem Windows-Domänenkonto  
 Im folgenden Beispiel wird ein Anmeldename von einem Windows-Domänenkonto mit dem Namen `Mary` in der Domäne `Contoso` erstellt. 
  
```sql  
CREATE LOGIN [Contoso\Mary] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 [Erste Schritte mit Berechtigungen für die Datenbank-Engine](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Prinzipale &amp;amp;#40;Datenbank-Engine&amp;amp;#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Kennwortrichtlinie](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [Erstellen eines Anmeldenamens](../../relational-databases/security/authentication-access/create-a-login.md)  
  
---  

::: moniker-end
