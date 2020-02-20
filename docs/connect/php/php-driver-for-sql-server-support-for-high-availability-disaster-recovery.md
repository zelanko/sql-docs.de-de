---
title: Unterstützung für Hochverfügbarkeit und Notfallwiederherstellung für die Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 73a80821-d345-4fea-b076-f4aabeb4af3e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9f67a0cc7f564683ed11ce7d7de9da5200128434
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "76929179"
---
# <a name="support-for-high-availability-disaster-recovery"></a>Unterstützung für hohe Verfügbarkeit bei Notfallwiederherstellung
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

In diesem Thema wird die Unterstützung von [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] (in Version 3.0 hinzugefügt) für Hochverfügbarkeit und Notfallwiederherstellung erläutert.

Ab Version 3.0 der Microsoft-Treiber für PHP für SQL Server können Sie den Verfügbarkeitsgruppenlistener einer Verfügbarkeitsgruppe für Hochverfügbarkeit und Notfallwiederherstellung oder einer Failoverclusterinstanz als Server in der Verbindungszeichenfolge angeben.

Die Verbindungseigenschaft **MultiSubnetFailover** gibt an, dass die Anwendung in einer Verfügbarkeitsgruppe oder einer Failoverclusterinstanz bereitgestellt wird und dass der Treiber versucht, eine Verbindung mit der Datenbank auf der primären SQL Server-Instanz herzustellen, indem er Verbindungsversuche mit allen IP-Adressen unternimmt. Geben Sie immer **MultiSubnetFailover=true** an, wenn Sie eine Verbindung mit einem SQL Server-Verfügbarkeitsgruppenlistener oder einer SQL Server-Failoverclusterinstanz herstellen. Wenn die Anwendung mit einer Always On-Datenbank verbunden ist, für die ein Failover ausgeführt wird, wird die ursprüngliche Verbindung unterbrochen, und die Anwendung muss eine neue Verbindung öffnen, damit ihre Ausführung nach dem Failover fortgesetzt werden kann.

Ausführliche Informationen zu Always On-Verfügbarkeitsgruppen finden Sie auf der Dokumentationsseite [Hochverfügbarkeit und Notfallwiederherstellung](https://docs.microsoft.com/sql/relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery).

## <a name="transparent-network-ip-resolution-tnir"></a>Transparente Netzwerk-IP-Auflösung (TNIR)

Die transparente Netzwerk-IP-Adressauflösung (Transparent Network IP Resolution, TNIR) ist eine Überarbeitung des vorhandenen **MultiSubnetFailover**-Features. Sie wirkt sich auf die Verbindungssequenz des Treibers aus, wenn die erste aufgelöste IP-Adresse des Hostnamens nicht reagiert und dem Hostnamen mehrere IP-Adressen zugeordnet sind. Die entsprechende Verbindungsoption lautet **TransparentNetworkIPResolution**. Zusammen mit **MultiSubnetFailover** stellt diese Option die folgenden vier Verbindungssequenzen bereit: 

- TNIR aktiviert und **MultiSubnetFailover** deaktiviert: Erst wird eine IP-Adresse ausprobiert, dann alle IP-Adressen gleichzeitig.
- TNIR aktiviert und **MultiSubnetFailover** aktiviert: Alle IP-Adressen werden gleichzeitig ausprobiert.
- TNIR deaktiviert und **MultiSubnetFailover** deaktiviert: Alle IP-Adressen werden nacheinander ausprobiert.
- TNIR deaktiviert und **MultiSubnetFailover** aktiviert: Alle IP-Adressen werden gleichzeitig ausprobiert.

TNIR ist standardmäßig aktiviert, **MultiSubnetFailover** ist standardmäßig deaktiviert.

Im Folgenden sehen Sie ein Beispiel für die Aktivierung sowohl von TNIR als auch von **MultiSubnetFailover** mit dem PDO_SQLSRV-Treiber:

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
Ein Verbindungsfehler tritt auf, wenn die Verbindungsschlüsselwörter **MultiSubnetFailover** und **Failover_Partner** in der Verbindungszeichenfolge vorhanden sind. Es tritt auch ein Fehler auf, wenn **MultiSubnetFailover** verwendet wird und SQL Server eine Failoverpartnerantwort zurückgibt, die angibt, dass es Teil eines Datenbankspiegelungspaars ist.  
  
Wenn Sie ein Upgrade einer PHP-Anwendung ausführen, die derzeit die Datenbankspiegelung in einem Szenario mit mehreren Subnetzen verwendet, entfernen Sie die Verbindungseigenschaft **Failover_Partner**, und ersetzen Sie sie durch **MultiSubnetFailover**, festgelegt auf **True**. Ersetzen Sie außerdem den Servernamen in der Verbindungszeichenfolge durch einen Verfügbarkeitsgruppenlistener. Wenn eine Verbindungszeichenfolge **Failover_Partner** und **MultiSubnetFailover=true**verwendet, generiert der Treiber einen Fehler. Wenn eine Verbindungszeichenfolge jedoch **Failover_Partner** und **MultiSubnetFailover=false** (oder **ApplicationIntent=ReadWrite**) verwendet, verwendet die Anwendung Datenbankspiegelung.  
  
Der Treiber gibt einen Fehler zurück, wenn die Datenbankspiegelung in der primären Datenbank in der Verfügbarkeitsgruppe verwendet wird, und wenn **MultiSubnetFailover=true** in der Verbindungszeichenfolge verwendet wird, die statt mit einem Verfügbarkeitsgruppenlistener eine Verbindung mit einer primären Datenbank herstellt.  

[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="see-also"></a>Weitere Informationen  
[Verbinden mit dem Server](../../connect/php/connecting-to-the-server.md)  
  
