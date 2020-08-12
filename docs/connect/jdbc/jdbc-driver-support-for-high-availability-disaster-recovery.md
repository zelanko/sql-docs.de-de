---
title: JDBC-Treiber-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung
description: Dieser Artikel befasst sich mit der Unterstützung des Microsoft JDBC-Treibers für SQL Server für Hochverfügbarkeit und Notfallwiederherstellung (Always On-Verfügbarkeitsgruppen).
ms.custom: ''
ms.date: 07/13/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 62de4be6-b027-427d-a7e5-352960e42877
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e3a79f3f47db8bfa048ecb5b910bcb4946cf7a7c
ms.sourcegitcommit: e08d28530e0ee93c78a4eaaee8800fd687babfcc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301819"
---
# <a name="jdbc-driver-support-for-high-availability-disaster-recovery"></a>JDBC-Treiber-Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  In diesem Artikel wird die [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Unterstützung für Hochverfügbarkeit und Notfallwiederherstellung ([!INCLUDE[ssHADR](../../includes/sshadr_md.md)]) thematisiert. Weitere Informationen über [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]finden Sie in der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Onlinedokumentation.  
  
 Ab Version 4.0 von [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] können Sie den Verfügbarkeitsgruppenlistener einer Verfügbarkeitsgruppe (Hochverfügbarkeit, Notfallwiederherstellung) in der Verbindungseigenschaft angeben. Wenn eine [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Anwendung mit einer Always On-Datenbank verbunden ist, für die ein Failover ausgeführt wird, wird die ursprüngliche Verbindung unterbrochen, und die Anwendung muss eine neue Verbindung öffnen, damit ihre Ausführung nach dem Failover fortgesetzt werden kann. Die folgenden [Verbindungseigenschaften](setting-the-connection-properties.md) wurden in [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] eingeführt:  
  
- **multiSubnetFailover**  
  
- **applicationIntent**

Geben Sie immer „multiSubnetFailover=true“ an, wenn Sie eine Verbindung mit dem Verfügbarkeitsgruppenlistener einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz herstellen. Beachten Sie, dass **multiSubnetFailover** standardmäßig auf „false“ festgelegt ist. Verwenden Sie **applicationIntent**, um den Workloadtyp der Anwendung zu deklarieren. Weitere Informationen finden Sie in den folgenden Abschnitten.

Ab Version 6.0 des Microsoft-JDBC-Treibers für SQL Server wird die neue Verbindungseigenschaft **transparentNetworkIPResolution** (TNIR) hinzugefügt, um transparente Verbindungen mit Always On-Verfügbarkeitsgruppen oder mit einem Server zu ermöglichen, dem mehrere IP-Adressen zugeordnet sind. Wenn **transparentNetworkIPResolution** auf „true“ festgelegt ist, versucht der Treiber, eine Verbindung mit der ersten verfügbaren IP-Adresse herzustellen. Wenn der erste Versuch nicht erfolgreich ist, versucht der Treiber, parallel eine Verbindung mit allen IP-Adressen herzustellen, bis ein Timeout auftritt. Dabei werden alle ausstehenden Verbindungsversuche verworfen, wenn ein Versuch erfolgreich ist.

Beachten Sie dabei Folgendes:

- transparentNetworkIPResolution ist standardmäßig „true“.
- „transparentNetworkIPResolution“ wird ignoriert, wenn „multiSubnetFailover“ „true“ ist.  
- „transparentNetworkIPResolution“ wird ignoriert, wenn die Datenbankspiegelung verwendet wird.  
- „transparentNetworkIPResolution“ wird ignoriert, wenn mehr als 64 IP-Adressen vorhanden sind.  
- Wenn transparentNetworkIPResolution „true“ ist, verwendet der erste Verbindungsversuch einen Timeoutwert von 500 ms. Alle anderen Verbindungsversuche folgen der gleichen Logik wie beim multiSubnetFailover-Feature.  

> [!NOTE]
> Wenn Sie Version 4.2 (oder niedriger) des Microsoft-JDBC-Treibers für SQL Server verwenden und **multiSubnetFailover** auf „false“ festgelegt ist, versucht der [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], eine Verbindung mit der ersten IP-Adresse herzustellen. Wenn [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] keine Verbindung mit der ersten IP-Adresse herstellen kann, tritt ein Verbindungsfehler auf. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] versucht nicht, eine Verbindung mit einer der nachfolgenden IP-Adressen herzustellen, die dem Server zugeordnet sind.

> [!NOTE]
> Das Erhöhen des Verbindungstimeouts sowie die Implementierung von Verbindungswiederholungslogik erhöhen die Wahrscheinlichkeit, dass eine Anwendung eine Verbindung zu einer Verfügbarkeitsgruppe herstellt. Da zudem eine Verbindung aufgrund eines Verfügbarkeitsgruppenfailovers fehlschlagen kann, empfiehlt sich die Implementierung von Verbindungswiederholungslogik, wodurch im Fall einer fehlgeschlagenen Verbindung bis zur erneuten Verbindung Wiederholungsversuche erfolgen.  

## <a name="connecting-with-multisubnetfailover"></a>Herstellen einer Verbindung mit multiSubnetFailover  

 Geben Sie immer **multiSubnetFailover=true** an, wenn Sie eine Verbindung mit dem Verfügbarkeitsgruppenlistener einer [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Verfügbarkeitsgruppe oder einer [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]-Failoverclusterinstanz herstellen. **multiSubnetFailover** ermöglicht einen schnelleren Failover für alle Verfügbarkeitsgruppen und Failoverclusterinstanzen in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und verringert die Failoverzeit für Always On-Topologien mit einem oder mehreren Subnetzen deutlich. Während eines Multisubnetzfailovers versucht der Client Verbindungen parallel. Während eines Subnetz-Failovers unternimmt [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] aggressive Wiederholungsversuche zum Herstellen der TCP-Verbindung.  
  
 Die **multiSubnetFailover**-Verbindungseigenschaft gibt an, dass die Anwendung in einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz bereitgestellt wird und [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] versucht, eine Verbindung mit der Datenbank auf der primären [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz herzustellen, indem mit allen IP-Adressen der Verfügbarkeitsgruppe Verbindungsversuche unternommen werden. Wenn **MultiSubnetFailover=true** für eine Verbindung angegeben wird, wiederholt der Client TCP-Verbindungsversuche schneller als dies bei den standardmäßigen TCP-Neuübertragungsintervallen des Betriebssystems der Fall ist. Dieses Verhalten ermöglicht, die Verbindung nach einem Failover einer AlwaysOn-Verfügbarkeitsgruppe oder einer AlwaysOn-Failoverclusterinstanz schneller wiederherzustellen, und gilt sowohl für Einzelsubnetz- als auch Multisubnetz-Verfügbarkeitsgruppen und -Failoverclusterinstanzen.  
  
 Weitere Informationen zu Schlüsselwörtern für Verbindungszeichenfolgen im [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] finden Sie unter [Festlegen der Verbindungseigenschaften](setting-the-connection-properties.md).  
  
 Das Angeben von **multiSubnetFailover=true** für ein anderes Verbindungsziel als einen Verfügbarkeitsgruppenlistener oder eine Failoverclusterinstanz kann die Leistung beeinträchtigen und wird nicht unterstützt.  
  
 Wenn der Sicherheits-Manager nicht installiert ist, werden virtuelle IP-Adressen (VIPs) von der Java Virtual Machine für einen begrenzten Zeitraum zwischengespeichert. Die jeweilige Dauer wird durch Ihre JDK-Implementierung und die Java-Eigenschaften networkaddress.cache.ttl und networkaddress.cache.negative.ttl bestimmt. Wenn der JDK-Sicherheits-Manager installiert ist, werden VIPs von der Java Virtual Machine zwischengespeichert, und der Cache wird standardmäßig nicht aktualisiert. Es empfiehlt sich die Gültigkeitsdauer, d. h. "time-to-live" (networkaddress.cache.ttl), für den Cache der Java Virtual Machine auf einen Tag festzulegen. Wenn Sie den Standardwert nicht auf einen Tag oder eine ähnliche Einstellung festlegen, wird der alte Wert beim Hinzufügen oder Aktualisieren einer VIP nicht aus dem Java Virtual Machine-Cache gelöscht. Weitere Informationen zu „networkaddress.cache.ttl“ und „networkaddress.cache.negative.ttl“ finden Sie unter [https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html](https://download.oracle.com/javase/6/docs/technotes/guides/net/properties.html).  
  
 Befolgen Sie beim Herstellen einer Verbindung mit einem Server in einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz die folgenden Richtlinien:  
  
- Der Treiber generiert einen Fehler, wenn die Verbindungseigenschaft **instanceName** in derselben Verbindungszeichenfolge wie die Verbindungseigenschaft **multiSubnetFailover** verwendet wird. Dieser Fehler spiegelt den Umstand wider, dass der SQL Browser-Dienst in Verfügbarkeitsgruppen nicht verwendet wird. Wenn jedoch die Verbindungseigenschaft **portNumber** ebenfalls angegeben wird, ignoriert der Treiber **instanceName** und verwendet **portNumber**.  
  
- Verwenden Sie die **multiSubnetFailover**-Verbindungseigenschaft, wenn Sie eine Verbindung mit einem oder mehreren Subnetzen herstellen. Dadurch wird die Leistung auf beiden Seiten verbessert.  
  
- Um eine Verbindung mit einer Verfügbarkeitsgruppe herzustellen, geben Sie in der Verbindungszeichenfolge den Verfügbarkeitsgruppenlistener der Verfügbarkeitsgruppe als Server an. Beispiel: jdbc:sqlserver://VNN1.  
  
- Ein Verbindungsversuch mit einer mit mehr als 64 IP-Adressen konfigurierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verursacht einen Verbindungsfehler.  
  
- Das Verhalten einer Anwendung, die die **multiSubnetFailover**-Verbindungseigenschaft verwendet, wird nicht vom Authentifizierungstyp beeinflusst: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung, Kerberos-Authentifizierung oder Windows-Authentifizierung.  
  
- Erhöhen Sie den Wert von **loginTimeout**, um die Failoverzeit zu berücksichtigen und Wiederholungsversuche für Anwendungsverbindungen zu reduzieren.  
  
- Verteilte Transaktionen werden nicht unterstützt.  
  
Wenn das schreibgeschützte Routing nicht aktiviert ist, scheitert das Herstellen der Verbindung mit einem sekundären Replikatspeicherort in einer Verfügbarkeitsgruppe in den folgenden Situationen:  
  
1. Wenn der sekundäre Replikatspeicherort nicht zum Akzeptieren von Verbindungen konfiguriert ist.  
  
2. Wenn eine Anwendung **applicationIntent=ReadWrite** verwendet (weiter unten erläutert) und der sekundäre Replikatspeicherort für schreibgeschützten Zugriff konfiguriert ist  
  
Es kann keine Verbindung hergestellt werden, wenn ein primäres Replikat so konfiguriert ist, dass schreibgeschützte Arbeitslasten abgelehnt werden, und die Verbindungszeichenfolge **ApplicationIntent=ReadOnly**enthält.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Aktualisieren zur Verwendung von Multisubnetzclustern aus Datenbankspiegelung  

Wenn Sie eine [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]-Anwendung aktualisieren, die derzeit Datenbankspiegelung in einem Multisubnetz-Szenario verwendet, müssen Sie die **failoverPartner**-Verbindungseigenschaft entfernen und durch **multiSubnetFailover** festgelegt auf **TRUE** ersetzen sowie den Servernamen in der Verbindungszeichenfolge durch einen Verfügbarkeitsgruppenlistener ersetzen. Wenn eine Verbindungszeichenfolge **failoverPartner** und **multiSubnetFailover=true** verwendet, generiert der Treiber einen Fehler. Wenn eine Verbindungszeichenfolge jedoch **failoverPartner** und **multiSubnetFailover=false** (oder **ApplicationIntent=ReadWrite**) verwendet, greift die Anwendung auf Datenbankspiegelung zurück.  
  
Der Treiber gibt einen Fehler zurück, wenn die Datenbankspiegelung in der primären Datenbank in der Verfügbarkeitsgruppe und **multiSubnetFailover=true** in der Verbindungszeichenfolge verwendet werden, die anstatt mit einem Verfügbarkeitsgruppenlistener eine Verbindung mit einer primären Datenbank herstellt.  

[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]

## <a name="connection-pooling"></a>Verbindungspooling

Beim Verwenden des Microsoft JDBC-Treibers für SQL Server in Kombination mit einer Verbindungspoolbibliothek sollten Sie Folgendes beachten:

- Wenn Sie schreibgeschütztes Routing sowie einen Pool aus schreibgeschützten Servern konfiguriert haben, über die Sie Last verteilen möchten, wird beim Verbindungspooling die Anzahl von Möglichkeiten für neue Verbindungen zum Verteilen auf die Zielserver reduziert.
- Wählen Sie Pooloptionen aus, die eine gleichmäßige Verteilung von Verbindungen im Pool unterstützen, um in einem Pool eine hohe Last auf einem einzelnen Server zu vermeiden.
- Stellen Sie sicher, dass der Verbindungspool mit einer Verbindungslebensdauer konfiguriert ist. Wenn ein schreibgeschütztes Replikat bei einer schreibgeschützten Verbindung nicht verfügbar ist, sollte durch die Konfiguration sichergestellt werden, dass die Verbindung ggf. geschlossen und auf einem schreibgeschützten Replikat neu erstellt wird, sobald ein solches wieder verfügbar ist.

## <a name="new-methods-supporting-multisubnetfailover-and-applicationintent"></a>Neue Methoden mit Unterstützung für multiSubnetFailover und applicationIntent  

Mit den folgenden Methoden erhalten Sie programmgesteuerten Zugriff auf die Schlüsselwörter **multiSubnetFailover**, **applicationIntent** und **transparentNetworkIPResolution** für Verbindungszeichenfolgen:  
  
- [SQLServerDataSource.getApplicationIntent](reference/getapplicationintent-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.setApplicationIntent](reference/setapplicationintent-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.getMultiSubnetFailover](reference/getmultisubnetfailover-method-sqlserverdatasource.md)  
  
- [SQLServerDataSource.setMultiSubnetFailover](reference/setmultisubnetfailover-method-sqlserverdatasource.md)  
  
- [SQLServerDriver.getPropertyInfo](reference/getpropertyinfo-method-sqlserverdriver.md)  

- SQLServerDataSource.setTransparentNetworkIPResolution

- SQLServerDataSource.getTransparentNetworkIPResolution
  
Die Methoden **getMultiSubnetFailover**, **setMultiSubnetFailover**, **getApplicationIntent**, **setApplicationIntent**, **getTransparentNetworkIPResolution** und **setTransparentNetworkIPResolution** werden ebenfalls [SQLServerDataSource Class](reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource Class](reference/sqlserverconnectionpooldatasource-class.md) und [SQLServerXADataSource Class](reference/sqlserverxadatasource-class.md) hinzugefügt.  
  
## <a name="tlsssl-certificate-validation"></a>TLS-/SSL-Zertifikatüberprüfung  

Eine Verfügbarkeitsgruppe besteht aus mehreren physischen Servern. Mit [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] wurde die Unterstützung von **Alternativen Antragstellernamen** in TLS-/SSL-Zertifikaten eingeführt, sodass einem Zertifikat mehrere Hosts zugeordnet werden können. Weitere Informationen zu TLS finden Sie unter [Verstehen der Verschlüsselungsunterstützung](understanding-ssl-support.md).  
  
## <a name="see-also"></a>Weitere Informationen  

[Verbinden mit SQL Server mit dem JDBC-Treiber](connecting-to-sql-server-with-the-jdbc-driver.md)  
[Festlegen von Verbindungseigenschaften](setting-the-connection-properties.md)  
