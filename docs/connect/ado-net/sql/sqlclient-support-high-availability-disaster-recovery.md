---
title: SqlClient-Unterstützung für Hochverfügbarkeit, Notfallwiederherstellung
description: Beschreibt die SqlClient-Unterstützung für Hochverfügbarkeit und Notfallwiederherstellung bei (Always On-)Verfügbarkeitsgruppen
ms.date: 08/15/2019
ms.assetid: 61e0b396-09d7-4e13-9711-7dcbcbd103a0
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: a7aa6a28a64e35c13c135e509b758a1636b3f896
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896286"
---
# <a name="sqlclient-support-for-high-availability-disaster-recovery"></a>SqlClient-Unterstützung für Hochverfügbarkeit, Notfallwiederherstellung

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Dieser Artikel befasst sich mit der Unterstützung des Microsoft SqlClient-Datenanbieters für SQL Server für Hochverfügbarkeit und Notfallwiederherstellung – Always On-Verfügbarkeitsgruppen.  Die Funktion für AlwaysOn-Verfügbarkeitsgruppen wurde SQL Server 2012 hinzugefügt. Weitere Informationen über AlwaysOn-Verfügbarkeitsgruppen finden Sie in der SQL Server-Onlinedokumentation.  
  
Sie können jetzt den Verfügbarkeitsgruppenlistener einer Verfügbarkeitsgruppe (für hohe Verfügbarkeit und Notfallwiederherstellung) oder eine SQL Server 2012-Failoverclusterinstanz in der Verbindungseigenschaft angeben. Wenn eine SqlClient-Anwendung mit einer Always On-Datenbank verbunden ist, für die ein Failover ausgeführt wird, wird die ursprüngliche Verbindung unterbrochen, und die Anwendung muss eine neue Verbindung öffnen, damit ihre Ausführung nach dem Failover fortgesetzt werden kann.  
  
Wenn Sie keine Verbindung mit einem Verfügbarkeitsgruppenlistener oder einer SQL Server 2012-Failoverclusterinstanz herstellen und mehrere IP-Adressen einem Hostnamen zugeordnet sind, durchläuft SqlClient nacheinander alle IP-Adressen, die dem DNS-Eintrag zugeordnet sind. Dies kann zeitaufwändig sein, wenn die erste vom DNS-Server zurückgegebene IP-Adresse an keine Netzwerkschnittstellenkarte (NIC) gebunden ist. Beim Herstellen einer Verbindung mit einem Verfügbarkeitsgruppenlistener oder einer SQL Server 2012-Failoverclusterinstanz versucht SqlClient, Verbindungen mit allen IP-Adressen gleichzeitig herzustellen, und wenn ein Verbindungsversuch erfolgreich war, verwirft der Treiber alle ausstehenden Verbindungsversuche.  
  
> [!NOTE]
>  Das Erhöhen des Verbindungstimeouts sowie die Implementierung von Verbindungswiederholungslogik erhöhen die Wahrscheinlichkeit, dass eine Anwendung eine Verbindung zu einer Verfügbarkeitsgruppe herstellt. Da zudem eine Verbindung aufgrund eines Failovers fehlschlagen kann, empfiehlt sich die Implementierung von Verbindungswiederholungslogik, wodurch im Fall einer fehlgeschlagenen Verbindung bis zur erneuten Verbindung Wiederholungsversuche erfolgen.  
  
Der Microsoft SqlClient-Datenanbieter für SQL Server unterstützt die folgenden Verbindungseigenschaften:  
  
- `ApplicationIntent`  
  
- `MultiSubnetFailover`  
  
Sie können diese Schlüsselwörter für Verbindungszeichenfolgen folgendermaßen programmgesteuert ändern:  
  
- <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.ApplicationIntent%2A>  
  
- <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>  
  
## <a name="connecting-with-multisubnetfailover"></a>Verbinden mit MultiSubnetFailover  
Geben Sie immer `MultiSubnetFailover=True` an, wenn Sie eine Verbindung mit einem SQL Server 2012-Verfügbarkeitsgruppenlistener oder einer SQL Server 2012-Failoverclusterinstanz herstellen. `MultiSubnetFailover` aktiviert schnelleres Failover für alle Verfügbarkeitsgruppen und die Failoverclusterinstanz in SQL Server 2012 und reduziert die Failoverzeit für einzelne und Multisubnetz-AlwaysOn-Topologien erheblich. Während eines Multisubnetzfailovers versucht der Client Verbindungen parallel. Während eines Subnetzfailovers wird der TCP-Verbindungsversuch aggressiv wiederholt.  
  
Die `MultiSubnetFailover`-Verbindungseigenschaft gibt an, dass die Anwendung in einer Verfügbarkeitsgruppe oder SQL Server 2012-Failoverclusterinstanz bereitgestellt wird und dass SqlClient versucht, eine Verbindung mit der Datenbank auf der primären SQL Server-Instanz herzustellen, indem eine Verbindung mit allen IP-Adressen versucht wird. Wenn `MultiSubnetFailover=True` für eine Verbindung angegeben wird, wiederholt der Client TCP-Verbindungsversuche schneller als dies bei den standardmäßigen TCP-Neuübertragungsintervallen des Betriebssystems der Fall ist. Auf diese Weise kann die Verbindung nach einem Failover einer AlwaysOn-Verfügbarkeitsgruppe oder einer AlwaysOn-Failoverclusterinstanz schneller wiederhergestellt werden. Diese Einstellung gilt sowohl für Einzelsubnetz- als auch Multisubnetz-Verfügbarkeitsgruppen und -Failoverclusterinstanzen.  
  
Weitere Informationen zu den Schlüsselwörtern für Verbindungszeichenfolgen, die in SqlClient unterstützt werden, finden Sie unter <xref:Microsoft.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
Das Angeben von `MultiSubnetFailover=True` wenn eine Verbindung mit anderen Komponenten als einem Verfügbarkeitsgruppenlistener oder einer SQL Server 2012-Failoverclusterinstanz hergestellt wird, führt zu verminderter Leistung und wird nicht unterstützt.  
  
Befolgen Sie beim Herstellen einer Verbindung mit einem Server in einer Verfügbarkeitsgruppe oder einer SQL Server 2012-Failoverclusterinstanz die folgenden Richtlinien:  
  
- Verwenden Sie die `MultiSubnetFailover`-Verbindungseigenschaft, wenn Sie eine Verbindung mit einem Einzelsubnetz oder Multisubnetz herstellen. Dadurch wird die Leistung für beide verbessert.  
  
- Um eine Verbindung mit einer Verfügbarkeitsgruppe herzustellen, geben Sie in der Verbindungszeichenfolge den Verfügbarkeitsgruppenlistener der Verfügbarkeitsgruppe als Server an.  
  
- Ein Verbindungsversuch mit einer mit mehr als 64 IP-Adressen konfigurierten SQL Server-Instanz verursacht einen Verbindungsfehler.  
  
- Das Verhalten einer Anwendung, die die `MultiSubnetFailover`-Verbindungseigenschaft verwendet, wird nicht vom Authentifizierungstyp beeinflusst: SQL Server-Authentifizierung, Kerberos-Authentifizierung oder Windows-Authentifizierung.  
  
- Vergrößern Sie den Wert von `Connect Timeout`, um eine ausreichende Failoverzeit zu konfigurieren und die Anzahl der Verbindungsherstellungsversuche der Anwendung zu reduzieren.  
  
- Verteilte Transaktionen werden nicht unterstützt.  
  
 Wenn das schreibgeschützte Routing nicht in Kraft ist, scheitert das Herstellen einer Verbindung mit einem sekundären Replikatspeicherort in den folgenden Situationen:  
  
- Wenn der sekundäre Replikatspeicherort nicht zum Akzeptieren von Verbindungen konfiguriert ist.  
  
- Wenn eine Anwendung `ApplicationIntent=ReadWrite` verwendet (weiter unten erläutert), und der sekundäre Replikatspeicherort für schreibgeschützten Zugriff konfiguriert ist.  
  
<xref:Microsoft.Data.SqlClient.SqlDependency> wird bei schreibgeschützten sekundären Replikaten nicht unterstützt.  
  
Es kann keine Verbindung hergestellt werden, wenn ein primäres Replikat so konfiguriert ist, dass schreibgeschützte Arbeitslasten abgelehnt werden, und die Verbindungszeichenfolge `ApplicationIntent=ReadOnly` enthält.  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Aktualisieren zur Verwendung von Multisubnetzclustern aus Datenbankspiegelung  
Ein Verbindungsfehler (<xref:System.ArgumentException>) tritt auf, wenn die Verbindungsschlüsselwörter `MultiSubnetFailover` und `Failover Partner` in der Verbindungszeichenfolge vorhanden sind oder wenn `MultiSubnetFailover=True` und ein anderes Protokoll als TCP verwendet wird. Es tritt auch ein Fehler (<xref:Microsoft.Data.SqlClient.SqlException>) auf, wenn `MultiSubnetFailover` verwendet wird und SQL Server eine Failoverpartnerantwort zurückgibt, die angibt, dass es Teil eines Datenbankspiegelungspaars ist.  
  
Wenn Sie eine SqlClient-Anwendung aktualisieren, die derzeit Datenbankspiegelung in einem Multisubnetz-Szenario verwendet, müssen Sie die `Failover Partner`-Verbindungseigenschaft entfernen und mit `MultiSubnetFailover`, festgelegt auf `True`, ersetzen, sowie den Servernamen in der Verbindungszeichenfolge mit einem Verfügbarkeitsgruppenlistener ersetzen. Wenn eine Verbindungszeichenfolge `Failover Partner` und `MultiSubnetFailover=True` verwendet, generiert der Treiber einen Fehler. Wenn eine Verbindungszeichenfolge jedoch `Failover Partner` und `MultiSubnetFailover=False` (oder `ApplicationIntent=ReadWrite`) verwendet, verwendet die Anwendung Datenbankspiegelung.  
  
Der Treiber gibt einen Fehler zurück, wenn die Datenbankspiegelung für die primäre Datenbank in der Verfügbarkeitsgruppe verwendet wird und wenn `MultiSubnetFailover=True` in der Verbindungszeichenfolge angegeben ist, wodurch eine Verbindung mit einer primären Datenbank und nicht mit einem Verfügbarkeitsgruppen-Listener hergestellt wird.  
  
## <a name="specifying-application-intent"></a>Angeben des Anwendungszwecks  
Im Fall von `ApplicationIntent=ReadOnly` fordert der Client eine Lesearbeitslast an, wenn eine Verbindung mit einer AlwaysOn-Datenbank hergestellt wird. Der Server erzwingt den Versuch zur Verbindungszeit und während einer USE-Datenbankanweisung, aber nur für eine AlwaysOn-aktivierte Datenbank.  
  
Das `ApplicationIntent`-Schlüsselwort funktioniert nicht mit schreibgeschützten Legacy-Datenbanken.  
  
Eine Datenbank kann Lesearbeitslasten auf der AlwaysOn-Zieldatenbank zulassen bzw. nicht zulassen. (Dies geschieht über die `ALLOW_CONNECTIONS`-Klausel der Transact-SQL-Anweisungen `PRIMARY_ROLE` und `SECONDARY_ROLE`.)  
  
Das `ApplicationIntent`-Schlüsselwort wird verwendet, um schreibgeschütztes Routing zu aktivieren.  
  
## <a name="read-only-routing"></a>Schreibgeschütztes Routing  
Schreibgeschütztes Routing ist eine Funktion, die die Verfügbarkeit eines schreibgeschützten Replikats einer Datenbank sicherstellen kann. So aktivieren Sie schreibgeschütztes Routing:  
  
- Sie müssen eine Verbindung zum Verfügbarkeitsgruppenlistener einer AlwaysOn-Verfügbarkeitsgruppe herstellen.  
  
- Das Schlüsselwort der `ApplicationIntent`-Verbindungszeichenfolge muss auf `ReadOnly` festgelegt werden.  
  
- Die Verfügbarkeitsgruppe muss vom Datenbankadministrator konfiguriert werden, um schreibgeschütztes Routing zu aktivieren.  
  
Möglicherweise werden bei mehreren Verbindungen mithilfe von schreibgeschütztem Routing nicht alle mit demselben schreibgeschützten Replikat verbunden. Änderungen in der Datenbanksynchronisierung oder Änderungen in der Routingkonfiguration des Servers können zu Clientverbindungen mit anderen schreibgeschützten Replikaten führen. Sie gewährleisten, dass alle schreibgeschützten Anforderungen Verbindungen mit demselben schreibgeschützten Replikat herstellen, indem Sie keinen Verfügbarkeitsgruppenlistener an das Schlüsselwort der `Data Source`-Verbindungszeichenfolge übermitteln. Geben Sie stattdessen den Namen der schreibgeschützten Instanz an.  
  
Schreibgeschütztes Routing dauert möglicherweise länger als das Herstellen einer primären Verbindung, da schreibgeschütztes Routing zuerst eine primäre Verbindung herstellt und dann nach der besten verfügbaren lesbaren Sekundärverbindung sucht. Deswegen sollten Sie das Anmeldetimeout vergrößern.  
  
## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Features und ADO.NET](sql-server-features-adonet.md)
