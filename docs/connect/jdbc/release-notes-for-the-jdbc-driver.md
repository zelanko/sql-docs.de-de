---
title: Anmerkungen zu dieser Version, für den JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
caps.latest.revision: 206
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10f14eedb1a74f74cb1ee055a247a96671224ce0
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662462"
---
# <a name="release-notes-for-the-jdbc-driver"></a>Versionshinweise für den JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-70-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 7.0 für SQL Server

Microsoft JDBC-Treiber 7.0 für SQL Server ist JDBC-API-Spezifikation 4.2 vollständig kompatibel. Die JAR-Dateien im Paket 7.0 werden nach Java-Versionskompatibilität benannt. Beispielsweise sollte die Mssql-Jdbc-7.0.0.jre10.jar-Datei aus dem Paket 7.0 mit Java 10 verwendet werden.

### <a name="support-for-jdk-10"></a>Unterstützung für JDK 10

Microsoft JDBC-Treiber 7.0 für SQL Server ist jetzt mit Java Development Kit (JDK) Version 10.0, zusätzlich zu JDK 1.8 kompatibel. Dieses Update stellt auch die des Treibers "Automatische-Module-Name" als `com.microsoft.sqlserver.jdbc` durch die Manifestdatei.

### <a name="support-for-spatial-datatypes"></a>Unterstützung für räumliche Daten

Microsoft JDBC-Treiber 7.0 für SQL Server bietet jetzt Unterstützung für SQL Server-räumliche Datentypen "Geography" und "Geometry". Weitere Informationen zu räumlichen Datentypen APIs und deren Verwendung finden Sie unter [hier](../../connect/jdbc/use-spatial-datatypes.md).

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>Implementierung der in JDBC 4.3 eingeführten java.sql.Connection-APIs beginRequest() und endRequest()

Microsoft JDBC-Treiber 7.0 für SQL Server nun implementiert `beginRequest()` und `endRequest()` -APIs von `java.sql.Connection` Klasse. Diese APIs wurden mit JDBC 4.3-Spezifikationen und JDK 9 eingeführt. Weitere Informationen zur Implementierung des Treibers, dieser APIs finden Sie unter [hier](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="support-for-sql-data-discovery-and-classification"></a>Unterstützung für die SQL-Datenermittlung und -klassifizierung

Microsoft JDBC-Treiber 7.0 für SQL Server bietet Unterstützung für "SQL-Datenermittlung und Klassifizierung"-Funktion mit keiner Zieldatenbank, die diese Funktion unterstützt. Der Treiber stellt jetzt `SQLServerResultSet.getSensitivityClassification()` APIs, um diese Informationen aus dem abgerufenen ResultSet zu extrahieren.

Weitere Informationen dazu, wie Sie dieses Feature mit dem JDBC-Treiber verwenden, finden Sie unter Beispiel [hier](../../connect/jdbc/data-discovery-classification-sample.md).

### <a name="added-new-connection-property-usebulkcopyforbatchinsert"></a>Neue Verbindungseigenschaft hinzugefügt: UseBulkCopyForBatchInsert

Microsoft JDBC-Treiber 7.0 für SQL Server führt eine neue Verbindungseigenschaft "UseBulkCopyForBatchInsert", die nur für die unterstützt werden **Azure Data Warehouse**.

Diese Eigenschaft ist **deaktiviert** vom Standardwert und kann aktiviert werden, um die Leistung von Anwendungen für den Benutzer zu erhöhen, beim Übertragen großer Daten in Azure Data Warehouse führt. Diese Eigenschaft aktiviert wurde, ändert das Verhalten von Batch Insert-Vorgänge, um Massenkopiervorgänge mit vom Benutzer bereitgestellten Daten zu wechseln. Weitere Informationen zu dieser Eigenschaft und die Einschränkungen finden Sie unter [hier](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md).

### <a name="added-new-connection-property-cancelquerytimeout"></a>Neue Verbindungseigenschaft hinzugefügt: CancelQueryTimeout

Microsoft JDBC-Treiber 7.0 für SQL Server führt neue Verbindungseigenschaft `cancelQueryTimeout`zum abzubrechen `queryTimeout` auf `java.sql.Connection` und `java.sql.Statement` Objekte.

### <a name="added-azure-key-vault-provider-constructors"></a>Zusätzliche Azure Key Vault-Anbieter-Konstruktoren

Microsoft JDBC-Treiber 7.0 für SQL Server ergeben sich einen zuvor entfernten Konstruktor für `SQLServerColumnEncryptionAzureKeyVaultProvider`, welche zulässigen Authentifizierung mithilfe einer benutzerdefinierten Methode, die über implementiert `SQLServerKeyVaultAuthenticationCallback` um ein Zugriffstoken abzurufen.

Die neuen Konstruktoren verfügen über die folgenden Definition:

```java
/* This constructor is added to provide backwards compatibility with 6.0
* version of the driver. It is marked deprecated for removal in next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New Constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-adal4j-version-to-160"></a>Aktualisierte ADAL4J Version 1.6.0

Microsoft JDBC-Treiber 7.0 für SQL Server wurde der Maven-Abhängigkeit von Azure-Activedirectory-Library-for-Java (ADAL4J) auf Version 1.6.0 aktualisiert. Weitere Informationen zu Abhängigkeiten finden Sie [hier](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 6.4 für SQL Server

Der Microsoft JDBC-Treiber 6.4 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Die JAR-Dateien im Paket 6,4 werden nach Java-Versionskompatibilität benannt. Beispielsweise muss die Mssql-Jdbc-6.4.0.jre8.jar-Datei aus dem Paket 6.4 mit Java 8 verwendet werden.

### <a name="support-for-jdk-9"></a>Unterstützung für JDK 9

Unterstützung für Java Development Kit (JDK), Version 9.0, zusätzlich zu JDK 8.0 und 7.0.

### <a name="jdbc-43-compliance"></a>JDBC 4.3-Kompatibilität

Unterstützung für die Java Database Connectivity-API-Spezifikation 4.3, zusätzlich zu 4.1 und 4.2. Der JDBC 4.3-API-Methoden werden hinzugefügt, aber noch nicht implementiert. Weitere Informationen finden Sie unter [JDBC 4.3-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="added-new-connection-property-sslprotocol"></a>Neue Verbindungseigenschaft hinzugefügt: SslProtocol

Hinzugefügt, eine neue Verbindungseigenschaft, die Benutzer, die das Schlüsselwort der TLS-Protokoll angeben kann. Mögliche Werte sind: "TLS", "TLSv1", "TLSv1. 1", "TLSv1. 2". Finden Sie unter [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol) Details.

### <a name="deprecated-connection-property-fipsprovider"></a>Veraltet-Verbindungseigenschaft: FipsProvider

Die Verbindungseigenschaft "FipsProvider" wird aus der Liste der Eigenschaften, die angenommene Verbindung entfernt. Ausführliche Informationen finden Sie [hier](https://github.com/Microsoft/mssql-jdbc/pull/460).

### <a name="added-connection-properties-for-specifying-custom-trustmanager"></a>Zusätzliche Verbindungseigenschaften für das Angeben eines benutzerdefinierten

Driver unterstützt jetzt das Angeben eines benutzerdefinierten mit hinzugefügten "TrustManagerClass" und "TrustManagerConstructorArg"-Verbindungseigenschaften. Dies ermöglicht dynamische Angabe eines Satzes von Zertifikaten, die pro-Verbindung als vertrauenswürdig eingestuft werden ohne Änderung der globalen Einstellungen für die JVM-Umgebung.

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters-tvp"></a>Unterstützung für die Datetime/SmallDatetime in Tabellenwertparametern (TVP)

Der Treiber unterstützt nun die Datentypen DATETIME und SMALLDATETIME bei Verwendung von Tabellenwertparametern (TVP).

### <a name="added-support-for-sqlvariant-datatype"></a>Unterstützung für Sql_variant-Datentyp

Der JDBC-Treiber unterstützt jetzt die Sql_variant-Datentypen, die mit SQL Server verwendet werden. Sql_variant wird ebenfalls mit Features wie Tabellenwertparametern (TVP) und BulkCopy mit folgenden Einschränkungen unterstützt:

1. Für Datumswerte: Wenn TVP zum Auffüllen einer Tabelle, die in Sql_variant-Spalte gespeicherte Datetime/Smalldatetime/Date-Werte enthält, funktioniert nicht und löst den folgenden Fehler für Resultset getDateTime()/getSmallDateTime()/getDate()-Methoden aufrufen:  `java java.lang.String cannot be cast to java.sql.Timestamp` Problemumgehung: Verwenden Sie stattdessen "getString()" oder "getObject()"-Methoden.

2. Verwenden von TVP mit SQL_Variant für NULL-Werte

Bei Verwendung TVP zum Auffüllen einer Tabelle, und senden NULL-Wert in Sql_variant-Spaltentyp, müssen Sie eine Ausnahme auftreten, wie das Einfügen von NULL-Wert, mit der Spalte Typ "Sql_variant" in TVP derzeit nicht unterstützt wird.

### <a name="implemented-prepared-statement-metadata-caching"></a>Die vorbereitete Anweisung implementiert Zwischenspeicherung von Metadaten

Der JDBC-Treiber hat für die Verbesserung der Leistung vorbereitete Anweisung Metadatencaching implementiert. -Treiber unterstützt jetzt die Zwischenspeicherung Metadaten zu vorbereiteten Anweisungen im Treiber mit den Verbindungseigenschaften "DisableStatementPooling" und "statementpoolingcachesize-Wert". Dieses Feature ist standardmäßig deaktiviert. Weitere Informationen finden Sie [hier](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md).

### <a name="added-support-for-aad-integrated-authentication-on-linuxmac"></a>Unterstützung für AAD-integrierte Authentifizierung auf Linux/Mac

Der JDBC-Treiber unterstützt nun auch die integrierte Azure Active Directory-Authentifizierung unter allen Betriebssystemen (Windows/Linux/macOS) mit Kerberos. Alternativ können für Windows-Betriebssysteme, Benutzer mit "sqljdbc_auth.dll" authentifizieren.

### <a name="updated-adal4j-version-to-140"></a>Aktualisierte ADAL4J Version 1.4.0

Der JDBC-Treiber wurde die Maven-Abhängigkeit von Azure-Activedirectory-Library-for-Java (ADAL4J) auf Version 1.4.0 aktualisiert werden. Weitere Informationen zu Abhängigkeiten finden Sie [hier](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 6.2 für SQL Server

Der Microsoft JDBC-Treiber 6.2 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Die JAR-Dateien im Paket 6.2 werden nach Java-Versionskompatibilität benannt. Beispielsweise empfiehlt sich die Mssql-Jdbc-6.2.2.jre8.jar-Datei aus dem Paket 6.2 mit Java 8 verwendet werden.

> [!NOTE]  
> In der JDBC-6.2 RTW am 29. Juni 2017 veröffentlicht wurde ein Problem mit der Verbesserung für die Zwischenspeicherung der Metadaten gefunden. Wurde ein Rollback für die Verbesserung und neue JAR-Dateien (Standard ist 6.2.1-Version) auf dem 17. Juli 2017 veröffentlicht wurden. 
>
> Eine weitere Verbesserung abhängige Library-Version von Azure Key Vault auf 1.0.0 Upgrade vorgenommen wurde, und neue JAR-Dateien (Version 6.2.2) am 19. Oktober 2017 veröffentlicht wurden.
>
> Laden Sie die neuesten Updates in der JDBC-Treiber 6.2 für [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2), und [Maven Central](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22). Aktualisieren Sie auf der Projekte zur Verwendung der 6.2.2 JAR-Dateien freigeben. Lesen Sie die Anmerkungen zu dieser Version [v6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) und [v6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2) Weitere Details.

### <a name="azure-active-directory-aad-support-for-linux"></a>Azure Active Directory (AAD) Unterstützung für Linux

Verbinden von Linux-Anwendungen in Azure SQL-Datenbank mithilfe von AAD-Authentifizierung über Benutzername/Kennwort und Sicherheitstoken-Zugriffsmethoden.

### <a name="federal-information-processing-standard-fips-enabled-jvms"></a>Federal Information Processing Standard (FIPS) aktiviert JVMs

Der JDBC-Treiber kann jetzt auf JVMs verwendet werden, die für die Ausführung im FIPS 140-Kompatibilitätsmodus federal Standards und Compliance zu erfüllen.

### <a name="kerberos-authentication-improvements"></a>Verbesserungen der Kerberos-Authentifizierung

Der JDBC-Treiber bietet jetzt Unterstützung für:

- Prinzipal und Kennwort-Methode für Anwendungen, in denen die Kerberos-Konfiguration geändert oder können nicht abgerufen werden ein neues Token oder Keytab-Datei sein nicht möglich. Diese Methode kann verwendet werden, für die Authentifizierung mit einer SQL-Server, die nur die Kerberos-Authentifizierung zulässt.
- Bereichsübergreifende Authentifizierung mithilfe der integrierten Kerberos-Authentifizierung ohne ausdrückliches Festlegen des Servers-SPN. Der Treiber berechnet jetzt automatisch den Bereich auch, wenn sie noch nicht bereitgestellt wurde.
- Eingeschränkte Kerberos-Delegierung, durch das akzeptieren angenommen Anmeldeinformationen des Benutzers als GSS-Anmeldeinformation-Objekt über die Datenquelle an. Diese Anmeldeinformation mit Identitätswechsel wird zum Herstellen einer Verbindung Kerberos verwendet.

### <a name="added-timeouts"></a>Hinzugefügte Timeouts

Der JDBC-Treiber unterstützt jetzt die folgenden konfigurierbare Timeouts, die Sie ändern können, basierend auf den Anforderungen Ihrer Anwendung:

- Abfragetimeout zum Steuern der Anzahl von Sekunden wartet, bevor ein Timeout tritt auf, wenn eine Abfrage ausführt.
- Sockettimeout angeben, die Anzahl der Millisekunden, die gewartet wird, bevor ein Timeout für einen Socket auftritt, lesen, oder übernehmen.

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 6.1 für SQL Server

Der Microsoft JDBC-Treiber 6.1 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Dies ist die erste Open-Source-Version des JDBC-Treibers und enthält die Mssql-Jdbc-6.1.0.jre8.jar Mssql-Jdbc-6.1.0.jre7.jar-Dateien, die die Kompatibilität der Java-Version entsprechen.

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 6.0 für SQL Server

Der Microsoft JDBC-Treiber 6.0 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Die JAR-Dateien im 6.0-Paket werden nach ihre Kompatibilität mit der JDBC-API-Version benannt. Beispielsweise ist die Datei "sqljdbc42.jar" aus dem Paket 6.0 JDBC-API 4.2-konform. Auf ähnliche Weise ist die Datei "sqljdbc41.jar" mit JDBC-API 4.1 kompatibel.

Führen Sie die folgenden Codezeilen, um sicherzustellen, dass Sie die richtige "sqljdbc42.jar" oder "sqljdbc41.jar" verfügen. Wenn die Ausgabe ist "Driver, Version: 6.0.7507.100", Sie haben das JDBC-Treiber 6.0-Paket.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Always Encrypted

Unterstützung für das kürzlich vorgestellte Always Encrypted-Feature in SQL Server 2016, ein neues Sicherheitsfeature, das sicherstellt, dass sensible Daten in einer SQL Server-Instanz zu keiner Zeit im Klartext sichtbar sind. Always Encrypted arbeitet mit transparenter Verschlüsselung der Daten in der Anwendung, sodass SQL Server nur die verschlüsselten Daten verarbeitet, aber keine Klartextwerte. Selbst wenn die Integrität der SQL-Instanz oder des Hostcomputers beschädigt ist, kann ein Angreifer sensible Daten nur als chiffrierten Text sehen. Einzelheiten finden Sie unter [Using Always Encrypted with the JDBC Driver (Verwenden von Always Encrypted mit dem JDBC-Treiber)](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).

### <a name="internationalized-domain-name-idn"></a>Internationaler Domänenname (IDN)

Unterstützung für internationale Domänennamen (IDNs) bei Servernamen. Details finden Sie unter Verwendung von internationalen Domänennamen auf die [internationale Funktionen des JDBC-Treibers](../../connect/jdbc/international-features-of-the-jdbc-driver.md) Seite.

### <a name="parameterized-query"></a>Parametrisierte Abfrage

Jetzt wird das Abrufen von Parametermetadaten mit vorbereiteten Anweisungen für komplexe Abfragen wie Teilabfragen und/oder Joins unterstützt. Beachten Sie, dass diese Verbesserung nur bei Verwendung von SQL Server 2012 und neueren Versionen verfügbar ist.

### <a name="azure-active-directory-aad"></a>Azure Active Directory (AAD)

AAD-Authentifizierung ist ein Mechanismus zum Herstellen einer Verbindung mit Azure SQL-Datenbank v12 mithilfe von Identitäten in AAD. Verwenden Sie AAD-Authentifizierung zur zentralen Verwaltung von Identitäten von Datenbankbenutzern und als Alternative zur SQL Server-Authentifizierung. Mit JDBC Driver 6.0 können Sie Ihre AAD-Anmeldeinformationen in der JDBC-Verbindungszeichenfolge angeben, um die Verbindung zur Azure SQL-Datenbank herzustellen. Weitere Details finden Sie unter der Authentifizierungseigenschaft auf die [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md) Seite.

### <a name="table-valued-parameters"></a>Tabellenwertparameter

Tabellenwertparameter bieten eine einfache Möglichkeit zum Marshallen mehrerer Datenzeilen aus einer Clientanwendung nach SQL Server, ohne dass mehrere Roundtrips oder eine spezielle serverseitige Logik für die Verarbeitung der Daten erforderlich sind. Sie können Tabellenwertparameter verwenden, um Datenzeilen in einer Clientanwendung zu kapseln und die Daten in einem einzigen parametrisierten Befehl an den Server zu senden. Die eingehenden Datenzeilen werden in einer Tabellenvariablen gespeichert, die dann verarbeitet werden können mithilfe von Transact-SQL. Weitere Informationen finden Sie unter [Using Table-Valued Parameter](../../connect/jdbc/using-table-valued-parameters.md).

### <a name="alwayson-availability-groups-ag"></a>Always On-Verfügbarkeitsgruppen (Availability Groups, AG)

Der Treiber unterstützt jetzt transparente Verbindungen mit AlwaysOn-Verfügbarkeitsgruppen. Der Treiber ermittelt schnell die aktuelle Always On-Topologie Ihrer Serverinfrastruktur und stellt transparent eine Verbindung mit dem derzeit aktiven Server her.

## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Updates im Microsoft JDBC-Treiber 4.2 für SQL Server und höheren Versionen

Der Microsoft JDBC-Treiber 4.2 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Die JAR-Dateien im 4.2-Paket werden nach ihre Kompatibilität mit der JDBC-API-Version benannt. Beispielsweise ist die Datei "sqljdbc42.jar" aus dem 4.2-Paket JDBC-API 4.2-konform. Auf ähnliche Weise ist die Datei "sqljdbc41.jar" mit JDBC-API 4.1 kompatibel.

Führen Sie die folgenden Codezeilen, um sicherzustellen, dass Sie die richtige "sqljdbc42.jar" oder "sqljdbc41.jar" verfügen. Wenn die Ausgabe ist "Driver, Version: 4.2.6420.100", Sie haben das JDBC-Treiber 4.2-Paket.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>Unterstützung für JDK 8

Unterstützung für Java Development Kit (JDK), Version 8.0, zusätzlich zu JDK 7.0, 6.0 und 5.0.

### <a name="jdbc-41-and-42-compliance"></a>JDBC 4.1- und 4.2-Kompatibilität

Unterstützung für die Java Database Connectivity-API-Spezifikationen 4.1 und 4.2, zusätzlich zu 4.0. Weitere Informationen finden Sie unter [JDBC 4.1-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) und [JDBC 4.2-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

### <a name="bulk-copy"></a>Massenkopieren

Die Massenkopierfunktion wird verwendet, um schnell große Datenmengen in Tabellen oder Ansichten in SQL Server-Datenbanken zu kopieren. Weitere Informationen finden Sie unter [Verwenden von Massenkopieren mit dem JDBC-Treiber](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

### <a name="xa-transaction-rollback-option"></a>Rollbackoption für XA-Transaktionen

Es wurden neue Timeoutoptionen für das vorhandene automatische Rollback nicht vorbereiteter Transaktionen hinzugefügt. Weitere Informationen finden Sie unter [Grundlegendes zu XA-Transaktionen](../../connect/jdbc/understanding-xa-transactions.md).

### <a name="new-kerberos-principal-connection-property"></a>Neue Kerberos-Prinzipalverbindungseigenschaft

Es wurde eine neue Verbindungseigenschaft hinzugefügt, um mehr Flexibilität für Kerberos-Verbindungen zu ermöglichen. Details finden Sie unter [Verwenden der integrierten Kerberos-Authentifizierung für Verbindungen mit SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Updates im Microsoft JDBC-Treiber 4.1 für SQL Server und höheren Versionen

### <a name="support-for-jdk-7"></a>Unterstützung für JDK 7

Unterstützung für Java Development Kit (JDK), Version 7.0, zusätzlich zu JDK 6.0 und 5.0.

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Keine Itanium-Unterstützung für JDBC-Treiber 6.4-, 6.0-, 4.2- und 4.1-Anwendungen

Die Ausführung der Microsoft JDBC-Treiber 6.4, 6.0, 4.2 und 4.1 für SQL Server-Anwendungen auf einem Itanium-Computer wird nicht unterstützt.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)
