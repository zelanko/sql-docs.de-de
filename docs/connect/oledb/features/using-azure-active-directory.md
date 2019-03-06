---
title: Verwenden von Azure Active Directory | Microsoft-Dokumentation für SQLServer
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
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744824"
---
# <a name="using-azure-active-directory"></a>Verwenden von Azure Active Directory
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

## <a name="purpose"></a>Zweck

Ab Version 18.2.1 können Sie Microsoft OLE DB-Treiber für SQL Server OLE DB-Anwendungen für die Verbindung mit einer Instanz von Azure SQL-Datenbank mithilfe eines Identitätsverbunds. Die neue Authentifizierungsmethoden gehören:
- Azure Active Directory-Benutzernamens und Kennworts
- Azure Active Directory-Zugriffstoken
- Integrierte Azure Active Directory-Authentifizierung
- SQL-Anmelde-ID und Kennwort

> [!NOTE]  
> Wenn Sie die folgenden Optionen für die Azure Active Directory mit dem OLE DB-Treiber verwenden, stellen Sie sicher, dass die [Active Directory-Authentifizierungsbibliothek für SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) installiert wurde:
> - Azure Active Directory-Benutzernamens und Kennworts
> - Integrierte Azure Active Directory-Authentifizierung
>
> ADAL nicht für die anderen Authentifizierungsmethoden oder OLE DB-Vorgänge erforderlich.

> [!NOTE]
> Verwenden die folgenden Authentifizierungsmodi mit `DataTypeCompatibility` (oder der entsprechenden Eigenschaft) legen Sie auf `80` ist **nicht** unterstützt:
> - Azure Active Directory-Authentifizierung mit Anmelde-ID und Kennwort
> - Azure Active Directory-Authentifizierung mit Zugriffstoken
> - Integrierte Azure Active Directory-Authentifizierung

## <a name="connection-string-keywords-and-properties"></a>Schlüsselwörter für Verbindungszeichenfolgen und Eigenschaften
Die folgenden Schlüsselwörter für Verbindungszeichenfolgen wurden eingeführt, um die Azure Active Directory-Authentifizierung unterstützen:

|Verbindungszeichenfolgen-Schlüsselwort|Verbindungseigenschaft|und Beschreibung|
|---               |---                |---        |
|Access Token|SSPROP_AUTH_ACCESS_TOKEN|Gibt ein Zugriffstoken für den Azure Active Directory zu authentifizieren. |
|Authentifizierung|SSPROP_AUTH_MODE|Gibt die zu verwendende Authentifizierungsmethode an.|

Weitere Informationen über die neuen Schlüsselwörter/Eigenschaften finden Sie unter den folgenden Seiten:
- [Verwenden von Verbindungszeichenfolgen-Schlüsselwörtern mit dem OLE DB-Treiber für SQL Server](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)
- [Initialisierungs- und Autorisierungseigenschaften](../ole-db-data-source-objects/initialization-and-authorization-properties.md)

## <a name="encryption-and-certificate-validation"></a>Verbindungsverschlüsselung und zertifikatüberprüfung
Dieser Abschnitt beschreibt die Änderungen in der Verschlüsselung und Zertifikat Validierungsverhalten. Diese Änderungen sind **nur** ab, die bei Verwendung der neuen Authentifizierung oder Zugriffstoken Schlüsselwörter für Verbindungszeichenfolgen (oder die entsprechenden Eigenschaften).

### <a name="encryption"></a>Verschlüsselung
Zur Verbesserung der Sicherheit, wenn die neuen Eigenschaften/Verbindungsschlüsselwörter verwendet werden, überschreibt der Treiber den Standardwert für die Verschlüsselung durch Festlegung auf `yes`. Überschreiben von erfolgt während der Initialisierung von Data Source-Objekt. Wenn Mitteln durch Verschlüsselung vor der Initialisierung festgelegt ist, wird der Wert berücksichtigt und nicht außer Kraft gesetzt.

> [!NOTE]   
> In ADO-Anwendungen und Anwendungen, die erhalten die `IDBInitialize` Schnittstelle, über `IDataInitialize::GetDataSource`, die zentrale Komponente, die die Schnittstelle explizit implementieren legt fest, Verschlüsselung auf den Standardwert des `no`. Die neuen Eigenschaften/Schlüsselwörter für die Benutzerauthentifizierung daher berücksichtigen, diese Einstellung und dem Verschlüsselungswert **ist nicht** außer Kraft gesetzt. Daher ist es **empfohlen** , die diese Anwendungen explizit festgelegt `Use Encryption for Data=true` auf den Standardwert überschreiben.

### <a name="certificate-validation"></a>Zertifikatüberprüfung
Zur Erhöhung der Sicherheit der neuen Eigenschaften/Verbindungsschlüsselwörter berücksichtigt die `TrustServerCertificate` Einstellung (und die entsprechenden Verbindungszeichenfolgen-Schlüsselwörter /-Eigenschaften) **unabhängig von der Clienteinstellung für die Verschlüsselung**. Serverzertifikat wird daher standardmäßig überprüft.

> [!NOTE]   
> Überprüfung des Zertifikats kann auch über gesteuert werden die `Value` Feld der `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SNI18.0\GeneralFlags\Flag2` Registrierungseintrag. Gültige Werte sind `0` und `1`. Der OLE DB-Treiber wählt die sicherste Option zwischen der Registrierung und die Verbindungseinstellungen für den Property-Schlüsselwort. D. h. überprüft der Treiber das Serverzertifikat, solange mindestens eine der die Registrierung/Verbindungseinstellungen für die Überprüfung des Serverzertifikats ermöglicht.

## <a name="gui-additions"></a>GUI-Erweiterungen
Die grafische Benutzeroberfläche für die Treiber wurde verbessert, um die Azure Active Directory-Authentifizierung zu ermöglichen. Weitere Informationen finden Sie in den folgenden Themen:
- [Dialogfeld „SQL Server-Anmeldung“](../help-topics/sql-server-login-dialog.md)
- [Universal Data Link (UDL)-Konfiguration](../help-topics/data-link-pages.md)

## <a name="example-connection-strings"></a>Exemplarische Verbindungszeichenfolgen
Dieser Abschnitt enthält Beispiele für neue und vorhandene Verbindung Schlüsselwörter für Verbindungszeichenfolgen mit `IDataInitialize::GetDataSource` und `DBPROP_INIT_PROVIDERSTRING` Eigenschaft.

### <a name="sql-authentication"></a>SQL-Authentifizierung
- Verwenden von `IDataInitialize::GetDataSource`:
    - Neu:
        > Provider = MSOLEDBSQL; Datenquelle = [Server]; Initial Catalog = [Database]; **Authentication = SqlPassword**; Benutzer-ID = [Benutzername]; Password =, [Password]; Verschlüsselung für Daten verwenden = True
    - Veraltet:
        > Provider = MSOLEDBSQL; Datenquelle = [Server]; Initial Catalog = [Database]; Benutzer-ID = [Benutzername]; Password =, [Password]; Verschlüsselung für Daten verwenden = True
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    - Neu:
        > Server = [Server], Datenbank = [Database]; **Authentication = SqlPassword**; Benutzer-ID = [Benutzername]; PWD =, [Password]; Verschlüsseln = Ja
    - Veraltet:
        > Server = [Server], Datenbank = [Database]; Benutzer-ID = [Benutzername]; PWD =, [Password]; Verschlüsseln = Ja

### <a name="integrated-windows-authentication-using-security-support-provider-interface--sspi"></a>Integrierte Windows-Authentifizierung, die mit der Security Support Provider Interface (SSPI)

- Verwenden von `IDataInitialize::GetDataSource`:
    - Neu:
        > Provider = MSOLEDBSQL; Datenquelle = [Server]; Initial Catalog = [Database]; **Authentication = ActiveDirectoryIntegrated**; Verschlüsselung für Daten verwenden = True
    - Veraltet:
        > Provider = MSOLEDBSQL; Datenquelle = [Server]; Initial Catalog = [Database]; **Integrierte Sicherheit = SSPI**; Verschlüsselung für Daten verwenden = True
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    - Neu:
        > Server = [Server], Datenbank = [Database]; **Authentication = ActiveDirectoryIntegrated**; Verschlüsseln = Ja
    - Veraltet:
        > Server = [Server], Datenbank = [Database]; **Trusted_Connection = Yes**; Verschlüsseln = Ja

### <a name="aad-username-and-password-authentication-using-adal"></a>AAD-Benutzername und Kennwort-Authentifizierung mit ADAL

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = MSOLEDBSQL; Datenquelle = [Server]; Initial Catalog = [Database]; **Authentication = ActiveDirectoryPassword**; Benutzer-ID = [Benutzername]; Password =, [Password]; Verschlüsselung für Daten verwenden = True
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [Server], Datenbank = [Database]; **Authentication = ActiveDirectoryPassword**; Benutzer-ID = [Benutzername]; PWD =, [Password]; Verschlüsseln = Ja

### <a name="integrated-azure-active-directory-authentication-using-adal"></a>Integrierte Azure Active Directory-Authentifizierung mit ADAL

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = MSOLEDBSQL; Datenquelle = [Server]; Initial Catalog = [Database]; **Authentication = ActiveDirectoryIntegrated**; Verschlüsselung für Daten verwenden = True
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Server = [Server], Datenbank = [Database]; **Authentication = ActiveDirectoryIntegrated**; Verschlüsseln = Ja

### <a name="azure-active-directory-authentication-using-an-access-token"></a>Azure Active Directory-Authentifizierung mithilfe eines Zugriffstokens

- Verwenden von `IDataInitialize::GetDataSource`:
    > Provider = MSOLEDBSQL; Datenquelle = [Server]; Initial Catalog = [Database]; **Zugriffstoken = [Zugriffstoken]**; Verschlüsselung für Daten verwenden = True
- Verwenden von `DBPROP_INIT_PROVIDERSTRING`:
    > Bereitstellen von Zugriffstoken mithilfe `DBPROP_INIT_PROVIDERSTRING` wird nicht unterstützt.

## <a name="code-samples"></a>Codebeispiele

Die folgenden Beispiele veranschaulichen den Code mit Verbindungsschlüsselwörter eine Verbindung mit Azure Active Directory erforderlich sind. 

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
- [Autorisieren des Zugriffs auf Azure Active Directory-Webanwendungen, die mit dem OAuth 2.0-Code Grant-Datenfluss](https://go.microsoft.com/fwlink/?linkid=2072672).

- Erfahren Sie mehr über die [Azure Active Directory-Authentifizierung](https://go.microsoft.com/fwlink/?linkid=2073783) bei SQL Server.

- Konfigurieren der Treiber-Verbindungen mithilfe von [Schlüsselwörter für Verbindungszeichenfolgen](../applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md) der OLE DB-Treiber unterstützt.
