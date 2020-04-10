---
title: Einführung in den Namespace „Microsoft.Data.SqlClient“
description: Die Einführungsseite für den Namespace Microsoft.Data.SqlClient.
ms.date: 09/30/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 9a5f787e9cd95e3d2966e5bc2b722aada5b97032
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928998"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Einführung in den Namespace „Microsoft.Data.SqlClient“

[!INCLUDE[Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

## <a name="release-notes-for-microsoftdatasqlclient-110"></a>Versionshinweise zu Microsoft.Data.SqlClient 1.1.0

Die Versionshinweise finden Sie auch im GitHub-Repository: [Hinweise zur Version 1.1](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1).

### <a name="new-features"></a>Neue Funktionen

#### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted mit Secure Enclaves

Always Encrypted ist ab Microsoft SQL Server 2016 verfügbar. Secure Enclaves sind ab Microsoft SQL Server 2019 verfügbar. Um das Enclave-Feature nutzen zu können, müssen die Verbindungszeichenfolgen das erforderliche Nachweisprotokoll und die Nachweis-URL enthalten. Beispiele:

```
Attestation Protocol=HGS;Enclave Attestation Url=<attestation_url_for_HGS>
```

Weitere Informationen finden Sie unter:

- [SqlClient-Unterstützung für Always Encrypted](sql/sqlclient-support-always-encrypted.md)
- [Tutorial: Entwickeln einer .NET-Anwendung mithilfe von Always Encrypted mit Secure Enclaves](sql/tutorial-always-encrypted-enclaves-develop-net-apps.md)

## <a name="release-notes-for-microsoftdatasqlclient-10"></a>Versionshinweise für Microsoft.Data.SqlClient 1.0

Die erste Version des Namespace Microsoft.Data.SqlClient bietet gegenüber dem bestehenden Namespace System.Data.SqlClient zusätzliche Funktionalität.
Die Versionshinweise finden Sie auch im GitHub-Repository: [Hinweise zur Version 1.0](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.0).

### <a name="new-features"></a>Neue Funktionen

#### <a name="new-features-over-net-framework-472-systemdatasqlclient"></a>Neue Features im Vergleich zu System.Data.SqlClient in .NET Framework 4.7.2

- **Datenklassifizierung**: verfügbar in Azure SQL-Datenbank und Microsoft SQL Server 2019.

- **UTF-8-Unterstützung**: verfügbar in Microsoft SQL Server 2019.

#### <a name="new-features-over-net-core-22-systemdatasqlclient"></a>Neue Features im Vergleich zu System.Data.SqlClient in .NET Core 2.2

- **Datenklassifizierung**: verfügbar in Azure SQL-Datenbank und Microsoft SQL Server 2019.

- **UTF-8-Unterstützung**: verfügbar in Microsoft SQL Server 2019.

- **Authentifizierung**: Active Directory-Kennwortauthentifizierungsmodus.

### <a name="data-classification"></a>Datenklassifizierung

Das Feature „Datenklassifizierung“ bietet eine neue Gruppe von APIs, die schreibgeschützte Informationen zur Datenvertraulichkeit und -klassifizierung von Objekten verfügbar machen. Diese werden über SqlDataReader abgerufen, wenn die zugrunde liegende Quelle das Feature unterstützt und Metadaten zu [Datenvertraulichkeit und -klassifizierung](../../relational-databases/security/sql-data-discovery-and-classification.md) enthält.

```csharp
public class SqlDataReader
{
    public Microsoft.Data.SqlClient.DataClassification.SensitivityClassification SensitivityClassification
}

namespace Microsoft.Data.SqlClient.DataClassification
{
    public class ColumnSensitivity
    {
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.SensitivityProperty> SensitivityProperties
    }
    public class InformationType
    {
        public string Id
        public string Name
    }
    public class Label
    {
        public string Id
        public string Name
    }
    public class SensitivityClassification
    {
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.ColumnSensitivity> ColumnSensitivities
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.InformationType> InformationTypes
        public System.Collections.ObjectModel.ReadOnlyCollection<Microsoft.Data.SqlClient.DataClassification.Label> Labels
    }
    public class SensitivityProperty
    {
        public Microsoft.Data.SqlClient.DataClassification.InformationType InformationType
        public Microsoft.Data.SqlClient.DataClassification.Label Label
    }
}
```

### <a name="utf-8-support"></a>Unterstützung für UTF-8

Für UTF-8-Unterstützung sind keine Änderungen am Anwendungscode erforderlich. Diese SqlClient-Änderungen optimieren lediglich die Kommunikation zwischen Client und Server, wenn der Server UTF-8 unterstützt und die zugrunde liegende Spaltensortierung UTF-8 ist. Weitere Informationen finden Sie unter [Neuerungen in SQL Server 2019](../../sql-server/what-s-new-in-sql-server-ver15.md) im Abschnitt „UTF-8“.

### <a name="always-encrypted-with-enclaves"></a>Always Encrypted mit Enclaves

Im Allgemeinen sollte die vorhandene Dokumentation zu System.Data.SqlClient in .NET Framework **und integrierten Anbietern von Speichern für Spaltenhauptschlüssel** nun auch für .NET Core gelten.

 [Entwickeln von Always Encrypted mit .NET Framework-Datenanbieter](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted: Schützen vertraulicher Daten und Speichern von Verschlüsselungsschlüsseln im Windows-Zertifikatspeicher](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>Authentifizierung

Unterschiedliche Authentifizierungsmodi können angegeben werden, indem in der Verbindungszeichenfolge die Option _Authentifizierung_ verwendet wird. Weitere Informationen finden Sie in der Dokumentation zu [SqlAuthenticationMethod](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2).

> [!NOTE]
> Anbieter benutzerdefinierter Schlüsselspeicher wie der Azure Key Vault-Anbieter müssen aktualisiert werden, damit Microsoft.Data.SqlClient unterstützt wird. Ebenso müssen auch die Enclave-Anbieter aktualisiert werden, um Microsoft.Data.SqlClient zu unterstützen.
> Always Encrypted wird nur für .NET Framework- und .NET Core-Ziele unterstützt. Das Feature wird nicht für .NET Standard nicht unterstützt, da .NET Standard bestimmte Verschlüsselungsabhängigkeiten fehlen.
