---
title: Einführung in den Namespace „Microsoft.Data.SqlClient“
description: Die Einführungsseite für den Microsoft. Data. SqlClient-Namespace.
ms.date: 09/30/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 4f4034c557c13054dcfb6ed425ca996b0c5363f6
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452382"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Einführung in den Namespace „Microsoft.Data.SqlClient“

![Download-DownArrow-Circled](../../ssdt/media/download.png)[ADO.NET herunterladen](../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Auf dieser Seite wird beschrieben, wie der Microsoft. Data. SqlClient-Namespace zusätzliche Funktionen für den vorhandenen System. Data. SqlClient-Namespace bietet.
  
## <a name="release-notes"></a>Versionshinweise
Alle Anmerkungen zur Version sind im [GitHub-Repository](https://github.com/dotnet/SqlClient/tree/master/release-notes)verfügbar.

## <a name="new-features"></a>Neue Funktionen

### <a name="new-features-over-net-framework-472-systemdatasqlclient"></a>Neue Features über .NET Framework 4.7.2 System. Data. SqlClient

Datenklassifizierung: verfügbar in Azure SQL-Datenbank und Microsoft SQL Server 2019 seit CTP 2,0.

UTF-8-Unterstützung: verfügbar in Microsoft SQL Server SQL Server 2019 seit CTP 2,3.

### <a name="new-features-over-net-core-22-systemdatasqlclient"></a>Neue Features von .net Core 2,2 System. Data. SqlClient

Datenklassifizierung: verfügbar in Azure SQL-Datenbank und Microsoft SQL Server 2019 seit CTP 2,0.

UTF-8-Unterstützung: verfügbar in Microsoft SQL Server SQL Server 2019 seit CTP 2,3.

Always Encrypted mit Enklaven-Always Encrypted ist in Microsoft SQL Server 2016 und höher verfügbar. Die Enclave-Unterstützung wurde in Microsoft SQL Server 2019 CTP 2,0 eingeführt.

Authentifizierungsmodus für Authentifizierungs Active Directory Kennwort.

### <a name="data-classification"></a>Datenklassifizierung

Die Datenklassifizierung bietet einen neuen Satz von APIs, die schreibgeschützte Daten Sensitivität und Klassifizierungs Informationen zu Objekten verfügbar machen, die über SqlDataReader abgerufen werden, wenn die zugrunde liegende Quelle das Feature unterstützt und Metadaten zur [Daten Empfindlichkeit und zur Klassifizierung](../../relational-databases/security/sql-data-discovery-and-classification.md).

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

Für die UTF-8-Unterstützung sind keine Änderungen am Anwendungscode erforderlich. Diese SqlClient-Änderungen optimieren einfach die Kommunikation zwischen dem Client und dem Server, wenn der Server UTF-8 unterstützt und die zugrunde liegende Spalten Sortierung UTF-8 ist. Weitere Informationen finden Sie im Abschnitt "UTF-8" unter [Neuerungen in SQL Server 2019 Preview](../../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="always-encrypted-with-enclaves"></a>Immer mit Enklaven verschlüsselt

Im Allgemeinen sollte die vorhandene Dokumentation, die System. Data. SqlClient auf .NET Framework **und integrierten Spalten Hauptschlüssel-Speicheranbietern** verwendet, jetzt auch mit .net Core funktionieren.

 [Entwickeln von Always Encrypted mit .NET Framework-Datenanbieter](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted: Schützen von sensiblen Daten und Speichern von Verschlüsselungsschlüsseln im Windows-Zertifikat Speicher](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>Authentifizierung

Unterschiedliche Authentifizierungs Modi können mithilfe der Option für die Verbindungs Zeichenfolge für die _Authentifizierung_ angegeben werden. Weitere Informationen finden Sie in der [Dokumentation zu sqlauthenticationmethod](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2).

> [!NOTE]
> Benutzerdefinierte Schlüsselspeicher Anbieter, wie der Azure Key Vault-Anbieter, müssen aktualisiert werden, damit Microsoft. Data. SqlClient unterstützt wird. Gleichermaßen müssen Enclave-Anbieter auch aktualisiert werden, damit Microsoft. Data. SqlClient unterstützt wird.
> Always Encrypted wird nur für .NET Framework-und .net Core-Ziele unterstützt. Sie wird für .NET Standard nicht unterstützt, da .NET Standard bestimmte Verschlüsselungs Abhängigkeiten fehlt.
