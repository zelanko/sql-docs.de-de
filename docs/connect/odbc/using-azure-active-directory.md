---
title: Mithilfe von Azure Active Directory mithilfe des ODBC­Treibers | Microsoft-Dokumentation für SQLServer
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
manager: craigg
ms.openlocfilehash: 949ae2e19279db895ca9bca1441f06c2b2d8948f
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51604100"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Verwenden von Azure Active Directory mit dem ODBC Driver
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Zweck

Microsoft ODBC Driver für SQL Server Version 13.1 oder höher ermöglicht ODBC-Anwendungen für die Verbindung mit einer Instanz von SQL Azure mithilfe eines Identitätsverbunds in Azure Active Directory mit Benutzername/Kennwort, ein Zugriffstoken für den Azure Active Directory oder Windows Integrierte Authentifizierung (_nur die Windows-Treiber_). Für den ODBC-Treiber Version 13.1, den Azure Active Directory-Zugriff, die die Tokenauthentifizierung ist _Windows nur_. Der ODBC-Treiber, Version 17 und unterstützen Sie über diese Authentifizierung auf allen Plattformen (Windows, Linux und Mac). Eine neue interaktive Azure Active Directory-Authentifizierung mit Anmelde-ID wird für Windows ODBC Driver, Version 17.1 eingeführt. Alle diese werden durch die Verwendung von neuen DSN und Schlüsselwörter für Verbindungszeichenfolgen sowie die Verbindungsattribute durchgeführt.

> [!NOTE]
> Der ODBC-Treiber unter Linux und MacOS wird die Active Directory Federation Services nicht unterstützt. Wenn Sie Azure Active Directory-Benutzername/Kennwort-Authentifizierung von einem Linux-verwenden oder MacOS-Client und der Active Directory-Konfiguration enthält Verbunddiensten, kann die Authentifizierung fehl.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Neue und/oder geänderte DSN und Schlüsselwörter für Verbindungszeichenfolgen

Die `Authentication` -Schlüsselwort kann verwendet werden bei der Verbindung mit einer Zeichenfolge DSN- oder Verbindungszeichenfolge den Authentifizierungsmodus zu steuern. Der Wert in der Verbindungszeichenfolge festgelegt werden, die in DSN angegebene, überschreibt, sofern bereitgestellt. Die _vorab-Attributwert_ von der `Authentication` Einstellung ist der Wert, der aus der Verbindungszeichenfolge und den DSN-Werte berechnet.

|Name|Werte|Default|und Beschreibung|
|-|-|-|-|
|`Authentication`|(nicht festgelegt), (leere Zeichenfolge), `SqlPassword`, `ActiveDirectoryPassword`, `ActiveDirectoryIntegrated`, `ActiveDirectoryInteractive`|(nicht festgelegt)|Steuert den Authentifizierungsmodus an.<table><tr><th>value<th>und Beschreibung<tr><td>(nicht festgelegt)<td>Authentifizierungsmodus, der bestimmt, indem andere Schlüsselwörter (vorhandene ältere Verbindungsoptionen.)<tr><td>(leere Zeichenfolge)<td>Verbindungszeichenfolge: "{0}" Außer Kraft setzen und die Festlegung einer `Authentication` Wert festgelegt, in der DSN.<tr><td>`SqlPassword`<td>Authentifizieren Sie direkt auf einer SQL Server-Instanz, die mithilfe von Benutzername und Kennwort.<tr><td>`ActiveDirectoryPassword`<td>Authentifizieren Sie mit einer Azure Active Directory-Identität mit einem Benutzernamen und Kennwort ein.<tr><td>`ActiveDirectoryIntegrated`<td>_Nur Windows-Treiber_. Mit einer Azure Active Directory-Identität, die mithilfe der integrierten Authentifizierung authentifizieren.<tr><td>`ActiveDirectoryInteractive`<td>_Nur Windows-Treiber_. Über eine interaktive Authentifizierung mit Azure Active Directory-Identität authentifiziert.</table>|
|`Encrypt`|(nicht festgelegt), `Yes`, `No`|(siehe Beschreibung)|Steuert die Verschlüsselung für eine Verbindung. Wenn das erforderliche Attribut-Wert, der die `Authentication` Einstellung ist nicht _keine_ in der Zeichenfolge DSN- oder Verbindungszeichenfolge, der Standardwert ist `Yes`. Andernfalls ist der Standardwert `No`. Wenn das Attribut `SQL_COPT_SS_AUTHENTICATION` überschreibt den Wert des Pre-Attributs `Authentication`explizit legen Sie den Wert der Verschlüsselung in die DSN- oder Verbindungszeichenfolge oder Verbindungsattribut. Der erforderliche Attributwert der Verschlüsselung ist `Yes` , wenn der Wert, um festgelegt ist `Yes` in entweder die DSN-oder Verbindungszeichenfolge.|

## <a name="new-andor-modified-connection-attributes"></a>Neue und/oder geänderte Verbindungsattribute

Die folgenden verbinden vorab Verbindung Attribute entweder eingeführt oder geändert wurden, um die Azure Active Directory-Authentifizierung unterstützen. Wenn ein Verbindungsattribut verfügt über eine entsprechende Verbindungszeichenfolge oder DSN-Schlüsselwort und festgelegt ist, hat das Verbindungsattribut Vorrang vor.

|attribute|Typ|Werte|Default|und Beschreibung|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_RESET`|(nicht festgelegt)|Finden Sie in der Beschreibung der `Authentication` Schlüsselwort oben. `SQL_AU_NONE` wird bereitgestellt, um eine Gruppe explizit überschreiben `Authentication` Wert in der Zeichenfolge DSN und/oder Verbindung während `SQL_AU_RESET` das Attribut, wenn er festgelegt wurde, sodass der Zeichenfolgenwert DSN- oder Verbindungszeichenfolge vorrangig ist, hebt die Festlegung.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Zeiger auf `ACCESSTOKEN` oder NULL|NULL|Wenn nicht Null ist, gibt Sie an das Azure AD-Zugriffstoken verwendet. Es ist ein Fehler an ein Zugriffstoken sowie `UID`, `PWD`, `Trusted_Connection`, oder `Authentication` Verbindungszeichenfolgen-Schlüsselwörter oder deren entsprechende Attribute. <br> **Hinweis:** ODBC Driver, Version 13.1 unterstützt dies nur auf _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(siehe Beschreibung)|Steuert die Verschlüsselung für eine Verbindung. `SQL_EN_OFF` und `SQL_EN_ON` deaktivieren und aktivieren Sie Verschlüsselung bzw. Wenn das erforderliche Attribut-Wert, der die `Authentication` Einstellung ist nicht _keine_ oder `SQL_COPT_SS_ACCESS_TOKEN` festgelegt ist, und `Encrypt` wurde nicht angegeben in entweder die DSN- oder Verbindungszeichenfolge-Zeichenfolge, die standardmäßig `SQL_EN_ON`. Andernfalls ist der Standardwert `SQL_EN_OFF`. Wenn das Verbindungsattribut `SQL_COPT_SS_AUTHENTICATION` nastaven NA hodnotu nicht _keine_, legen Sie explizit `SQL_COPT_SS_ENCRYPT` auf den gewünschten Wert Wenn `Encrypt` wurde nicht in der Zeichenfolge DSN- oder Verbindungszeichenfolge angegeben. Der effektive Wert der dieses Attribut steuert [gibt an, ob Verschlüsselung für die Verbindung verwendet wird.](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Mit Azure Active Directory, unterstützt nicht, da kennwortänderungen an AAD-Prinzipalen nicht über eine ODBC-Verbindung erreicht werden können. <br><br>Der Ablauf von Kennwörtern bei der SQL Server-Authentifizierung wurde mit SQL Server 2005 eingeführt. Die `SQL_COPT_SS_OLDPWD` -Attribut wurde hinzugefügt, damit der Client sowohl das alte als auch das neue Kennwort für die Verbindung angeben kann. Wenn diese Eigenschaft festgelegt ist, verwendet der Anbieter für die erste Verbindung oder für nachfolgende Verbindungen keinen Verbindungspool, da die Verbindungszeichenfolge das "alte Kennwort" enthält, das inzwischen geändert wurde.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Als veraltet markiert_; verwenden Sie `SQL_COPT_SS_AUTHENTICATION` festgelegt `SQL_AU_AD_INTEGRATED` stattdessen. <br><br>Verwenden Sie erzwingt, dass der Windows-Authentifizierung (Kerberos unter Linux und MacOS) für die Überprüfung der Zugriff auf Server-Anmeldung. Wenn Windows-Authentifizierung verwendet wird, ignoriert der Treiber als Teil des angegebenen Werte für Benutzer-ID und Kennwort `SQLConnect`, `SQLDriverConnect`, oder `SQLBrowseConnect` verarbeiten.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>UI-Erweiterungen für Azure Active Directory (nur Windows-Treiber)

Die DSN-Setup und die Verbindung Benutzeroberflächen des Treibers wurden mit den zusätzlichen Optionen für die Authentifizierung mit Azure AD notwendigen verbessert.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Erstellen und Bearbeiten von DSNs in der Benutzeroberfläche

Es ist möglich, verwenden Sie das neue Azure AD Authentication-Optionen beim Erstellen oder Bearbeiten von einem vorhandenen DSN mithilfe des Treibers Setup-Benutzeroberfläche:

`Authentication=ActiveDirectoryIntegrated` für die integrierte Azure Active Directory-Authentifizierung bei SQL Azure

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword` für die Benutzername/Kennwort-Authentifizierung für Azure Active Directory, SQL Azure

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` für die interaktive Azure Active Directory-Authentifizierung für SQL Azure

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword` für die Benutzername/Kennwort-Authentifizierung mit SQL Server (Azure oder anderweitig)

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes` für Windows integrierte legacy-SSPI-Authentifizierung

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

Die fünf Optionen entsprechen den `Trusted_Connection=Yes` (vorhandene ältere Windows integrierte Authentifizierung nur über SSPI) und `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, `ActiveDirectoryPassword`, und `ActiveDirectoryInteractive`bzw.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect-Eingabeaufforderung (nur Windows-Treiber)

Eingabeaufforderungs-Dialogfeld angezeigt, wenn es zum Herstellen die Verbindung erforderlichen Informationen anfordert, indem SQLDriverConnect enthält drei neue Optionen für Azure AD-Authentifizierung:

![ServerLogin.png](windows/ServerLogin.png)

Diese Optionen entsprechen den gleichen fünf in der DSN-Setup-Benutzeroberfläche, die oben genannten verfügbar.

### <a name="example-connection-strings"></a>Exemplarische Verbindungszeichenfolgen
1. SQL Server-Authentifizierung – legacy-Syntax. Serverzertifikat wird nicht überprüft, und nur dann, wenn der Server, die es erzwingt, wird Verschlüsselung verwendet. Der Benutzername und Kennwort wird in der Verbindungszeichenfolge übergeben.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. SQL-Authentifizierung – neue Syntax. Der Client fordert Verschlüsselung (der Standardwert von `Encrypt` ist `true`) und das Serverzertifikat überprüft, unabhängig von der verschlüsselungseinstellung (es sei denn, `TrustServerCertificate` nastaven NA hodnotu `true`). Der Benutzername und Kennwort wird in der Verbindungszeichenfolge übergeben.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Integrierte Windows-Authentifizierung (Kerberos unter Linux und MacOS) mithilfe der SSPI (mit SQL Server oder SQL-IaaS) – aktuelle Syntax. Serverzertifikat wird nicht überprüft, es sei denn, die Verschlüsselung verwendet wird. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Nur die Windows-Treiber_.) Integrierte Windows-Authentifizierung mit SSPI (wenn die Zieldatenbank in SQL Server oder SQL-IaaS-ist): der neue Syntax. Der Client fordert Verschlüsselung (der Standardwert von `Encrypt` ist `true`) und das Serverzertifikat überprüft, unabhängig von der verschlüsselungseinstellung (es sei denn, `TrustServerCertificate` nastaven NA hodnotu `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. AAD Benutzername/Kennwort-Authentifizierung (wenn die Zieldatenbank in Azure SQL-Datenbank ist). Serverzertifikat überprüft Ruft ab, unabhängig von der verschlüsselungseinstellung (es sei denn, `TrustServerCertificate` nastaven NA hodnotu `true`). Der Benutzername und Kennwort wird in der Verbindungszeichenfolge übergeben. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Nur die Windows-Treiber_.) Integrierte Windows-Authentifizierung mit ADAL, dies erfordert das Windows-Anmeldeinformationen für ein AAD-ausgestellte Zugriffstoken einlösen, vorausgesetzt, dass die Zieldatenbank in Azure SQL-Datenbank ist. Serverzertifikat überprüft Ruft ab, unabhängig von der verschlüsselungseinstellung (es sei denn, `TrustServerCertificate` nastaven NA hodnotu `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Nur die Windows-Treiber_.) Interaktive Authentifizierung mit AAD verwendet Azure Multi-Factor Authentication-Technologie, um die Verbindung einzurichten. In diesem Modus wird durch die Bereitstellung der Anmelde-ID ein Dialogfeld "Windows Azure-Authentifizierung" wird ausgelöst, und ermöglicht dem Benutzer zur Eingabe des Kennworts zum Herstellen die Verbindung. Der Benutzername ist in der Verbindungszeichenfolge übergeben.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

> [!NOTE] 
>- Wenn Sie die Optionen für den neuen Active Directory mit der Windows-ODBC-Treiber verwenden, stellen Sie sicher, dass die [Active Directory-Authentifizierungsbibliothek für SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) installiert wurde. Wenn Sie die Treiber für Linux und MacOS verwenden, stellen Sie sicher, dass `libcurl` installiert wurde. Treiber, Version 17.2 und spätere ist dies nicht explizite Abhängigkeit, da er nicht für die anderen Authentifizierungsmethoden oder ODBC-Vorgänge erforderlich ist.
>- Zum Verbinden mit SQL Server-Konto-Benutzername und Kennwort jetzt können Sie die neue `SqlPassword` Option, die speziell für SQL Azure empfohlen, da diese Option sicherer Standardwerte für die Verbindung aktiviert.
>- Beim Verbinden mit einer Azure Active Directory-Konto-Benutzernamen und Kennwort angeben `Authentication=ActiveDirectoryPassword` in der Verbindungszeichenfolge und die `UID` und `PWD` Schlüsselwörter, mit dem Benutzernamen und Kennwort bzw.
>- Geben Sie zum Verbinden mit Windows-integrierte oder Active Directory-integrierte (nur Windows-Treiber) Authentifizierung `Authentication=ActiveDirectoryIntegrated` in der Verbindungszeichenfolge. Der Treiber den richtigen Authentifizierungsmodus automatisch ausgewählt. `UID` und `PWD` darf nicht angegeben werden.
>- Die Verbindung mithilfe der Active Directory Interavtive (nur Windows-Treiber) Authentifizierung `UID` muss angegeben werden.

## <a name="authenticating-with-an-access-token"></a>Authentifizieren mit einem Zugriffstoken

Die `SQL_COPT_SS_ACCESS_TOKEN` vorverbindungsattribut ermöglicht die Verwendung eines Zugriffstokens von Azure AD für die Authentifizierung anstelle von Benutzername und Kennwort erhalten haben, und auch umgeht die Aushandlung und Abrufen eines Zugriffstokens vom Treiber. Um ein Zugriffstoken zu verwenden, legen die `SQL_COPT_SS_ACCESS_TOKEN` -Verbindungsattribut auf einen Zeiger auf ein `ACCESSTOKEN` Struktur:

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

Die `ACCESSTOKEN` ist eine variabler Länge, die Struktur, bestehend aus einem 4-Byte- _Länge_ gefolgt von _Länge_ Bytes nicht transparenten Daten, die das Zugriffstoken zu bilden. Aufgrund der wie SQL Server Zugangs-Token verarbeitet, eine über abgerufen ein [OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios) JSON-Antwort muss erweitert werden, sodass jedes Byte gefolgt von 0 Byte, ähnlich wie eine UCS-2-Zeichenfolge, die mit der nur ASCII-Zeichen aufgefüllt ist jedoch das Token ein nicht transparenter Wert und die Länge, die in Bytes angegeben ist, darf keine null-Terminator enthalten. Aufgrund ihrer beträchtlichen Länge und Format-Einschränkungen, diese Methode der Authentifizierung ist nur verfügbar, programmgesteuert über die `SQL_COPT_SS_ACCESS_TOKEN` Verbindungsattribut; es gibt keine entsprechenden DSN oder das Schlüsselwort für Verbindungszeichenfolgen. Die Verbindungszeichenfolge darf keinen `UID`, `PWD`, `Authentication`, oder `Trusted_Connection` Schlüsselwörter.

> [!NOTE]
> Der ODBC-Treiber Version 13.1 unterstützt nur diese Authentifizierung auf _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Azure Active Directory-Authentifizierungsbibliotheken

Das folgende Beispiel zeigt den Code für die Verbindung mit SQL Server mit Azure Active Directory mit Verbindungsschlüsselwörter. Beachten Sie, dass es nicht erforderlich, den Anwendungscode selbst zu ändern; die Verbindungszeichenfolge oder DSN, sofern einer verwendet wird, ist die einzige Änderung, die für die Verwendung von AAD für die Authentifizierung erforderlich sind:
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
Das folgende Beispiel zeigt den Code für die Verbindung mit SQL Server Access-token-Authentifizierung mit Azure Active Directory. In diesem Fall ist es erforderlich, ändern Anwendungscode so, dass das Zugriffstoken zu verarbeiten, und legen Sie das zugeordnete Verbindungsattribut.
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
Folgendes ist eine Beispiel-Verbindungszeichenfolge für die Verwendung mit Azure Active Directory interaktive Authentifizierung. Beachten Sie, dass keine PWD-Feld enthalten sind, wie Sie das Kennwort eingegeben werden müssten, Bildschirm für Windows Azure-Authentifizierung verwenden.
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~

## <a name="see-also"></a>Weitere Informationen finden Sie unter
[Tokenbasierte authentifizierungsunterstützung für Azure SQL-Datenbank mithilfe von Azure AD-Authentifizierung](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

