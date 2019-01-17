---
title: Unterstützung des JDBC-Treibers für Hochverfügbarkeit und Notfallwiederherstellung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e2df0607162f5f2cb90ff6b0525fdc530b7be66
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53211820"
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>JDBC Driver-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  In diesem Artikel wird die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Unterstützung für Hochverfügbarkeit und Notfallwiederherstellung ([!INCLUDE[ssHADR](../../includes/sshadr_md.md)]) thematisiert. Weitere Informationen über [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]finden Sie in der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Onlinedokumentation.  
  
 Ab Version 4.0 von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] können Sie den Verfügbarkeitsgruppenlistener einer Verfügbarkeitsgruppe (Hochverfügbarkeit, Notfallwiederherstellung) in der Verbindungseigenschaft angeben. Wenn eine [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Anwendung mit einer Always On-Datenbank verbunden ist, für die ein Failover ausgeführt wird, wird die ursprüngliche Verbindung unterbrochen, und die Anwendung muss eine neue Verbindung öffnen, damit ihre Ausführung nach dem Failover fortgesetzt werden kann. Die folgenden [Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md) wurden in [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] eingeführt:  
  
-   **multiSubnetFailover**  
  
-   **applicationIntent**
 
Geben Sie immer „multiSubnetFailover=true“ an, wenn Sie eine Verbindung mit dem Verfügbarkeitsgruppenlistener einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz herstellen. Beachten Sie, dass **MultiSubnetFailover** ist standardmäßig "false". Verwendung **ApplicationIntent** deklariert den Arbeitsauslastungstyp der Anwendung. Finden Sie in den folgenden Abschnitten Weitere Informationen.
 
Ab Version 6.0 von der Microsoft JDBC-Treiber für SQL Server, eine neue Verbindungseigenschaft **TransparentNetworkIPResolution** (TNIR) wird für transparente Verbindung hinzugefügt, oder auf einem Server mit Always On-Verfügbarkeitsgruppen mehrere IP-Adressen. Wenn **TransparentNetworkIPResolution** "true", der Treiber versucht, für die Verbindung mit der ersten IP-Adresse verfügbar ist. Wenn der erste Versuch fehlschlägt, versucht der Treiber, für die Verbindung mit allen IP-Adressen parallel, bis das Timeout abläuft, verwirft alle ausstehenden Verbindungsversuche, wenn eines davon erfolgreich abgeschlossen wurde.   

Bitte beachten Sie Folgendes:
* TransparentNetworkIPResolution ist standardmäßig "true"
* TransparentNetworkIPResolution wird ignoriert, wenn Sie "MultiSubnetFailover" ist "true"
* TransparentNetworkIPResolution wird ignoriert, wenn die datenbankspiegelung verwendet wird
* TransparentNetworkIPResolution wird ignoriert, wenn mehr als 64 IP-Adressen vorhanden sind
* Wenn TransparentNetworkIPResolution auf "true" festgelegt ist, verwendet der erste Verbindungsversuch einen Timeoutwert von 500 ms. Rest Verbindungen führen Sie die gleiche Logik wie die MultiSubnetFailover-Funktion. 

> [!NOTE]
> Wenn Sie Microsoft JDBC-Treiber 4.2 (oder senken) für SQL Server und **MultiSubnetFailover** ist "false", die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] versucht, eine Verbindung mit der ersten IP-Adresse herstellen. Wenn [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] keine Verbindung mit der ersten IP-Adresse herstellen kann, tritt ein Verbindungsfehler auf. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] versucht nicht, eine Verbindung mit einer der nachfolgenden IP-Adressen herzustellen, die dem Server zugeordnet sind. 
> 
> 
> [!NOTE]
>  Das Erhöhen des Verbindungstimeouts sowie die Implementierung von Verbindungswiederholungslogik erhöhen die Wahrscheinlichkeit, dass eine Anwendung eine Verbindung zu einer Verfügbarkeitsgruppe herstellt. Da zudem eine Verbindung aufgrund eines Verfügbarkeitsgruppenfailovers fehlschlagen kann, empfiehlt sich die Implementierung von Verbindungswiederholungslogik, wodurch im Fall einer fehlgeschlagenen Verbindung bis zur erneuten Verbindung Wiederholungsversuche erfolgen.  
  
 
  
## <a name="connecting-with-multisubnetfailover"></a>Verbinden mit MultiSubnetFailover  
 Geben Sie immer **multiSubnetFailover=true** an, wenn Sie eine Verbindung mit dem Verfügbarkeitsgruppenlistener einer [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Verfügbarkeitsgruppe oder einer [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Failoverclusterinstanz herstellen. **multiSubnetFailover** ermöglicht einen schnelleren Failover für alle Verfügbarkeitsgruppen und Failoverclusterinstanzen in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und verringert die Failoverzeit für Always On-Topologien mit einem oder mehreren Subnetzen deutlich. Während eines Multisubnetzfailovers versucht der Client Verbindungen parallel. Während eines Subnetz-Failovers unternimmt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] aggressive Wiederholungsversuche zum Herstellen der TCP-Verbindung.  
  
 Die **multiSubnetFailover**-Verbindungseigenschaft gibt an, dass die Anwendung in einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz bereitgestellt wird und [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] versucht, eine Verbindung mit der Datenbank auf der primären [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz herzustellen, indem mit allen IP-Adressen der Verfügbarkeitsgruppe Verbindungsversuche unternommen werden. Wenn **MultiSubnetFailover=true** für eine Verbindung angegeben wird, wiederholt der Client TCP-Verbindungsversuche schneller als dies bei den standardmäßigen TCP-Neuübertragungsintervallen des Betriebssystems der Fall ist. Auf diese Weise kann die Verbindung nach einem Failover einer AlwaysOn-Verfügbarkeitsgruppe oder einer AlwaysOn-Failoverclusterinstanz schneller wiederhergestellt werden. Diese Einstellung gilt sowohl für Einzelsubnetz- als auch Multisubnetz-Verfügbarkeitsgruppen und -Failoverclusterinstanzen.  
  
 Weitere Informationen zu Schlüsselwörtern der Verbindungszeichenfolge in der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], finden Sie unter [Festlegen der Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Das Angeben von **multiSubnetFailover=true** für ein anderes Verbindungsziel als einen Verfügbarkeitsgruppenlistener oder eine Failoverclusterinstanz kann die Leistung beeinträchtigen und wird nicht unterstützt.  
  
 Wenn der Sicherheits-Manager nicht installiert ist, werden virtuelle IP-Adressen (VIPs) von der Java Virtual Machine für einen begrenzten Zeitraum zwischengespeichert. Die jeweilige Dauer wird durch Ihre JDK-Implementierung und die Java-Eigenschaften networkaddress.cache.ttl und networkaddress.cache.negative.ttl bestimmt. Wenn der JDK-Sicherheits-Manager installiert ist, werden VIPs von der Java Virtual Machine zwischengespeichert, und der Cache wird standardmäßig nicht aktualisiert. Es empfiehlt sich die Gültigkeitsdauer, d. h. "time-to-live" (networkaddress.cache.ttl), für den Cache der Java Virtual Machine auf einen Tag festzulegen. Wenn Sie den Standardwert nicht auf einen Tag oder eine ähnliche Einstellung festlegen, wird der alte Wert beim Hinzufügen oder Aktualisieren einer VIP nicht aus dem Java Virtual Machine-Cache gelöscht. Weitere Informationen zu networkaddress.cache.ttl und networkaddress.cache.negative.ttl, finden Sie unter [ https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html ](https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html).  
  
 Befolgen Sie beim Herstellen einer Verbindung mit einem Server in einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz die folgenden Richtlinien:  
  
-   Der Treiber löst einen Fehler, wenn die **InstanceName** Connection-Eigenschaft wird verwendet, in derselben Verbindungszeichenfolge wie die **MultiSubnetFailover** Connection-Eigenschaft. Dies spiegelt den Umstand wider, dass der SQL Browser-Dienst in Verfügbarkeitsgruppen nicht verwendet wird. Aber wenn die **PortNumber** -Verbindungseigenschaft ebenfalls angegeben wird, ignoriert der Treiber **InstanceName** und **PortNumber**.  
  
-   Verwenden Sie die **multiSubnetFailover**-Verbindungseigenschaft, wenn Sie eine Verbindung mit einem oder mehreren Subnetzen herstellen. Dadurch wird die Leistung auf beiden Seiten verbessert.  
  
-   Um eine Verbindung mit einer Verfügbarkeitsgruppe herzustellen, geben Sie in der Verbindungszeichenfolge den Verfügbarkeitsgruppenlistener der Verfügbarkeitsgruppe als Server an. Beispiel: jdbc:sqlserver://VNN1.  
  
-   Ein Verbindungsversuch mit einer mit mehr als 64 IP-Adressen konfigurierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verursacht einen Verbindungsfehler.  
  
-   Das Verhalten einer Anwendung, die die **multiSubnetFailover**-Verbindungseigenschaft verwendet, wird nicht vom Authentifizierungstyp beeinflusst: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung, Kerberos-Authentifizierung oder Windows-Authentifizierung.  
  
-   Erhöhen Sie den Wert von **loginTimeout**, um die Failoverzeit zu berücksichtigen und Wiederholungsversuche für Anwendungsverbindungen zu reduzieren.  
  
-   Verteilte Transaktionen werden nicht unterstützt.  
  
 Wenn das schreibgeschützte Routing nicht aktiviert ist, scheitert das Herstellen der Verbindung mit einem sekundären Replikatspeicherort in einer Verfügbarkeitsgruppe in den folgenden Situationen:  
  
1.  Wenn der sekundäre Replikatspeicherort nicht zum Akzeptieren von Verbindungen konfiguriert ist.  
  
2.  Wenn eine Anwendung **applicationIntent=ReadWrite** verwendet (weiter unten erläutert) und der sekundäre Replikatspeicherort für schreibgeschützten Zugriff konfiguriert ist  
  
 Es kann keine Verbindung hergestellt werden, wenn ein primäres Replikat so konfiguriert ist, dass schreibgeschützte Arbeitslasten abgelehnt werden, und die Verbindungszeichenfolge **ApplicationIntent=ReadOnly**enthält.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Aktualisieren zur Verwendung von Multisubnetzclustern aus Datenbankspiegelung  
 Wenn Sie eine [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Anwendung aktualisieren, die derzeit Datenbankspiegelung in einem Multisubnetz-Szenario verwendet, müssen Sie die **failoverPartner** -Verbindungseigenschaft entfernen und durch **multiSubnetFailover** festgelegt auf **TRUE** ersetzen sowie den Servernamen in der Verbindungszeichenfolge durch einen Verfügbarkeitsgruppenlistener ersetzen. Wenn eine Verbindungszeichenfolge **failoverPartner** und **multiSubnetFailover=true** verwendet, generiert der Treiber einen Fehler. Wenn eine Verbindungszeichenfolge jedoch **failoverPartner** und **multiSubnetFailover=false** (oder **ApplicationIntent=ReadWrite**) verwendet, greift die Anwendung auf Datenbankspiegelung zurück.  
  
 Der Treiber gibt einen Fehler zurück, wenn die Datenbankspiegelung in der primären Datenbank in der Verfügbarkeitsgruppe und **multiSubnetFailover=true** in der Verbindungszeichenfolge verwendet werden, die anstatt mit einem Verfügbarkeitsgruppenlistener eine Verbindung mit einer primären Datenbank herstellt.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>Neue Methoden, die multiSubnetFailover und applicationIntent unterstützen  
 Die folgenden Methoden ermöglichen den programmgesteuerten Zugriff auf die **MultiSubnetFailover**, **ApplicationIntent** und **TransparentNetworkIPResolution** Verbindungszeichenfolge Schlüsselwörter:  
  
-   [SQLServerDataSource.getApplicationIntent](../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setApplicationIntent](../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.getMultiSubnetFailover](../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDataSource.setMultiSubnetFailover](../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
-   [SQLServerDriver.getPropertyInfo](../../connect/jdbc/reference/getpropertyinfo-method-sqlserverdriver.md)  

-   SQLServerDataSource.setTransparentNetworkIPResolution

-   SQLServerDataSource.getTransparentNetworkIPResolution
  
 Die **GetMultiSubnetFailover**, **SetMultiSubnetFailover**, **GetApplicationIntent**, **SetApplicationIntent**, **GetTransparentNetworkIPResolution** und **SetTransparentNetworkIPResolution** Methoden werden ebenfalls hinzugefügt, um [SQLServerDataSource-Klasse](../../connect/jdbc/reference/sqlserverdatasource-class.md), [ SQLServerConnectionPoolDataSource-Klasse](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md), und [SQLServerXADataSource-Klasse](../../connect/jdbc/reference/sqlserverxadatasource-class.md).  
  
## <a name="ssl-certificate-validation"></a>SSL-Zertifikatüberprüfung  
 Eine Verfügbarkeitsgruppe besteht aus mehreren physischen Servern. In [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] wird die Unterstützung von **alternativen Antragstellernamen** in SSL-Zertifikaten eingeführt, sodass einem Zertifikat mehrere Hosts zugeordnet werden können. Weitere Informationen zu SSL finden Sie unter [Grundlegendes zur SSL-Unterstützung](../../connect/jdbc/understanding-ssl-support.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Connecting to SQL Server with the JDBC Driver (Verbinden von SQL Server mit dem JDBC-Treiber)](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)   
 [Festlegen von Verbindungseigenschaften](../../connect/jdbc/setting-the-connection-properties.md)  
  
  
