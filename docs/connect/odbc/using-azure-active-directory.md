---
title: Verwenden von Azure Active Directory mit dem ODBC-Treiber | Microsoft-Dokumentation für SQL Server
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
ms.openlocfilehash: c0f9d73dace4e17d87e1c93da703786fc920b2fb
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176168"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Verwenden von Azure Active Directory mit dem ODBC Driver
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Zweck

Mit dem Microsoft ODBC Driver for SQL Server mit Version 13,1 oder höher können ODBC-Anwendungen eine Verbindung mit einer Instanz von SQL Azure mithilfe einer Verbund Identität in Azure Active Directory mit einem Benutzernamen/Kennwort, einem Azure Active Directory Zugriffs Token, einem Azure Active Verzeichnis verwaltete Dienst Identität oder integrierte Windows-Authentifizierung (_nur Windows-Treiber_). Bei der ODBC-Treiber Version 13,1 ist die Azure Active Directory Zugriffs Token-Authentifizierung _nur Windows_. Der ODBC-Treiber Version 17 und höher unterstützt diese Authentifizierung auf allen Plattformen (Windows, Linux und Mac). Eine neue Azure Active Directory interaktive Authentifizierung mit Anmelde-ID wird in der ODBC-Treiber Version 17,1 für Windows eingeführt. Eine neue Azure Active Directory verwaltete Dienst Identitäts Authentifizierungsmethode wurde in der ODBC-Treiber Version 17.3.1.1 sowohl für vom System zugewiesene als auch für vom Benutzer zugewiesene Identitäten hinzugefügt. All dies wird durch die Verwendung neuer DSN und Verbindungs Zeichenfolgen-Schlüsselwörter und Verbindungs Attribute erreicht.

> [!NOTE]
> Der ODBC-Treiber unter Linux und macOS unterstützt Active Directory-Verbunddienste (AD FS) nicht. Wenn Sie Azure Active Directory Benutzernamen-/Kennwort-Authentifizierung von einem Linux-oder macOS-Client verwenden und die Active Directory Konfiguration Verbund Dienste umfasst, kann die Authentifizierung fehlschlagen.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Neue und/oder geänderte DSN und Verbindungs Zeichenfolgen-Schlüsselwörter

Das `Authentication` Schlüsselwort kann verwendet werden, wenn eine Verbindung mit einem DSN oder einer Verbindungs Zeichenfolge zum Steuern des Authentifizierungsmodus hergestellt wird. Der in der Verbindungs Zeichenfolge festgelegte Wert überschreibt den Wert im DSN, falls angegeben. Der _präattributwert_ `Authentication` der Einstellung ist der Wert, der aus der Verbindungs Zeichenfolge und den DSN-Werten berechnet wird.

|Name|Werte|Default|und Beschreibung|
|-|-|-|-|
|`Authentication`|(nicht festgelegt), (leere Zeichenfolge `SqlPassword`) `ActiveDirectoryPassword`, `ActiveDirectoryIntegrated`, `ActiveDirectoryInteractive`,,,`ActiveDirectoryMsi` |(nicht festgelegt)|Steuert den Authentifizierungsmodus.<table><tr><th>value<th>und Beschreibung<tr><td>(nicht festgelegt)<td>Der Authentifizierungsmodus, der durch andere Schlüsselwörter (vorhandene Legacy Verbindungsoptionen) bestimmt wird.<tr><td>(leere Zeichenfolge)<td>Hilfe zur Verbindungszeichenfolge Überschreiben Sie einen `Authentication` im DSN festgelegten Wert, und setzen Sie ihn zurück.<tr><td>`SqlPassword`<td>Authentifizieren Sie sich mit einem Benutzernamen und einem Kennwort direkt bei einer SQL Server Instanz.<tr><td>`ActiveDirectoryPassword`<td>Authentifizieren Sie sich mit einer Azure Active Directory Identität mithilfe eines Benutzernamens und Kennworts.<tr><td>`ActiveDirectoryIntegrated`<td>_Nur Windows-Treiber_. Authentifizieren Sie sich mit einer Azure Active Directory Identität mithilfe der integrierten Authentifizierung.<tr><td>`ActiveDirectoryInteractive`<td>_Nur Windows-Treiber_. Authentifizieren Sie sich mit einer Azure Active Directory Identität mithilfe der interaktiven Authentifizierung.<tr><td>`ActiveDirectoryMsi`<td>Authentifizieren Sie sich mit Azure Active Directory Identität mithilfe der Authentifizierung der verwalteten Dienst Identität. Für die Identität, die dem Benutzer zugewiesen wurde, ist die Benutzer-ID auf die Objekt-ID der Benutzeridentität festgelegt.</table>|
|`Encrypt`|(nicht festgelegt), `Yes`, `No`|(siehe Beschreibung)|Steuert die Verschlüsselung für eine Verbindung. Wenn der präattributwert der `Authentication` Einstellung im DSN oder in der Verbindungs Zeichenfolge nicht " _None_ " ist `Yes`, ist der Standardwert. Andernfalls ist der Standardwert `No`. Wenn das Attribut `SQL_COPT_SS_AUTHENTICATION` den präattributwert von `Authentication`überschreibt, legen Sie den Wert der Verschlüsselung explizit im DSN oder in der Verbindungs Zeichenfolge oder im Verbindungs Attribut fest. Der präattributwert der Verschlüsselung ist `Yes` , wenn der Wert entweder in `Yes` der DSN oder in der Verbindungs Zeichenfolge auf festgelegt ist.|

## <a name="new-andor-modified-connection-attributes"></a>Neue und/oder geänderte Verbindungs Attribute

Die folgenden Verbindungs Attribute für die Verbindungs Herstellung wurden entweder eingeführt oder geändert, um Azure Active Directory Authentifizierung zu unterstützen. Wenn ein Verbindungs Attribut über eine entsprechende Verbindungs Zeichenfolge oder ein DSN-Schlüsselwort verfügt und festgelegt wird, hat das Verbindungs Attribut Vorrang.

|attribute|Typ|Werte|Default|und Beschreibung|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_AD_MSI`, `SQL_AU_RESET`|(nicht festgelegt)|Siehe Beschreibung des `Authentication` oben genannten Schlüssel Worts. `SQL_AU_NONE`wird bereitgestellt, um einen festgelegten `Authentication` Wert im DSN und/oder in der Verbindungs Zeichenfolge explizit zu überschreiben, während `SQL_AU_RESET` das Attribut zurücksetzt, wenn es festgelegt wurde, sodass der DSN-oder Verbindungs Zeichenfolgen-Wert Vorrang hat.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Zeiger auf `ACCESSTOKEN` oder NULL|NULL|Wenn der Wert ungleich NULL ist, wird das zu verwendende azuread-Zugriffs Token angegeben. Es ist ein Fehler, ein Zugriffs Token `UID`sowie, `PWD`, `Trusted_Connection`, oder `Authentication` Verbindungs Zeichenfolgen-Schlüsselwörter oder deren Äquivalente Attribute anzugeben. <br> **Hinweis:** Der ODBC-Treiber Version 13,1 unterstützt dies nur unter _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(siehe Beschreibung)|Steuert die Verschlüsselung für eine Verbindung. `SQL_EN_OFF` und `SQL_EN_ON` deaktivieren und aktivieren Sie Verschlüsselung bzw. `Authentication` Wenn der präattributwert der Einstellung nicht " _None_ " ist `SQL_COPT_SS_ACCESS_TOKEN` oder festgelegt ist `Encrypt` und nicht in der DSN oder Verbindungs Zeichenfolge angegeben wurde, ist `SQL_EN_ON`der Standardwert. Andernfalls ist der Standardwert `SQL_EN_OFF`. Wenn das Verbindungs Attribut `SQL_COPT_SS_AUTHENTICATION` auf nicht _None_festgelegt ist, wird `SQL_COPT_SS_ENCRYPT` explizit auf den gewünschten Wert `Encrypt` festgelegt, wenn nicht im DSN oder in der Verbindungs Zeichenfolge angegeben wurde. Der effektive Wert dieses Attributs steuert, [ob die Verschlüsselung für die Verbindung verwendet wird.](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Wird nicht mit Azure Active Directory unterstützt, da Kenn Wort Änderungen für Aad-Prinzipale nicht über eine ODBC-Verbindung durchgeführt werden können. <br><br>Der Ablauf von Kennwörtern bei der SQL Server-Authentifizierung wurde mit SQL Server 2005 eingeführt. Das `SQL_COPT_SS_OLDPWD` -Attribut wurde hinzugefügt, damit der Client sowohl das alte als auch das neue Kennwort für die Verbindung bereitstellen kann. Wenn diese Eigenschaft festgelegt ist, verwendet der Anbieter für die erste Verbindung oder für nachfolgende Verbindungen keinen Verbindungspool, da die Verbindungszeichenfolge das "alte Kennwort" enthält, das inzwischen geändert wurde.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Veraltet_; verwenden `SQL_COPT_SS_AUTHENTICATION` Sie`SQL_AU_AD_INTEGRATED` stattdessen. <br><br>Erzwingt die Verwendung der Windows-Authentifizierung (Kerberos unter Linux und macOS) für die Zugriffs Validierung bei der Server Anmeldung. Wenn die Windows-Authentifizierung verwendet wird, ignoriert der Treiber Benutzer-ID-und Kenn Wort `SQLConnect`Werte `SQLDriverConnect`, die `SQLBrowseConnect` als Teil der Verarbeitung von, oder bereitgestellt werden.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>UI-Ergänzungen für Azure Active Directory (nur Windows-Treiber)

Der DSN-Setup-und der Verbindungs-UIs des Treibers wurden um die zusätzlichen Optionen erweitert, die für die Verwendung der-Authentifizierung mit Azure AD erforderlich sind.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Erstellen und Bearbeiten von DSNs in der Benutzeroberfläche

Es ist möglich, die neuen Azure AD Authentifizierungs Optionen zu verwenden, wenn Sie einen vorhandenen DSN mithilfe der Setup Benutzeroberfläche des Treibers erstellen oder bearbeiten:

`Authentication=ActiveDirectoryIntegrated` für die integrierte Azure Active Directory-Authentifizierung bei SQL Azure

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword`zum Azure Active Directory der Authentifizierung mit Benutzername und Kennwort auf SQL Azure

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` für die interaktive Azure Active Directory-Authentifizierung für SQL Azure

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword`für die Authentifizierung mit Benutzername und Kennwort SQL Server (Azure oder anderweitig)

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes`für Windows-Legacy-integrierte SSPI-Authentifizierung

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

Die fünf Optionen entsprechen den `Trusted_Connection=Yes` (vorhandene ältere Windows integrierte Authentifizierung nur über SSPI) und `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, `ActiveDirectoryPassword`, und `ActiveDirectoryInteractive`bzw.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect-Eingabeaufforderung (nur Windows-Treiber)

Das von SQLDriverConnect angezeigte Eingabe Aufforderungs Dialogfeld, wenn zum Beenden der Verbindung erforderliche Informationen angefordert werden, enthält drei neue Optionen für Azure AD Authentifizierung:

![ServerLogin.png](windows/ServerLogin.png)

Diese Optionen entsprechen denselben fünf Optionen, die oben in der DSN-Setup-Benutzeroberfläche verfügbar sind.

### <a name="example-connection-strings"></a>Exemplarische Verbindungszeichenfolgen
1. SQL Server Authentifizierung: Legacy-Syntax. Das Serverzertifikat wird nicht überprüft, und die Verschlüsselung wird nur verwendet, wenn der Server Dies erzwingt. Der Benutzername/das Kennwort wird in der Verbindungs Zeichenfolge angegeben.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. SQL-Authentifizierung: neue Syntax. Der Client fordert die Verschlüsselung an (der Standard `Encrypt` Wert `true`von ist), und das Serverzertifikat wird unabhängig von der Verschlüsselungs Einstellung überprüft `TrustServerCertificate` (es sei `true`denn, ist auf festgelegt). Der Benutzername/das Kennwort wird in der Verbindungs Zeichenfolge angegeben.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Integrierte Windows-Authentifizierung (Kerberos unter Linux und macOS) mithilfe von SSPI (für SQL Server oder SQL-IaaS): aktuelle Syntax. Das Server Zertifikat wird nicht überprüft, es sei denn, die Verschlüsselung wird verwendet. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Nur Windows-Treiber_.) Integrierte Windows-Authentifizierung mithilfe von SSPI (wenn sich die Zieldatenbank in SQL Server oder SQL-IaaS befindet): neue Syntax. Der Client fordert die Verschlüsselung an (der Standard `Encrypt` Wert `true`von ist), und das Serverzertifikat wird unabhängig von der Verschlüsselungs Einstellung überprüft `TrustServerCertificate` (es sei `true`denn, ist auf festgelegt). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Aad-Benutzernamen-/Kennwortauthentifizierung (wenn die Zieldatenbank in Azure SQL-Datenbank gespeichert ist). Das Server Zertifikat wird unabhängig von der Verschlüsselungs Einstellung überprüft (es `TrustServerCertificate` sei denn, `true`ist auf festgelegt). Der Benutzername/das Kennwort wird in der Verbindungs Zeichenfolge angegeben. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Nur Windows-Treiber_.) Integrierte Windows-Authentifizierung mit Adal, bei der die Anmelde Informationen des Windows-Kontos für ein Aad-ausgestelltes Zugriffs Token übernommen werden, vorausgesetzt, die Zieldatenbank befindet sich in der Azure SQL-Datenbank. Das Server Zertifikat wird unabhängig von der Verschlüsselungs Einstellung überprüft (es `TrustServerCertificate` sei denn, `true`ist auf festgelegt). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Nur Windows-Treiber_.) Die interaktive Aad-Authentifizierung verwendet die Azure Multi-Factor Authentication-Technologie, um die Verbindung einzurichten. In diesem Modus wird durch Angabe der Anmelde-ID ein Azure-Authentifizierungs Dialogfeld ausgelöst, das es dem Benutzer ermöglicht, das Kennwort einzugeben, um die Verbindung abzuschließen. Der Benutzername wird in der Verbindungs Zeichenfolge übermittelt.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

8. Die Aad-verwaltete Dienstidentität Authentifizierung verwendet die vom System zugewiesene oder vom Benutzer zugewiesene Identität zur Authentifizierung zum Einrichten der Verbindung. Für die Identität, die dem Benutzer zugewiesen wurde, ist die Benutzer-ID auf die Objekt-ID der Benutzeridentität festgelegt.<br>
Für systemseitig zugewiesene Identität:<br>
`server=Server;database=Database;Authentication=ActiveDirectoryMsi;`<br>
Für eine vom Benutzer zugewiesene Identität mit der Objekt-ID, die myobjectid entspricht,<br>
`server=Server;database=Database;UID=myObjectId;Authentication=ActiveDirectoryMsi;`

> [!NOTE] 
>- Wenn Sie die neuen Active Directory Optionen mit dem Windows ODBC-Treiber verwenden, stellen Sie sicher, dass die [Active Directory-Authentifizierungsbibliothek für SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) installiert wurde. Wenn Sie die Linux-und macOS-Treiber verwenden `libcurl` , stellen Sie sicher, dass installiert ist. Bei Treiber Version 17,2 und höher ist dies keine explizite Abhängigkeit, da Sie für die anderen Authentifizierungsmethoden oder ODBC-Vorgänge nicht erforderlich ist.
>- Zum Herstellen einer Verbindung mit einem Benutzernamen und einem Kennwort für SQL Server-Konto `SqlPassword` können Sie jetzt die neue Option verwenden. Dies wird besonders für SQL Azure empfohlen, da diese Option sicherere Verbindungs Standardwerte ermöglicht.
>- Um eine Verbindung über den Benutzernamen und das Kennwort eines Azure Active Directory-Kontos herzustellen, geben Sie `Authentication=ActiveDirectoryPassword` in der Verbindungszeichenfolge und die Schlüsselwörter `UID` und `PWD` mit dem Benutzernamen und dem Kennwort an.
>- Geben `Authentication=ActiveDirectoryIntegrated` Sie in der Verbindungs Zeichenfolge an, um eine Verbindung mithilfe der integrierten oder Active Directory integrierten Windows-Treiber Authentifizierung herzustellen. Der Treiber wählt automatisch den richtigen Authentifizierungsmodus aus. `UID`und `PWD` dürfen nicht angegeben werden.
>- Zum Herstellen einer Verbindung mit Active Directory interaktiven Authentifizierung `UID` (nur Windows-Treiber) muss angegeben werden.

## <a name="authenticating-with-an-access-token"></a>Authentifizieren mit einem Zugriffs Token

Das `SQL_COPT_SS_ACCESS_TOKEN` präverbindungsattribut ermöglicht die Verwendung eines Zugriffs Tokens, das von Azure AD für die Authentifizierung abgerufen wurde, anstelle von Benutzername und Kennwort, und umgeht außerdem die Aushandlung und das Abrufen eines Zugriffs Tokens durch den Treiber. Um ein Zugriffs Token zu verwenden, legen `SQL_COPT_SS_ACCESS_TOKEN` Sie das Verbindungs Attribut auf einen Zeiger `ACCESSTOKEN` auf eine-Struktur fest:

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

Die `ACCESSTOKEN` ist eine Struktur variabler Länge, die aus einer _Länge_ von 4 Byte gefolgt von _Längen_ Bytes von nicht transparenten Daten besteht, die das Zugriffs Token bilden. Aufgrund der Art und Weise, wie SQL Server Zugriffs Token verarbeitet, muss eine über eine [OAuth 2,0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios) JSON-Antwort abgerufen werden, sodass jedem Byte ein 0-Auffüll Byte folgt, ähnlich wie eine UCS-2-Zeichenfolge, die nur ASCII-Zeichen enthält. Allerdings ist das Token ein nicht transparenter Wert, und die angegebene Länge in Byte darf keinen null-Terminator enthalten. Aufgrund der beträchtlichen Längen-und Format Einschränkungen ist diese Authentifizierungsmethode nur Programm gesteuert über das `SQL_COPT_SS_ACCESS_TOKEN` Verbindungs Attribut verfügbar. es gibt kein entsprechendes DSN-oder Verbindungs Zeichenfolgen-Schlüsselwort. Die Verbindungs Zeichenfolge darf `UID`nicht `PWD`die Schlüsselwörter `Trusted_Connection` ,, `Authentication`oder enthalten.

> [!NOTE]
> Der ODBC-Treiber Version 13,1 unterstützt diese Authentifizierung nur unter _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Azure Active Directory-Authentifizierungsbibliotheken

Das folgende Beispiel zeigt den Code, der zum Herstellen einer Verbindung mit SQL Server mithilfe Azure Active Directory mit Verbindungs Schlüsselwörtern erforderlich ist. Beachten Sie, dass es nicht erforderlich ist, den Anwendungscode selbst zu ändern. die Verbindungs Zeichenfolge oder DSN, wenn eine verwendet wird, ist die einzige Änderung, die für die Verwendung von Aad für die Authentifizierung erforderlich ist:
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
Das folgende Beispiel zeigt den Code, der zum Herstellen einer Verbindung mit SQL Server mithilfe Azure Active Directory mit Zugriffs Token-Authentifizierung erforderlich ist. In diesem Fall muss der Anwendungscode geändert werden, um das Zugriffs Token zu verarbeiten und das zugehörige Verbindungs Attribut festzulegen.
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
Im folgenden finden Sie eine Beispiel Verbindungs Zeichenfolge für die Verwendung mit Azure Active Directory interaktiven Authentifizierung. Beachten Sie, dass es kein pwd-Feld enthält, da das Kennwort über den Azure-Authentifizierungs Bildschirm eingegeben würde.
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~
Im folgenden finden Sie eine Beispiel Verbindungs Zeichenfolge für die Verwendung mit Azure Active Directory verwaltete Dienstidentität-Authentifizierung. Beachten Sie, dass die UID für die vom Benutzer zugewiesene Identität auf die Objekt-ID der Benutzeridentität festgelegt ist.
~~~
// For system-assigned identity,
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};Authentication=ActiveDirectoryMsi"
...
// For user-assigned identity with object ID equals to myObjectId
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myObjectId;Authentication=ActiveDirectoryMsi"
~~~

## <a name="see-also"></a>Weitere Informationen
[Unterstützung für die tokenbasierte Authentifizierung für Azure SQL-Datenbank mithilfe Azure AD Authentifizierung](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

