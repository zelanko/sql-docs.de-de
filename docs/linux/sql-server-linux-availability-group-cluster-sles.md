---
title: SLES-Cluster für SQL Server-Verfügbarkeitsgruppe konfigurieren | Microsoft-Dokumentation
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 85180155-6726-4f42-ba57-200bf1e15f4d
ms.openlocfilehash: 95c9c2b9bdbcbfb6573688ad220ab504dc89e337
ms.sourcegitcommit: ef7f2540ba731cc6a648005f2773d759df5c6405
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39415509"
---
# <a name="configure-sles-cluster-for-sql-server-availability-group"></a>Konfigurieren Sie SLES-Cluster für SQL Server-Verfügbarkeitsgruppe

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieses Handbuch enthält Anweisungen, um einen Cluster mit drei Knoten für SQL Server unter SUSE Linux Enterprise Server (SLES) 12 SP2 zu erstellen. Für hohe Verfügbarkeit, eine verfügbarkeitsgruppe für Linux erfordert drei Knoten – Siehe [hohe Verfügbarkeit und Datenschutz für verfügbarkeitsgruppenkonfigurationen](sql-server-linux-availability-group-ha.md). Die clustering-Ebene basiert darauf, dass SUSE [hohe Verfügbarkeit-Erweiterung (HAE)](https://www.suse.com/products/highavailability) baut auf [Pacemaker](http://clusterlabs.org/). 

Weitere Informationen für die Clusterkonfiguration, Ressourcenoptionen-Agent, Management, bewährte Methoden und Empfehlungen finden Sie unter [SUSE Linux Enterprise hohe Verfügbarkeit Erweiterung 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html).

>[!NOTE]
>SQL Server Integration mit Pacemaker unter Linux ist an diesem Punkt nicht als gekoppelt als mit WSFC unter Windows. SQL Server Service unter Linux ist nicht clusterabhängig. Pacemaker steuert alle von der Orchestrierung der Clusterressourcen, einschließlich der Verfügbarkeitsgruppen-Ressource. Unter Linux sollten Sie nicht für immer auf Verfügbarkeit Gruppe Dynamic Management Views (DMVs) verlassen, die Clusterinformationen, z. B. sys. dm_hadr_cluster bereitstellen. Darüber hinaus Name des virtuellen Netzwerks ist spezifisch für die WSFC, es gibt keine Entsprechung desselben in Pacemaker. Sie können einen Listener für die Verwendung für transparente erneute Verbindung nach einem Failover weiterhin erstellen, aber müssen Sie manuell den verfügbarkeitsgruppenlistener-Namen in der DNS-Server registrieren, mit der IP-Adresse verwendet, um die virtuelle IP-Ressource (wie in den folgenden Abschnitten erläutert wird) zu erstellen.


## <a name="roadmap"></a>Roadmap für die

Das Verfahren zum Erstellen einer verfügbarkeitsgruppe für hochverfügbarkeit unterscheidet sich zwischen Linux-Servern und einem Windows Server-Failovercluster. Die folgende Liste beschreibt die allgemeinen Schritte: 

1. [Konfigurieren von SQL Server auf den Clusterknoten](sql-server-linux-setup.md).

2. [Erstellen der verfügbarkeitsgruppe](sql-server-linux-availability-group-failover-ha.md). 

3. Konfigurieren Sie eine Clusterressourcen-Manager, z.B. Pacemaker. Diese Anweisungen sind in diesem Dokument.
   
   Die Möglichkeit, einen Cluster-Ressourcen-Manager zu konfigurieren, hängt von der jeweilige Linux-Distribution. 

   >[!IMPORTANT]
   >Produktionsumgebungen sind erforderlich, einen umgrenzungs-Agent, wie STONITH für hohe Verfügbarkeit. In die Beispielen in diesem Artikel verwenden Sie umgrenzungs-Agents nicht. Sie sind für Tests und nur die Überprüfung. 
   
   >Ein Pacemaker-Cluster verwendet Umgrenzung, um den Cluster in einen bekannten Zustand zurückzugeben. Die Möglichkeit zum Konfigurieren der Umgrenzung hängt davon ab, die Verteilung und der Umgebung. Zu diesem Zeitpunkt ist die Umgrenzung nicht in eine Cloud-Umgebungen verfügbar. Finden Sie unter [SUSE Linux Enterprise-Erweiterung für hohe Verfügbarkeit](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. [Fügen Sie die verfügbarkeitsgruppe als Ressource im Cluster](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server). 

## <a name="prerequisites"></a>Erforderliche Komponenten

Um das folgende End-to-End-Szenario abzuschließen, benötigen Sie drei Computer, die den drei Knoten-Cluster bereitzustellen. Die folgenden Schritte beschreiben, wie Sie diese Server zu konfigurieren.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Richten Sie ein und konfigurieren Sie das Betriebssystem auf jedem Clusterknoten 

Der erste Schritt ist das Betriebssystem auf den Clusterknoten zu konfigurieren. Verwenden Sie für diese exemplarische Vorgehensweise SLES 12 SP2 mit einem gültigen Abonnement, für die HA-Add-On.

### <a name="install-and-configure-sql-server-service-on-each-cluster-node"></a>Installieren und Konfigurieren von SQL Server-Dienst auf jedem Clusterknoten

1. Installieren und Einrichten von SQL Server-Dienst auf allen Knoten. Ausführliche Anweisungen finden Sie unter [Installieren von SQL Server unter Linux](sql-server-linux-setup.md).

1. Legen Sie einen Knoten als primären als auch andere Knoten als sekundäre Datenbanken ein. Verwenden Sie diese Begriffe in diesem Handbuch.

1. Stellen Sie sicher, dass der Knoten, die Teil des Clusters sein werden, die miteinander kommunizieren können.

   Das folgende Beispiel zeigt `/etc/hosts` mit Ergänzungen für drei Knoten, die mit dem Namen, SLES1, SLES2 und SLES3.

   ```
   127.0.0.1   localhost
   10.128.16.33 SLES1
   10.128.16.77 SLES2
   10.128.16.22 SLES3
   ```

   Alle Clusterknoten müssen über SSH, aufeinander zugreifen können. Tools wie `hb_report` oder `crm_report` (zur Problembehandlung) und Hawk's History Explorer erfordern kennwortlosen SSH-Zugriff zwischen den Knoten, andernfalls können sie nur Daten sammeln, aus dem aktuellen Knoten. Für den Fall, dass Sie einen nicht standardmäßigen SSH-Port verwenden, verwenden Sie die Option-X (finden Sie unter `man` Seite). Wenn Ihr SSH-Port 3479 ist, z. B. Rufen Sie eine `crm_report` mit:

   ```bash
   sudo crm_report -X "-p 3479" [...]
   ```

   Weitere Informationen finden Sie unter den [SLES-Administratorhandbuch - Abschnitt Sonstiges](http://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc).


## <a name="create-a-sql-server-login-for-pacemaker"></a>Erstellen Sie eine SQL Server-Anmeldung für Pacemaker

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="configure-an-always-on-availability-group"></a>Konfigurieren einer AlwaysOn-Verfügbarkeitsgruppe

Konfigurieren Sie auf Linux-Servern die verfügbarkeitsgruppe, und konfigurieren Sie die Clusterressourcen. Um die verfügbarkeitsgruppe zu konfigurieren, finden Sie unter [Konfigurieren von AlwaysOn-Verfügbarkeitsgruppe für SQL Server unter Linux](sql-server-linux-availability-group-configure-ha.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installieren Sie und konfigurieren Sie auf jedem Clusterknoten die Pacemaker

1. Installieren der Erweiterung für hohe Verfügbarkeit

   Finden Sie unter [Installieren von SUSE Linux Enterprise Server und die hohe Verfügbarkeit-Erweiterung](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.installation)

1. Installieren Sie SQL Server-Ressourcen-Agent-Paket auf beiden Knoten.

   ```bash
   sudo zypper install mssql-server-ha
   ```

## <a name="set-up-the-first-node"></a>Richten Sie den ersten Knoten

   Finden Sie unter [SLES-installationsanweisungen](http://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node)

1. Melden Sie sich als `root` auf dem physischen oder virtuellen Computer, die Sie als Clusterknoten verwenden möchten.
2. Starten Sie das bootstrap-Skript, indem Sie Ausführung:
   ```bash
   sudo ha-cluster-init
   ```

   Wenn NTP nicht so konfiguriert wurde, dass beim Booten startet, wird eine Meldung angezeigt. 

   Wenn Sie den Vorgang trotzdem fortsetzen möchten, wird das Skript automatisch für SSH-Zugriff und das Synchronisierungstool Csync2-Schlüssel generiert, und starten Sie die Dienste, die für beide erforderlich sind. 

3. So konfigurieren Sie die clusterkommunikationsebene (Corosync): 

   A. Geben Sie eine Netzwerkadresse zum Binden an. In der Standardeinstellung schlägt das Skript die Netzwerkadresse des "eth0". Alternativ geben Sie eine andere Netzwerkadresse, z. B. die Adresse des bond0 aus. 

   B. Geben Sie eine Multicastadresse. Das Skript schlägt eine zufällige Adresse, die Sie als Standard verwenden können. 

   c. Geben Sie einen multicast-Port ein. Das Skript schlägt 5405 als Standard. 

   d. So konfigurieren Sie `SBD ()`, geben Sie einen persistenten Pfads auf die Partition des Geräts blockieren, die Sie für die SBD verwenden möchten. Der Pfad muss in allen Knoten im Cluster konsistent sein. 
   Schließlich wird das Skript den Pacemaker-Dienst zum Onlineschalten des Clusters einem Knoten, und aktivieren die Web-Verwaltungsschnittstelle Hawk2 gestartet. Die URL für Hawk2 verwenden, wird auf dem Bildschirm angezeigt. 

4. Überprüfen Sie alle Details des Setupvorgangs, `/var/log/sleha-bootstrap.log`. Sie haben nun eine Ausführung Einzelknotencluster. Überprüfen Sie den Status des Clusters mit Crm-Status:

   ```bash
   sudo crm status
   ```

   Sie sehen auch die Konfiguration eines Clusters mit `crm configure show xml` oder `crm configure show`.

5. Das bootstrapverfahren erstellt einen Linux-Benutzer, die mit dem Namen "hacluster" mit dem Kennwort-Linux. Ersetzen Sie das Standardkennwort durch eine sichere so bald wie möglich: 

   ```bash
   sudo passwd hacluster
   ```

## <a name="add-nodes-to-the-existing-cluster"></a>Hinzufügen von Knoten zum vorhandenen cluster

Wenn Sie einen Cluster mit einem oder mehreren Knoten ausgeführt haben, fügen Sie mehrere Clusterknoten mit dem bootstrap-ha-Cluster-Join-Skript hinzu. Das Skript nur den Zugriff auf einen vorhandenen Clusterknoten und die grundlegende Einrichtung auf dem aktuellen Computer werden automatisch vervollständigt wird. Verwenden Sie die folgenden Schritte aus:

Wenn Sie die vorhandenen Clusterknoten konfiguriert haben die `YaST` cluster-Modul, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind, vor dem Ausführen von `ha-cluster-join`:
- Der Root-Benutzer auf den vorhandenen Knoten über SSH-Schlüssel für die Anmeldung ohne Kennwort verfügt. 
- `Csync2` wird auf den vorhandenen Knoten konfiguriert. Weitere Informationen finden Sie unter Konfigurieren von Csync2 mit YaST. 

1. Melden Sie sich als Root-Benutzer auf dem physischen oder virtuellen Computer, die dem Cluster beitreten soll. 
2. Starten Sie das bootstrap-Skript, indem Sie Ausführung: 

   ```bash
   sudo ha-cluster-join
   ```

   Wenn NTP nicht so konfiguriert wurde, dass beim Booten startet, wird eine Meldung angezeigt. 

3. Wenn Sie den Vorgang trotzdem fortsetzen möchten, werden Sie aufgefordert, die IP-Adresse von einem vorhandenen Knoten anzugeben. Geben Sie die IP-Adresse ein. 

4. Wenn Sie einer kennwortlosen SSH-Zugriff zwischen den beiden Computern nicht bereits konfiguriert haben, werden Sie auch das Stammkennwort für den vorhandenen Knoten aufgefordert werden. 

   Nach der Anmeldung mit dem angegebenen Knoten das Skript kopiert die Corosync-Konfiguration, SSH konfiguriert und `Csync2`, und den aktuelle Computer online als neuen Clusterknoten aus. Abgesehen von der, dass wird den Dienst nach der Hawk gestartet. Wenn Sie freigegebenen Speicher mit konfiguriert haben `OCFS2`, erstellt es automatisch auch das Verzeichnis Bereitstellungspunkt für das `OCFS2` -Dateisystem. 

5. Wiederholen Sie die vorherigen Schritte für alle Computer, die Sie dem Cluster hinzufügen möchten. 

6. Überprüfen Sie die Einzelheiten des Prozesses `/var/log/ha-cluster-bootstrap.log`. 

1. Überprüfen Sie den Status des Clusters mit `sudo crm status`. Wenn Sie einen zweiten Knoten erfolgreich hinzugefügt haben, sieht die Ausgabe ähnlich der folgenden aus:

   ```bash
   sudo crm status
   
   3 nodes configured
   1 resource configured
   Online: [ SLES1 SLES2 SLES3]
   Full list of resources:   
   admin_addr     (ocf::heartbeat:IPaddr2):       Started node1
   ```

   >[!NOTE]
   >`admin_addr` ist die virtuelle IP-Clusterressource, die während der Installation des ersten Einzelknotencluster konfiguriert ist.

Überprüfen Sie nachdem alle Knoten hinzugefügt haben, ob Sie keine-Quorum-Richtlinie in den Optionen für die globale clusteraktion anpassen müssen. Dies ist besonders wichtig für Cluster mit zwei Knoten. Weitere Informationen finden Sie in Abschnitt 4.1.2 Option keine-Quorum-Richtlinie. 

## <a name="set-cluster-property-cluster-recheck-interval"></a>Legen Sie die Cluster-Cluster-erneute zugriffsprüfung während-Interval-Eigenschaft

`cluster-recheck-interval` Gibt an, das Abrufintervall auf Änderungen in der Ressourcenparameter, Einschränkungen oder andere Clusteroptionen an dem der Cluster überprüft. Wenn ein Replikat ausfällt, versucht der Cluster, das Replikat in einem Intervall neu zu starten, die gebunden wird, indem die `failure-timeout` Wert und die `cluster-recheck-interval` Wert. Z. B. wenn `failure-timeout` auf 60 Sekunden festgelegt ist und `cluster-recheck-interval` festgelegt ist auf 120 Sekunden, wird versucht, der Neustart in einem Intervall, das mehr als 60 Sekunden, jedoch weniger als 120 Sekunden ist. Es wird empfohlen, dass Sie die Fehler-Timeout 60er-Bereich und die Cluster-erneute zugriffsprüfung während--Intervall auf einen Wert, der größer als 60 Sekunden festlegen. Cluster-erneute zugriffsprüfung während-Intervall auf einen niedrigen Wert festlegen, wird nicht empfohlen.

Aktualisieren Sie den Eigenschaftswert an `2 minutes` ausführen:

```bash
crm configure property cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Wenn Sie bereits eine Ressource durch einen Pacemaker-Cluster verwaltet haben, beachten Sie, dass alle Verteilungen, die die neuesten verfügbaren Pacemaker Paket 1.1.18-11.el7 verwenden eine verhaltensänderung für den Start-Fehler-ist--Schwerwiegender-Einstellung, wenn Cluster stellen Sie vor der Wert ist "false". Diese Änderung wirkt sich auf die testfailover-Workflow. Wenn ein primäres Replikat ein Ausfall auftritt, wird der Cluster für ein Failover auf eines der sekundären Replikate verfügbar erwartet. Stattdessen sehen Benutzer, dass der Cluster immer wieder versucht, das fehlerhafte primäre Replikat zu starten. Wenn dieser primären (aufgrund von einem dauerhaften Ausfall) nicht online ist, ein Failover des Clusters nicht an ein anderes verfügbares sekundäres Replikat. Aufgrund dieser Änderung eine zuvor empfohlene Konfiguration festzulegende Start Fehler-ist-schwerwiegender ist nicht mehr gültig und die Einstellung muss auf den Standardwert zurückgesetzt werden `true`. Darüber hinaus muss die AG-Ressource aktualisiert werden, enthält die `failover-timeout` Eigenschaft. 
>
>Aktualisieren Sie den Eigenschaftswert an `true` ausführen:
>
>```bash
>crm configure property start-failure-is-fatal=true
>```
>
>Aktualisieren Sie Ihre vorhandenen Verfügbarkeitsgruppe Ressourceneigenschaft `failure-timeout` zu `60s` ausführen (ersetzen Sie `ag1` durch den Namen des Ihre Verfügbarkeitsgruppen-Ressource): 
>
>```bash
>crm configure edit ag1
># In the text editor, add `meta failure-timeout=60s` after any `param`s and before any `op`s
>```

Weitere Informationen zu den Eigenschaften der Pacemaker-Cluster, finden Sie unter [Konfigurieren von Clusterressourcen](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html).

## <a name="configure-fencing-stonith"></a>Konfigurieren von Umgrenzung (STONITH)
Pacemaker-Clusters Anbieter erfordern STONITH aktiviert werden und ein umgrenzungs-Gerät, das für einen unterstützten Cluster-Setup konfiguriert. Wenn der Clusterressourcen-Manager den Status eines Knotens oder einer Ressource auf einem Knoten nicht ermitteln kann, Umgrenzung dient zum Cluster erneut in einen bekannten Zustand zu bringen.

Ressource Ebene Umgrenzung hauptsächlich wird sichergestellt, dass es keine datenbeschädigung bei einem Ausfall durch Konfigurieren einer Ressource. Können Sie Ressourcen auf Umgrenzung, z. B. mit DRBD (Distributed repliziert Blockgerät), um den Datenträger auf einem Knoten, wie wenn veraltet zu markieren die kommunikationsverbindung ausfällt.

Ebene Umgrenzung Knoten wird sichergestellt, dass alle Ressourcen von ein Knoten nicht ausgeführt werden kann. Dies erfolgt durch das Zurücksetzen des Knotens, und die Implementierung dieser Pacemaker STONITH (das steht für "den anderen Knoten im Kopf dafür") aufgerufen. Pacemaker unterstützt eine Vielzahl von Geräten, z. B. eine unterbrechungsfreie bereitstellen oder die Verwaltung Netzwerkschnittstellenkarten für Server für das umgrenzen.

Weitere Informationen finden Sie unter [Pacemaker-Cluster von Grund auf Neu](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html), [Umgrenzung und Stonith](http://clusterlabs.org/doc/crm_fencing.html) und [SUSE-HA-Dokumentation: Umgrenzung und STONITH](https://www.suse.com/documentation/sle_ha/book_sleha/data/cha_ha_fencing.html).

STONITH wird zum Zeitpunkt der Initialisierung deaktiviert, wenn keine Konfiguration erkannt wird. Es kann mit dem folgenden Befehl später aktiviert werden:

```bash
sudo crm configure property stonith-enabled=true
```
  
>[!IMPORTANT]
>Deaktivieren die STONITH ist nur für Testzwecke verwenden. Wenn Sie Pacemaker in einer produktionsumgebung verwenden möchten, sollten Sie eine STONITH-Implementierung planen, je nach Umgebung und behalten sie die Einstellung aktiviert. SUSE stellt keine Umgrenzung-Agents für alle Cloud-Umgebungen (einschließlich Azure) oder Hyper-V bereit. Nichts enthält, bietet der Hersteller der Cluster keine Unterstützung für Produktionscluster in diesen Umgebungen ausgeführt. Wir arbeiten an einer Lösung für diese Lücke zu schließen, die in zukünftigen Versionen zur Verfügung stehen.


## <a name="configure-the-cluster-resources-for-sql-server"></a>Konfigurieren Sie die Clusterressourcen für SQL Server

Finden Sie unter [SLES-Verwaltung-Guid](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config)

## <a name="enable-pacemaker"></a>Aktivieren von Pacemaker

Aktivieren Sie Pacemaker, sodass er automatisch gestartet.

Führen Sie den folgenden Befehl auf jedem Knoten im Cluster.

```bash
systemctl enable pacemaker
```

### <a name="create-availability-group-resource"></a>Verfügbarkeitsgruppen-Ressource erstellen

Der folgende Befehl erstellt und konfiguriert die verfügbarkeitsgruppenressource für drei Replikate der verfügbarkeitsgruppe [ag1]. Das Überwachen von Vorgängen und Timeouts müssen explizit in SLES angegeben werden, beruht auf der Tatsache, dass Timeouts hoher arbeitsauslastung abhängig werden und müssen sorgfältig für jede Bereitstellung angepasst werden.
Führen Sie den Befehl auf einem der Knoten im Cluster aus:

1. Führen Sie `crm configure` auf die Crm-Eingabeaufforderung öffnen:

   ```bash
   sudo crm configure 
   ```

1. Führen Sie in der Crm-Eingabeaufforderung den folgenden Befehl so konfigurieren Sie die Ressourceneigenschaften aus.

   ```bash
   primitive ag_cluster \
      ocf:mssql:ag \
      params ag_name="ag1" \
      meta failure-timeout=60s \
      op start timeout=60s \
      op stop timeout=60s \
      op promote timeout=60s \
      op demote timeout=10s \
      op monitor timeout=60s interval=10s \
      op monitor timeout=60s interval=11s role="Master" \
      op monitor timeout=60s interval=12s role="Slave" \
      op notify timeout=60s
   ms ms-ag_cluster ag_cluster \
      meta master-max="1" master-node-max="1" clone-max="3" \
     clone-node-max="1" notify="true" \
   commit
      ```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

### <a name="create-virtual-ip-resource"></a>Erstellen Sie virtuelle IP-Ressource

Wenn Sie nicht die virtuelle IP-Ressource erstellt haben, bei der Ausführung `ha-cluster-init` Erstellen dieser Ressource können Sie jetzt. Der folgende Befehl erstellt eine virtuelle IP-Ressource. Ersetzen Sie dies `<**0.0.0.0**>` mit eine verfügbare Adresse aus dem Netzwerk und `<**24**>` mit der Anzahl von Bits in der CIDR-Subnetzmaske. Führen Sie auf einem Knoten.

```bash
crm configure \
primitive admin_addr \
   ocf:heartbeat:IPaddr2 \
   params ip=<**0.0.0.0**> \
      cidr_netmask=<**24**>
```

### <a name="add-colocation-constraint"></a>Zusammenstellung-Einschränkung hinzufügen
Fast jeder Entscheidung im eines Pacemaker-Clusters, z. B. auswählen, in dem eine Ressource ausgeführt werden soll, erfolgt durch Vergleichen der Ergebnisse. Pro Ressource Bewertungen berechnet werden, und der Clusterressourcen-Manager wählt den Knoten mit der höchsten Bewertung für eine bestimmte Ressource. (Wenn ein Knoten ein negatives Ergebnis für eine Ressource verfügt, kann nicht die Ressourcen auf diesem Knoten ausgeführt.) Wir können die Entscheidungen des Clusters mit Einschränkungen ändern. Eine Bewertung eine Beschränkung vorliegt. Wenn eine Einschränkung auf einen Wert kleiner als UNENDLICH ist, ist es nur eine Empfehlung aus. Eine Bewertung von UNENDLICH bedeutet, dass es sich um ein muss ist. Wir möchten, um sicherzustellen, dass primäre der verfügbarkeitsgruppe und virtuellen IP-Ressource werden auf demselben Host, damit wir eine Zusammenstellung-Einschränkung mit einer Bewertung von UNENDLICH definieren. 

Um mithilfe der Zusammenstellung-Einschränkung für die virtuelle IP-Adresse zur Ausführung auf demselben Knoten wie der Masterknoten festzulegen, führen Sie den folgenden Befehl auf einem Knoten ein:

```bash
crm configure
colocation vip_on_master inf: \
    admin_addr ms-ag_cluster:Master
commit
```

### <a name="add-ordering-constraint"></a>Sortieren-Einschränkung hinzufügen
Die Zusammenstellung-Einschränkung verfügt über eine implizite Sortierung Einschränkung. Die virtuelle IP-Adressressource verschoben wird, bevor sie die verfügbarkeitsgruppenressource verschoben. Standardmäßig ist die Abfolge der Ereignisse: 

1. Benutzerressource für Probleme, mit dem Availability Group-Master von Knoten1 auf Knoten2 migrieren.
2. Die virtuelle IP-Adressressource, die auf Knoten 1 beendet werden.
3. Die virtuelle IP-Adressressource, die auf Knoten 2 wird gestartet. An diesem Punkt die IP-Adresse temporär verweist auf Knoten 2 während Knoten 2 immer noch ein vor dem Failover ist sekundären. 
4. Der Verfügbarkeit auf Knoten 1 Master wird herabgestuft, um sekundärgerät.
5. Der Availability-Gruppe untergeordnete Knoten auf Knoten 2 höher gestuft wird zum Master. 

Um zu verhindern, dass die IP-Adresse vorübergehend auf den Knoten mit der vor dem Failover sekundären Datenbank verweist, fügen Sie eine Sortierung Einschränkung hinzu. Um eine Sortierung Einschränkung hinzuzufügen, führen Sie den folgenden Befehl auf einem Knoten ein: 

```bash
crm crm configure \
   order ag_first inf: ms-ag_cluster:promote admin_addr:start
```


>[!IMPORTANT]
>Nachdem Sie den Cluster konfigurieren, und fügen Sie als Clusterressource der verfügbarkeitsgruppe hinzu, können Sie Transact-SQL keine für das Failover der verfügbarkeitsgruppenressourcen. Ressourcen für SQL Server-Clusters unter Linux sind nicht so eng mit dem Betriebssystem verknüpft, wie sie auf einem Windows Server Failover Cluster (WSFC) sind. SQL Server-Dienst ist nicht über das Vorhandensein des Clusters. Alle Orchestrierung erfolgt über die Verwaltungstools. Verwenden Sie SLES `crm`. 

Ausführen des manuellen Failovers der verfügbarkeitsgruppe mit `crm`. Initiieren Sie nicht Failover mit Transact-SQL. Weitere Informationen finden Sie unter [Failover](sql-server-linux-availability-group-failover-ha.md#failover).


Weitere Informationen finden Sie in den folgenden Themen:
- [Verwalten von Clusterressourcen](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm).   
- [HA Konzepte](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.concepts)
- [Pacemaker-Kurzübersicht](https://github.com/ClusterLabs/pacemaker/blob/master/doc/pcs-crmsh-quick-ref.md) 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>Nächste Schritte

[Betreiben von HA-verfügbarkeitsgruppe](sql-server-linux-availability-group-failover-ha.md)
