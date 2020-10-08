---
title: Verwenden von Azure Active Directory mit dem ODBC Driver
description: Der Microsoft ODBC Driver for SQL Server ermöglicht, dass ODBC-Anwendungen über Azure Active Directory eine Verbindung mit einer Azure SQL-Datenbankinstanz herstellen.
ms.custom: ''
ms.date: 09/01/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6925b2b79629fbcbe84f6577e2617e9b45ea82c
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727382"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Verwenden von Azure Active Directory mit dem ODBC Driver
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Zweck

Der Microsoft ODBC Driver for SQL Server, Version 13.1 oder höher, ermöglicht ODBC-Anwendungen das Herstellen einer Verbindung mit einer Azure SQL-Datenbank-Instanz unter Verwendung dieser Optionen: Verbundidentität in Azure Active Directory mit Benutzername/Kennwort, Azure Active Directory-Zugriffstoken, verwaltete Azure Active Directory-Identität (17.3+) oder integrierte Windows-Authentifizierung (17.6+ unter Linux/macOS). Bei der ODBC Driver-Version 13.1 funktioniert die Authentifizierung über ein Azure Active Directory-Zugriffstoken _nur unter Windows_. Die ODBC Driver-Version 17 und höhere Versionen unterstützen diese Authentifizierung auf allen Plattformen (Windows, Linux und macOS). In der ODBC Driver-Version 17.1 für Windows wird eine neue interaktive Azure Active Directory-Authentifizierung mit Anmelde-ID eingeführt. In der ODBC Driver-Version 17.3.1.1 wurde eine neue Authentifizierungsmethode mit verwalteten Azure Active Directory-Identitäten sowohl für systemseitig als auch für benutzerseitig zugewiesene Identitäten hinzugefügt. All diese Methoden werden mithilfe von neuen Schlüsselwörtern für DSN und Verbindungszeichenfolgen sowie von Verbindungsattributen umgesetzt.

> [!NOTE]
> Der ODBC-Treiber unterstützt unter Linux und macOS vor Version 17.6 ausschließlich die Azure Active Directory-Authentifizierung nur direkt für Azure Active Directory. Wenn Sie die Benutzernamen-/Kennwortauthentifizierung von Azure Active Directory über einen Linux- oder macOS-Client verwenden und erforderlich ist, dass sich der Client beim Active Directory-Verbunddienstendpunkt authentifiziert, kann bei der Authentifizierung ein Fehler auftreten. Diese Einschränkung wurde von Version 17.6 an entfernt.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Neue und/oder geänderte Schlüsselwörter für DSN und Verbindungszeichenfolgen

Das Schlüsselwort `Authentication` kann beim Herstellen einer Verbindung mit einem DSN oder einer Verbindungszeichenfolge verwendet werden, um den Authentifizierungsmodus zu steuern. Der in der Verbindungszeichenfolge festgelegte Wert überschreibt den Wert im DSN, sofern angegeben. Der _pre-attribute-Wert_ der Einstellung `Authentication` ist der Wert, der aus den Werten für Verbindungszeichenfolge und DSN berechnet wird.

|Name|Werte|Standard|BESCHREIBUNG|
|-|-|-|-|
|`Authentication`|(nicht festgelegt), (leere Zeichenfolge), `SqlPassword`, `ActiveDirectoryPassword`, `ActiveDirectoryIntegrated`, `ActiveDirectoryInteractive`, `ActiveDirectoryMsi` |(nicht festgelegt)|Steuert den Authentifizierungsmodus.<table><tr><th>Wert<th>BESCHREIBUNG<tr><td>(nicht festgelegt)<td>Der Authentifizierungsmodus wird durch andere Schlüsselwörter bestimmt (vorhandene ältere Verbindungsoptionen).<tr><td>(leere Zeichenfolge)<td>(Nur Verbindungszeichenfolge.) Überschreibt und löscht einen im DSN festgelegten `Authentication`-Wert.<tr><td>`SqlPassword`<td>Direkte Authentifizierung bei einer SQL Server-Instanz unter Verwendung eines Benutzernamens und eines Kennworts.<tr><td>`ActiveDirectoryPassword`<td>Authentifizierung mit einer Azure Active Directory-Identität unter Verwendung eines Benutzernamens und eines Kennworts.<tr><td>`ActiveDirectoryIntegrated`<td>_Nur Windows-Treiber und Linux/Mac-Treiber mit Version 17.6+_ . Authentifizierung mit einer Azure Active Directory-Identität unter Verwendung der integrierten Authentifizierung.<tr><td>`ActiveDirectoryInteractive`<td>_Nur Windows-Treiber_. Authentifizierung mit einer Azure Active Directory-Identität unter Verwendung der interaktiven Authentifizierung.<tr><td>`ActiveDirectoryMsi`<td>Authentifizierung mit einer Azure Active Directory-Identität unter Verwendung der Authentifizierung mit einer verwalteten Identität. Für die Identität, die dem Benutzer zugewiesen wurde, ist die Benutzer-ID auf die Objekt-ID der Benutzeridentität festgelegt.</table>|
|`Encrypt`|(nicht festgelegt), `Yes`, `No`|(Siehe Beschreibung)|Steuert die Verschlüsselung für eine Verbindung. Wenn der pre-attribute-Wert der Einstellung `Authentication` im DSN oder der Verbindungszeichenfolge nicht _none_ lautet, ist der Standardwert `Yes`. Andernfalls ist der Standardwert `No`. Wenn das Attribut `SQL_COPT_SS_AUTHENTICATION` den pre-attribute-Wert `Authentication` überschreibt, legen Sie den Wert von „Encryption“ im DSN, in der Verbindungszeichenfolge oder im Verbindungsattribut explizit fest. Der pre-attribute-Wert von „Encryption“ ist `Yes`, wenn der Wert im DSN oder in der Verbindungszeichenfolge auf `Yes` festgelegt ist.|

## <a name="new-andor-modified-connection-attributes"></a>Neue und/oder geänderte Verbindungsattribute

Die folgenden pre-connect-Verbindungsattribute wurden eingeführt oder geändert, um die Azure Active Directory-Authentifizierung zu unterstützen. Wenn ein Verbindungsattribut über ein entsprechendes Schlüsselwort für Verbindungszeichenfolge oder DSN verfügt und festgelegt ist, hat das Verbindungsattribut Vorrang.

|attribute|type|Werte|Standard|BESCHREIBUNG|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_AD_MSI`, `SQL_AU_RESET`|(nicht festgelegt)|Siehe Beschreibung des `Authentication`-Schlüsselworts weiter oben. `SQL_AU_NONE` wird bereitgestellt, um einen festgelegten `Authentication`-Wert im DSN und/oder der Verbindungszeichenfolge explizit zu überschreiben. `SQL_AU_RESET` hebt die Festlegung des Attributs auf, falls dieses festgelegt war, sodass der DSN- bzw. Verbindungszeichenfolgenwert Vorrang erhalten kann.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Zeiger auf `ACCESSTOKEN` oder NULL|NULL|Wenn der Wert ungleich NULL ist, wird hiermit das zu verwendende Azure AD-Zugriffstoken angegeben. Es ist ein Fehler, ein Zugriffstoken und auch die Schlüsselwörter `UID`, `PWD`, `Trusted_Connection` oder `Authentication` für Verbindungszeichenfolgen oder deren äquivalente Attribute anzugeben. <br> **HINWEIS:** Die ODBC Driver-Version 13.1 unterstützt dies nur unter _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(Siehe Beschreibung)|Steuert die Verschlüsselung für eine Verbindung. `SQL_EN_OFF` und `SQL_EN_ON` deaktivieren und aktivieren Sie Verschlüsselung bzw. Wenn der pre-attribute-Wert der Einstellung `Authentication` nicht _none_ lautet oder `SQL_COPT_SS_ACCESS_TOKEN` festgelegt ist und `Encrypt` weder im DSN noch in der Verbindungszeichenfolge angegeben wurde, lautet der Standardwert `SQL_EN_ON`. Andernfalls ist der Standardwert `SQL_EN_OFF`. Wenn das Verbindungsattribut `SQL_COPT_SS_AUTHENTICATION` auf einen anderen Wert als _none_ festgelegt ist, legen Sie `SQL_COPT_SS_ENCRYPT` explizit auf den gewünschten Wert fest, wenn `Encrypt` im DSN oder der Verbindungszeichenfolge nicht angegeben war. Der effektive Wert dieses Attributs steuert, [ob die Verschlüsselung für die Verbindung verwendet wird](../../relational-databases/native-client/features/using-encryption-without-validation.md).|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Wird mit Azure Active Directory nicht unterstützt, da Kennwortänderungen bei Azure Active Directory-Prinzipalen nicht über eine ODBC-Verbindung durchgeführt werden können. <br><br>Der Ablauf von Kennwörtern bei der SQL Server-Authentifizierung wurde mit SQL Server 2005 eingeführt. Das `SQL_COPT_SS_OLDPWD`-Attribut wurde hinzugefügt, damit der Client sowohl das alte als auch das neue Kennwort für die Verbindung angeben kann. Wenn diese Eigenschaft festgelegt ist, verwendet der Anbieter für die erste Verbindung oder für nachfolgende Verbindungen keinen Verbindungspool, da die Verbindungszeichenfolge das „alte Kennwort“ enthält, das inzwischen geändert wurde.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Veraltet_. Verwenden Sie stattdessen `SQL_COPT_SS_AUTHENTICATION`, festgelegt auf `SQL_AU_AD_INTEGRATED`. <br><br>Erzwingt die Verwendung der Windows-Authentifizierung (Kerberos unter Linux und macOS) für die Überprüfung des Zugriffs bei der Serveranmeldung. Wenn die Windows-Authentifizierung verwendet wird, ignoriert der Treiber die Werte für Benutzer-ID und Kennwort, die bei der Verarbeitung von `SQLConnect`, `SQLDriverConnect` oder `SQLBrowseConnect` bereitgestellt werden.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Ergänzungen der Benutzeroberfläche für Azure Active Directory (nur Windows-Treiber)

Die Benutzeroberflächen für DSN-Setup und Verbindungen des Treibers wurden um die zusätzlichen Optionen erweitert, die zur Verwendung der Authentifizierung mit Azure AD erforderlich sind.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Erstellen und Bearbeiten von DSNs auf der Benutzeroberfläche

Sie können die neuen Azure AD-Authentifizierungsoptionen verwenden, wenn Sie einen neuen DSN über die Setup-Benutzeroberfläche des Treibers erstellen oder bearbeiten:

`Authentication=ActiveDirectoryIntegrated` für die integrierte Azure Active Directory-Authentifizierung bei Azure SQL-Datenbank

![Der DSN-Erstellungs-und Bearbeitungsbildschirm mit ausgewählter integrierter Azure Active Directory-Authentifizierung.](windows/create-dsn-ad-integrated.png)

`Authentication=ActiveDirectoryPassword` für die Azure Active Directory-Authentifizierung mit Benutzername/Kennwort bei Azure SQL-Datenbank

![Der DSN-Erstellungs-und Bearbeitungsbildschirm mit ausgewählter Azure Active Directory-Kennwortauthentifizierung.](windows/create-dsn-ad-password.png)

`Authentication=ActiveDirectoryInteractive` für die interaktive Azure Active Directory-Authentifizierung bei Azure SQL-Datenbank

![Der DSN-Erstellungs-und Bearbeitungsbildschirm mit ausgewählter interaktiver Azure Active Directory-Authentifizierung.](windows/create-dsn-ad-interactive.png)

`Authentication=SqlPassword` für die Authentifizierung bei SQL Server (Azure oder andere Plattform) mit Benutzername/Kennwort

![Der DSN-Erstellungs- und Bearbeitungsbildschirm mit ausgewählter SQL Server Authentifizierung.](windows/create-dsn-ad-sql-server.png)

`Trusted_Connection=Yes` für die ältere integrierte Windows-Authentifizierung über SSPI

![Der DSN-Erstellungs- und Bearbeitungsbildschirm mit ausgewählter integrierter Windows-Authentifizierung.](windows/create-dsn-win-sspi.png)

`Authentication=ActiveDirectoryMsi` für die Azure Active Directory-Authentifizierung mit einer verwalteten Identität

![Der DSN-Erstellungs- und Bearbeitungsbildschirm mit ausgewählter Authentifizierung durch eine verwaltete Dienstidentität.](windows/create-dsn-ad-msi.png)

Die sechs Optionen entsprechen `Trusted_Connection=Yes` (vorhandene ältere integrierte Windows-Authentifizierung nur über SSPI), `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, `ActiveDirectoryPassword`, `ActiveDirectoryInteractive` bzw. `ActiveDirectoryMsi`.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect-Eingabeaufforderung (nur Windows-Treiber)

Die von SQLDriverConnect angezeigte Eingabeaufforderung, die Informationen zum Abschließen der Verbindung anfordert, enthält vier neue Optionen für die Azure AD-Authentifizierung:

![Das von SQLDriverConnect angezeigte SQL Server-Anmeldedialogfeld.](windows/server-login.png)

Diese Optionen entsprechen den sechs in der Benutzeroberfläche des DSN-Setups enthaltenen Optionen, wie oben beschrieben.

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
6. (_Nur Windows-Treiber und Linux/Mac-Treiber mit Version 17.6+_ .) Integrierte Windows-Authentifizierung mit ADAL oder Kerberos – dies umfasst das Abrufen von Windows-Kontoanmeldeinformationen für ein von Azure Active Directory ausgestelltes Zugriffstoken. Vorausgesetzt wird eine Zieldatenbank in Azure SQL-Datenbank. Das Serverzertifikat wird unabhängig von der Verschlüsselungseinstellung überprüft (sofern `TrustServerCertificate` nicht auf `true` festgelegt ist). Unter Linux/macOS muss ein geeignetes Kerberos-Ticket verfügbar sein. Weitere Informationen finden Sie im Abschnitt über Verbundkonten und die [Nutzung der integrierten Authentifizierung](linux-mac/using-integrated-authentication.md).
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Nur Windows-Treiber_.) Die interaktive Azure Active Directory-Authentifizierung verwendet die Multi-Factor Authentication-Technologie von Azure zum Einrichten einer Verbindung. In diesem Modus wird durch Bereitstellen der Anmelde-ID ein Dialogfeld für die Azure-Authentifizierung ausgelöst, das dem Benutzer die Eingabe des Kennworts ermöglicht, um die Verbindung einzurichten. Der Benutzername wird in der Verbindungszeichenfolge übergeben.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![Benutzeroberfläche der Windows Azure-Authentifizierung bei Verwendung der interaktiven Active Directory-Authentifizierung.](windows/WindowsAzureAuth.png)

8. Die Authentifizierung mit einer verwalteten Azure Active Directory-Dienstidentität verwendet eine systemseitig oder benutzerseitig zugewiesene Identität zur Authentifizierung, um die Verbindung einzurichten. Für die Identität, die dem Benutzer zugewiesen wurde, ist die Benutzer-ID auf die Objekt-ID der Benutzeridentität festgelegt.<br>
Für systemseitig zugewiesene Identität:<br>
`server=Server;database=Database;Authentication=ActiveDirectoryMsi;`<br>
Für eine benutzerseitig zugewiesene Identität mit der Objekt-ID „myObjectId“:<br>
`server=Server;database=Database;UID=myObjectId;Authentication=ActiveDirectoryMsi;`

> [!NOTE]
>- Wenn Sie die Active Directory-Optionen mit dem Windows-ODBC-Treiber ***vor*** Version 17.4.2 verwenden, stellen Sie sicher, dass die [Active Directory-Authentifizierungsbibliothek für SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) installiert wurde. Wenn Sie Linux- und macOS-Treiber verwenden, stellen Sie sicher, dass `libcurl` installiert wurde. Für die Treiberversion 17.2 und höher ist dies keine explizite Abhängigkeit, da diese Bibliothek für die anderen Authentifizierungsmethoden oder ODBC-Vorgänge nicht erforderlich ist.
>- Wenn die Azure Active Directory-Konfiguration Richtlinien für bedingten Zugriff beinhaltet und es sich bei dem Client um Windows 10 oder Server 2016 oder höher handelt, kann bei Verwendung der integrierten Authentifizierung oder der Authentifizierung mit Benutzername/Kennwort ein Fehler auftreten. Für Richtlinien für bedingten Zugriff ist die Verwendung des Windows-Konto-Managers (Windows Account Manager, WAM) erforderlich, der in Treiberversion 17.6 oder höher für Windows unterstützt wird. Erstellen Sie zum Verwenden von WAM einen neuen Zeichenfolgen- oder DWORD-Wert mit dem Namen `ADALuseWAM` in `HKLM\Software\ODBC\ODBCINST.INI\ODBC Driver 17 for SQL Server`, bzw. `HKCU\Software\ODBC\ODBC.INI\<your-user-DSN-name>` oder `HKLM\Software\ODBC\ODBC.INI\<your-system-DSN-name>` für die Konfiguration mit globalem, Benutzer-DSN- oder System-DSN-Umfang, und legen Sie ihn auf den Wert „1“ fest. Beachten Sie, dass bei der Authentifizierung mit WAM die Ausführung der Anwendung als anderer Benutzer mit `runas` nicht unterstützt wird. Szenarien, die Richtlinien für bedingten Zugriff erfordern, werden für Linux oder macOS nicht unterstützt.
>- Zum Herstellen einer Verbindung mit einem SQL Server-Benutzernamen und dem zugehörigen Kennwort können Sie jetzt die neue `SqlPassword`-Option verwenden, die insbesondere für Azure SQL empfohlen wird, weil sie Verbindungsstandardwerte mit höherer Sicherheit ermöglicht.
>- Um eine Verbindung über den Benutzernamen und das Kennwort eines Azure Active Directory-Kontos herzustellen, geben Sie `Authentication=ActiveDirectoryPassword` in der Verbindungszeichenfolge und die Schlüsselwörter `UID` und `PWD` mit dem Benutzernamen und dem Kennwort an.
>- Zum Herstellen einer Verbindung mit der integrierten Windows- oder der integrierten Active Directory-Authentifizierung (nur Windows-Treiber und Linux/macOS-Treiber ab Version 17.6) geben Sie `Authentication=ActiveDirectoryIntegrated` in der Verbindungszeichenfolge an. Der Treiber wählt automatisch den richtigen Authentifizierungsmodus aus. `UID` und `PWD` dürfen nicht angegeben werden.
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

`ACCESSTOKEN` ist eine Struktur mit variabler Länge, die aus einem 4 Bytes langen _length_-Wert gefolgt von _length_ Bytes an nicht transparenten Daten besteht, die das Zugriffstoken bilden. Aufgrund der Art und Weise, in der SQL Server Zugriffstoken verarbeitet, muss ein über eine [OAuth 2.0](/azure/active-directory/develop/active-directory-authentication-scenarios)-JSON-Antwort abgerufenes Token erweitert werden, sodass jedem Byte ein 0-Füllbyte folgt, ähnlich wie bei einer UCS-2-Zeichenfolge, die nur aus ASCII-Zeichen besteht. Das Token ist jedoch ein nicht transparenter Wert und die in Bytes angegebene Länge darf KEINEN NULL-Terminator enthalten. Aufgrund der erheblichen Einschränkungen in Bezug auf Länge und Format ist diese Authentifizierungsmethode nur programmgesteuert über das Verbindungsattribut `SQL_COPT_SS_ACCESS_TOKEN` verfügbar – es gibt kein entsprechendes Schlüsselwort für DNS oder Verbindungszeichenfolge. Die Verbindungszeichenfolge darf die Schlüsselwörter `UID`, `PWD`, `Authentication` und `Trusted_Connection` nicht enthalten.

> [!NOTE]
> Die ODBC Driver-Version 13.1 unterstützt diese Authentifizierung nur unter _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Azure Active Directory-Authentifizierungsbibliotheken

Das folgende Beispiel zeigt den erforderlichen Code, um mithilfe von Azure Active Directory und Verbindungsschlüsselwörtern eine Verbindung mit SQL Server herzustellen. Beachten Sie, dass der Anwendungscode selbst nicht geändert werden muss. Die Verbindungszeichenfolge bzw. der DSN, sofern verwendet, ist die einzige Änderung, die zum Verwenden von Azure Active Directory zur Authentifizierung erforderlich ist:
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);    
    ...
~~~
Das folgende Beispiel zeigt den erforderlichen Code, um mithilfe der Authentifizierung über Azure Active Directory und Zugriffstoken eine Verbindung mit SQL Server herzustellen. In diesem Fall muss der Anwendungscode geändert werden, um das Zugriffstoken zu verarbeiten und das zugehörige Verbindungsattribut festzulegen.
~~~
    SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server}"
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
Im Folgenden finden Sie ein Beispiel für eine Verbindungszeichenfolge zur Verwendung mit der Authentifizierung über eine verwaltete Azure Active Directory-Identität. Beachten Sie, dass die UID für die vom Benutzer zugewiesene Identität auf die Objekt-ID der Benutzeridentität festgelegt ist.
~~~
// For system-assigned identity,
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};Authentication=ActiveDirectoryMsi"
...
// For user-assigned identity with object ID equals to myObjectId
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myObjectId;Authentication=ActiveDirectoryMsi"
~~~

## <a name="considerations-for-using-adfs-federated-accounts-on-linuxmacos"></a>Überlegungen zur Verwendung von ADFS-Verbundkonten unter Linux/macOS

Von Version 17.6 an unterstützen die Treiber für Linux und macOS die Authentifizierung mithilfe von Azure Active Directory ADFS-Verbundkonten unter Verwendung von Benutzername/Kennwort (`ActiveDirectoryPassword`) oder Kerberos (`ActiveDirectoryIntegrated`). Bei der Verwendung des integrierten Modus bestehen einige Einschränkungen in Abhängigkeit von der Plattform.

Wenn Sie sich bei einem Benutzer authentifizieren, dessen UPN-Suffix nicht mit dem Kerberos-Bereich identisch ist, d. h., es wird ein alternatives UPN-Suffix verwendet, muss beim Abrufen von Kerberos-Tickets die Option Unternehmens-Prinzipal verwendet werden (verwenden Sie die Option `-E` mit `kinit`, und geben Sie den Prinzipalnamen in der Form `user@federated-domain` an). Dadurch kann der Treiber sowohl die Verbunddomäne als auch den Kerberos-Bereich korrekt bestimmen.

Sie können überprüfen, ob ein passendes Kerberos-Ticket verfügbar ist, indem Sie die Ausgabe des `klist`-Befehls untersuchen. Wenn die Verbunddomäne mit dem Kerberos-Bereich und dem UPN-Suffix übereinstimmt, weist der Prinzipalname die Form `user@realm` auf. Weichen sie ab, sollte der Prinzipalname die Form `user@federated-domain@realm`haben.

### <a name="linux"></a>Linux

Unter SuSE 11 unterstützt die standardmäßige Kerberos-Bibliotheksversion 1.6.x nicht die Unternehmens-Prinzipaloption, die für die Verwendung alternativer UPN-Suffixe erforderlich ist. Zum Verwenden alternativer UPN-Suffixe mit integrierter Azure AD-Authentifizierung führen Sie ein Upgrade der Kerberos-Bibliothek auf 1.7 oder höher durch.

Unter Alpine Linux unterstützt die standardmäßige `libcurl` nicht die SPNEGO/Kerberos-Authentifizierung, die für die integrierte Azure AD-Authentifizierung erforderlich ist.

### <a name="macos"></a>macOS

Die Kerberos-Systembibliothek `kinit` unterstützt Unternehmens-Prinzipal mit der Option `--enterprise`, führt jedoch zugleich implizit eine Namenskanonisierung durch, was die Verwendung alternativer UPN-Suffixe verhindert. Um alternative UPN-Suffixe mit integrierter Azure AD-Authentifizierung zu verwenden, installieren Sie über `brew install krb5` eine neuere Kerberos-Bibliothek, und verwenden Sie ihre `kinit` mit der Option `-E`, wie oben beschrieben.

## <a name="see-also"></a>Weitere Informationen

[Tokenbasierte Authentifizierungsunterstützung für Azure SQL-Datenbank mithilfe der Azure AD-Authentifizierung](/archive/blogs/sqlsecurity/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

[Nutzung der Integrierten Authentifizierung](linux-mac/using-integrated-authentication.md)