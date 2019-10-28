---
title: Verwenden von Azure Active Directory | Microsoft-Dokumentation für SQL Server
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: bazizi
ms.author: v-beaziz
ms.openlocfilehash: b459877be731da11b33d13772bbf186ecf72198c
ms.sourcegitcommit: 4c75b49599018124f05f91c1df3271d473827e4d
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72381851"
---
# <a name="using-azure-active-directory"></a>Verwenden von Azure Active Directory
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>Zweck

Ab Version 18.2.1 ermöglicht der Microsoft OLE DB-Treiber für SQL Server OLE DB Anwendungen das Herstellen einer Verbindung mit einer Instanz von Azure SQL-Datenbank mithilfe einer Verbund Identität. Die neuen Authentifizierungsmethoden umfassen:
- Azure Active Directory Anmelde-ID und Kennwort
- Azure Active Directory-Zugriffstoken
- Integrierte Azure Active Directory-Authentifizierung
- SQL-Anmelde-ID und Kennwort

In Version 18,3 wird Unterstützung für die folgenden Authentifizierungsmethoden hinzugefügt:
- Interaktive Azure Active Directory-Authentifizierung
- Azure Active Directory-MSI-Authentifizierung

> [!NOTE]
> Die Verwendung der folgenden Authentifizierungs Modi, bei denen `DataTypeCompatibility` (oder die entsprechende-Eigenschaft) auf `80` festgelegt ist, wird **nicht** unterstützt:
> - Azure Active Directory Authentifizierung mit Anmelde-ID und Kennwort
> - Azure Active Directory Authentifizierung mit Zugriffs Token
> - Integrierte Azure Active Directory-Authentifizierung
> - Interaktive Azure Active Directory-Authentifizierung
> - Azure Active Directory-MSI-Authentifizierung

## <a name="connection-string-keywords-and-properties"></a>Verbindungs Zeichenfolgen-Schlüsselwörter
Die folgenden Schlüsselwörter für Verbindungs Zeichenfolgen wurden eingeführt, um Azure Active Directory Authentifizierung zu unterstützen:

|Verbindungszeichenfolgen-Schlüsselwort|Verbindungseigenschaft|und Beschreibung|
|---               |---                |---        |
|Access Token|SSPROP_AUTH_ACCESS_TOKEN|Gibt ein Zugriffs Token für die Authentifizierung bei Azure Active Directory an. |
|Authentifizierung|SSPROP_AUTH_MODE|Gibt die zu verwendende Authentifizierungsmethode an.|

Weitere Informationen zu den neuen Schlüsselwörtern/Eigenschaften finden Sie auf den folgenden Seiten:
- [Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Initialisierungs- und Autorisierungseigenschaften](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>Verschlüsselung und Zertifikatüberprüfung
In diesem Abschnitt werden die Änderungen im Verhalten bei der Verschlüsselung und der Zertifikat Validierung erläutert. Diese Änderungen sind **nur** wirksam, wenn die Verbindungs Zeichenfolgen-Schlüsselwörter für die neue Authentifizierung oder Zugriffs Token verwendet werden (oder die entsprechenden Eigenschaften).

### <a name="encryption"></a>Verschlüsselung
Um die Sicherheit zu verbessern, überschreibt der Treiber bei Verwendung der neuen Verbindungs Eigenschaften/-Schlüsselwörter den Standard Verschlüsselungs Wert, indem er auf `yes` festgelegt wird. Überschreiben erfolgt beim Initialisierungs Zeitpunkt des Datenquellen Objekts. Wenn die Verschlüsselung auf irgendeine Weise vor der Initialisierung festgelegt wird, wird der Wert beachtet und nicht überschrieben.

> [!NOTE]   
> In ADO-Anwendungen und Anwendungen, die die `IDBInitialize`-Schnittstelle über `IDataInitialize::GetDataSource` abrufen, legt die Kernkomponente, die die-Schnittstelle implementiert, die Verschlüsselung explizit auf den Standardwert `no` fest. Folglich beachten die neuen Authentifizierungs Eigenschaften/-Schlüsselwörter diese Einstellung, und der Verschlüsselungs Wert wird **nicht** überschrieben. Daher wird **empfohlen** , dass diese Anwendungen `Use Encryption for Data=true` explizit festlegen, um den Standardwert zu überschreiben.

### <a name="certificate-validation"></a>Zertifikatüberprüfung
Um die Sicherheit zu verbessern, berücksichtigen die neuen Verbindungs Eigenschaften/-Schlüsselwörter die `TrustServerCertificate` Einstellung (und die entsprechenden Schlüsselwörter/Eigenschaften der Verbindungs Zeichenfolge) **unabhängig von der Client Verschlüsselungs Einstellung**. Dies hat zur Folge, dass das Serverzertifikat standardmäßig überprüft wird.

> [!NOTE]   
> Die Zertifikat Überprüfung kann auch über das `Value`-Feld des `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2` Registrierungs Eintrags gesteuert werden. Gültige Werte sind `0` und `1`. Der OLE DB Treiber wählt die sicherste Option zwischen der Registrierung und den Einstellungen für die Verbindungs Eigenschaft/das Schlüsselwort aus. Das heißt, der Treiber überprüft das Serverzertifikat, solange mindestens eine der Registrierungs-/Verbindungseinstellungen die Serverzertifikats Überprüfung ermöglicht.

## <a name="gui-additions"></a>GUI-Ergänzungen
Die grafische Benutzeroberfläche des Treibers wurde erweitert, um Azure Active Directory Authentifizierung zu ermöglichen. Weitere Informationen finden Sie in den folgenden Themen:
- [Dialogfeld „SQL Server-Anmeldung“](../help-topics/sql-server-login-dialog.md)
- [Konfiguration von Universal Data Link (UDL)](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>Exemplarische Verbindungszeichenfolgen
In diesem Abschnitt werden Beispiele für neue und vorhandene Verbindungs Zeichenfolgen-Schlüsselwörter angezeigt, die mit `IDataInitialize::GetDataSource` und `DBPROP_INIT_PROVIDERSTRING`-Eigenschaft verwendet werden.

### <a name="sql-authentication"></a>SQL-Authentifizierung
- Verwenden von `IDataInitialize::GetDataSource`:
    - Neu:
        > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Authentifizierung = sqlpassword**; Benutzer-ID = [username]; Password = [Kennwort]; Verschlüsselung für Daten verwenden = true
    - Veraltet:
        > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; Benutzer-ID = [username]; Password = [Kennwort]; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    - Neu:
        > Server = [Server];D atabase = [Datenbank]; **Authentifizierung = sqlpassword**; UID = [username]; PWD = [Kennwort]; Verschlüsseln = ja
    - Veraltet:
        > Server = [Server];D atabase = [Datenbank]; UID = [username]; PWD = [Kennwort]; Verschlüsseln = ja

### <a name="integrated-windows-authentication-using-security-support-provider-interface-sspi"></a>Integrierte Windows-Authentifizierung mithilfe der Security Support Provider Interface (SSPI)

- Verwenden von `IDataInitialize::GetDataSource`:
    - Neu:
        > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Authentication = activedirectoryintegrated**; Verschlüsselung für Daten verwenden = true
    - Veraltet:
        > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Integrierte Sicherheit = SSPI**; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    - Neu:
        > Server = [Server];D atabase = [Datenbank]; **Authentication = activedirectoryintegrated**; Verschlüsseln = ja
    - Veraltet:
        > Server = [Server];D atabase = [Datenbank]; **Trusted_Connection = ja**; Verschlüsseln = ja

### <a name="azure-active-directory-username-and-password-authentication"></a>Azure Active Directory Authentifizierung mit Benutzername und Kennwort

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Authentifizierung = activedirectorypassword**; Benutzer-ID = [username]; Password = [Kennwort]; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [Server];D atabase = [Datenbank]; **Authentifizierung = activedirectorypassword**; UID = [username]; PWD = [Kennwort]; Verschlüsseln = ja

### <a name="azure-active-directory-integrated-authentication"></a>Integrierte Azure Active Directory-Authentifizierung

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Authentication = activedirectoryintegrated**; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [Server];D atabase = [Datenbank]; **Authentication = activedirectoryintegrated**; Verschlüsseln = ja

### <a name="azure-active-directory-authentication-using-an-access-token"></a>Azure Active Directory Authentifizierung mit einem Zugriffs Token

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Zugriffs Token = [Zugriffs Token]** ; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Das Bereitstellen von Zugriffs Token über `DBPROP_INIT_PROVIDERSTRING` wird nicht unterstützt

### <a name="azure-active-directory-interactive-authentication"></a>Interaktive Azure Active Directory-Authentifizierung

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Authentication = activedirectoryinteractive**; Benutzer-ID = [username]; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [Server];D atabase = [Datenbank]; **Authentication = activedirectoryinteractive**; UID = [username]; Verschlüsseln = ja

### <a name="azure-active-directory-msi-authentication"></a>Azure Active Directory-MSI-Authentifizierung

- Verwenden von `IDataInitialize::GetDataSource`:
    - Benutzerseitig zugewiesene verwaltete Identität:
        > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Authentication = activedirectorymsi**; Benutzer-ID = [Objekt-ID]; Verschlüsselung für Daten verwenden = true
    - Systemseitig zugewiesene verwaltete Identität:
        > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Authentication = activedirectorymsi**; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    - Benutzerseitig zugewiesene verwaltete Identität:
        > Server = [Server];D atabase = [Datenbank]; **Authentication = activedirectorymsi**; UID = [Objekt-ID]; Verschlüsseln = ja
    - Systemseitig zugewiesene verwaltete Identität:
        > Server = [Server];D atabase = [Datenbank]; **Authentication = activedirectorymsi**; Verschlüsseln = ja

## <a name="code-samples"></a>Codebeispiele

Die folgenden Beispiele zeigen den Code, der zum Herstellen einer Verbindung mit Azure Active Directory mit Verbindungs Schlüsselwörtern erforderlich ist. 

### <a name="access-token"></a>Access Token
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    wchar_t accessToken[] = L"eyJ0eXAiOi...";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Access Token=" + accessToken + L";Use Encryption for Data=true;";
    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```
### <a name="active-directory-integrated"></a>ActiveDirectoryIntegrated
```cpp
#include <string>
#include <iostream>
#include <msdasc.h>

int main()
{
    wchar_t azureServer[] = L"server";
    wchar_t azureDatabase[] = L"mydatabase";
    IDBInitialize *pIDBInitialize = nullptr;
    IDataInitialize* pIDataInitialize = nullptr;
    HRESULT hr = S_OK;

    CoInitialize(nullptr);

    // Construct the connection string.
    std::wstring connString = L"Provider=MSOLEDBSQL;Data Source=" + std::wstring(azureServer) + L";Initial Catalog=" + 
                              std::wstring(azureDatabase) + L";Authentication=ActiveDirectoryIntegrated;Use Encryption for Data=true;";

    hr = CoCreateInstance(CLSID_MSDAINITIALIZE, nullptr, CLSCTX_INPROC_SERVER, 
                          IID_IDataInitialize, reinterpret_cast<LPVOID*>(&pIDataInitialize));
    if (FAILED(hr)) 
    {
        std::cout << "Failed to create an IDataInitialize instance." << std::endl;
        goto Cleanup;
    }
    hr = pIDataInitialize->GetDataSource(nullptr, CLSCTX_INPROC_SERVER, connString.c_str(), 
                                         IID_IDBInitialize, reinterpret_cast<IUnknown**>(&pIDBInitialize));
    if (FAILED(hr))
    {
        std::cout << "Failed to get data source object." << std::endl;
        goto Cleanup;
    }
    hr = pIDBInitialize->Initialize();
    if (FAILED(hr))
    {
        std::cout << "Failed to establish connection." << std::endl;
        goto Cleanup;
    }

Cleanup:
    if (pIDBInitialize)
    {
        pIDBInitialize->Uninitialize();
        pIDBInitialize->Release();
    }
    if (pIDataInitialize)
    {
        pIDataInitialize->Release();
    }

    CoUninitialize();
}
```

## <a name="next-steps"></a>Nächste Schritte
- [Autorisieren Sie den Zugriff auf Azure Active Directory Webanwendungen mit dem OAuth 2,0-Code Grant-Flow](https://go.microsoft.com/fwlink/?linkid=2072672).

- Erfahren Sie mehr über die [Azure Active Directory-Authentifizierung](https://go.microsoft.com/fwlink/?linkid=2073783) bei SQL Server.

- Konfigurieren von Treiber Verbindungen mithilfe von [Schlüsselwörtern für Verbindungs Zeichenfolgen](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md) , die vom OLE DB Treiber
