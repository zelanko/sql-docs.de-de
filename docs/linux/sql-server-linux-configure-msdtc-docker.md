---
title: 'Vorgehensweise: Verwenden verteilter Transaktionen mit SQL Server unter Docker'
description: Dieser Artikel bietet eine exemplarische Vorgehensweise zum Konfigurieren von MS DTC unter Linux.
author: VanMSFT
ms.author: vanto
ms.date: 09/25/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 8304bc95a15a5a9cf74ab23bc2e8e47bf7cf72d1
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68476045"
---
# <a name="how-to-use-distributed-transactions-with-sql-server-on-docker"></a>Vorgehensweise: Verwenden verteilter Transaktionen mit SQL Server unter Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird erläutert, wie Sie SQL Server-Linux-Container unter Docker für verteilte Transaktionen einrichten.

Ab SQL Server 2019 (Vorschauversion) unterstützen Containerimages den für verteilte Transaktionen erforderlichen Microsoft Distributed Transaction Coordinator (MS DTC). Informationen zu den Kommunikationsanforderungen für MS DTC finden Sie unter [Konfigurieren des Microsoft Distributed Transaction Coordinator (MS DTC) unter Linux](sql-server-linux-configure-msdtc.md). In diesem Artikel werden die besonderen Anforderungen und Szenarien im Zusammenhang mit SQL Server-Docker-Containern erläutert.

## <a name="configuration"></a>Konfiguration

Um die MS DTC-Transaktion in Containern für Docker zu aktivieren, müssen Sie zwei neue Umgebungsvariablen festlegen:

- **MSSQL_RPC_PORT**: der TCP-Port, wo der RPC-Endpunktzuordnungs-Dienst gebunden wird und lauscht.  
- **MSSQL_DTC_TCP_PORT**: der Port, für den der MS DTC-Dienst konfiguriert ist, und wo er lauscht.

### <a name="pull-and-run"></a>Pullen und Ausführen

Im folgenden Beispiel wird gezeigt, wie diese Umgebungsvariablen verwendet werden, um einen einzelnen SQL Server-Container zu pullen und auszuführen, der für MS DTC konfiguriert ist. Dies ermöglicht, mit jeder beliebigen Anwendung auf allen Hosts zu kommunizieren.

```bash
docker run \
   -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -e 'MSSQL_RPC_PORT=135' -e 'MSSQL_DTC_TCP_PORT=51000' \
   -p 51433:1433 -p 135:135 -p 51000:51000  \
   -d mcr.microsoft.com/mssql/server:2019-CTP3.2-ubuntu
```

> [!IMPORTANT]
> Der vorherige Befehl funktioniert nur für Docker bei Ausführung unter Linux. Für Docker unter Windows lauscht der Windows-Host bereits auf Port 135. Sie können den `-p 135:135`-Parameter für Docker unter Windows entfernen, es gibt jedoch einige Einschränkungen. Der resultierende Container kann dann nicht für verteilte Transaktionen verwendet werden, die den Host einschließen. Er kann nur an verteilten Transaktionen zwischen Docker-Containern auf dem Host beteiligt sein.

In diesem Befehl ist der **RPC-Endpunktzuordnungs-Dienst** an Port 135 gebunden, und der **MS DTC**-Dienst wurde an Port 51000 innerhalb des virtuellen Docker-Netzwerks gebunden. SQL Server-TDS-Kommunikation erfolgt auf Port 1433 innerhalb des virtuellen Docker-Netzwerks. Diese Ports wurden extern für den Host als TDS-Port 51433, RPC-Endpunktzuordnungs-Port 135 und MS DTC-Port 51000 verfügbar gemacht.

> [!NOTE]
> Der RPC-Endpunktzuordnungs- und MS DTC-Port müssen auf Host und Container nicht identisch sein. Während der RPC-Endpunktzuordnungs-Port für den Container mit 135 konfiguriert wurde, kann er auf dem Hostserver möglicherweise Port 13501 oder einem beliebigen anderen verfügbaren Port zugeordnet werden.

## <a name="configure-the-firewall"></a>Konfigurieren der Firewall

Um mit und über den Host zu kommunizieren, müssen Sie auch die Firewall auf dem Hostserver für die Container konfigurieren. Öffnen Sie die Firewall für alle Ports, die der Docker-Container für die externe Kommunikation verfügbar macht. Im vorherigen Beispiel waren dies die Ports 135, 51433 und 51000. Dabei handelt es sich um die Ports auf dem Host selbst und nicht um die Ports, die im Container zugeordnet sind. Wenn also der RPC-Endpunktzuordnungs-Port 51000 des Containers dem Hostport 51001 zugeordnet wurde, sollte Port 51001 (nicht 51000) in der Firewall für die Kommunikation mit dem Host geöffnet werden.  

Im folgenden Beispiel wird das Erstellen dieser Regeln unter Ubuntu gezeigt.

```bash
sudo ufw allow from any to any port 51433 proto tcp
sudo ufw allow from any to any port 51000 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

Im folgenden Beispiel wird gezeigt, wie dies unter Red Hat Enterprise Linux (RHEL) durchgeführt werden kann:

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=51433/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

## <a name="configure-port-routing-on-the-host"></a>Konfigurieren des Portroutings auf dem Host

Da im vorherigen Beispiel ein einzelner Docker-Container den RPC-Port 135 dem Port 135 auf dem Host zuordnet, sollten verteilte Transaktionen mit dem Host jetzt ohne weitere Konfiguration funktionieren. Beachten Sie, dass der Port 135 direkt im Container verwendet werden kann, da SQL Server in einem Container mit erhöhten Rechten ausgeführt wird. Bei Ausführung von SQL Server außerhalb eines Containers muss ein anderer kurzlebiger Port verwendet werden, und der Datenverkehr zu Port 135 muss dann an diesen Port weitergeleitet werden.

Wenn Sie jedoch beschlossen haben, den Port 135 des Containers einem anderen Port auf dem Host zuzuordnen, z.B. 13500, müssen Sie das Portrouting auf dem Host konfigurieren. So kann der Docker-Container an verteilten Transaktionen mit dem Host und anderen externen Servern teilnehmen. Weitere Informationen finden Sie unter [Konfigurieren des Portroutings](sql-server-linux-configure-msdtc.md#configure-port-routing).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu MS DTC unter Linux finden Sie unter [Konfigurieren des Microsoft Distributed Transaction Coordinator (MS DTC) unter Linux](sql-server-linux-configure-msdtc.md).
