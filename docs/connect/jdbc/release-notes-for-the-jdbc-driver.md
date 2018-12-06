---
title: Anmerkungen zu dieser Version, für den JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2e7225da803185074e50f3c33d734ec50ccdc29b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52514568"
---
# <a name="release-notes-for-the-jdbc-driver"></a>Versionshinweise für den JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-70-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 7.0 für SQL Server

Microsoft JDBC-Treiber 7.0 für SQL Server ist JDBC-API-Spezifikation 4.2 vollständig kompatibel. Die JAR-Dateien im Paket 7.0 werden nach Java-Versionskompatibilität benannt. Beispielsweise sollte die Mssql-Jdbc-7.0.0.jre10.jar-Datei aus dem Paket 7.0 mit Java 10 verwendet werden.

### <a name="support-for-jdk-10"></a>Unterstützung für JDK 10

Der Microsoft JDBC-Treiber 7.0 für SQL Server ist jetzt mit Java Development Kit (JDK) Version 10.0 zusätzlich zu JDK 1.8 kompatibel. Dieses Update stellt auch vom Treibers `Automatic-Module-Name` als `com.microsoft.sqlserver.jdbc` durch die Manifestdatei.

### <a name="support-for-spatial-datatypes"></a>Unterstützung für räumliche Datentypen

Microsoft JDBC-Treiber 7.0 für SQL Server bietet jetzt Unterstützung für SQL Server von räumlichen Datentypen Geography und Geometry. Weitere Informationen zu räumlichen Datentyp APIs und deren Verwendung finden Sie unter [mit räumlichen Datentypen](../../connect/jdbc/use-spatial-datatypes.md).

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>Implementierung der in JDBC 4.3 eingeführten java.sql.Connection-APIs beginRequest() und endRequest()

Microsoft JDBC-Treiber 7.0 für SQL Server nun implementiert `beginRequest()` und `endRequest()` -APIs aus dem `java.sql.Connection` Klasse. Diese APIs wurden mit JDBC 4.3-Spezifikationen und JDK 9 eingeführt. Weitere Informationen zur Implementierung des Treibers, dieser APIs finden Sie unter [JDBC 4.3-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="support-for-sql-data-discovery-and-classification"></a>Unterstützung für die SQL-Datenermittlung und -klassifizierung

Microsoft JDBC-Treiber 7.0 für SQL Server bietet Unterstützung für SQL-Datenermittlung und-Klassifizierung mit keiner Zieldatenbank, die diese Funktion unterstützt. Der Treiber stellt jetzt `SQLServerResultSet.getSensitivityClassification()` APIs, um diese Informationen aus den abgerufenen extrahieren `ResultSet`.

Weitere Informationen dazu, wie Sie diese Funktion mit dem JDBC-Treiber verwenden, finden Sie im Beispiel in [SQL-Datenermittlung und-Klassifizierung](../../connect/jdbc/data-discovery-classification-sample.md).

### <a name="added-connection-property-usebulkcopyforbatchinsert"></a>Connection-Eigenschaft hinzugefügt: UseBulkCopyForBatchInsert

Microsoft JDBC-Treiber 7.0 für SQL Server führt eine neue Verbindungseigenschaft `useBulkCopyForBatchInsert`. Diese Eigenschaft wird nur für Azure SQL Data Warehouse unterstützt.

Diese Eigenschaft ist standardmäßig deaktiviert. Sie können es um die Leistung von Anwendungen für den Benutzer zu erhöhen, wenn Sie große Mengen von Daten in Azure SQL Data Warehouse übertragen werden. Diese Eigenschaft aktiviert wurde, ändert das Verhalten des Batch-Insert-Vorgänge, um Massenkopiervorgänge mit vom Benutzer bereitgestellte Daten zu wechseln. Weitere Informationen zu dieser Eigenschaft und die Einschränkungen finden Sie unter [mithilfe von API für Massenkopieren für Batch-Einfügevorgang](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md).

### <a name="added-connection-property-cancelquerytimeout"></a>Connection-Eigenschaft hinzugefügt: CancelQueryTimeout

Microsoft JDBC-Treiber 7.0 für SQL Server führt eine neue Verbindungseigenschaft `cancelQueryTimeout`zum abzubrechen `queryTimeout` auf `java.sql.Connection` und `java.sql.Statement` Objekte.

### <a name="added-azure-key-vault-provider-constructors"></a>Zusätzliche Azure Key Vault Provider-Konstruktoren

Microsoft JDBC-Treiber 7.0 für SQL Server Rückkehr zum einen Konstruktor zuvor entfernten für `SQLServerColumnEncryptionAzureKeyVaultProvider`. Es die Authentifizierung über eine benutzerdefinierte Methode, die über implementiert zulässig `SQLServerKeyVaultAuthenticationCallback` um ein Zugriffstoken abzurufen.

Die neuen Konstruktoren haben die folgende Definition:

```java
/* This constructor is added to provide backward compatibility with 6.0
* version of the driver. It is marked deprecated for removal in the next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-adal4j-version-160"></a>Aktualisierte Version der ADAL4J: 1.6.0

Microsoft JDBC-Treiber 7.0 für SQL Server wurde der Maven-Abhängigkeit auf Azure-Activedirectory-Library-for-Java (ADAL4J) auf Version 1.6.0 aktualisiert. Weitere Informationen zu Abhängigkeiten finden Sie unter [Featureabhängigkeiten des Microsoft JDBC-Treiber für SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 6.4 für SQL Server

Microsoft JDBC-Treiber 6.4 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Die JAR-Dateien im Paket 6,4 werden nach Java-Versionskompatibilität benannt. Beispielsweise muss die Mssql-Jdbc-6.4.0.jre8.jar-Datei aus dem Paket 6.4 mit Java 8 verwendet werden.

### <a name="support-for-jdk-9"></a>Unterstützung für JDK 9

Der Treiber unterstützt JDK Version 9.0 zusätzlich zu JDK 8.0 und 7.0.

### <a name="jdbc-43-compliance"></a>JDBC 4.3-Kompatibilität

Der Treiber unterstützt die Java Database Connectivity-API-Spezifikation 4.3, zusätzlich zu 4.1 und 4.2. Der JDBC 4.3-API-Methoden werden hinzugefügt, aber noch nicht implementiert. Weitere Informationen finden Sie unter [JDBC 4.3-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="added-connection-property-sslprotocol"></a>Connection-Eigenschaft hinzugefügt: SslProtocol

Eine neue Verbindungseigenschaft ermöglicht Benutzern, die das TLS-Protokoll-Schlüsselwort angeben. Mögliche Werte sind: "TLS", "TLSv1", "TLSv1. 1" und "TLSv1. 2". Weitere Informationen finden Sie unter [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol).

### <a name="deprecated-connection-property-fipsprovider"></a>Veraltet-Verbindungseigenschaft: FipsProvider

Die Verbindungseigenschaft `fipsProvider` wird aus der Liste der Eigenschaften, die angenommene Verbindung entfernt. Weitere Informationen finden Sie im zugehörigen [Pull Request auf GitHub](https://github.com/Microsoft/mssql-jdbc/pull/460).

### <a name="added-connection-properties-for-specifying-a-custom-trustmanager"></a>Zusätzliche Verbindungseigenschaften für die Angabe einer benutzerdefinierten TrustManager

Der Treiber jetzt hinzugefügt unterstützt das Festlegen einer benutzerdefinierten TrustManager mit `trustManagerClass` und `trustManagerConstructorArg` Verbindungseigenschaften. Sie können eine Gruppe von Zertifikaten, die als vertrauenswürdig eingestuft werden dynamisch auf Basis pro Verbindung angeben, ohne Änderung der globalen Einstellungen für die Umgebung der Java Virtual Machine (JVM).

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters"></a>Unterstützung für die Datetime/SmallDatetime in Tabellenwertparameter

Der Treiber unterstützt jetzt die Datentypen `datetime` und `smallDatetime` bei der Verwendung von Tabellenwertparameter (TVPs).

### <a name="added-support-for-the-sqlvariant-datatype"></a>Unterstützung für den Sql_variant-Datentyp

Der JDBC-Treiber unterstützt jetzt `sql_variant` Datentypen, die mit SQL Server verwendet werden. Die `sql_variant` Datentyp wird auch mit Features wie TVPs und Massenkopieren mit folgenden Einschränkungen unterstützt:

* **Für Datumswerte**: 

  Bei der Verwendung von TVP zum Auffüllen einer Tabelle, die enthält `datetime`, `smalldatetime`, oder `date` gespeicherten Werte eine `sql_variant` Spalte, Aufrufen der `getDateTime()`, `getSmallDateTime()`, oder `getDate()` Methode für das Resultset nicht funktioniert und wird die folgende Ausnahme ausgelöst:

  `java java.lang.String cannot be cast to java.sql.Timestamp`
    
  Dieses Problem zu umgehen, verwenden Sie die `getString()` oder `getObject()` Methode stattdessen.

* **Verwenden von TVP mit sql_variant für Nullwerte**:
  
  Wenn Sie TVP zum Auffüllen einer Tabelle, und senden einen NULL-Wert zu verwenden, die `sql_variant` Spaltentyp, eine Ausnahme auftritt. Einen NULL-Wert mit dem Datentyp der Spalte einfügen `sql_variant` in TVP derzeit nicht unterstützt.

### <a name="implemented-prepared-statement-metadata-caching"></a>Implementiert Zwischenspeicherung von Metadaten in die vorbereitete Anweisung

Der JDBC-Treiber implementiert, die vorbereitete Anweisung Metadaten-Zwischenspeicherung zur leistungsverbesserung. Der Treiber unterstützt jetzt die Zwischenspeichern von Metadaten der vorbereiteten Anweisung im Treiber mit `disableStatementPooling` und `statementPoolingCacheSize` Verbindungseigenschaften. Dieses Feature ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [vorbereitete Anweisung Zwischenspeichern von Metadaten für den JDBC-Treiber](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md).

### <a name="added-support-for-azure-ad-integrated-authentication-on-linuxmac"></a>Unterstützung für Azure AD-integrierte Authentifizierung auf Linux/Mac

Der JDBC-Treiber unterstützt nun auch die integrierte Azure Active Directory-Authentifizierung (Azure AD) unter allen Betriebssystemen (Windows, Linux und Mac) mit Kerberos. Alternativ können Benutzer unter Windows-Betriebssystemen mit "sqljdbc_auth.dll" authentifizieren.

### <a name="updated-adal4j-version-140"></a>Aktualisierte Version der ADAL4J: 1.4.0

Der JDBC-Treiber wurde die Abhängigkeit von Maven für Azure-Activedirectory-Library-for-Java (ADAL4J) auf Version 1.4.0 aktualisiert werden. Weitere Informationen zu Abhängigkeiten finden Sie unter [Featureabhängigkeiten des Microsoft JDBC-Treiber für SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 6.2 für SQL Server

Microsoft JDBC-Treiber 6.2 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Die JAR-Dateien im Paket 6.2 werden nach Java-Versionskompatibilität benannt. Beispielsweise empfiehlt sich die Mssql-Jdbc-6.2.2.jre8.jar-Datei aus dem 6.2-Paket für die Verwendung mit Java 8.

> [!NOTE]  
> In der JDBC-6.2 RTW am 29. Juni 2017 veröffentlicht wurde ein Problem mit der Verbesserung für die Zwischenspeicherung der Metadaten gefunden. Wurde ein Rollback für die Verbesserung und neue JAR-Dateien (Standard ist 6.2.1-Version) auf dem 17. Juli 2017 veröffentlicht wurden. 
>
> Eine weitere Verbesserung die abhängige Bibliothek-Version von Azure Key Vault auf 1.0.0 aktualisiert und neue JAR-Dateien (Version 6.2.2) am 19. Oktober 2017 veröffentlicht wurden.
>
> Laden Sie die neuesten Updates für die JDBC-Treiber 6.2 aus [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2), und [Maven Central](https://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22). Aktualisieren Sie auf der Projekte zur Verwendung der 6.2.2 JAR-Dateien freigeben. Weitere Informationen finden Sie Anmerkungen zu dieser Version [Standard ist 6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) und [6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2).

### <a name="azure-ad-support-for-linux"></a>Azure AD-Unterstützung für Linux

Verbinden von Linux-Anwendungen in Azure SQL-Datenbank mithilfe von Azure AD-Authentifizierung über Benutzername/Kennwort und Sicherheitstoken-Zugriffsmethoden.

### <a name="fips-enabled-jvms"></a>JVMs FIPS aktiviert

Der JDBC-Treiber kann jetzt auf JVMs verwendet werden, die ausgeführt werden im Federal Information Processing Standard (FIPS) 140-Kompatibilitätsmodus um federal Standards-Compliance zu erfüllen.

### <a name="kerberos-authentication-improvements"></a>Verbesserungen der Kerberos-Authentifizierung

Der JDBC-Treiber bietet jetzt Unterstützung für:

- Prinzipal und Kennwort-Methode für Anwendungen, in denen die Kerberos-Konfiguration kann nicht geändert werden oder ein neues Token oder Keytab-Datei kann nicht abgerufen werden. Diese Methode kann verwendet werden, für die Authentifizierung mit SQL Server-Instanz, die nur die Kerberos-Authentifizierung ermöglicht.
- Bereichsübergreifende Authentifizierung, die integrierte Kerberos-Authentifizierung verwendet wird, ohne explizit festlegen, dass der Server-SPN. Der Treiber berechnet jetzt automatisch den Bereich, auch wenn es nicht bereitgestellt wird.
- Eingeschränkte Kerberos-Delegierung, durch das akzeptieren angenommen Anmeldeinformationen des Benutzers als ein Objekt mit GSS-Anmeldeinformationen über die Datenquelle an. Diese Anmeldeinformation mit Identitätswechsel wird zum Herstellen einer Verbindung Kerberos verwendet.

### <a name="added-timeouts"></a>Hinzugefügte timeouts

Der JDBC-Treiber unterstützt jetzt die folgenden konfigurierbare Timeouts. Sie können basierend auf den Anforderungen Ihrer Anwendung ändern.

- Abfragetimeout zum Steuern der Anzahl von Sekunden wartet, bevor ein Timeout tritt auf, wenn Sie eine Abfrage ausführen.
- Sockettimeout angeben, die Anzahl der Millisekunden, die gewartet wird, bevor ein Timeout für einen Socket auftritt, lesen, oder übernehmen.

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 6.1 für SQL Server

Microsoft JDBC-Treiber 6.1 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Dies ist die erste Open-Source-Version des JDBC-Treibers. Sie enthält die Dateien mit der Mssql-Jdbc-6.1.0.jre8.jar und Mssql-Jdbc-6.1.0.jre7.jar, die Kompatibilität für Java-Version entsprechen.

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Updates im Microsoft JDBC-Treiber 6.0 für SQL Server

Microsoft JDBC-Treiber 6.0 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Die JAR-Dateien im 6.0-Paket werden nach ihre Kompatibilität mit der JDBC-API-Version benannt. Beispielsweise ist die Datei "sqljdbc42.jar" aus dem Paket 6.0 JDBC-API 4.2-konform. Auf ähnliche Weise ist die Datei "sqljdbc41.jar" mit JDBC-API 4.1 kompatibel.

Führen Sie die folgenden Codezeilen, um sicherzustellen, dass Sie die richtige "sqljdbc42.jar" oder "sqljdbc41.jar"-Datei verfügen. Wenn die Ausgabe ist "Driver, Version: 6.0.7507.100", Sie haben das JDBC-Treiber 6.0-Paket.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Always Encrypted

Der Treiber unterstützt Always Encrypted-Funktion in SQL Server 2016. Dieses Feature stellt sicher, dass vertrauliche Daten niemals in Klartext in einer SQL Server-Instanz angezeigt werden. Always Encrypted arbeitet mit transparenter Verschlüsselung der Daten in der Anwendung, sodass SQL Server nur die verschlüsselten Daten verarbeitet, aber keine Klartextwerte. Selbst wenn die Integrität der SQL Server-Instanz oder des Hostcomputers beschädigt ist, kann ein Angreifer sensible Daten nur als chiffrierten Text sehen. Einzelheiten finden Sie unter [Using Always Encrypted with the JDBC Driver (Verwenden von Always Encrypted mit dem JDBC-Treiber)](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).

### <a name="internationalized-domain-names"></a>Internationale Domänennamen

Der Treiber unterstützt internationalisierte Domänennamen (IDNs) für Server-Namen. Weitere Informationen finden Sie unter "Verwenden von internationalen Domänennamen" in der [internationale Funktionen des JDBC-Treibers](../../connect/jdbc/international-features-of-the-jdbc-driver.md) Artikel.

### <a name="parameterized-queries"></a>Parameterized queries

Der Treiber unterstützt jetzt das Abrufen von Parametermetadaten mit vorbereiteten Anweisungen für komplexe Abfragen wie Teilabfragen und/oder Joins. Beachten Sie, dass diese Verbesserung nur bei Verwendung von SQL Server 2012 und neueren Versionen verfügbar ist.

### <a name="azure-active-directory"></a>Azure Active Directory

Azure AD-Authentifizierung ist ein Mechanismus zum Herstellen einer Verbindung mit Azure SQL-Datenbank v12 mithilfe von Identitäten in Azure AD. Verwenden Sie Azure AD-Authentifizierung zur zentralen Verwaltung von Identitäten von Datenbankbenutzern und als Alternative zur SQL Server-Authentifizierung. 

Sie können die JDBC-Treiber 6.0 verwenden, an Ihre Azure AD-Anmeldeinformationen in der JDBC-Verbindungszeichenfolge zur Verbindung mit Azure SQL-Datenbank. Weitere Informationen finden Sie unter der Authentifizierungseigenschaft in der [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md) Artikel.

### <a name="table-valued-parameters"></a>Tabellenwertparameter

TVPs bieten eine einfache Möglichkeit zum Marshallen mehrerer Datenzeilen aus einer Clientanwendung nach SQL Server, ohne dass mehrere Roundtrips oder eine spezielle serverseitige Logik für die Verarbeitung der Daten erforderlich sind. Sie können TVPs verwenden, um Datenzeilen in einer Clientanwendung zu kapseln und die Daten in einem einzigen parametrisierten Befehl an den Server zu senden. Die eingehenden Datenzeilen werden in einer Tabellenvariablen gespeichert, die Sie dann auf ausführen können, mithilfe von Transact-SQL. Weitere Informationen finden Sie unter [mit Tabellenwertparametern](../../connect/jdbc/using-table-valued-parameters.md).

### <a name="always-on-availability-groups"></a>AlwaysOn-Verfügbarkeitsgruppen

Der Treiber unterstützt jetzt transparente Verbindungen mit AlwaysOn-Verfügbarkeitsgruppen. Der Treiber ermittelt schnell die aktuelle Always On-Topologie Ihrer Serverinfrastruktur und stellt transparent eine Verbindung mit dem derzeit aktiven Server her.

## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Updates im Microsoft JDBC-Treiber 4.2 für SQL Server und höheren Versionen

Microsoft JDBC-Treiber 4.2 für SQL Server ist vollständig kompatibel mit den JDBC-Spezifikationen 4.1 und 4.2. Die JAR-Dateien im 4.2-Paket werden nach ihre Kompatibilität mit der JDBC-API-Version benannt. Beispielsweise ist die Datei "sqljdbc42.jar" aus dem 4.2-Paket JDBC-API 4.2-konform. Auf ähnliche Weise ist die Datei "sqljdbc41.jar" mit JDBC-API 4.1 kompatibel.

Um sicherzustellen, dass müssen Sie die richtige "sqljdbc42.jar" oder "sqljdbc41.jar"-Datei, führen Sie die folgenden Codezeilen. Wenn die Ausgabe ist "Driver, Version: 4.2.6420.100", Sie haben das JDBC-Treiber 4.2-Paket.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>Unterstützung für JDK 8

Der Treiber unterstützt die JDK-Version 8.0, zusätzlich zu JDK 7.0, 6.0 und 5.0.

### <a name="jdbc-41-and-42-compliance"></a>JDBC 4.1- und 4.2-Kompatibilität

Der Treiber unterstützt die Java Database Connectivity-API-Spezifikationen 4.1 und 4.2, zusätzlich zu 4.0. Weitere Informationen finden Sie unter [JDBC 4.1-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) und [JDBC 4.2-Kompatibilität für den JDBC-Treiber](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

### <a name="bulk-copy"></a>Massenkopieren

Die Massenkopierfunktion wird verwendet, um schnell große Datenmengen in Tabellen oder Ansichten in SQL Server-Datenbanken zu kopieren. Weitere Informationen finden Sie unter [Verwenden von Massenkopieren mit dem JDBC-Treiber](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

### <a name="xa-transaction-rollback-option"></a>Rollbackoption für XA-Transaktionen

Der Treiber hat neue Timeoutoptionen für das vorhandene automatische Rollback nicht vorbereiteter Transaktionen. Weitere Informationen finden Sie unter [Grundlegendes zu XA-Transaktionen](../../connect/jdbc/understanding-xa-transactions.md).

### <a name="new-kerberos-principal-connection-property"></a>Neue Kerberos-Prinzipalverbindungseigenschaft

Der Treiber verwendet neue Verbindungseigenschaft, um mehr Flexibilität für Kerberos-Verbindungen zu ermöglichen. Details finden Sie unter [Verwenden der integrierten Kerberos-Authentifizierung für Verbindungen mit SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Updates im Microsoft JDBC-Treiber 4.1 für SQL Server und höheren Versionen

### <a name="support-for-jdk-7"></a>Unterstützung für JDK 7

Der Treiber unterstützt die JDK-Version 7.0 zusätzlich zu JDK 6.0 und 5.0.

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Keine Itanium-Unterstützung für JDBC-Treiber 6.4-, 6.0-, 4.2- und 4.1-Anwendungen

Die Ausführung der Microsoft JDBC-Treiber 6.4, 6.0, 4.2 und 4.1 für SQL Server-Anwendungen auf einem Itanium-Computer wird nicht unterstützt.

## <a name="see-also"></a>Siehe auch

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)
