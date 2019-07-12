---
title: 'Gewusst wie: Konfigurieren von MSDTC unter Linux'
description: Dieser Artikel enthält eine schrittweise Anleitung zum Konfigurieren von MSDTC unter Linux.
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 03/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: f4fe81c5e306b059414fe0f2245aca9c9787ee1b
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834026"
---
# <a name="how-to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-on-linux"></a>Gewusst wie: Konfigurieren der Microsoft Distributed Transaction Coordinator (MSDTC) unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel beschreibt, wie Sie den Microsoft Distributed Transaction Coordinator (MSTDC) unter Linux konfigurieren. Unterstützung von MSDTC unter Linux wurde in SQL Server-2019 Vorschau eingeführt.

## <a name="overview"></a>Übersicht

Verteilte Transaktionen sind für SQL Server unter Linux durch die Einführung von MS DTC und RPC Endpoint Mapper Funktionalität in SQL Server aktiviert. Wird standardmäßig ein RPC-endpunktzuordnung Prozess lauscht an Port 135 für eingehende RPC-Anforderungen sowie registrierte Komponenteninformationen zu Remoteanforderungen. Remote-Anforderungen können von der endpunktzuordnung zurückgegebene Informationen für die Kommunikation mit registrierten RPC-Komponenten, z. B. MSDTC-Dienste verwenden. Ein Prozess erfordert Superuser-Berechtigungen zum Binden an bekannten Ports (Portnummern unter 1024) unter Linux. Um zu vermeiden, Starten von SQL Server mit Stammberechtigungen für den RPC Endpoint Mapper-Prozess, müssen Systemadministratoren "iptables" zum Erstellen von Netzwerkadressübersetzung zur Weiterleitung von Datenverkehr auf Port 135 für den SQL Server RPC-endpunktzuordnung Prozess verwenden.

SQL Server-2019 führt zwei Konfigurationsparameter für die Mssql-Conf-Hilfsprogramm.

| mssql-conf setting | Beschreibung |
|---|---|
| **network.rpcport** | Der TCP-Port, an die der RPC Endpoint Mapper-Prozess gebunden. |
| **distributedtransaction.servertcpport** | Der Port, dem der MSDTC-Server überwacht. Wenn nicht festgelegt, der MSDTC-Dienst verwendet einen zufälligen kurzlebigen Port auf den-Dienst neu gestartet wird und Firewall-Ausnahmen müssen neu konfiguriert werden, um sicherzustellen, dass die Kommunikation von MSDTC-Dienst fortgesetzt werden kann. |

Weitere Informationen zu diesen Einstellungen und andere verwandten MSDTC-Einstellungen finden Sie unter [Konfigurieren von SQL Server unter Linux mit der Mssql-Conf-Tool](sql-server-linux-configure-mssql-conf.md#msdtc).

## <a name="supported-msdtc-configurations"></a>Unterstützte Konfigurationen für MSDTC

Die folgenden MSDTC-Konfigurationen werden unterstützt:

- OLE-TX verteilt Sie Transaktionen für SQL Server unter Linux für ODBC-Anbieter.
- Für verteilte XA-Transaktionen für SQL Server unter Linux mithilfe von JDBC- und ODBC-Anbieter. Für den XA-Transaktionen mithilfe der ODBC-Anbieter ausgeführt werden müssen Sie Microsoft ODBC-Treiber für SQL Server-Version 17.3 oder höher verwenden.
- Verteilte Transaktionen für Verbindungsserver.

Einschränkungen und bekannte Probleme für MSDTC in der Vorschau finden Sie [Versionsanmerkungen zu SQL Server-2019-Vorschauversion unter Linux](sql-server-linux-release-notes-2019.md#msdtc).

## <a name="msdtc-configuration-steps"></a>MSDTC-Konfigurationsschritte

Es gibt drei Schritte zum Konfigurieren von MSDTC-Kommunikation und Funktionalität. Wenn die erforderlichen Konfigurationsschritte nicht fertig sind, wird die MSDTC-Funktion von SQL Server nicht aktivieren.

- Konfigurieren von **network.rpcport** und **distributedtransaction.servertcpport** mit Mssql-conf
- Konfigurieren der Firewall zum Zulassen von Kommunikation auf **distributedtransaction.servertcpport** und -Port 135.
- Konfigurieren von Linux-Server so, dass RPC-Kommunikation an Port 135, um SQL Server umgeleitet wird routing **network.rpcport**.

Die folgenden Abschnitte enthalten ausführliche Anweisungen für die einzelnen Schritte.

## <a name="configure-rpc-and-msdtc-ports"></a>Konfigurieren von RPC- und MS DTC-ports

Konfigurieren Sie zunächst **network.rpcport** und **distributedtransaction.servertcpport** mit Mssql-conf Diesen Schritt, wenn SQL Server-spezifische und allgemeine auf alle unterstützten Verteilungen aufgeteilt.

1. Mit der Mssql-Conf fest der **network.rpcport** Wert. Im folgenden Beispiel wird es auf 13500.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.rpcport 13500
   ```

2. Legen Sie die **distributedtransaction.servertcpport** Wert. Im folgenden Beispiel wird es auf 51999.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set distributedtransaction.servertcpport 51999
   ```

3. Starten Sie SQL Server neu.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="configure-the-firewall"></a>Konfigurieren der Firewall

Der zweite Schritt ist zum Konfigurieren der Firewall zum Zulassen von Kommunikation auf **Servertcpport** und -Port 135.  Dies ermöglicht die RPC-endpunktzuordnung Prozess und die MSDTC-Prozess, extern auf andere Transaktions-Managern und Koordinatoren zu kommunizieren. Die tatsächlichen Schritte für diese variiert je nach Firewall und Linux-Distribution. 

Das folgende Beispiel zeigt, wie Sie diese Regeln auf Erstellen **Ubuntu**.

```bash
sudo ufw allow from any to any port 51999 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

Das folgende Beispiel zeigt, wie dies auf durchgeführt werden konnte **Red Hat Enterprise Linux (RHEL)** :

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

Es ist wichtig zum Konfigurieren der Firewall vor dem Konfigurieren der portweiterleitung im nächsten Abschnitt. Aktualisieren die Firewall können Sie die Port-Routingregeln in einigen Fällen deaktivieren.

## <a name="configure-port-routing"></a>Konfigurieren des Routings port

Die Routingtabelle für Linux-Server so konfigurieren, dass RPC-Kommunikation an Port 135, um SQL Server umgeleitet wird **network.rpcport**. Konfigurationsverfahren für die portweiterleitung andere Verteilung abweichen. Die folgenden Abschnitte enthalten Leitfäden für Ubuntu, Red Hat Enterprise Linux (RHEL) und SUS Enterprise Linux (SLES).

### <a name="port-routing-in-ubuntu-and-sles"></a>Routing in Ubuntu und SLES-Port

Ubuntu und SLES verwenden nicht die **Firewalld** Dienst, also **Iptable** Regeln sind von effizienten portweiterleitung erreichen. Die **Iptable** Regeln möglicherweise während des Neustarts, nicht beibehalten, damit die folgenden Befehle auch Anweisungen zum Wiederherstellen der Regeln nach einem Neustart bereitstellen.

1. Erstellen Sie Routingregeln zu Port 135. Im folgenden Beispiel wird Port 135 zum RPC-Port 13500, definiert, die im vorherigen Abschnitt geleitet. Ersetzen Sie dies `<ipaddress>` mit der IP-Adresse des Servers.

   ```bash
   sudo iptables -t nat -A PREROUTING -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL  \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   sudo iptables -t nat -A OUTPUT -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   ```

   Die `--comment RpcEndPointMapper` Parameter in den vorherigen Befehlen hilft bei der Verwaltung dieser Regeln in späteren-Befehlen.

2. Zeigen Sie die Routingregeln, die Sie mit dem folgenden Befehl erstellt haben:

   ```bash
   sudo iptables -S -t nat | grep "RpcEndPointMapper"
   ```

3. Speichern Sie die Senderegeln in eine Datei auf Ihrem Computer.

   ```bash
   sudo iptables-save > /etc/iptables.conf
   ```

4. Um die Regeln nach einem Neustart zu laden, fügen Sie den folgenden Befehl aus, um `/etc/rc.local` (für Ubuntu) oder `/etc/init.d/after.local` (für SLES):

   ```bash
   iptables-restore < /etc/iptables.conf
   ```

   > [!NOTE]
   > Sie benötigen Administrator ("sudo") Berechtigungen zum Bearbeiten der **rc.local** oder **after.local** Dateien.

Die **Iptables speichern** und **Iptables-Restore** Befehle zusammen mit `rc.local` / `after.local` Startkonfiguration, geben Sie einen einfachen Mechanismus zum Speichern und Wiederherstellen von "iptables" Einträge. Je nach Ihrer Linux-Distribution, gibt es möglicherweise werden erweiterte oder Ihre bevorzugte automatisierte verfügbaren Optionen. Beispielsweise eine Ubuntu-Alternative ist die **"iptables" persistenter** Paket, um Einträge dauerhaft zu machen.

> [!IMPORTANT]
> Die vorherigen Schritte wird davon ausgegangen, eine feste IP-Adresse. Wenn sich die IP-Adresse für Ihre SQL Server-Instanz (aufgrund von manueller Eingriff "oder" DHCP ") ändert, müssen Sie diese entfernen und neu der Routingregeln erstellen, wenn sie mit" iptables "erstellt wurden. Bei Bedarf neu erstellen oder vorhandene Regeln für die nachrichtenweiterleitung zu löschen, können den folgenden Befehl zum Entfernen der alten `RpcEndPointMapper` Regeln:
> 
> ```bash
> sudo iptables -S -t nat | grep "RpcEndPointMapper" | sed 's/^-A //' | while read rule; do iptables -t nat -D $rule; done
> ```

### <a name="port-routing-in-rhel"></a>Portrouting in RHEL

Für Distributionen, mit denen **Firewalld** Dienst, z. B. Red Hat Enterprise Linux, den gleichen Dienst, die für beide Öffnen des Ports auf dem Server und den internen Port Forwarding verwendet werden kann. Beispielsweise unter Red Hat Enterprise Linux, befolgen Sie **Firewalld** Dienst (über **Firewall-Cmd** Serverkonfigurations-Hilfsprogramm mit `-add-forward-port` oder ähnliche Optionen) zum Erstellen und Verwalten von permanenten Port die Weiterleitungsregeln anstelle von "iptables".

```bash
sudo firewall-cmd --permanent --add-forward-port=port=135:proto=tcp:toport=13500
sudo firewall-cmd --reload
```

## <a name="verify"></a>Stellen Sie sicher

An diesem Punkt sollte SQL Server an verteilten Transaktionen teilnehmen können. Um sicherzustellen, dass SQL Server lauscht, führen Sie die **Netstat** Befehl (Wenn Sie RHEL verwenden, müssen Sie möglicherweise zuerst installieren die **Net-Tools** Paket):

```bash
sudo netstat -tulpn | grep sqlservr
```

Eine Ausgabe ähnlich der folgenden sollte angezeigt werden:

```bash
tcp 0 0 0.0.0.0:1433 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 127.0.0.1:1434 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:13500 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:51999 0.0.0.0:* LISTEN 13911/sqlservr
tcp6 0 0 :::1433 :::* LISTEN 13911/sqlservr
tcp6 0 0 ::1:1434 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::13500 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::51999 :::* LISTEN 13911/sqlservr
```

Allerdings nach einem Neustart, SQL Server startet nicht lauscht der **Servertcpport** bis die erste Transaktion verteilt. In diesem Fall würden Sie SQL Server-Port 51999 in diesem Beispiel lauscht, bis die erste verteilte Transaktion nicht angezeigt.

## <a name="configure-authentication-on-rpc-communication-for-msdtc"></a>Konfigurieren der Authentifizierung für RPC-Kommunikation für MSDTC

MSDTC für SQL Server unter Linux verwendet keine Authentifizierung für RPC-Kommunikation in der Standardeinstellung. Jedoch, wenn der Hostcomputer einer Active Directory (AD)-Domäne angehört, es ist möglich, konfigurieren Sie MSDTC zum Verwenden der authentifizierte RPC-Kommunikation mit folgenden **Mssql-Conf** Einstellungen:

| Einstellung | Beschreibung |
|---|---|
| **distributedtransaction.allowonlysecurerpccalls**          | Konfigurieren Sie die sichere nur RPC-Aufrufe für verteilte Transaktionen. |
| **distributedtransaction.fallbacktounsecurerpcifnecessary** | Konfigurieren der Sicherheit, die nur RPC für verteilte Transaktionen aufruft. |
| **distributedtransaction.turnoffrpcsecurity**               | Aktivieren Sie oder deaktivieren Sie der RPC-Sicherheit für verteilte Transaktionen. |

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server unter Linux finden Sie unter [SQL Server unter Linux](sql-server-linux-overview.md).
