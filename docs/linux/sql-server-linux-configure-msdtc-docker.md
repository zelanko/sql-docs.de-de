---
title: Verwenden Sie verteilte Transaktionen mit SQL Server unter Docker | Microsoft-Dokumentation
description: In diesem Artikel wird erläutert, wie Dprovides eine schrittweise Anleitung zum Konfigurieren von MSDTC unter Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/25/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 1e38c1cf0fb82c70f57a1648619d584b06281cba
ms.sourcegitcommit: 65ceea905030582f8d89e75e97758abf3b1f0bd6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400059"
---
# <a name="how-to-use-distributed-transactions-with-sql-server-on-docker"></a>Verwenden Sie verteilte Transaktionen mit SQL Server unter Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel erläutert das Einrichten von SQL Server Linux-Containern in Docker für verteilte Transaktionen.

Ab SQL Server-2019-Preview, unterstützen Container-Images der Microsoft Distributed Transaction Coordinator (MSDTC) für verteilte Transaktionen erforderlich sind. Die Kommunikation-Anforderungen für die MS DTC finden Sie unter [konfigurieren Sie den Microsoft Distributed Transaction Coordinator (MSDTC) auf Linux](sql-server-linux-configure-msdtc.md). In diesem Artikel wird erläutert, die besonderen Anforderungen und Szenarien im Zusammenhang mit SQL Server-Docker-Container.

## <a name="configuration"></a>Konfiguration

Um MS DTC-Transaktion in Containern für Docker zu aktivieren, müssen Sie zwei neue Umgebungsvariablen festlegen:

- **MSSQL_RPC_PORT**: der, die RPC-endpunktzuordnung an gebunden und lauscht an TCP-Port.  
- **MSSQL_DTC_TCP_PORT**: der Port, dass MS DTC-Dienst für die Überwachung konfiguriert ist.

### <a name="pull-and-run"></a>Pullen und auszuführen

Das folgende Beispiel zeigt, wie Sie diese Umgebungsvariablen verwenden, und führen Sie einen einzelnen SQL Server-Container für MSDTC konfiguriert wird. Dadurch kann er mit jeder Anwendung auf allen Hosts kommunizieren.

```bash
docker run \
   -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -e 'MSSQL_RPC_PORT=135' -e 'MSSQL_DTC_TCP_PORT=51000' \
   -p 51433:1433 -p 135:135 -p 51000:51000  \
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

> [!IMPORTANT]
> Der vorherige Befehl funktioniert nur für Docker unter Linux ausgeführt wird. Docker unter Windows lauscht der Windows-Host bereits an Port 135. Sie können entfernen, die `-p 135:135` -Parameter für Docker unter Windows, aber es gelten einige Einschränkungen. Der resultierende Container kann dann nicht für verteilte Transaktionen verwendet werden, die den Host betreffen; Es kann nur in verteilte Transaktionen zwischen Docker-Container auf dem Host teilnehmen.

In diesem Befehl wird die **RPC-Endpunktzuordnung** Dienst an Port 135, gebunden wurde und die **MSDTC** Dienst an Port 51000 in virtuellen Docker-Netzwerk gebunden wurde. SQL Server-TDS-Kommunikation erfolgt über Port 1433 in virtuellen Docker-Netzwerk. Diese Ports extern verfügbar gemacht als TDS-Port 51433, RPC Endpoint Mapper-Port 135 und MS DTC-Port 51000 an Host.

> [!NOTE]
> Die RPC-Endpunktzuordnung und den MS DTC-Port müssen nicht auf dem Host und dem Container identisch sein. Also während der RPC-Endpunktzuordnung-Port 135 für Container konfiguriert wurde, kann es möglicherweise zugeordnet werden 13501 oder ein beliebiger anderer verfügbaren Port auf dem Host port.

## <a name="configure-the-firewall"></a>Konfigurieren der Firewall

Um mit und über den Host zu kommunizieren, müssen Sie auch die Firewall für den Container auf dem Host konfigurieren. Öffnen die Firewall für alle ports, in dem Docker Container verfügbar macht, für die externe Kommunikation. Im vorherigen Beispiel wäre dies die Ports 135, 51433 und 51000. Dies sind die Ports auf dem Host selbst und nicht die Ports, die sie im Container zugeordnet. Wenn RPC-Endpunkt hostPort 51001, Mapper Port 51000 des Containers zugeordnet wurde dann port sollte also 51001 (nicht 51000) in der Firewall für die Kommunikation mit dem Host geöffnet werden.  

Das folgende Beispiel zeigt, wie Sie diese Regeln auf Ubuntu erstellen.

```bash
sudo ufw allow from any to any port 51433 proto tcp
sudo ufw allow from any to any port 51000 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

Das folgende Beispiel zeigt, wie dies unter Red Hat Enterprise Linux (RHEL) ausgeführt werden konnte:

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=51433/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

## <a name="configure-port-routing-on-the-host"></a>Konfigurieren der portweiterleitung auf dem host

Im vorherigen Beispiel da er ein einzelnen Docker-Container RPC-Port 135 zu Port 135, auf dem Host zugeordnet sollten verteilte Transaktionen mit dem Host ohne weitere Konfiguration funktioniert. Beachten Sie, dass es möglich, direkt zu Port 135 im Container verwenden, da SQL Server mit erweiterten Berechtigungen in einem Container ausgeführt wird. Für SQL Server außerhalb eines Containers muss ein anderen kurzlebiger Port verwendet werden, und Datenverkehr an Port 135 klicken Sie dann an diesen Port weitergeleitet werden muss.

Jedoch wenn Sie des Containers Port 135 für einen anderen Port auf dem Host, z. B. 13500 zuordnen möchten, müssen Sie zum Konfigurieren der portweiterleitung auf dem Host. Dadurch wird den Docker-Container zur Teilnahme an verteilter Transaktionen mit dem Host und anderen externen Servern. Weitere Informationen finden Sie unter [Konfigurieren des Routings Port](sql-server-linux-configure-msdtc.md#configure-port-routing).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu MSDTC unter Linux finden Sie unter [konfigurieren Sie den Microsoft Distributed Transaction Coordinator (MSDTC) auf Linux](sql-server-linux-configure-msdtc.md).
