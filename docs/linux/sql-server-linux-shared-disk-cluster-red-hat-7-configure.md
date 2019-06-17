---
title: Konfigurieren Sie freigegebenen Cluster Red Hat Enterprise Linux für SQL Server | Microsoft-Dokumentation
description: Implementieren Sie hohen Verfügbarkeit durch Cluster mit freigegebenen Datenträgern Red Hat Enterprise Linux für SQL Server konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: dcc0a8d3-9d25-4208-8507-a5e65d2a9a15
ms.openlocfilehash: 73dff2be37cade58991078fec4663a9ac351f49b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712897"
---
# <a name="configure-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>Konfigurieren Sie Red Hat Enterprise Linux Cluster mit freigegebenen Datenträgern werden für SQL Server.

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieses Handbuch enthält Anweisungen, um einen Cluster mit zwei Knoten freigegebenen Datenträgern für SQL Server unter Red Hat Enterprise Linux zu erstellen. Die clustering-Ebene basiert auf Red Hat Enterprise Linux (RHEL) [HA-Add-On](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) baut auf [Pacemaker](https://clusterlabs.org/). SQL Server-Instanz ist auf einem Knoten oder die andere aktiv.

> [!NOTE] 
> Zugriff auf Red Hat-HA-Add-On und Dokumentation erfordert ein Abonnement. 

Wie das folgende Diagramm zeigt, wird der Speicher auf zwei Servern angezeigt. Clustering Komponenten - Corosync und Pacemaker - Kommunikation und ressourcenverwaltung zu koordinieren. Einer der Server hat die aktive Verbindung mit dem Storage-Ressourcen und der SQL Server. Wenn Pacemaker ein Fehler erkannt wird verwalten die Clusterkomponenten an, die Ressourcen auf dem anderen Knoten verschieben.  

![Red Hat Enterprise Linux 7 freigegebene Datenträgercluster für SQL](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

Weitere Informationen zu Clusterkonfiguration, Optionen für Agents und Management finden Sie unter [RHEL-Referenzdokumentation](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).


> [!NOTE] 
> SQL Server Integration mit Pacemaker ist an diesem Punkt nicht als gekoppelt als mit WSFC unter Windows. Von in SQL, besteht keine Kenntnisse über das Vorhandensein des Clusters, alle Orchestrierung befindet sich außerhalb im und der Dienst wird als eigenständige Instanz von Pacemaker gesteuert. Außerdem werden z. B. Cluster Dmvs Sys. dm_os_cluster_nodes und dm_os_cluster_properties keine Datensätze.
Eine Verbindungszeichenfolge, die auf einem Zeichenfolgennamen für den Server verweist und nicht die IP-Adresse verwenden, müssen sie in ihren DNS-Server die IP-Adresse verwendet, um die virtuelle IP-Adressressource erstellen (wie in den folgenden Abschnitten erläutert wird) mit dem ausgewählten Server registrieren.

Die folgenden Abschnitte führen die Schritte zum Einrichten einer Lösung mit Failovercluster. 

## <a name="prerequisites"></a>Erforderliche Komponenten

Um das folgende End-to-End-Szenario abzuschließen, benötigen Sie zwei Computer, der zwei Knoten-Cluster und einem anderen Server so konfigurieren Sie den NFS-Server bereitstellen. Unten aufgeführten Schritte beschreiben Sie, wie diese Server konfiguriert werden.

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>Richten Sie ein und konfigurieren Sie das Betriebssystem auf jedem Clusterknoten

Der erste Schritt ist das Betriebssystem auf den Clusterknoten zu konfigurieren. Verwenden Sie für diese exemplarische Vorgehensweise RHEL mit einem gültigen Abonnement, für die HA-Add-On. 

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>Installieren und Konfigurieren von SQL Server auf jedem Clusterknoten

1. Installieren und Einrichten von SQL Server auf beiden Knoten.  Ausführliche Anweisungen finden Sie unter [Installieren von SQL Server unter Linux](sql-server-linux-setup.md).

1. Festlegen Sie ein Knoten als primärer und der andere wird als sekundäre Datenbank, für die Zwecke der Konfiguration. Verwenden Sie diese Bedingungen für die folgenden dieses Handbuchs.  

1. Klicken Sie auf dem sekundären Knoten beenden, und Deaktivieren von SQL Server.

   Im folgenden Beispiel wird beendet und deaktiviert SQL Server: 

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl disable mssql-server
   ```
> [!NOTE] 
> Beim Setup ein Server-Hauptschlüssel für die SQL Server-Instanz generiert und an platziert `/var/opt/mssql/secrets/machine-key`. Unter Linux wird SQL Server immer ausgeführt, als ein lokales Konto Mssql aufgerufen werden. Da es sich um ein lokales Konto handelt, ist nicht die Identität über Knoten hinweg gemeinsam genutzt werden. Aus diesem Grund müssen Sie den Verschlüsselungsschlüssel aus dem primären Knoten für jeden sekundären Knoten kopieren, damit jedes lokalen Mssql-Konto, um den Server-Hauptschlüssel entschlüsseln zugreifen kann. 

1. Klicken Sie auf dem Primärknoten, erstellen Sie eine SQL Server-Anmeldung für Pacemaker, und erteilen Sie die Login-Berechtigung zum Ausführen `sp_server_diagnostics`. Pacemaker verwendet dieses Konto, um zu überprüfen, welcher Knoten die SQL Server ausgeführt wird. 

   ```bash
   sudo systemctl start mssql-server
   ```

   Verbinden mit dem SQL Server `master` -Datenbank mit der sa-Konto, und führen Sie Folgendes:

   ```bashsql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'

   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```
   Alternativ können Sie die Berechtigungen detaillierter festlegen. Die Pacemaker-Anmeldung erfordert `VIEW SERVER STATE` zum Abfrage-Integritätsstatus mit Sp_server_diagnostics, `setupadmin` und `ALTER ANY LINKED SERVER` auf den Namen der FCI-Instanz mit den Namen der Ressource zu aktualisieren, indem Sie Ausführung Sp_dropserver und Sp_addserver. 

1. Klicken Sie auf dem primären Knoten beenden, und Deaktivieren von SQL Server. 

1. Konfigurieren der Hosts-Datei für jeden Clusterknoten. Die Hosts-Datei muss es sich um den IP-Adresse und den Namen der einzelnen Clusterknoten enthalten. 

    Überprüfen Sie die IP-Adresse für jeden Knoten. Das folgende Skript zeigt die IP-Adresse Ihres aktuellen Knotens. 

   ```bash
   sudo ip addr show
   ```

   Legen Sie den Namen des Computers, auf den einzelnen Knoten. Weisen Sie jedem Knoten einen eindeutigen Namen, die 15 Zeichen lang ist oder weniger. Den Namen des Computers festlegen, indem Sie es `/etc/hosts`. Mithilfe des folgenden Skripts können Sie `/etc/hosts` mit `vi` bearbeiten. 

   ```bash
   sudo vi /etc/hosts
   ```
   Das folgende Beispiel zeigt `/etc/hosts` mit Ergänzungen für zwei Knoten, die mit dem Namen `sqlfcivm1` und `sqlfcivm2`.

   ```bash
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 sqlfcivm1
   10.128.16.77 sqlfcivm2
   ```

Im nächsten Abschnitt Konfigurieren freigegebenen Speicher und die Datenbankdateien auf den Speicher zu verschieben. 

## <a name="configure-shared-storage-and-move-database-files"></a>Konfigurieren von freigegebenem Speicher, und Verschieben von Datenbankdateien 

Es gibt eine Vielzahl von Lösungen zum Bereitstellen von freigegebenen Speichers. In dieser exemplarischen Vorgehensweise veranschaulicht das Konfigurieren von freigegebenen Speichers mit NFS. Es wird empfohlen, bewährte Methoden befolgen und Verwenden von Kerberos zum Sichern von NFS (finden Sie hier ein Beispiel: https://www.certdepot.net/rhel7-use-kerberos-control-access-nfs-network-shares/). 

>[!Warning]
>Wenn Sie NFS nicht sichern, klicken Sie dann werden jede Person, die Zugriff auf Ihr Netzwerk und die IP-Adresse eines SQL-Knotens zu spoofen können auf die Datendateien zugreifen. Wie immer, stellen Sie sicher, dass Sie Bedrohungsmodells für Ihr System vor der Verwendung in der Produktion. Eine weitere Option für Storage ist die Verwendung von SMB-Dateifreigabe.

### <a name="configure-shared-storage-with-nfs"></a>Konfigurieren von freigegebenem Speicher mit NFS

> [!IMPORTANT] 
> Hosten der Datenbankdateien auf einer NFS-Server mit Version < 4 wird in dieser Version nicht unterstützt. Dies schließt die Verwendung von NFS für freigegebene Datenträger Failovercluster sowie Datenbanken auf nicht gruppierte Instanzen. Wir arbeiten daran, dass andere NFS-Server-Versionen in zukünftigen Releases. 

Führen Sie folgende Schritte aus, auf dem NFS-Server:

1. Installieren Sie `nfs-utils`

   ```bash
   sudo yum -y install nfs-utils
   ```

1. Aktivieren und starten `rpcbind`

   ```bash
   sudo systemctl enable rpcbind && sudo systemctl start rpcbind
   ```

1. Aktivieren und starten `nfs-server`
 
   ```bash
   sudo systemctl enable nfs-server && sudo systemctl start nfs-server
   ```
 
1.  Bearbeiten Sie `/etc/exports` um das Verzeichnis zu exportieren, Sie freigeben möchten. 1 Zeile erforderlich für jede Freigabe. Zum Beispiel: 

   ```bash
   /mnt/nfs  10.8.8.0/24(rw,sync,no_subtree_check,no_root_squash)
   ```

1. Exportieren Sie die Freigaben

   ```bash
   sudo exportfs -rav
   ```

1. Stellen Sie sicher, dass die Pfade/freigegebene exportiert werden, führen Sie aus der NFS-server

   ```bash
   sudo showmount -e
   ```

1. Ausnahme im SELinux hinzufügen

   ```bash
   sudo setsebool -P nfs_export_all_rw 1
   ```
   
1. Öffnen Sie die Firewall den Server.

   ```bash 
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>Konfigurieren Sie alle Knoten des Clusters für die Verbindung mit dem freigegebenen NFS-Speicher

Führen Sie die folgenden Schritte aus, auf allen Clusterknoten.

1.  Installieren Sie `nfs-utils`

   ```bash
   sudo yum -y install nfs-utils
   ```

1. Öffnen Sie die Firewall auf Clients und Server für NFS

   ```bash
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

1. Stellen Sie sicher, dass Sie die NFS-Freigaben auf Clientcomputern sehen

   ```bash
   sudo showmount -e <IP OF NFS SERVER>
   ```

1. Wiederholen Sie diese Schritte auf allen Clusterknoten aus.

Weitere Informationen zur Verwendung von NFS finden Sie unter den folgenden Ressourcen:

* [NFS-Servern und Firewalld | Stack Exchange](https://unix.stackexchange.com/questions/243756/nfs-servers-and-firewalld)
* [Bereitstellen von einem NFS-Volume | Linux-Netzwerk – Administratorhandbuch](https://www.tldp.org/LDP/nag2/x-087-2-nfs.mountd.html)
* [NFS-Serverkonfiguration | Red Hat-Kundenportal](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/storage_administration_guide/nfs-serverconfig)

### <a name="mount-database-files-directory-to-point-to-the-shared-storage"></a>Bereitstellen der Datenbank-Dateiverzeichnis auf dem freigegebenen Speicher verweisen

1.  **Auf dem primären Knoten nur**, speichern Sie die Datenbankdateien an einem temporären Speicherort. Das folgende Skript erstellt ein neues temporäres Verzeichnis, die die Datenbankdateien in das neue Verzeichnis kopiert und entfernt die alten Datenbankdateien. Wie SQL Server als lokaler Benutzer Mssql ausgeführt wird, müssen Sie sicherstellen, dass nach dem Übertragen von Daten in der eingebundenen Freigabe, lokaler Benutzer Lese-/ Schreibzugriff auf die Freigabe verfügt. 

   ``` 
   $ sudo su mssql
   $ mkdir /var/opt/mssql/tmp
   $ cp /var/opt/mssql/data/* /var/opt/mssql/tmp
   $ rm /var/opt/mssql/data/*
   $ exit
   ``` 

1.  Bearbeiten Sie auf allen Clusterknoten `/etc/fstab` hinzu, um den Bereitstellungsbefehl einzubeziehen.  

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr 
   ```
   
   Das folgende Skript zeigt ein Beispiel für die Bearbeitung.  

   ``` 
   10.8.8.0:/mnt/nfs /var/opt/mssql/data nfs timeo=14,intr 
   ``` 
> [!NOTE] 
>Wenn eine Ressource für die Datei System (FS) mit einer wie empfohlen, ist es nicht erforderlich, um den Befehl bereitstellen in/etc/fstab zu erhalten. Pacemaker übernimmt den Ordner einbinden, beim Starten der FS gruppierte Ressource. Mithilfe des umgrenzungs wird es stellen Sie sicher, dass das FS nie zweimal bereitgestellt wird. 

1.  Führen Sie `mount -a` Befehl für das System die bereitgestellten Pfade zu aktualisieren.  

1.  Kopieren der Datenbank und Protokolldateien, die Sie in gespeichert `/var/opt/mssql/tmp` auf die neu eingebundenen Freigabe `/var/opt/mssql/data`. Dies ist nur erforderlich, werden **auf dem primären Knoten**. Stellen Sie sicher, dass Sie Berechtigungen für Lese-/ "Mssql" Lokale Benutzer erteilen.

   ``` 
   $ sudo chown mssql /var/opt/mssql/data
   $ sudo chgrp mssql /var/opt/mssql/data
   $ sudo su mssql
   $ cp /var/opt/mssql/tmp/* /var/opt/mssql/data/
   $ rm /var/opt/mssql/tmp/*
   $ exit
   ``` 
 
1.  Überprüfen Sie, dass SQL Server erfolgreich mit dem neuen Dateipfad gestartet wird. Hierzu auf jedem Knoten. An diesem Punkt sollte nur ein Knoten, über SQL Server zu einem Zeitpunkt ausführen. Sie können nicht beide gleichzeitig ausgeführt, da sie beide versuchen werden, auf die Datendateien gleichzeitig (um zu vermeiden, versehentlich Starten von SQL Server auf beiden Knoten eine Dateisystem-Clusterressource verwenden, um sicherzustellen, dass die Dateifreigabe nicht zweimal von den anderen Knoten bereitgestellt ist). Die folgenden Befehle Starten von SQL Server, den Status überprüfen und beenden Sie SQL Server.
 
   ```bash
   sudo systemctl start mssql-server
   sudo systemctl status mssql-server
   sudo systemctl stop mssql-server
   ```
 
An diesem Punkt sind beide Instanzen von SQL Server für die Ausführung mit den Datenbankdateien auf dem freigegebenen Speicher konfiguriert. Der nächste Schritt ist so konfigurieren Sie SQL Server für Pacemaker. 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installieren Sie und konfigurieren Sie auf jedem Clusterknoten die Pacemaker


2. Erstellen Sie auf beiden Clusterknoten eine Datei zum Speichern von Benutzername und Kennwort für SQL Server für die Pacemaker-Anmeldung. Der folgende Befehl erstellt und füllt diese Datei:

   ```bash
   sudo touch /var/opt/mssql/secrets/passwd
   echo '<loginName>' | sudo tee -a /var/opt/mssql/secrets/passwd
   echo '<loginPassword>' | sudo tee -a /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd 
   sudo chmod 600 /var/opt/mssql/secrets/passwd    
   ```

3. Öffnen Sie auf beiden Clusterknoten die Pacemaker-Firewallports. Führen Sie zum Öffnen dieser Ports mit `firewalld` folgenden Befehl aus:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Wenn Sie eine andere Firewall verwenden, die nicht über eine integrierte Konfiguration mit hoher Verfügbarkeit verfügt, müssen die folgenden Ports geöffnet werden, damit Pacemaker mit anderen Knoten im Cluster kommunizieren können
   >
   > * TCP: Ports 2224, 3121, 21064
   > * UDP: Port 5405

1. Installieren Sie Pacemaker-Pakete auf jedem Knoten.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

    

2. Legen Sie das Kennwort für den Standardbenutzer fest, der beim Installieren von Pacemaker und Corosync-Paketen erstellt wird. Verwenden Sie auf beiden Knoten dasselbe Kennwort. 

   ```bash
   sudo passwd hacluster
   ```

    

3. Aktivieren und starten Sie den `pcsd`-Dienst und Pacemaker. So können Knoten dem Cluster nach dem Neustart erneut beitreten. Führen Sie den folgenden Befehl auf beiden Knoten aus.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. Installieren Sie den FCI-Ressourcenagent für SQL Server. Führen Sie die folgenden Befehle auf beiden Knoten aus. 

   ```bash
   sudo yum install mssql-server-ha
   ```

## <a name="create-the-cluster"></a>Erstellen des Clusters 

1. Erstellen Sie auf einem der Knoten den Cluster ein.

   ```bash
   sudo pcs cluster auth <nodeName1 nodeName2 ...> -u hacluster
   sudo pcs cluster setup --name <clusterName> <nodeName1 nodeName2 ...>
   sudo pcs cluster start --all
   ```

   > RHEL-HA-Add-On wurde für das umgrenzen der Agents für VMWare und KVM. Umgrenzung muss für alle anderen Hypervisoren deaktiviert werden. Deaktivieren des umgrenzungs-Agents wird in produktionsumgebungen nicht empfohlen. Zum Zeitpunkt der Zeitrahmen gibt es keine Umgrenzung-Agents für Hyper-v oder in der Cloud-Umgebungen. Wenn Sie eine dieser Konfigurationen ausführen, müssen Sie Umgrenzung zu deaktivieren. \**Dies wird nicht in einem Produktionssystem empfohlen.* *

   Der folgende Befehl deaktiviert die umgrenzungs-Agents.

   ```bash
   sudo pcs property set stonith-enabled=false
   sudo pcs property set start-failure-is-fatal=false
   ```

2. Konfigurieren Sie die Clusterressourcen für SQL Server, Dateisystem und virtuellen IP-Ressourcen aus, und drücken Sie die Konfiguration mit dem Cluster. Sie benötigen die folgenden Informationen:

   - **SQL Server-Ressourcenname**: Ein Name für die SQL Server-Clusterressource. 
   - **Floating-IP-Ressourcennamen**: Ein Name für die virtuelle IP-Adressressource.
   - **IP-Adresse**: Die IP-Adresse, die Clients verwenden, um an der gruppierten Instanz von SQL Server eine Verbindung herstellen. 
   - **File System-Ressourcenname**: Ein Name für die Dateisystem-Ressource.
   - **device**: Pfad für die NFS-Freigabe
   - **device**: Der lokale Pfad, dass sie auf die Freigabe eingebunden ist
   - **fstype**: Dateityp (z. B. Nfs) freigeben

   Aktualisieren Sie die Werte aus dem folgenden Skript für Ihre Umgebung. Führen Sie auf einem Knoten zum Konfigurieren und starten den Clusterdienst.  

   ```bash
   sudo pcs cluster cib cfg 
   sudo pcs -f cfg resource create <sqlServerResourceName> ocf:mssql:fci
   sudo pcs -f cfg resource create <floatingIPResourceName> ocf:heartbeat:IPaddr2 ip=<ip Address>
   sudo pcs -f cfg resource create <fileShareResourceName> Filesystem device=<networkPath> directory=<localPath>         fstype=<fileShareType>
   sudo pcs -f cfg constraint colocation add <virtualIPResourceName> <sqlResourceName>
   sudo pcs -f cfg constraint colocation add <fileShareResourceName> <sqlResourceName> 
   sudo pcs cluster cib-push cfg
   ```

   Das folgende Skript erstellt z. B. eine gruppierten SQL Server-Ressource, die mit dem Namen `mssqlha`, und eine floating IP-Adressressourcen mit IP-Adresse `10.0.0.99`. Außerdem erstellt eine Dateisystem-Ressource und Einschränkungen hinzugefügt, damit alle Ressourcen, die auf demselben Knoten wie SQL-Ressource zusammengestellt werden. 

   ```bash
   sudo pcs cluster cib cfg
   sudo pcs -f cfg resource create mssqlha ocf:mssql:fci
   sudo pcs -f cfg resource create virtualip ocf:heartbeat:IPaddr2 ip=10.0.0.99
   sudo pcs -f cfg resource create fs Filesystem device="10.8.8.0:/mnt/nfs" directory="/var/opt/mssql/data" fstype="nfs"
   sudo pcs -f cfg constraint colocation add virtualip mssqlha
   sudo pcs -f cfg constraint colocation add fs mssqlha
   sudo pcs cluster cib-push cfg
   ```

   Nachdem die Konfiguration per Push übertragen wird, wird SQL Server auf einem Knoten gestartet. 

3. Stellen Sie sicher, dass SQL Server gestartet wurde. 

   ```bash
   sudo pcs status 
   ```

   In den folgenden Beispielen werden die Ergebnisse auf, wenn Pacemaker eine gruppierte Instanz von SQL Server wurde erfolgreich gestartet wurde. 

   ```
   fs     (ocf::heartbeat:Filesystem):    Started sqlfcivm1
   virtualip     (ocf::heartbeat:IPaddr2):      Started sqlfcivm1
   mssqlha  (ocf::mssql:fci): Started sqlfcivm1
   
   PCSD Status:
    slqfcivm1: Online
    sqlfcivm2: Online
   
   Daemon Status:
    corosync: active/disabled
    pacemaker: active/enabled
    pcsd: active/enabled
   ```

## <a name="additional-resources"></a>Zusätzliche Ressourcen

* [Clustern von Grund auf Neu](https://clusterlabs.org/doc/Cluster_from_Scratch.pdf) Leitfaden für Pacemaker

## <a name="next-steps"></a>Nächste Schritte

[Arbeiten Sie SQL Server mit Red Hat Enterprise Linux Cluster mit freigegebenen Datenträgern](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
