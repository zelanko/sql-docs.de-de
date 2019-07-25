---
title: Verwenden von Azure Active Directory | Microsoft-Dokumentation für SQL Server
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: bazizi
ms.author: v-beaziz
ms.openlocfilehash: 44f92e782a497005ea47847301279e4341722d36
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68213553"
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

> [!NOTE]  
> Wenn Sie die folgenden Azure Active Directory Optionen mit dem OLE DB-Treiber verwenden, stellen Sie sicher, dass die [Active Directory-Authentifizierungsbibliothek für SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) installiert wurde:
> - Azure Active Directory Anmelde-ID und Kennwort
> - Integrierte Azure Active Directory-Authentifizierung
>
> Adal ist für die anderen Authentifizierungsmethoden oder OLE DB Vorgänge nicht erforderlich.

> [!NOTE]
> Die Verwendung der folgenden Authentifizierungs Modi `DataTypeCompatibility` , auf die (oder die entsprechende- `80` Eigenschaft) festgelegt ist, wird **nicht** unterstützt:
> - Azure Active Directory Authentifizierung mit Anmelde-ID und Kennwort
> - Azure Active Directory Authentifizierung mit Zugriffs Token
> - Integrierte Azure Active Directory-Authentifizierung

## <a name="connection-string-keywords-and-properties"></a>Verbindungs Zeichenfolgen-Schlüsselwörter
Die folgenden Schlüsselwörter für Verbindungs Zeichenfolgen wurden eingeführt, um Azure Active Directory Authentifizierung zu unterstützen:

|Verbindungszeichenfolgen-Schlüsselwort|Verbindungseigenschaft|und Beschreibung|
|---               |---                |---        |
|Access Token|SSPROP_AUTH_ACCESS_TOKEN|Gibt ein Zugriffs Token für die Authentifizierung bei Azure Active Directory an. |
|Authentifizierung|SSPROP_AUTH_MODE|Gibt die zu verwendende Authentifizierungsmethode an.|

Weitere Informationen zu den neuen Schlüsselwörtern/Eigenschaften finden Sie auf den folgenden Seiten:
- [Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Initialisierungs- und Autorisierungseigenschaften](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>Verschlüsselung und Zertifikat Überprüfung
In diesem Abschnitt werden die Änderungen im Verhalten bei der Verschlüsselung und der Zertifikat Validierung erläutert. Diese Änderungen sind **nur** wirksam, wenn die Verbindungs Zeichenfolgen-Schlüsselwörter für die neue Authentifizierung oder Zugriffs Token verwendet werden (oder die entsprechenden Eigenschaften).

### <a name="encryption"></a>Verschlüsselung
Um die Sicherheit zu verbessern, überschreibt der Treiber bei Verwendung der neuen Verbindungs Eigenschaften/-Schlüsselwörter den Standard Verschlüsselungs Wert, `yes`indem er auf festgelegt wird. Überschreiben erfolgt beim Initialisierungs Zeitpunkt des Datenquellen Objekts. Wenn die Verschlüsselung auf irgendeine Weise vor der Initialisierung festgelegt wird, wird der Wert beachtet und nicht überschrieben.

> [!NOTE]   
> In ADO-Anwendungen und Anwendungen, die die `IDBInitialize` -Schnitt `IDataInitialize::GetDataSource`Stelle über abrufen, legt die Kernkomponente, die die-Schnittstelle implementiert `no`, die Verschlüsselung explizit auf den Standardwert fest. Folglich beachten die neuen Authentifizierungs Eigenschaften/-Schlüsselwörter diese Einstellung, und der Verschlüsselungs Wert wird **nicht** überschrieben. Daher wird **empfohlen** , diese Anwendungen explizit festzulegen `Use Encryption for Data=true` , um den Standardwert zu überschreiben.

### <a name="certificate-validation"></a>Zertifikatüberprüfung
Um die Sicherheit zu verbessern, berücksichtigen die neuen Verbindungs Eigenschaften `TrustServerCertificate` /-Schlüsselwörter die Einstellung (und die zugehörigen Schlüsselwörter/Eigenschaften der Verbindungs Zeichenfolge) **unabhängig von der Client Verschlüsselungs Einstellung**. Dies hat zur Folge, dass das Serverzertifikat standardmäßig überprüft wird.

> [!NOTE]   
> Die Zertifikat Überprüfung kann auch durch das `Value` -Feld `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2` des Registrierungs Eintrags gesteuert werden. Gültige Werte sind `0` und `1`. Der OLE DB Treiber wählt die sicherste Option zwischen der Registrierung und den Einstellungen für die Verbindungs Eigenschaft/das Schlüsselwort aus. Das heißt, der Treiber überprüft das Serverzertifikat, solange mindestens eine der Registrierungs-/Verbindungseinstellungen die Serverzertifikats Überprüfung ermöglicht.

## <a name="gui-additions"></a>GUI-Ergänzungen
Die grafische Benutzeroberfläche des Treibers wurde erweitert, um Azure Active Directory Authentifizierung zu ermöglichen. Weitere Informationen finden Sie in den folgenden Themen:
- [Dialogfeld „SQL Server-Anmeldung“](../help-topics/sql-server-login-dialog.md)
- [Konfiguration von Universal Data Link (UDL)](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>Exemplarische Verbindungszeichenfolgen
Dieser Abschnitt enthält Beispiele für neue und vorhandene Verbindungs Zeichenfolgen-Schlüsselwörter `IDataInitialize::GetDataSource` , `DBPROP_INIT_PROVIDERSTRING` die mit der-und-Eigenschaft verwendet werden

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

### <a name="integrated-windows-authentication-using-security-support-provider-interface--sspi"></a>Integrierte Windows-Authentifizierung mithilfe der Security Support Provider Interface (SSPI)

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

### <a name="aad-username-and-password-authentication-using-adal"></a>Aad-Benutzernamen-und Kenn Wort Authentifizierung mit Adal

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Authentifizierung = activedirectorypassword**; Benutzer-ID = [username]; Password = [Kennwort]; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [Server];D atabase = [Datenbank]; **Authentifizierung = activedirectorypassword**; UID = [username]; PWD = [Kennwort]; Verschlüsseln = ja

### <a name="integrated-azure-active-directory-authentication-using-adal"></a>Integrierte Azure Active Directory Authentifizierung mit Adal

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Authentication = activedirectoryintegrated**; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [Server];D atabase = [Datenbank]; **Authentication = activedirectoryintegrated**; Verschlüsseln = ja

### <a name="azure-active-directory-authentication-using-an-access-token"></a>Azure Active Directory Authentifizierung mit einem Zugriffs Token

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = msoledbsql; Datenquelle = [Server]; anfangs Katalog = [Datenbank]; **Zugriffs Token = [Zugriffs Token]** ; Verschlüsselung für Daten verwenden = true
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Das Bereitstellen von `DBPROP_INIT_PROVIDERSTRING` Zugriffs Token über wird nicht unter

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

- Konfigurieren von Treiber Verbindungen mithilfe von [Schlüsselwörtern für Verbindungs](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md) Zeichenfolgen, die vom OLE DB Treiber
