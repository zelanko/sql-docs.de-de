---
title: Unterstützung für hohe Verfügbarkeit, Notfallwiederherstellung für die Microsoft-Treiber für PHP für SQLServer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 73a80821-d345-4fea-b076-f4aabeb4af3e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb0af342ac2ccbe916fba9edb497e8197b2fe7f5
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42787038"
---
# <a name="support-for-high-availability-disaster-recovery"></a>Unterstützung für hohe Verfügbarkeit bei Notfallwiederherstellung
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Thema wird [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Unterstützung (in Version 3.0 hinzugefügt) für Hochverfügbarkeit, Disaster Recovery -- [!INCLUDE[ssHADR](../../includes/sshadr_md.md)] erläutert.  [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]-Support wurde in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] hinzugefügt. Weitere Informationen über [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
  
In Version 3.0 von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] können Sie den Verfügbarkeitsgruppenlistener einer Verfügbarkeitsgruppe (Hochverfügbarkeit, Notfallwiederherstellung) in der Verbindungseigenschaft angeben. Wenn eine [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]-Anwendung mit einer Always On-Datenbank verbunden ist, für die ein Failover ausgeführt wird, wird die ursprüngliche Verbindung unterbrochen, und die Anwendung muss eine neue Verbindung öffnen, damit ihre Ausführung nach dem Failover fortgesetzt werden kann.  
  
Wenn Sie keine Verbindung zu einem verfügbaren Gruppenlistener herstellen und mehrere IP-Adressen einem Hostnamen zugeordnet sind, durchläuft [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] nacheinander alle IP-Adressen, die dem DNS-Eintrag zugeordnet sind. Dies kann zeitaufwändig sein, wenn die erste vom DNS-Server zurückgegebene IP-Adresse an keine Netzwerkschnittstellenkarte (NIC) gebunden ist. Beim Herstellen einer Verbindung zu einem verfügbaren Gruppenlistener versucht der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)], Verbindungen zu allen IP-Adressen parallel herzustellen, und wenn ein Verbindungsversuch erfolgreich ist, verwirft der Treiber alle ausstehenden Verbindungsversuche.  
  
> [!NOTE]  
> Das Erhöhen des Verbindungstimeouts sowie die Implementierung von Verbindungswiederholungslogik erhöhen die Wahrscheinlichkeit, dass eine Anwendung eine Verbindung zu einer Verfügbarkeitsgruppe herstellt. Da zudem eine Verbindung aufgrund eines Verfügbarkeitsgruppenfailovers fehlschlagen kann, empfiehlt sich die Implementierung von Verbindungswiederholungslogik, wodurch im Fall einer fehlgeschlagenen Verbindung bis zur erneuten Verbindung Wiederholungsversuche erfolgen.  
  
## <a name="connecting-with-multisubnetfailover"></a>Verbinden mit MultiSubnetFailover  
Die **MultiSubnetFailover** -Verbindungseigenschaft gibt an, dass die Anwendung in einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz bereitgestellt wird und [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] versucht, eine Verbindung mit der Datenbank auf der primären [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz herzustellen, indem mit allen IP-Adressen der Verfügbarkeitsgruppe Verbindungsversuche unternommen werden. Wenn **MultiSubnetFailover=true** für eine Verbindung angegeben wird, wiederholt der Client TCP-Verbindungsversuche schneller als dies bei den standardmäßigen TCP-Neuübertragungsintervallen des Betriebssystems der Fall ist. Auf diese Weise kann die Verbindung nach einem Failover einer AlwaysOn-Verfügbarkeitsgruppe oder einer AlwaysOn-Failoverclusterinstanz schneller wiederhergestellt werden. Diese Einstellung gilt sowohl für Einzelsubnetz- als auch Multisubnetz-Verfügbarkeitsgruppen und -Failoverclusterinstanzen.  
  
Geben Sie immer **MultiSubnetFailover=true** an, wenn Sie eine Verbindung mit einem SQL Server 2012-Verfügbarkeitsgruppenlistener oder einer SQL Server 2012-Failoverclusterinstanz herstellen. **MultiSubnetFailover** aktiviert schnelleres Failover für alle Verfügbarkeitsgruppen und die Failoverclusterinstanz in SQL Server 2012 und reduziert die Failoverzeit für einzelne und Always On-Multisubnetztopologien erheblich. Während eines Multisubnetzfailovers versucht der Client Verbindungen parallel. Während eines Subnetz-Failovers unternimmt [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] aggressive Wiederholungsversuche zum Herstellen der TCP-Verbindung.  
  
Weitere Informationen zu Verbindungszeichenfolgenschlüsselwörtern in [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] finden Sie unter [Verbindungsoptionen](../../connect/php/connection-options.md).  
  
Das Angeben von **MultiSubnetFailover=true** für ein anderes Verbindungsziel als einen Verfügbarkeitsgruppenlistener oder eine Failoverclusterinstanz kann die Leistung beeinträchtigen und wird nicht unterstützt.  
  
Stellen Sie mithilfe der folgenden Richtlinien eine Verbindung mit einem Server in einer Verfügbarkeitsgruppe her:  
  
-   Verwenden Sie die **MultiSubnetFailover** -Verbindungseigenschaft, wenn Sie eine Verbindung mit einem Einzelsubnetz oder Multisubnetz herstellen. Dadurch wird die Leistung für beide verbessert.  
  
-   Um eine Verbindung mit einer Verfügbarkeitsgruppe herzustellen, geben Sie in der Verbindungszeichenfolge den Verfügbarkeitsgruppenlistener der Verfügbarkeitsgruppe als Server an.  
  
-   Ein Verbindungsversuch mit einer mit mehr als 64 IP-Adressen konfigurierten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz verursacht einen Verbindungsfehler.  
  
-   Das Verhalten einer Anwendung, die die **MultiSubnetFailover**-Verbindungseigenschaft verwendet, wird durch den Authentifizierungstyp nicht beeinflusst: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Authentifizierung, Kerberos-Authentifizierung oder Windows-Authentifizierung.  
  
-   Erhöhen Sie den Wert von **loginTimeout**, um die Failoverzeit zu berücksichtigen und Wiederholungsversuche für Anwendungsverbindungen zu reduzieren.  
  
-   Verteilte Transaktionen werden nicht unterstützt.  
  
Wenn das schreibgeschützte Routing nicht aktiviert ist, scheitert das Herstellen der Verbindung mit einem sekundären Replikatspeicherort in einer Verfügbarkeitsgruppe in den folgenden Situationen:  
  
- Wenn der sekundäre Replikatspeicherort nicht zum Akzeptieren von Verbindungen konfiguriert ist.  
  
- Wenn eine Anwendung **ApplicationIntent=ReadWrite** verwendet (weiter unten erläutert), und der sekundäre Replikatspeicherort für schreibgeschützten Zugriff konfiguriert ist.  
  
Es kann keine Verbindung hergestellt werden, wenn ein primäres Replikat so konfiguriert ist, dass schreibgeschützte Arbeitslasten abgelehnt werden, und die Verbindungszeichenfolge **ApplicationIntent=ReadOnly**enthält.  

## <a name="transparent-network-ip-resolution-tnir"></a>Transparente Netzwerk-IP-Auflösung (TNIR)

Transparente Netzwerk-IP-Auflösung (TNIR) ist es sich um eine Überarbeitung der vorhandenen MultiSubnetFailover-Funktion. Es wirkt sich auf der Verbindungssequenz des Treibers aus, die erste beseitigt, IP-Adresse den Hostnamen nicht reagiert, und es gibt mehrere IP-Adressen, die den Hostnamen zugeordnet. Zusammen mit MultiSubnetFailover bieten die folgenden vier Verbindung Sequenzen: 

- TNIR aktiviert und deaktiviert MultiSubnetFailover: eine IP-Adresse versucht wird, gefolgt von allen IP-Adressen parallel
- TNIR aktiviert & MultiSubnetFailover aktiviert: alle IP-Adressen parallel versucht werden
- Deaktivierte TNIR & MultiSubnetFailover deaktiviert: alle IP-Adressen versucht werden nacheinander
- TNIR deaktiviert und aktiviert MultiSubnetFailover: alle IP-Adressen parallel versucht werden

TNIR ist standardmäßig aktiviert, und MultiSubnetFailover ist standardmäßig deaktiviert.

Dies ist ein Beispiel, aktivieren Sie die TNIR und MultiSubnetFailover mit dem PDO_SQLSRV-Treiber:

```
<?php
$serverName = "yourservername";
$username = "yourusername";
$password = "yourpassword";
$connectionString = "sqlsrv:Server=$serverName; TransparentNetworkIPResolution=Enabled; MultiSubnetFailover=yes";
try {
    $conn = new PDO($connectionString, $username, $password, array(PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION));
    // your code 
    // more of your code
    // when done, close the connection
    unset($conn);
} catch(PDOException $e) {
    print_r($e->errorInfo);
}
?>
```

## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>Aktualisieren zur Verwendung von Multisubnetzclustern aus Datenbankspiegelung  
Ein Verbindungsfehler tritt auf, wenn die Verbindungsschlüsselwörter **MultiSubnetFailover** und **Failover_Partner** in der Verbindungszeichenfolge vorhanden sind. Es tritt auch ein Fehler auf, wenn **MultiSubnetFailover** verwendet wird und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eine Failoverpartnerantwort zurückgibt, die angibt, dass es Teil eines Datenbankspiegelungspaars ist.  
  
Wenn Sie eine [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] Anwendung aktualisieren, die derzeit Datenbankspiegelung in einem Multisubnetz-Szenario verwendet, müssen Sie die **Failover_Partner** -Verbindungseigenschaft entfernen und mit **MultiSubnetFailover** , festgelegt auf **Yes** , ersetzen, sowie den Servernamen in der Verbindungszeichenfolge mit einem Verfügbarkeitsgruppenlistener ersetzen. Wenn eine Verbindungszeichenfolge **Failover_Partner** und **MultiSubnetFailover=true**verwendet, generiert der Treiber einen Fehler. Wenn eine Verbindungszeichenfolge jedoch **Failover_Partner** und **MultiSubnetFailover=false** (oder **ApplicationIntent=ReadWrite**) verwendet, verwendet die Anwendung Datenbankspiegelung.  
  
Der Treiber gibt einen Fehler zurück, wenn die Datenbankspiegelung in der primären Datenbank in der Verfügbarkeitsgruppe verwendet wird, und wenn **MultiSubnetFailover=true** in der Verbindungszeichenfolge verwendet wird, die statt mit einem Verfügbarkeitsgruppenlistener eine Verbindung mit einer primären Datenbank herstellt.  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Verbinden mit dem Server](../../connect/php/connecting-to-the-server.md)  
  
