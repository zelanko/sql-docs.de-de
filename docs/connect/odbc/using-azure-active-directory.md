---
title: Verwenden von Azure Active Directory mit dem ODBC Driver | Microsoft-Dokumentation für SQL Server
ms.custom: ''
ms.date: 11/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e32889ceafa78d6c6eac716fca213f17badc5cea
ms.sourcegitcommit: 12051861337c21229cfbe5584e8adaff063fc8e3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77363222"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Verwenden von Azure Active Directory mit dem ODBC Driver
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Zweck

Der Microsoft ODBC Driver for SQL Server 13.1 oder höher ermöglicht ODBC-Anwendungen das Herstellen einer Verbindung mit einer SQL Azure-Instanz unter Verwendung dieser Optionen: Verbundidentität in Azure Active Directory mit Benutzername/Kennwort, Azure Active Directory-Zugriffstoken, verwaltete Azure Active Directory-Dienstidentität oder integrierte Windows-Authentifizierung (_nur Windows-Treiber_). Bei der ODBC Driver-Version 13.1 funktioniert die Authentifizierung über ein Azure Active Directory-Zugriffstoken _nur unter Windows_. Die ODBC Driver-Version 17 und höhere Versionen unterstützen diese Authentifizierung auf allen Plattformen (Windows, Linux und Mac). In der ODBC Driver-Version 17.1 für Windows wird eine neue interaktive Azure Active Directory-Authentifizierung mit Anmelde-ID eingeführt. In der ODBC Driver-Version 17.3.1.1 wurde eine neue Authentifizierungsmethode mit verwalteten Azure Active Directory-Dienstidentitäten sowohl für systemseitig als auch für benutzerseitig zugewiesene Identitäten hinzugefügt. All diese Methoden werden mithilfe von neuen Schlüsselwörtern für DSN und Verbindungszeichenfolgen sowie von Verbindungsattributen umgesetzt.

> [!NOTE]
> Der ODBC-Treiber unterstützt unter Linux und macOS ausschließlich die Azure Key Vault-Authentifizierung nur direkt für Azure Active Directory. Wenn Sie die Benutzernamen-/Kennwortauthentifizierung von Azure Active Directory über einen Linux- oder macOS-Client verwenden und erforderlich ist, dass sich der Client beim Active Directory-Verbunddienstendpunkt authentifiziert, kann bei der Authentifizierung ein Fehler auftreten.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Neue und/oder geänderte Schlüsselwörter für DSN und Verbindungszeichenfolgen

Das Schlüsselwort `Authentication` kann beim Herstellen einer Verbindung mit einem DSN oder einer Verbindungszeichenfolge verwendet werden, um den Authentifizierungsmodus zu steuern. Der in der Verbindungszeichenfolge festgelegte Wert überschreibt den Wert im DSN, sofern angegeben. Der _pre-attribute-Wert_ der Einstellung `Authentication` ist der Wert, der aus den Werten für Verbindungszeichenfolge und DSN berechnet wird.

|Name|Werte|Standard|BESCHREIBUNG|
|-|-|-|-|
|`Authentication`|(nicht festgelegt), (leere Zeichenfolge), `SqlPassword`, `ActiveDirectoryPassword`, `ActiveDirectoryIntegrated`, `ActiveDirectoryInteractive`, `ActiveDirectoryMsi` |(nicht festgelegt)|Steuert den Authentifizierungsmodus.<table><tr><th>value<th>Beschreibung<tr><td>(nicht festgelegt)<td>Der Authentifizierungsmodus wird durch andere Schlüsselwörter bestimmt (vorhandene ältere Verbindungsoptionen).<tr><td>(leere Zeichenfolge)<td>(Nur Verbindungszeichenfolge.) Überschreibt und löscht einen im DSN festgelegten `Authentication`-Wert.<tr><td>`SqlPassword`<td>Direkte Authentifizierung bei einer SQL Server-Instanz unter Verwendung eines Benutzernamens und eines Kennworts.<tr><td>`ActiveDirectoryPassword`<td>Authentifizierung mit einer Azure Active Directory-Identität unter Verwendung eines Benutzernamens und eines Kennworts.<tr><td>`ActiveDirectoryIntegrated`<td>_Nur Windows-Treiber_. Authentifizierung mit einer Azure Active Directory-Identität unter Verwendung der integrierten Authentifizierung.<tr><td>`ActiveDirectoryInteractive`<td>_Nur Windows-Treiber_. Authentifizierung mit einer Azure Active Directory-Identität unter Verwendung der interaktiven Authentifizierung.<tr><td>`ActiveDirectoryMsi`<td>Authentifizierung mit einer Azure Active Directory-Identität unter Verwendung der Authentifizierung mit einer verwalteten Dienstidentität. Für die Identität, die dem Benutzer zugewiesen wurde, ist die Benutzer-ID auf die Objekt-ID der Benutzeridentität festgelegt.</table>|
|`Encrypt`|(nicht festgelegt), `Yes`, `No`|(Siehe Beschreibung)|Steuert die Verschlüsselung für eine Verbindung. Wenn der pre-attribute-Wert der Einstellung `Authentication` im DSN oder der Verbindungszeichenfolge nicht _none_ lautet, ist der Standardwert `Yes`. Andernfalls ist der Standardwert `No`. Wenn das Attribut `SQL_COPT_SS_AUTHENTICATION` den pre-attribute-Wert `Authentication` überschreibt, legen Sie den Wert von „Encryption“ im DSN, in der Verbindungszeichenfolge oder im Verbindungsattribut explizit fest. Der pre-attribute-Wert von „Encryption“ ist `Yes`, wenn der Wert im DSN oder in der Verbindungszeichenfolge auf `Yes` festgelegt ist.|

## <a name="new-andor-modified-connection-attributes"></a>Neue und/oder geänderte Verbindungsattribute

Die folgenden pre-connect-Verbindungsattribute wurden eingeführt oder geändert, um die Azure Active Directory-Authentifizierung zu unterstützen. Wenn ein Verbindungsattribut über ein entsprechendes Schlüsselwort für Verbindungszeichenfolge oder DSN verfügt und festgelegt ist, hat das Verbindungsattribut Vorrang.

|attribute|type|Werte|Standard|BESCHREIBUNG|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_AD_MSI`, `SQL_AU_RESET`|(nicht festgelegt)|Siehe Beschreibung des `Authentication`-Schlüsselworts weiter oben. `SQL_AU_NONE` wird bereitgestellt, um einen festgelegten `Authentication`-Wert im DSN und/oder der Verbindungszeichenfolge explizit zu überschreiben. `SQL_AU_RESET` hebt die Festlegung des Attributs auf, falls dieses festgelegt war, sodass der DSN- bzw. Verbindungszeichenfolgenwert Vorrang erhalten kann.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Zeiger auf `ACCESSTOKEN` oder NULL|NULL|Wenn der Wert ungleich NULL ist, wird hiermit das zu verwendende Azure AD-Zugriffstoken angegeben. Es ist ein Fehler, ein Zugriffstoken und auch die Schlüsselwörter `UID`, `PWD`, `Trusted_Connection` oder `Authentication` für Verbindungszeichenfolgen oder deren äquivalente Attribute anzugeben. <br> **HINWEIS:** Die ODBC Driver-Version 13.1 unterstützt dies nur unter _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(Siehe Beschreibung)|Steuert die Verschlüsselung für eine Verbindung. `SQL_EN_OFF` und `SQL_EN_ON` deaktivieren und aktivieren Sie Verschlüsselung bzw. Wenn der pre-attribute-Wert der Einstellung `Authentication` nicht _none_ lautet oder `SQL_COPT_SS_ACCESS_TOKEN` festgelegt ist und `Encrypt` weder im DSN noch in der Verbindungszeichenfolge angegeben wurde, lautet der Standardwert `SQL_EN_ON`. Andernfalls ist der Standardwert `SQL_EN_OFF`. Wenn das Verbindungsattribut `SQL_COPT_SS_AUTHENTICATION` auf einen anderen Wert als _none_ festgelegt ist, legen Sie `SQL_COPT_SS_ENCRYPT` explizit auf den gewünschten Wert fest, wenn `Encrypt` im DSN oder der Verbindungszeichenfolge nicht angegeben war. Der effektive Wert dieses Attributs steuert, [ob die Verschlüsselung für die Verbindung verwendet wird](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation).|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Wird mit Azure Active Directory nicht unterstützt, da Kennwortänderungen bei Azure Active Directory-Prinzipalen nicht über eine ODBC-Verbindung durchgeführt werden können. <br><br>Der Ablauf von Kennwörtern bei der SQL Server-Authentifizierung wurde mit SQL Server 2005 eingeführt. Das `SQL_COPT_SS_OLDPWD`-Attribut wurde hinzugefügt, damit der Client sowohl das alte als auch das neue Kennwort für die Verbindung angeben kann. Wenn diese Eigenschaft festgelegt ist, verwendet der Anbieter für die erste Verbindung oder für nachfolgende Verbindungen keinen Verbindungspool, da die Verbindungszeichenfolge das "alte Kennwort" enthält, das inzwischen geändert wurde.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Veraltet_. Verwenden Sie stattdessen `SQL_COPT_SS_AUTHENTICATION`, festgelegt auf `SQL_AU_AD_INTEGRATED`. <br><br>Erzwingt die Verwendung der Windows-Authentifizierung (Kerberos unter Linux und macOS) für die Überprüfung des Zugriffs bei der Serveranmeldung. Wenn die Windows-Authentifizierung verwendet wird, ignoriert der Treiber die Werte für Benutzer-ID und Kennwort, die bei der Verarbeitung von `SQLConnect`, `SQLDriverConnect` oder `SQLBrowseConnect` bereitgestellt werden.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Ergänzungen der Benutzeroberfläche für Azure Active Directory (nur Windows-Treiber)

Die Benutzeroberflächen für DSN-Setup und Verbindungen des Treibers wurden um die zusätzlichen Optionen erweitert, die zur Verwendung der Authentifizierung mit Azure AD erforderlich sind.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Erstellen und Bearbeiten von DSNs auf der Benutzeroberfläche

Sie können die neuen Azure AD-Authentifizierungsoptionen verwenden, wenn Sie einen neuen DSN über die Setup-Benutzeroberfläche des Treibers erstellen oder bearbeiten:

`Authentication=ActiveDirectoryIntegrated` für die integrierte Azure Active Directory-Authentifizierung bei SQL Azure

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword` für die Azure Active Directory-Authentifizierung bei SQL Azure mit Benutzername und Kennwort

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` für die interaktive Azure Active Directory-Authentifizierung für SQL Azure

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword` für die Authentifizierung bei SQL Server (Azure oder andere Plattform) mit Benutzername/Kennwort

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes` für die ältere integrierte Windows-Authentifizierung über SSPI

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

Die fünf Optionen entsprechen `Trusted_Connection=Yes` (vorhandene ältere integrierte Windows-Authentifizierung nur über SSPI), `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, `ActiveDirectoryPassword` bzw. `ActiveDirectoryInteractive`.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect-Eingabeaufforderung (nur Windows-Treiber)

Die von SQLDriverConnect angezeigte Eingabeaufforderung, die Informationen zum Abschließen der Verbindung anfordert, enthält drei neue Optionen für die Azure AD-Authentifizierung:

![ServerLogin.png](windows/ServerLogin.png)

Diese Optionen entsprechen den fünf in der Benutzeroberfläche des DSN-Setups enthaltenen Optionen, wie oben beschrieben.

### <a name="example-connection-strings"></a>Exemplarische Verbindungszeichenfolgen
1. SQL Server-Authentifizierung: Legacysyntax. Das Serverzertifikat wird nicht überprüft, und eine Verschlüsselung wird nur verwendet, wenn der Server sie erzwingt. Benutzername und Kennwort werden in der Verbindungszeichenfolge übergeben.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. SQL-Authentifizierung: neue Syntax. Der Client fordert eine Verschlüsselung an (der Standardwert für `Encrypt` lautet `true`), und das Serverzertifikat wird unabhängig von der Verschlüsselungseinstellung überprüft (sofern `TrustServerCertificate` nicht auf `true` festgelegt ist). Benutzername und Kennwort werden in der Verbindungszeichenfolge übergeben.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Integrierte Windows-Authentifizierung (Kerberos unter Linux und macOS) unter Verwendung von SSPI (bei SQL Server oder SQL IaaS): aktuelle Syntax. Das Serverzertifikat wird nicht überprüft, es sei denn, es wird eine Verschlüsselung verwendet. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Nur Windows-Treiber_.) Integrierte Windows-Authentifizierung mit SSPI (wenn es sich um eine Zieldatenbank in SQL Server oder SQL IaaS handelt): neue Syntax. Der Client fordert eine Verschlüsselung an (der Standardwert für `Encrypt` lautet `true`), und das Serverzertifikat wird unabhängig von der Verschlüsselungseinstellung überprüft (sofern `TrustServerCertificate` nicht auf `true` festgelegt ist). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Azure Active Directory-Authentifizierung mit Benutzername und Kennwort (wenn es sich um eine Zieldatenbank in Azure SQL-Datenbank handelt). Das Serverzertifikat wird unabhängig von der Verschlüsselungseinstellung überprüft (sofern `TrustServerCertificate` nicht auf `true` festgelegt ist). Benutzername und Kennwort werden in der Verbindungszeichenfolge übergeben. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Nur Windows-Treiber_.) Integrierte Windows-Authentifizierung mit ADAL – dies umfasst das Abrufen von Windows-Kontoanmeldeinformationen für ein von Azure Active Directory ausgestelltes Zugriffstoken. Vorausgesetzt wird eine Zieldatenbank in Azure SQL-Datenbank. Das Serverzertifikat wird unabhängig von der Verschlüsselungseinstellung überprüft (sofern `TrustServerCertificate` nicht auf `true` festgelegt ist). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Nur Windows-Treiber_.) Die interaktive Azure Active Directory-Authentifizierung verwenden die Multi-Factor Authentication-Technologie von Azure zum Einrichten einer Verbindung. In diesem Modus wird durch Bereitstellen der Anmelde-ID ein Dialogfeld für die Azure-Authentifizierung ausgelöst, das dem Benutzer die Eingabe des Kennworts ermöglicht, um die Verbindung einzurichten. Der Benutzername wird in der Verbindungszeichenfolge übergeben.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

8. Die Authentifizierung mit einer verwalteten Azure Active Directory-Dienstidentität verwendet eine systemseitig oder benutzerseitig zugewiesene Identität zur Authentifizierung, um die Verbindung einzurichten. Für die Identität, die dem Benutzer zugewiesen wurde, ist die Benutzer-ID auf die Objekt-ID der Benutzeridentität festgelegt.<br>
Für systemseitig zugewiesene Identität:<br>
`server=Server;database=Database;Authentication=ActiveDirectoryMsi;`<br>
Für eine benutzerseitig zugewiesene Identität mit der Objekt-ID „myObjectId“:<br>
`server=Server;database=Database;UID=myObjectId;Authentication=ActiveDirectoryMsi;`

> [!NOTE] 
>- Wenn Sie die neuen Active Directory-Optionen mit dem Windows-ODBC-Treiber verwenden, stellen Sie sicher, dass die [Active Directory-Authentifizierungsbibliothek für SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) installiert wurde. Wenn Sie Linux- und macOS-Treiber verwenden, stellen Sie sicher, dass `libcurl` installiert wurde. Für die Treiberversion 17.2 und höher ist dies keine explizite Abhängigkeit, da diese Bibliothek für die anderen Authentifizierungsmethoden oder ODBC-Vorgänge nicht erforderlich ist.
>- Zum Herstellen einer Verbindung mit einem SQL Server-Benutzernamen und dem zugehörigen Kennwort können Sie jetzt die neue `SqlPassword`-Option verwenden, die insbesondere für SQL Azure empfohlen wird, weil sie Verbindungsstandardwerte mit höherer Sicherheit ermöglicht.
>- Um eine Verbindung über den Benutzernamen und das Kennwort eines Azure Active Directory-Kontos herzustellen, geben Sie `Authentication=ActiveDirectoryPassword` in der Verbindungszeichenfolge und die Schlüsselwörter `UID` und `PWD` mit dem Benutzernamen und dem Kennwort an.
>- Zum Herstellen einer Verbindung mit der integrierten Windows- oder der integrierten Active Directory-Authentifizierung (nur Windows) geben Sie `Authentication=ActiveDirectoryIntegrated` in der Verbindungszeichenfolge an. Der Treiber wählt automatisch den richtigen Authentifizierungsmodus aus. `UID` und `PWD` dürfen nicht angegeben werden.
>- Zum Herstellen einer Verbindung mit der interaktiven Active Directory-Authentifizierung (nur Windows) muss `UID` angegeben werden.

## <a name="authenticating-with-an-access-token"></a>Authentifizieren mit einem Zugriffstoken

Das pre-connection-Attribut `SQL_COPT_SS_ACCESS_TOKEN` ermöglicht die Verwendung eines aus Azure AD für die Authentifizierung abgerufenen Zugriffstokens anstelle von Benutzername und Kennwort und umgeht auch die Aushandlung und den Abruf eines Zugriffstokens durch den Treiber. Um ein Zugriffstoken zu verwenden, legen Sie das Verbindungsattribut `SQL_COPT_SS_ACCESS_TOKEN` auf einen Zeiger zu einer `ACCESSTOKEN`-Struktur fest:

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

`ACCESSTOKEN` ist eine Struktur mit variabler Länge, die aus einem 4 Bytes langen _length_-Wert gefolgt von _length_ Bytes an nicht transparenten Daten besteht, die das Zugriffstoken bilden. Aufgrund der Art und Weise, in der SQL Server Zugriffstoken verarbeitet, muss ein über eine [OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)-JSON-Antwort abgerufenes Token erweitert werden, sodass jedem Byte ein 0-Füllbyte folgt, ähnlich wie bei einer UCS-2-Zeichenfolge, die nur aus ASCII-Zeichen besteht. Das Token ist jedoch ein nicht transparenter Wert und die in Bytes angegebene Länge darf KEINEN NULL-Terminator enthalten. Aufgrund der erheblichen Einschränkungen in Bezug auf Länge und Format ist diese Authentifizierungsmethode nur programmgesteuert über das Verbindungsattribut `SQL_COPT_SS_ACCESS_TOKEN` verfügbar – es gibt kein entsprechendes Schlüsselwort für DNS oder Verbindungszeichenfolge. Die Verbindungszeichenfolge darf die Schlüsselwörter `UID`, `PWD`, `Authentication` und `Trusted_Connection` nicht enthalten.

> [!NOTE]
> Die ODBC Driver-Version 13.1 unterstützt diese Authentifizierung nur unter _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Azure Active Directory-Authentifizierungsbibliotheken

Das folgende Beispiel zeigt den erforderlichen Code, um mithilfe von Azure Active Directory und Verbindungsschlüsselwörtern eine Verbindung mit SQL Server herzustellen. Beachten Sie, dass der Anwendungscode selbst nicht geändert werden muss. Die Verbindungszeichenfolge bzw. der DSN, sofern verwendet, ist die einzige Änderung, die zum Verwenden von Azure Active Directory zur Authentifizierung erforderlich ist:
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
Das folgende Beispiel zeigt den erforderlichen Code, um mithilfe der Authentifizierung über Azure Active Directory und Zugriffstoken eine Verbindung mit SQL Server herzustellen. In diesem Fall muss der Anwendungscode geändert werden, um das Zugriffstoken zu verarbeiten und das zugehörige Verbindungsattribut festzulegen.
~~~
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server}"
    SQLCHAR accessToken[] = "eyJ0eXAiOi..."; // In the format extracted from an OAuth JSON response
    ...
    DWORD dataSize = 2 * strlen(accessToken);
    ACCESSTOKEN *pAccToken = malloc(sizeof(ACCESSTOKEN) + dataSize);
    pAccToken->dataSize = dataSize;
    // Expand access token with padding bytes
    for(int i = 0, j = 0; i < dataSize; i += 2, j++) {
        pAccToken->data[i] = accessToken[j];
        pAccToken->data[i+1] = 0;
    }
    ...
    SQLSetConnectAttr(hDbc, SQL_COPT_SS_ACCESS_TOKEN, (SQLPOINTER)pAccToken, SQL_IS_POINTER);
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);      
    ...
    free(pAccToken);
~~~
Im Folgenden finden Sie ein Beispiel für eine Verbindungszeichenfolge zur Verwendung mit der interaktiven Azure Active Directory-Authentifizierung. Beachten Sie, dass dieses Beispiel kein PWD-Feld enthält, da das Kennwort über den Bildschirm der Azure-Authentifizierung eingegeben wird.
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~
Im Folgenden finden Sie ein Beispiel für eine Verbindungszeichenfolge zur Verwendung mit der Authentifizierung über eine verwaltete Azure Active Directory-Dienstidentität. Beachten Sie, dass die UID für die vom Benutzer zugewiesene Identität auf die Objekt-ID der Benutzeridentität festgelegt ist.
~~~
// For system-assigned identity,
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};Authentication=ActiveDirectoryMsi"
...
// For user-assigned identity with object ID equals to myObjectId
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myObjectId;Authentication=ActiveDirectoryMsi"
~~~

## <a name="see-also"></a>Weitere Informationen
[Tokenbasierte Authentifizierungsunterstützung für Azure SQL DB mithilfe der Azure AD-Authentifizierung](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

