---
title: Einführung in den Namespace „Microsoft.Data.SqlClient“
description: Die Einführungsseite für den Namespace Microsoft.Data.SqlClient.
ms.date: 06/23/2019
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 3a4f0611d3708aba9557deb81ab702f29e7a7462
ms.sourcegitcommit: 22f687e9e8b4f37b877b2d19c5090dade8fa26d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334589"
---
# <a name="introduction-to-microsoftdatasqlclient-namespace"></a>Einführung in den Namespace „Microsoft.Data.SqlClient“

[!INCLUDE [Driver_ADONET_Download](../../includes/driver_adonet_download.md)]

## <a name="release-notes-for-microsoftdatasqlclient-20"></a>Versionshinweise für Microsoft.Data.SqlClient 2.0

Die Versionshinweise finden Sie auch im GitHub-Repository: [Versionshinweise zu 2.0](https://github.com/dotnet/SqlClient/tree/master/release-notes/2.0)

### <a name="breaking-changes"></a>Aktuelle Änderungen

- Die Zugriffsmodifizierer für die Schnittstelle `SqlColumnEncryptionEnclaveProvider` des Enclave-Anbieters wurde von `public` in `internal` geändert.

- Konstanten in der `SqlClientMetaDataCollectionNames`-Klasse wurden aktualisiert, um die Änderungen in SQL Server widerzuspiegeln.

- Der Treiber führt nun eine Überprüfung des Serverzertifikats aus, wenn die SQL Server-Zielinstanz TLS-Verschlüsselung erzwingt. Dies ist die Standardeinstellung für Azure-Verbindungen.

- `SqlDataReader.GetSchemaTable()` gibt nun anstelle von `null` eine leere `DataTable`-Klasse zurück.

- Der Treiber führt nun eine Rundung von Dezimalzahlen durch, um dem Verhalten von SQL Server zu entsprechen. Wenn eine Abwärtskompatibilität erforderlich ist, kann das bisherige Verhalten (Kürzen) mithilfe einer AppContext-Option aktiviert werden.

- Bei .NET Framework-Anwendungen, die **Microsoft.Data.SqlClient** nutzen, heißen die zuvor in die Ordner `bin\x64` und `bin\x86` heruntergeladenen SNI.dll-Dateien nun `Microsoft.Data.SqlClient.SNI.x64.dll` und ` Microsoft.Data.SqlClient.SNI.x86.dll` und werden in das `bin`-Verzeichnis heruntergeladen.

- Neue Synonyme für Verbindungszeichenfolgeneigenschaften ersetzen alte Eigenschaften beim Abrufen von Verbindungszeichenfolgen aus `SqlConnectionStringBuilder` aus Gründen der Konsistenz. [Weitere Informationen](#new-connection-string-property-synonyms)

### <a name="new-features"></a>Neue Funktionen

#### <a name="dns-failure-resiliency"></a>DNS-Fehlerresilienz

Der Treiber speichert IP-Adressen ab sofort für jede erfolgreiche Verbindung zu einem SQL Server-Endpunkt zwischen, der das Feature unterstützt. Wenn während eines Verbindungsversuchs ein Fehler bei der DNS-Auflösung auftritt, versucht der Treiber, mithilfe einer zwischengespeicherten IP-Adresse für diesen Server (sofern vorhanden) eine Verbindung herzustellen. 

#### <a name="eventsource-tracing"></a>EventSource-Nachverfolgung

Ab diesem Release wird das Erfassen von Ereignisablaufprotokollen unterstützt, um Anwendungen zu debuggen. Zur Erfassung dieser Ereignisse müssen Clientanwendungen auf Ereignisse aus der EventSource-Implementierung von SqlClient lauschen:

```
Microsoft.Data.SqlClient.EventSource
```

Weitere Informationen finden Sie unter [Aktivieren der Ereignisablaufverfolgung in SqlClient](enable-eventsource-tracing.md).

#### <a name="enabling-managed-networking-on-windows"></a>Aktivieren verwalteter Netzwerke unter Windows

Mithilfe der neuen AppContext-Option **Switch.Microsoft.Data.SqlClient.UseManagedNetworkingOnWindows** kann unter Windows zu Test- und Debuggingzwecken eine verwaltete SNI-Implementierung verwendet werden. Diese Option schaltet das Verhalten des Treibers so um, dass in Projekten in .NET Core 2.1 und höher und in .NET Standard 2.0 und höher unter Windows eine verwaltete SNI verwendet wird. Dies beseitigt alle Abhängigkeiten von nativen Bibliotheken für die Microsoft.Data.SqlClient-Bibliothek.

```csharp
AppContext.SetSwitch("Switch.Microsoft.Data.SqlClient.UseManagedNetworkingOnWindows", true);
```

Unter [AppContext-Optionen in SqlClient](appcontext-switches.md) finden Sie eine vollständige Liste verfügbarer Optionen für den Treiber.

#### <a name="enabling-decimal-truncation-behavior"></a>Aktivieren des Kürzungsverhaltens für Dezimalzahlen 

decimal-Datentypen werden vom Treiber standardmäßig gerundet, wie das auch bei SQL Server der Fall ist. Aus Gründen der Abwärtskompatibilität können Sie die AppContext-Option **Switch.Microsoft.Data.SqlClient.TruncateScaledDecimal** auf **True** festlegen.

```csharp
AppContext.SetSwitch("Switch.Microsoft.Data.SqlClient.TruncateScaledDecimal", true);
```

#### <a name="new-connection-string-property-synonyms"></a>Neue Synonyme für Verbindungszeichenfolgeneigenschaften

Für die folgenden vorhandenen Verbindungszeichenfolgeneigenschaften wurden neue Synonyme hinzugefügt, um Verwirrung bei den Leerzeichen von Eigenschaften zu verhindern, die aus mehr als einem Wort bestehen. Aus Gründen der Abwärtskompatibilität werden alte Eigenschaftennamen weiterhin unterstützt, die neuen Verbindungszeichenfolgeneigenschaften werden ab sofort aber eingeschlossen, wenn Verbindungszeichenfolgen aus [SqlConnectionStringBuilder](https://docs.microsoft.com/dotnet/api/microsoft.data.sqlclient.sqlconnectionstringbuilder) abgerufen werden.

|Vorhandene Verbindungszeichenfolgeneigenschaft|Neues Synonym|
|-----------------------------------|-----------|
| ApplicationIntent | Application Intent |
| ConnectRetryCount | Connect Retry Count (Anzahl der Verbindungsversuche) |
| ConnectRetryInterval | Connect Retry Interval (Verbindungswiederholungsintervall) |
| PoolBlockingPeriod | Pool Blocking Period (Blockierungszeitraum für einen Pool) |
| MultipleActiveResultSets | Multiple Active Result Sets (Mehrere aktive Resultsets) |
| MultiSubnetFailover | Multiple Subnet Failover (Failover für mehrere Subnetze) |
| TransparentNetworkIPResolution | Transparent Network IP Resolution (Transparente Netzwerk-IP-Adressauflösung) |
| TrustServerCertificate | TrustServerCertificate |

#### <a name="sqlbulkcopy-rowscopied-property"></a>SqlBulkCopy-Eigenschaft „RowsCopied“

Die RowsCopied-Eigenschaft bietet schreibgeschützten Zugriff auf die Anzahl der Datensätze, die von einem aktiven Massenkopiervorgang bereits verarbeitet wurden. Dieser Wert entspricht nicht unweigerlich der endgültigen Anzahl an Datensätzen, die der Zieltabelle hinzugefügt wurden. 

#### <a name="connection-open-overrides"></a>Überschreibungen von SqlConnection.Open

Das Standardverhalten von SqlConnection.Open() kann überschrieben werden, um die Verzögerung von zehn Sekunden und automatische erneute Verbindungsversuche zu deaktivieren, die von vorübergehenden Fehlern ausgelöst werden.

```csharp
using SqlConnection sqlConnection = new SqlConnection("Data Source=(local);Integrated Security=true;Initial Catalog=AdventureWorks;");
sqlConnection.Open(SqlConnectionOverrides.OpenWithoutRetry);
```

> [!NOTE]
> Beachten Sie, dass diese Überschreibung nur auf SqlConnection.Open() angewendet werden kann, nicht auf SqlConnection.OpenAsync().

#### <a name="username-support-for-active-directory-interactive-mode"></a>Unterstützung für Benutzernamen bei der interaktiven Active Directory-Authentifizierung

Bei Verwendung der interaktiven Active Directory-Authentifizierung kann sowohl für .NET Framework als auch für .NET Core ein Benutzername in der Verbindungszeichenfolge angegeben werden.

Legen Sie einen Benutzernamen mithilfe der Verbindungszeichenfolgeneigenschaft **User ID** oder **UID** fest:

```
"Server=<server name>; Database=<db name>; Authentication=Active Directory Interactive; User Id=<username>;"
```

#### <a name="order-hints-for-sqlbulkcopy"></a>Hinweise für die Sortierung für SqlBulkCopy

Hinweise für die Sortierung können bereitgestellt werden, um die Leistung von Massenkopiervorgängen für Tabellen mit gruppierten Indizes zu verbessern. Weitere Informationen finden Sie unter [Hinweise für die Sortierung für Massenkopiervorgänge](sql/bulk-copy-order-hints.md).

#### <a name="sni-dependency-changes"></a>SNI-Abhängigkeitsänderungen

Microsoft.Data.SqlClient (.NET Core und .NET Standard) weisen unter Windows nun eine Abhängigkeit von **Microsoft.Data.SqlClient.SNI.runtime** auf. Dadurch wird die bisherige Abhängigkeit von **runtime.native.System.Data.SqlClient.SNI** ersetzt. Mit der neuen Abhängigkeit wird die ARM-Plattform zusammen mit den bereits unterstützten Plattformen ARM64, x64 und x86 unter Windows unterstützt.

## <a name="release-notes-for-microsoftdatasqlclient-110"></a>Versionshinweise zu Microsoft.Data.SqlClient 1.1.0

Die Versionshinweise finden Sie auch im GitHub-Repository: [Hinweise zur Version 1.1](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1).

### <a name="new-features"></a>Neue Funktionen

#### <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted mit Secure Enclaves

Always Encrypted ist ab Microsoft SQL Server 2016 verfügbar. Secure Enclaves sind ab Microsoft SQL Server 2019 verfügbar. Die Verbindungszeichenfolgen müssen das erforderliche Nachweisprotokoll und die Nachweis-URL enthalten, um das Enclave-Feature nutzen zu können. Beispiel:

```
Attestation Protocol=HGS;Enclave Attestation Url=<attestation_url_for_HGS>
```

Weitere Informationen finden Sie unter

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

Das Feature „Datenklassifizierung“ bietet eine neue Gruppe von APIs, die schreibgeschützte Informationen zur Datenvertraulichkeit und -klassifizierung von Objekten verfügbar machen. Diese werden über SqlDataReader abgerufen, wenn die zugrunde liegende Quelle das Feature unterstützt und Metadaten zu [Datenvertraulichkeit und -klassifizierung](../../relational-databases/security/sql-data-discovery-and-classification.md) enthält. Unter [Microsoft.Data.SqlClient 1.1-Releases](https://github.com/dotnet/SqlClient/tree/master/release-notes/1.1) finden Sie die Beispielanwendung.

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

Für UTF-8-Unterstützung sind keine Änderungen am Anwendungscode erforderlich. Diese SqlClient-Änderungen optimieren die Kommunikation zwischen Client und Server, wenn der Server UTF-8 unterstützt und die zugrunde liegende Spaltensortierung UTF-8 ist. Weitere Informationen finden Sie unter [Neuerungen in SQL Server 2019](../../sql-server/what-s-new-in-sql-server-ver15.md) im Abschnitt „UTF-8“.

### <a name="always-encrypted-with-enclaves"></a>Always Encrypted mit Enclaves

Im Allgemeinen sollte die vorhandene Dokumentation zu System.Data.SqlClient in .NET Framework **und integrierten Anbietern von Speichern für Spaltenhauptschlüssel** nun auch für .NET Core gelten.

 [Entwickeln von Always Encrypted mit .NET Framework-Datenanbieter](../../relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider.md)

 [Always Encrypted: Schützen vertraulicher Daten und Speichern von Verschlüsselungsschlüsseln im Windows-Zertifikatspeicher](https://docs.microsoft.com/azure/sql-database/sql-database-always-encrypted)

### <a name="authentication"></a>Authentifizierung

Unterschiedliche Authentifizierungsmodi können angegeben werden, indem in der Verbindungszeichenfolge die Option _Authentifizierung_ verwendet wird. Weitere Informationen finden Sie in der Dokumentation zu [SqlAuthenticationMethod](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlauthenticationmethod?view=netframework-4.7.2).

> [!NOTE]
> Anbieter benutzerdefinierter Schlüsselspeicher wie der Azure Key Vault-Anbieter müssen aktualisiert werden, damit Microsoft.Data.SqlClient unterstützt wird. Ebenso müssen auch die Enclave-Anbieter aktualisiert werden, um Microsoft.Data.SqlClient zu unterstützen.
> Always Encrypted wird nur für .NET Framework- und .NET Core-Ziele unterstützt. Das Feature wird nicht für .NET Standard nicht unterstützt, da .NET Standard bestimmte Verschlüsselungsabhängigkeiten fehlen.
