---
title: 'Gewusst wie: Konfigurieren von MSDTC unter Linux | Microsoft-Dokumentation'
description: Dieser Artikel enthält eine schrittweise Anleitung zum Konfigurieren von MSDTC unter Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b32b3465184d5a8be1ef07f42b6b764b0600940d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815548"
---
# <a name="how-to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-on-linux"></a>Gewusst wie: Konfigurieren der Microsoft Distributed Transaction Coordinator (MSDTC) unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel beschreibt, wie Sie den Microsoft Distributed Transaction Coordinator (MSTDC) unter Linux konfigurieren. Unterstützung von MSDTC unter Linux wurde in SQL Server 2019 CTP 2.0 eingeführt.

## <a name="overview"></a>Übersicht

Verteilte Transaktionen sind für SQL Server unter Linux durch die Einführung von MS DTC und RPC Endpoint Mapper Funktionalität in SQL Server aktiviert. Standardmäßig wird ein RPC-endpunktzuordnung Prozess lauscht an Port 135 für eingehende RPC-Anforderungen und weiterleitet, der entsprechenden Komponenten (z. B. der MSDTC-Dienst). Ein Prozess erfordert die Berechtigung zum Administrator zum Binden an bekannten Ports (Portnummern unter 1024) unter Linux. Um zu vermeiden, Starten von SQL Server mit Stammberechtigungen für den RPC Endpoint Mapper-Prozess, müssen Systemadministratoren "iptables" zum Erstellen von NAT-Adressübersetzung zur Weiterleitung von Datenverkehr auf Port 135 für den SQL Server RPC-endpunktzuordnung Prozess verwenden.

SQL Server-2019 führt zwei Konfigurationsparameter für die Mssql-Conf-Hilfsprogramm.

| MSSQL-Conf-Einstellung | Description |
|---|---|
| **Network.rpcport** | Der TCP-Port, an die der RPC Endpoint Mapper-Prozess gebunden. |
| **Network.servertcpport** | Der Port, dem der MSDTC-Server überwacht. Wenn nicht festgelegt, der MSDTC-Dienst verwendet einen zufälligen kurzlebigen Port auf den-Dienst neu gestartet wird und Firewall-Ausnahmen müssen werden neu konfiguriert, um sicherzustellen, dass die Kommunikation von MSDTC-Dienst fortgesetzt werden kann. |

Weitere Informationen zu diesen Einstellungen und andere verwandten MSDTC-Einstellungen finden Sie unter [Konfigurieren von SQL Server unter Linux mit der Mssql-Conf-Tool](sql-server-linux-configure-mssql-conf.md#msdtc).

## <a name="supported-msdtc-configurations"></a>Unterstützte Konfigurationen für MSDTC

Die folgenden MSDTC-Konfigurationen werden unterstützt:

- OLE-TX verteilt Sie Transaktionen für SQL Server unter Linux für JDBC- und ODBC-Anbieter.
- Für verteilte XA-Transaktionen für SQL Server unter Linux mithilfe von JDBC-Anbietern.
- Verteilte Transaktionen für Verbindungsserver.

Einschränkungen und bekannte Probleme bei der MSDTC in CTP 2.0 finden Sie [Release Notes for 2019 CTP für SQL Server unter Linux Version](sql-server-linux-release-notes-2019.md#msdtc).

## <a name="msdtc-configuration-steps"></a>MSDTC-Konfigurationsschritte

Es gibt drei Schritte zum Konfigurieren von MSDTC-Kommunikation und Funktionalität. Wenn die erforderlichen Konfigurationsschritte nicht fertig sind, wird die MSDTC-Funktion von SQL Server nicht aktivieren.

- Konfigurieren von **network.rpcport** und **distributedtransaction.servertcpport** mit Mssql-conf
- Konfigurieren der Firewall zum Zulassen von Kommunikation auf **Rpcport**, **Servertcpport**, und Port 135.
- Konfigurieren von Linux-Server so, dass RPC-Kommunikation an Port 135, um SQL Server umgeleitet wird routing **network.rpcport**.

Die folgenden Abschnitte enthalten ausführliche Anweisungen für die einzelnen Schritte.

## <a name="configure-rpc-and-msdtc-ports"></a>Konfigurieren von RPC- und MS DTC-ports

Konfigurieren Sie zunächst **network.rpcport** und **distributedtransaction.servertcpport** mit Mssql-conf

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

Der letzte Schritt ist zum Konfigurieren der Firewall zum Zulassen von Kommunikation auf **Rpcport**, **Servertcpport**, und Port 135.  Dies ermöglicht die RPC-endpunktzuordnung Prozess und die MSDTC-Prozess, extern auf andere Transaktions-Managern und Koordinatoren zu kommunizieren. Die tatsächlichen Schritte für diese variiert je nach Firewall und Linux-Distribution. 

Das folgende Beispiel zeigt, wie Sie diese Regeln auf Ubuntu erstellen.

```bash
sudo ufw allow from any to any port 51999 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

Das folgende Beispiel zeigt, wie dies unter Red Hat Enterprise Linux (RHEL) ausgeführt werden konnte:

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

Es ist wichtig zum Konfigurieren der Firewall vor dem Konfigurieren der portweiterleitung im nächsten Abschnitt. Aktualisieren die Firewall können Sie die Port-Routingregeln in einigen Fällen deaktivieren.

## <a name="configure-port-routing"></a>Konfigurieren des Routings port

Die Routingtabelle für Linux-Server so konfigurieren, dass RPC-Kommunikation an Port 135, um SQL Server umgeleitet wird **network.rpcport**. Iptable-Regeln können während des Neustarts, nicht beibehalten, damit die folgenden Befehle auch Anweisungen zum Wiederherstellen der Regeln nach einem Neustart bereitstellen.

1. Erstellen Sie Routingregeln zu Port 135. Im folgenden Beispiel wird Port 135 zum RPC-Port 13500, definiert, die im vorherigen Abschnitt geleitet. Ersetzen Sie dies `<ipaddress>` mit der IP-Adresse des Servers.

   ```bash
   iptables -t nat -A PREROUTING -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL  \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   iptables -t nat -A OUTPUT -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   ```

   Die `--comment RpcEndPointMapper` Parameter in den vorherigen Befehlen hilft bei der Verwaltung dieser Regeln in späteren-Befehlen.

2. Zeigen Sie die Routingregeln, die Sie mit dem folgenden Befehl erstellt haben:

   ```bash
   iptables -S -t nat | grep "RpcEndPointMapper"
   ```

3. Speichern Sie die Senderegeln in eine Datei auf Ihrem Computer.

   ```bash
   iptables-save > /etc/iptables.conf
   ```

4. Um die Regeln nach einem Neustart zu laden, fügen Sie den folgenden Befehl aus, um `/etc/rc.local` (für Ubuntu oder RHEL) oder `/etc/init.d/after.local` (für SLES):

   ```bash
   iptables-restore < /etc/iptables.conf
   ```

Die **Iptables speichern** und **Iptables-Restore** Befehle geben Sie einen einfachen Mechanismus zum Speichern und Wiederherstellen von "iptables" Einträge. Je nach Ihrer Linux-Distribution, gibt es möglicherweise werden erweiterte oder Ihre bevorzugte automatisierte verfügbaren Optionen. Beispielsweise eine Ubuntu-Alternative ist die **"iptables" persistenter** Paket, um Einträge dauerhaft zu machen. Oder für Red Hat Enterprise Linux, möglicherweise Firewalld-Diensts (über Firewall-Cmd-Serverkonfigurations-Hilfsprogramm mit – hinzufügen-vorwärts-Port oder ähnliche Optionen) zum Erstellen von permanenten portweiterleitungsregeln anstelle von "iptables".

> [!IMPORTANT]
> Die vorherigen Schritte wird davon ausgegangen, eine feste IP-Adresse. Wenn sich die IP-Adresse für Ihre SQL Server-Instanz (aufgrund von manueller Eingriff "oder" DHCP ") ändert, müssen Sie diese entfernen und erstellen Sie die Senderegeln neu. Bei Bedarf neu erstellen oder vorhandene Regeln für die nachrichtenweiterleitung zu löschen, können den folgenden Befehl zum Entfernen der alten `RpcEndPointMapper` Regeln:
> 
> ```bash
> iptables -S -t nat | grep "RpcEndPointMapper" | sed 's/^-A //' | while read rule; do iptables -t nat -D $rule; done
> ```

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

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu SQL Server unter Linux finden Sie unter [SQL Server unter Linux](sql-server-linux-overview.md).
