---
title: Arbeiten Sie freigegebenen Cluster Red Hat Enterprise Linux für SQL Server | Microsoft-Dokumentation
description: Implementieren Sie hohen Verfügbarkeit durch Cluster mit freigegebenen Datenträgern Red Hat Enterprise Linux für SQL Server konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 075ab7d8-8b68-43f3-9303-bbdf00b54db1
ms.openlocfilehash: c2faf04abf313f318adaf8971e986de5d80bff2f
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086592"
---
# <a name="operate-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Betreiben Sie Cluster mit freigegebenen Datenträgern Red Hat Enterprise Linux für SQL Server

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Dokument wird beschrieben, wie Sie die folgenden Aufgaben für SQL Server auf einem Failovercluster für freigegebene Datenträger mit Red Hat Enterprise Linux.

- Ein manuelles Failover des Clusters
- Überwachen eines Failoverclusters SQL Server-Dienst
- Hinzufügen eines Clusterknotens
- Entfernen eines Clusterknotens
- Ändern Sie den SQL Server-Ressourcen, die Überwachung der Häufigkeit

## <a name="architecture-description"></a>Beschreibung der Architektur

Die clustering-Ebene basiert auf Red Hat Enterprise Linux (RHEL) [HA-Add-On](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) baut auf [Pacemaker](http://clusterlabs.org/). Corosync und Pacemaker Clusterkommunikation und ressourcenverwaltung zu koordinieren. SQL Server-Instanz ist auf einem Knoten oder die andere aktiv.

Das folgende Diagramm veranschaulicht die Komponenten in einem Linux-Cluster mit SQL Server. 

![Red Hat Enterprise Linux 7 freigegebene Datenträgercluster für SQL](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

Weitere Informationen zu Clusterkonfiguration, Optionen für Agents und Management finden Sie unter [RHEL-Referenzdokumentation](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).

## <a name = "failManual"></a>Failovercluster manuell

Die `resource move` Befehl erstellt eine Einschränkung, die die Ressource auf dem Zielknoten zu erzwingen.  Nach dem Ausführen der `move` Befehl, eine Ressource ausgeführt, `clear` wird die Einschränkung entfernt, deshalb es möglich ist, verschieben Sie die Ressource erneut, oder die Ressource automatisch ein Failover ausgeführt haben. 

```bash
sudo pcs resource move <sqlResourceName> <targetNodeName>  
sudo pcs resource clear <sqlResourceName> 
```

Im folgenden Beispiel wird die **Mssqlha** Ressource, um einen Knoten namens **sqlfcivm2**, und klicken Sie dann die Einschränkung entfernt, sodass die Ressource später auf einen anderen Knoten verschieben kann.  

```bash
sudo pcs resource move mssqlha sqlfcivm2 
sudo pcs resource clear mssqlha 
```

## <a name="monitor-a-failover-cluster-sql-server-service"></a>Überwachen eines Failoverclusters SQL Server-Dienst

Zeigen Sie den Status des aktuellen Clusters an:

```bash
sudo pcs status  
```

Live Status des Clusters und Ressourcen anzeigen:

```bash
sudo crm_mon 
```

Anzeigen der Ressourcen-Agent-Protokolle an `/var/log/cluster/corosync.log`

## <a name="add-a-node-to-a-cluster"></a>Hinzufügen eines Knotens zu einem cluster

1. Überprüfen Sie die IP-Adresse für jeden Knoten. Das folgende Skript zeigt die IP-Adresse Ihres aktuellen Knotens. 

   ```bash
   ip addr show
   ```

3. Der neue Knoten benötigt einen eindeutigen Namen, die 15 Zeichen lang ist oder weniger. In Red Hat Linux standardmäßig den Namen des Computers ist `localhost.localdomain`. Dieser Standardname möglicherweise nicht eindeutig sein und ist zu lang. Legen Sie den Namen des Computers den neuen Knoten. Den Namen des Computers festlegen, indem Sie es `/etc/hosts`. Mithilfe des folgenden Skripts können Sie `/etc/hosts` mit `vi` bearbeiten. 

   ```bash
   sudo vi /etc/hosts
   ```

   Das folgende Beispiel zeigt `/etc/hosts` mit Ergänzungen für drei Knoten, die mit dem Namen `sqlfcivm1`, `sqlfcivm2`, und`sqlfcivm3`.

   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1         localhost localhost6 localhost6.localdomain6
   10.128.18.128 fcivm1
   10.128.16.77 fcivm2
   10.128.14.26 fcivm3
    ```
    
   Die Datei sollte auf allen Knoten identisch sein. 

1. Beenden Sie den SQL Server-Dienst auf dem neuen Knoten an.

1. Führen Sie die Anweisungen, um das Verzeichnis der Datenbankdatei auf den freigegebenen Speicherort bereitstellen:

   Aus der NFS-Server installieren `nfs-utils`

   ```bash
   sudo yum -y install nfs-utils 
   ``` 

   Öffnen Sie die Firewall auf Clients und Server für NFS 

   ```bash
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

   Bearbeiten von/etc/fstab-Datei, um den Mount-Befehl enthalten: 

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr
   ```

   Führen Sie `mount -a` für die Änderungen wirksam werden.
   
1. Erstellen Sie eine Datei zum Speichern von SQL Server-Benutzername und Kennwort für die Pacemaker-Anmeldung, auf dem neuen Knoten. Der folgende Code erstellt und füllt diese Tabelle:

   ```bash
   sudo touch /var/opt/mssql/passwd
   sudo echo "<loginName>" >> /var/opt/mssql/secrets/passwd
   sudo echo "<loginPassword>" >> /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/passwd
   sudo chmod 600 /var/opt/mssql/passwd
   ```

3. Öffnen Sie auf dem neuen Knoten die Pacemaker-Firewallports. Führen Sie zum Öffnen dieser Ports mit `firewalld` folgenden Befehl aus:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > [!NOTE]
   > Wenn Sie eine andere Firewall verwenden, in die keine Konfiguration mit hoher Verfügbarkeit integriert ist, müssen die folgenden Ports geöffnet werden, damit Pacemaker mit anderen Knoten im Cluster kommunizieren kann:
   >
   > * TCP: Ports 2224, 3121, 21064
   > * UDP: Port 5405

1. Installieren Sie Pacemaker-Pakete auf dem neuen Knoten an.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```
 
2. Legen Sie das Kennwort für den Standardbenutzer fest, der beim Installieren von Pacemaker und Corosync-Paketen erstellt wird. Verwenden Sie dasselbe Kennwort wie die vorhandenen Knoten. 

   ```bash
   sudo passwd hacluster
   ```
 
3. Aktivieren und starten Sie den `pcsd`-Dienst und Pacemaker. Dadurch wird den neuen Knoten des Clusters nach dem Neustart erneut beitreten. Führen Sie den folgenden Befehl auf dem neuen Knoten an.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Installieren Sie den FCI-Ressourcenagent für SQL Server. Führen Sie die folgenden Befehle auf dem neuen Knoten an. 

   ```bash
   sudo yum install mssql-server-ha
   ```

1. Klicken Sie auf einen vorhandenen Knoten aus dem Cluster authentifizieren Sie den neuen Knoten, und es soll dem Cluster hinzugefügt:

    ```bash
    sudo pcs    cluster auth <nodeName3> -u hacluster 
    sudo pcs    cluster node add <nodeName3> 
    ```

    Das folgende Beispiel fügt einen Knoten namens **vm3** mit dem Cluster.

    ```bash
    sudo pcs    cluster auth  
    sudo pcs    cluster start 
    ```

## <a name="remove-nodes-from-a-cluster"></a>Entfernen von Knoten aus einem cluster

Zum Entfernen eines Knotens aus einem Cluster den folgenden Befehl ausführen:

```bash
sudo pcs    cluster node remove <nodeName>  
```

## <a name="change-the-frequency-of-sqlservr-resource-monitoring-interval"></a>Ändern Sie die Häufigkeit der Überwachungszeitraum Sqlservr-Ressource

```bash
sudo pcs    resource op monitor interval=<interval>s <sqlResourceName> 
```

Im folgenden Beispiel wird das Überwachungsintervall auf 2 Sekunden für die Mssql-Ressource:

```bash
sudo pcs    resource op monitor interval=2s mssqlha 
```
## <a name="troubleshoot-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Problembehandlung für Cluster mit freigegebenen Datenträgern Red Hat Enterprise Linux für SQL Server

Bei der Problembehandlung des Clusters kann es hilfreich sein, um zu verstehen, wie die drei Daemons zusammenarbeiten, um Clusterressourcen zu verwalten. 

| Daemon | Description 
| ----- | -----
| Corosync | Bietet Quorum-Mitgliedschaft und messaging zwischen Clusterknoten.
| Pacemaker | Befindet sich auf Corosync und stellt die Zustandsautomaten für Ressourcen bereit. 
| PCSD | Verwaltet sowohl Pacemaker und Corosync über die `pcs` Tools

PCSD muss ausgeführt werden, um verwenden `pcs` Tools. 

### <a name="current-cluster-status"></a>Aktuellen Status des Clusters 

`sudo pcs status` grundlegende Informationen zu den Cluster, Quorum, Knoten, Ressourcen und Daemon-Status für jeden Knoten zurückgegeben. 

Ein Beispiel für eine fehlerfreie Pacemaker-Quorum-Ausgabe wäre:

```
Cluster name: MyAppSQL 
Last updated: Wed Oct 31 12:00:00 2016  Last change: Wed Oct 31 11:00:00 2016 by root via crm_resource on sqlvmnode1 
Stack: corosync 
Current DC: sqlvmnode1  (version 1.1.13-10.el7_2.4-44eb2dd) - partition with quorum 
3 nodes and 1 resource configured 

Online: [ sqlvmnode1 sqlvmnode2 sqlvmnode3] 

Full list of resources: 

mssqlha (ocf::sql:fci): Started sqlvmnode1 

PCSD Status: 
sqlvmnode1: Online 
sqlvmnode2: Online 
sqlvmnode3: Online 

Daemon Status: 
corosync: active/disabled 
pacemaker: active/enabled 
```

Im Beispiel `partition with quorum` bedeutet, dass ein mehrheitsquorum von Knoten online ist. Wenn der Cluster ein mehrheitsquorum von Knoten, verliert `pcs status` zurück `partition WITHOUT quorum` und alle Ressourcen werden beendet. 

`online: [sqlvmnode1 sqlvmnode2 sqlvmnode3]` Gibt den Namen aller Knoten, die zurzeit Teil des Clusters. Wenn keine Knoten beteiligt sind, `pcs status` gibt `OFFLINE: [<nodename>]`.

`PCSD Status` Zeigt den Status für jeden Knoten des Clusters an.

### <a name="reasons-why-a-node-may-be-offline"></a>Gründe, warum ein Knoten offline sein kann

Überprüfen Sie die folgenden Elemente aus, wenn ein Knoten offline ist.

- **Firewall**

    Die folgenden Ports müssen auf allen Knoten, damit Pacemaker kommunizieren können geöffnet sein.
    
    - ** TCP: 2224, 3121, 21064

- **Pacemaker oder Corosync-Dienste, die ausgeführt wird**

- **Kommunikation von Knoten**

- **Knoten namenszuordnungen**

## <a name="additional-resources"></a>Weitere Ressourcen

* [Clustern von Grund auf Neu](http://clusterlabs.org/doc/Cluster_from_Scratch.pdf) Leitfaden für Pacemaker

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren Sie Red Hat Enterprise Linux Cluster mit freigegebenen Datenträgern werden für SQL Server.](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)

