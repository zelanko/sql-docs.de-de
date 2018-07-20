---
title: Ubuntu-Cluster für SQL Server-Verfügbarkeitsgruppe konfigurieren | Microsoft-Dokumentation
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
ms.assetid: dd0d6fb9-df0a-41b9-9f22-9b558b2b2233
ms.openlocfilehash: 48a6ed32b8b0898d44c28a425064ef46fc1e1561
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083132"
---
# <a name="configure-ubuntu-cluster-and-availability-group-resource"></a>Konfigurieren von Ubuntu-Cluster und Availability Group-Ressource

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Dokument wird erläutert, wie erstellen einen Cluster mit drei Knoten unter Ubuntu, und fügen eine zuvor erstellte verfügbarkeitsgruppe als Ressource im Cluster. Für hohe Verfügbarkeit, eine verfügbarkeitsgruppe für Linux erfordert drei Knoten – Siehe [hohe Verfügbarkeit und Datenschutz für verfügbarkeitsgruppenkonfigurationen](sql-server-linux-availability-group-ha.md).

> [!NOTE] 
> SQL Server Integration mit Pacemaker unter Linux ist an diesem Punkt nicht als gekoppelt als mit WSFC unter Windows. Aus innerhalb von SQL, es ist keine Kenntnisse über das Vorhandensein des Clusters alle Orchestrierung befindet sich außerhalb im und der Dienst wird als eigenständige Instanz von Pacemaker gesteuert. Darüber hinaus Name des virtuellen Netzwerks ist spezifisch für die WSFC, es gibt keine Entsprechung desselben in Pacemaker. Always On-dynamische Verwaltungssichten, die Clusterinformationen Abfragen werden leere Zeilen zurückgeben. Sie können einen Listener für die Verwendung für transparente erneute Verbindung nach einem Failover weiterhin erstellen, aber müssen Sie manuell den verfügbarkeitsgruppenlistener-Namen in der DNS-Server registrieren, mit der IP-Adresse verwendet, um die virtuelle IP-Ressource (wie in den folgenden Abschnitten erläutert wird) zu erstellen.

Die folgenden Abschnitte führen die Schritte zum Einrichten einer Lösung mit Failovercluster. 

## <a name="roadmap"></a>Roadmap für die

Die Schritte zum Erstellen einer verfügbarkeitsgruppe auf Linux-Servern für hochverfügbarkeit unterscheiden sich von den Schritten in einem Windows Server-Failovercluster. Die folgende Liste beschreibt die allgemeinen Schritte: 

1. [Konfigurieren von SQL Server auf den Clusterknoten](sql-server-linux-setup.md).

2. [Erstellen der verfügbarkeitsgruppe](sql-server-linux-availability-group-configure-ha.md). 

3. Konfigurieren Sie eine Clusterressourcen-Manager, z.B. Pacemaker. Diese Anweisungen sind in diesem Dokument.
   
   Die Möglichkeit, einen Cluster-Ressourcen-Manager zu konfigurieren, hängt von der jeweilige Linux-Distribution. 

   >[!IMPORTANT]
   >Produktionsumgebungen sind erforderlich, einen umgrenzungs-Agent, wie STONITH für hohe Verfügbarkeit. Die Demos in dieser Dokumentation verwenden keine Umgrenzung-Agents. Die Demos sind für Tests und Überprüfung nur auf. 
   
   >Ein Linux-Cluster verwendet Umgrenzung, um den Cluster in einen bekannten Zustand zurückzugeben. Die Möglichkeit zum Konfigurieren der Umgrenzung hängt davon ab, die Verteilung und der Umgebung. Zu diesem Zeitpunkt ist die Umgrenzung nicht in eine Cloud-Umgebungen verfügbar. Finden Sie unter [Supportrichtlinien für RHEL High Availability Cluster - Virtualisierungsplattformen](https://access.redhat.com/articles/29440) für Weitere Informationen.

5.  [Fügen Sie die verfügbarkeitsgruppe als Ressource im Cluster](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource). 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installieren Sie und konfigurieren Sie auf jedem Clusterknoten die Pacemaker

1. Öffnen Sie die Firewallports auf allen Knoten. Öffnen Sie den Port für die Pacemaker-Dienst hohe Verfügbarkeit, SQL Server-Instanz und den Endpunkt der verfügbarkeitsgruppe. Der TCP-Standardport für SQL Server ausgeführt wird, ist 1433.  

   ```bash
   sudo ufw allow 2224/tcp
   sudo ufw allow 3121/tcp
   sudo ufw allow 21064/tcp
   sudo ufw allow 5405/udp
        
   sudo ufw allow 1433/tcp # Replace with TDS endpoint
   sudo ufw allow 5022/tcp # Replace with DATA_MIRRORING endpoint
        
   sudo ufw reload
   ```
   
   Alternativ können Sie nur die Firewall deaktivieren:
        
   ```bash
   sudo ufw disable
   ```

1. Installieren Sie Pacemaker-Pakete. Führen Sie auf allen Knoten die folgenden Befehle aus:

   ```bash
   sudo apt-get install pacemaker pcs fence-agents resource-agents
   ```

2. Legen Sie das Kennwort für den Standardbenutzer fest, der beim Installieren von Pacemaker und Corosync-Paketen erstellt wird. Verwenden Sie auf allen Knoten dasselbe Kennwort. 

   ```bash
   sudo passwd hacluster
   ```

## <a name="enable-and-start-pcsd-service-and-pacemaker"></a>Aktivieren Sie und starten Sie Pcsd-Dienst und Pacemaker

Der folgende Befehl aktiviert und beginnt Pcsd-Dienst und Pacemaker. Führen Sie auf allen Knoten. Dadurch werden die Knoten des Clusters nach dem Neustart erneut beitreten. 

```bash
sudo systemctl enable pcsd
sudo systemctl start pcsd
sudo systemctl enable pacemaker
```
>[!NOTE]
>Enable Pacemaker Befehl möglicherweise mit Fehler abgeschlossen "Pacemaker Standard-Start enthält keine Ausführungsstufe, wird abgebrochen." Dieser harmlos ist, kann die Clusterkonfiguration fortgesetzt. 

## <a name="create-the-cluster"></a>Erstellen des Clusters

1. Entfernen Sie alle vorhandenen Clusterkonfiguration, von allen Knoten. 

   Laufende "Sudo apt-Get Install Pcs" Pacemaker und Corosync-Pcs zur selben Zeit installiert und startet die Ausführung alle 3 der Dienste.  Starten Corosync eine Vorlage generiert "/ etc/cluster/corosync.conf' Datei.  Damit die nächsten Schritte erfolgreich ausgeführt werden, kann diese Datei nicht vorhanden sein – also die problemumgehung besteht, beim Beenden des Pacemaker darin / Corosync und Löschen von "/ etc/cluster/corosync.conf", und klicken Sie dann weitere Schritte erfolgreich abgeschlossen. "Pcs Cluster destroy" führt die gleiche Aufgabe aus, und Sie können es verwenden, wie eine Zeitschritt ersten Cluster-Setup.
   
   Der folgende Befehl entfernt alle vorhandenen Konfigurationsdateien für den Cluster und alle Clusterdienste beendet. Dies zerstört dauerhaft den Cluster. Führen sie als ersten Schritt in einer präproduktionsumgebung. Beachten Sie, dass "Pcs Cluster destroy" deaktiviert die Pacemaker-Dienst und muss erneut aktiviert werden. Führen Sie den folgenden Befehl auf allen Knoten aus.
   
   >[!WARNING]
   >Der Befehl löscht alle vorhandenen Clusterressourcen.

   ```bash
   sudo pcs cluster destroy 
   sudo systemctl enable pacemaker
   ```

1. Erstellen des Clusters an. 

   >[!WARNING]
   >Aufgrund eines bekannten Problems, die der clustering-Anbieter ist untersuchen, starten gibt der Cluster ("Pcs Cluster Start") folgende Fehlermeldung zurück. Dies ist, da die Protokolldatei in /etc/corosync/corosync.conf die wird erstellt, wenn der Cluster-Setup-Befehl ausgeführt wird, ist falsch konfiguriert. Um dieses Problem zu umgehen, ändern Sie die Protokolldatei: /var/log/corosync/corosync.log. Alternativ können Sie die /var/log/cluster/corosync.log-Datei erstellen.
 
   ```Error
   Job for corosync.service failed because the control process exited with error code. 
   See "systemctl status corosync.service" and "journalctl -xe" for details.
   ```
  
Der folgende Befehl erstellt einen Cluster mit drei Knoten. Bevor Sie das Skript ausführen, ersetzen Sie die Werte zwischen `< ... >`. Führen Sie den folgenden Befehl auf dem primären Knoten. 

   ```bash
   sudo pcs cluster auth <node1> <node2> <node3> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <node1> <node2…> <node3>
   sudo pcs cluster start --all
   sudo pcs cluster enable --all
   ```
   
   >[!NOTE]
   >Wenn Sie vorher einen Cluster auf denselben Knoten konfiguriert haben, müssen Sie die Option „--force“ verwenden, wenn Sie „pcs cluster setup“ ausführen. Beachten Sie, dass dies der Ausführung von „pcs cluster destroy“ entspricht, und der Peacemaker-Dienst muss erneut mithilfe von „sudo systemctl enable pacemaker“ aktiviert werden.


## <a name="configure-fencing-stonith"></a>Konfigurieren von Umgrenzung (STONITH)

Pacemaker-Clusters Anbieter erfordern STONITH aktiviert werden und ein umgrenzungs-Gerät, das für einen unterstützten Cluster-Setup konfiguriert. Wenn der Clusterressourcen-Manager den Status eines Knotens oder einer Ressource auf einem Knoten nicht ermitteln kann, Umgrenzung dient zum Cluster erneut in einen bekannten Zustand zu bringen. Ressource Ebene Umgrenzung hauptsächlich wird sichergestellt, dass es keine datenbeschädigung bei einem Ausfall durch Konfigurieren einer Ressource. Können Sie Ressourcen auf Umgrenzung, z. B. mit DRBD (Distributed repliziert Blockgerät), um den Datenträger auf einem Knoten, wie wenn veraltet zu markieren die kommunikationsverbindung ausfällt. Ebene Umgrenzung Knoten wird sichergestellt, dass alle Ressourcen von ein Knoten nicht ausgeführt werden kann. Dies erfolgt durch das Zurücksetzen des Knotens, und die Implementierung dieser Pacemaker STONITH (das steht für "den anderen Knoten im Kopf dafür") aufgerufen. Pacemaker unterstützt eine Vielzahl von umgrenzungs-Geräte, z. B. eine unterbrechungsfreie Stromversorgung oder Management Netzwerkschnittstellenkarten für Server. Weitere Informationen finden Sie unter [Pacemaker-Cluster von Grund auf Neu](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html) und [Umgrenzung und Stonith](http://clusterlabs.org/doc/crm_fencing.html) 

Da die Ebene des Knotens für das umgrenzen der Konfiguration in Ihrer Umgebung stark abhängig ist, deaktivieren wir sie für dieses Tutorial (es kann zu einem späteren Zeitpunkt konfiguriert werden). Führen Sie das folgende Skript auf dem primären Knoten aus: 

```bash
sudo pcs property set stonith-enabled=false
```

>[!IMPORTANT]
>Deaktivieren die STONITH ist nur für Testzwecke verwenden. Wenn Sie Pacemaker in einer produktionsumgebung verwenden möchten, sollten Sie eine STONITH-Implementierung planen, je nach Umgebung und behalten sie die Einstellung aktiviert. Beachten Sie, dass an diesem Punkt keine Umgrenzung-Agents für alle Cloud-Umgebungen (einschließlich Azure) oder Hyper-V. Nichts enthält, bietet der Hersteller der Cluster keine Unterstützung für Produktionscluster in diesen Umgebungen ausgeführt. 

## <a name="set-cluster-property-cluster-recheck-interval"></a>Legen Sie die Cluster-Cluster-erneute zugriffsprüfung während-Interval-Eigenschaft

`cluster-recheck-interval` Gibt an, das Abrufintervall auf Änderungen in der Ressourcenparameter, Einschränkungen oder andere Clusteroptionen an dem der Cluster überprüft. Wenn ein Replikat ausfällt, versucht der Cluster, das Replikat in einem Intervall neu zu starten, die gebunden wird, indem die `failure-timeout` Wert und die `cluster-recheck-interval` Wert. Z. B. wenn `failure-timeout` auf 60 Sekunden festgelegt ist und `cluster-recheck-interval` festgelegt ist auf 120 Sekunden, wird versucht, der Neustart in einem Intervall, das mehr als 60 Sekunden, jedoch weniger als 120 Sekunden ist. Es wird empfohlen, dass Sie die Fehler-Timeout 60er-Bereich und die Cluster-erneute zugriffsprüfung während--Intervall auf einen Wert, der größer als 60 Sekunden festlegen. Cluster-erneute zugriffsprüfung während-Intervall auf einen niedrigen Wert festlegen, wird nicht empfohlen.

Aktualisieren Sie den Eigenschaftswert an `2 minutes` ausführen:

```bash
sudo pcs property set cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Wenn Sie bereits eine Ressource durch einen Pacemaker-Cluster verwaltet haben, beachten Sie, dass alle Verteilungen, die die neuesten verfügbaren Pacemaker Paket 1.1.18-11.el7 verwenden eine verhaltensänderung für den Start-Fehler-ist--Schwerwiegender-Einstellung, wenn Cluster stellen Sie vor der Wert ist "false". Diese Änderung wirkt sich auf die testfailover-Workflow. Wenn ein primäres Replikat ein Ausfall auftritt, wird der Cluster für ein Failover auf eines der sekundären Replikate verfügbar erwartet. Stattdessen sehen Benutzer, dass der Cluster immer wieder versucht, das fehlerhafte primäre Replikat zu starten. Wenn dieser primären (aufgrund von einem dauerhaften Ausfall) nicht online ist, ein Failover des Clusters nicht an ein anderes verfügbares sekundäres Replikat. Aufgrund dieser Änderung eine zuvor empfohlene Konfiguration festzulegende Start Fehler-ist-schwerwiegender ist nicht mehr gültig und die Einstellung muss auf den Standardwert zurückgesetzt werden `true`. Darüber hinaus muss die AG-Ressource aktualisiert werden, enthält die `failover-timeout` Eigenschaft. 
>
>Aktualisieren Sie den Eigenschaftswert an `true` ausführen:
>
>```bash
>sudo pcs property set start-failure-is-fatal=true
>```
>
>Aktualisieren Sie Ihre vorhandenen Verfügbarkeitsgruppe Ressourceneigenschaft `failure-timeout` zu `60s` ausführen (ersetzen Sie `ag1` durch den Namen des Ihre Verfügbarkeitsgruppen-Ressource):
>
>```bash
>pcs resource update ag1 meta failure-timeout=60s
>```

## <a name="install-sql-server-resource-agent-for-integration-with-pacemaker"></a>Installieren von SQL Server-ressourcenagent für die Integration mit Pacemaker

Führen Sie die folgenden Befehle auf allen Knoten aus. 

```bash
sudo apt-get install mssql-server-ha
```

## <a name="create-a-sql-server-login-for-pacemaker"></a>Erstellen Sie eine SQL Server-Anmeldung für Pacemaker

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>Verfügbarkeitsgruppen-Ressource erstellen

Verwenden Sie zum Erstellen der verfügbarkeitsgruppenressource `pcs resource create` -Befehl aus, und legen Sie die Ressourceneigenschaften. Folgenden Befehl erstellt eine `ocf:mssql:ag` Typressource für die verfügbarkeitsgruppe mit dem Namen, Master/Slave `ag1`. 

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 meta failure-timeout=30s --master meta notify=true

```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

## <a name="create-virtual-ip-resource"></a>Erstellen Sie virtuelle IP-Ressource

Um die virtuelle IP-Adressressource zu erstellen, führen Sie den folgenden Befehl auf einem Knoten ein. Verwenden Sie eine verfügbare statische IP-Adresse aus dem Netzwerk. Bevor Sie das Skript ausführen, ersetzen Sie die Werte zwischen `< ... >` mit einer gültigen IP-Adresse.

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

Es gibt keinen virtuellen Server-Namen Pacemaker entspricht. Verwenden Sie eine Verbindungszeichenfolge, die auf einem Zeichenfolgennamen für den Server verweist und nicht die IP-Adresse, die Adresse der IP-Ressource und den Namen des gewünschten virtuellen Servers in DNS registrieren. Registrieren Sie für DR-Konfigurationen den gewünschten virtuellen Servernamen und die IP-Adresse mit dem DNS-Servern auf primären und DR-Standort aus.

## <a name="add-colocation-constraint"></a>Zusammenstellung-Einschränkung hinzufügen

Fast jeder Entscheidung im eines Pacemaker-Clusters, z. B. auswählen, in dem eine Ressource ausgeführt werden soll, erfolgt durch Vergleichen der Ergebnisse. Pro Ressource Bewertungen berechnet werden, und der Clusterressourcen-Manager wählt den Knoten mit der höchsten Bewertung für eine bestimmte Ressource. (Wenn ein Knoten ein negatives Ergebnis für eine Ressource verfügt, kann nicht die Ressourcen auf diesem Knoten ausgeführt.) Verwenden Sie Einschränkungen, um die Entscheidungen des Clusters zu konfigurieren. Eine Bewertung eine Beschränkung vorliegt. Wenn eine Einschränkung auf einen Wert kleiner als UNENDLICH ist, ist es nur eine Empfehlung aus. Eine Bewertung von UNENDLICH bedeutet, dass es erforderlich ist. Um sicherzustellen, dass das primäre Replikat und die virtuelle IP-Ressource auf dem gleichen Host sind, definieren Sie eine Zusammenstellung-Einschränkung mit einer Bewertung von UNENDLICH. Um die Zusammenstellung Einschränkung hinzuzufügen, führen Sie den folgenden Befehl auf einem Knoten ein. 

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>Sortieren-Einschränkung hinzufügen

Die Zusammenstellung-Einschränkung verfügt über eine implizite Sortierung Einschränkung. Die virtuelle IP-Adressressource verschoben wird, bevor sie die verfügbarkeitsgruppenressource verschoben. Standardmäßig ist die Abfolge der Ereignisse:

1. Benutzerproblemen `pcs resource move` auf dem primären verfügbarkeitsgruppenobjekt von Knoten1 auf Knoten2.
1. Die virtuelle IP-Adressressource, die auf node1 beendet werden.
1. Die virtuelle IP-Adressressource startet auf Node2 her.

   >[!NOTE]
   >An diesem Punkt die IP-Adresse vorübergehend Punkte auf node2 während node2 immer noch ein vor dem Failover ist sekundären. 
   
1. Die verfügbarkeitsgruppe auf node1 primären zum sekundären Standort tiefer gestuft wird.
1. Die sekundären Datenbank auf node2 verfügbarkeitsgruppe wird zum primären Replikat höher gestuft. 

Um zu verhindern, dass die IP-Adresse vorübergehend auf den Knoten mit der vor dem Failover sekundären Datenbank verweist, fügen Sie eine Sortierung Einschränkung hinzu. 

Um eine Sortierung Einschränkung hinzuzufügen, führen Sie den folgenden Befehl auf einem Knoten ein:

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>Nachdem Sie den Cluster konfigurieren, und fügen Sie als Clusterressource der verfügbarkeitsgruppe hinzu, können Sie Transact-SQL keine für das Failover der verfügbarkeitsgruppenressourcen. Ressourcen für SQL Server-Clusters unter Linux sind nicht so eng mit dem Betriebssystem verknüpft, wie sie auf einem Windows Server Failover Cluster (WSFC) sind. SQL Server-Dienst ist nicht über das Vorhandensein des Clusters. Alle Orchestrierung erfolgt über die Verwaltungstools. In RHEL oder Ubuntu verwenden `pcs`. 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>Nächste Schritte

[Betreiben von HA-verfügbarkeitsgruppe](sql-server-linux-availability-group-failover-ha.md)

