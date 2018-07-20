---
title: Failoverclusterinstanz – SQL Server unter Linux (RHEL) konfigurieren | Microsoft-Dokumentation
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: 90235a612617fef28a02f980b349fc15490cba3f
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39086152"
---
# <a name="configure-failover-cluster-instance---sql-server-on-linux-rhel"></a>Konfigurieren Sie Failoverclusterinstanz – SQL Server unter Linux (RHEL)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Eine Failoverclusterinstanz von SQL Server zwei Knoten freigegebenen Datenträger bietet Redundanz auf Serverebene, um hochverfügbarkeit zu erzielen. In diesem Tutorial erfahren Sie, wie eine zwei-Knoten-Failover-Clusterinstanz von SQL Server unter Linux zu erstellen. Die einzelnen Schritte, die Sie abgeschlossen werden, gehören:

> [!div class="checklist"]
> * Einrichten und Konfigurieren von Linux
> * Installieren und Konfigurieren von SQL Server
> * Konfigurieren Sie die Datei "Hosts"
> * Konfigurieren von freigegebenem Speicher, und verschieben Sie die Dateien
> * Installieren Sie und konfigurieren Sie auf jedem Clusterknoten die Pacemaker
> * Konfigurieren Sie die Failover-Clusterinstanz

In diesem Artikel wird erläutert, wie eine zwei-Knoten freigegebenen Datenträger-Failoverclusterinstanz (FCI) für SQL Server zu erstellen. Der Artikel enthält Anleitungen und Skriptbeispiele für Red Hat Enterprise Linux (RHEL). Ubuntu-Distributionen sind ähnlich wie RHEL, sodass die Skriptbeispiele normalerweise werden auch unter Ubuntu funktionieren. 

Konzeptionelle Informationen finden Sie unter [SQL Server Failoverclusterinstanz (FCI) unter Linux](sql-server-linux-shared-disk-cluster-concepts.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Um das folgende End-to-End-Szenario abzuschließen, benötigen Sie zwei Computer, der zwei Knoten-Cluster und einem anderen Server für den Speicher bereitstellen. Unten aufgeführten Schritte beschreiben Sie, wie diese Server konfiguriert werden.

## <a name="set-up-and-configure-linux"></a>Einrichten und Konfigurieren von Linux

Der erste Schritt ist das Betriebssystem auf den Clusterknoten zu konfigurieren. Konfigurieren Sie auf jedem Knoten im Cluster eine Linux-Distribution. Verwenden Sie die gleichen Distribution und Version, auf beiden Knoten. Verwenden Sie entweder einen oder dem anderen die folgenden Distributionen:
    
* RHEL mit einem gültigen Abonnement, für die HA-Add-On

## <a name="install-and-configure-sql-server"></a>Installieren und Konfigurieren von SQL Server

1. Installieren und Einrichten von SQL Server auf beiden Knoten.  Ausführliche Anweisungen finden Sie unter [Installieren von SQL Server unter Linux](sql-server-linux-setup.md).
1. Festlegen Sie ein Knoten als primärer und der andere wird als sekundäre Datenbank, für die Zwecke der Konfiguration. Verwenden Sie diese Bedingungen für die folgenden dieses Handbuchs.  
1. Klicken Sie auf dem sekundären Knoten beenden, und Deaktivieren von SQL Server.
    Im folgenden Beispiel wird beendet und deaktiviert SQL Server: 
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE] 
    > Gruppe Zeit, einen Server-Hauptschlüssel für die SQL Server-Instanz generiert und platziert `var/opt/mssql/secrets/machine-key`. Unter Linux wird SQL Server immer ausgeführt, als ein lokales Konto Mssql aufgerufen werden. Da es sich um ein lokales Konto handelt, ist nicht die Identität über Knoten hinweg gemeinsam genutzt werden. Aus diesem Grund müssen Sie den Verschlüsselungsschlüssel aus dem primären Knoten für jeden sekundären Knoten kopieren, damit jedes lokalen Mssql-Konto, um den Server-Hauptschlüssel entschlüsseln zugreifen kann. 

1.  Klicken Sie auf dem Primärknoten, erstellen Sie eine SQL Server-Anmeldung für Pacemaker, und erteilen Sie die Login-Berechtigung zum Ausführen `sp_server_diagnostics`. Pacemaker verwendet dieses Konto, um zu überprüfen, welcher Knoten die SQL Server ausgeführt wird. 

    ```bash
    sudo systemctl start mssql-server
    ```
   
   Verbinden mit dem SQL Server `master` -Datenbank mit der sa-Konto, und führen Sie Folgendes:

   ```sql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```

   Alternativ können Sie die Berechtigungen detaillierter festlegen. Die Pacemaker-Anmeldung erfordert `VIEW SERVER STATE` zum Abfrage-Integritätsstatus mit Sp_server_diagnostics, `setupadmin` und `ALTER ANY LINKED SERVER` auf den Namen der FCI-Instanz mit den Namen der Ressource zu aktualisieren, indem Sie Ausführung Sp_dropserver und Sp_addserver. 

1. Klicken Sie auf dem primären Knoten beenden, und Deaktivieren von SQL Server. 

## <a name="configure-the-hosts-file"></a>Konfigurieren Sie die Datei "Hosts"

Konfigurieren Sie die Datei "Hosts" auf jedem Clusterknoten. Die Datei "Hosts" muss es sich um den IP-Adresse und den Namen der einzelnen Clusterknoten enthalten.

1. Überprüfen Sie die IP-Adresse für jeden Knoten. Das folgende Skript zeigt die IP-Adresse Ihres aktuellen Knotens. 

    ```bash
    sudo ip addr show
    ```

1. Legen Sie den Namen des Computers, auf den einzelnen Knoten. Weisen Sie jedem Knoten einen eindeutigen Namen, die 15 Zeichen lang ist oder weniger. Den Namen des Computers festlegen, indem Sie es `/etc/hosts`. Mithilfe des folgenden Skripts können Sie `/etc/hosts` mit `vi` bearbeiten. 

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

## <a name="configure-storage--move-database-files"></a>Konfigurieren des Speichers und das Verschieben von Datenbankdateien  

Sie müssen Speicher bereitzustellen, die auf beiden Knoten zugreifen können. Sie können es sich um iSCSI, SMB oder NFS verwenden. Konfigurieren Sie des Speichers, vorhanden Sie des Speichers auf den Clusterknoten und klicken Sie dann verschieben Sie die Datenbankdateien auf den neuen Speicher. In den folgenden Artikeln wird erläutert, die Schritte für jeden Speichertyp:

- [Konfigurieren von Failover-Clusterinstanz - iSCSI - SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [Konfigurieren Sie Failoverclusterinstanz – NFS - SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [Konfigurieren der Failoverclusterinstanz – SMB – SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure-smb.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>Installieren Sie und konfigurieren Sie auf jedem Clusterknoten die Pacemaker

1. Erstellen Sie auf beiden Clusterknoten eine Datei zum Speichern von Benutzername und Kennwort für SQL Server für die Pacemaker-Anmeldung. 

    Der folgende Befehl erstellt und füllt diese Datei:

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd    
    ```

1. Öffnen Sie auf beiden Clusterknoten die Pacemaker-Firewallports. Führen Sie zum Öffnen dieser Ports mit `firewalld` folgenden Befehl aus:

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > Wenn Sie eine andere Firewall verwenden, in die keine Konfiguration mit hoher Verfügbarkeit integriert ist, müssen die folgenden Ports geöffnet werden, damit Pacemaker mit anderen Knoten im Cluster kommunizieren kann:
   >
   > * TCP: Ports 2224, 3121, 21064
   > * UDP: Port 5405

1. Installieren Sie Pacemaker-Pakete auf jedem Knoten.

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```
1. Legen Sie das Kennwort für den Standardbenutzer fest, der beim Installieren von Pacemaker und Corosync-Paketen erstellt wird. Verwenden Sie auf beiden Knoten dasselbe Kennwort. 

   ```bash
   sudo passwd hacluster
   ```
1. Aktivieren und starten Sie den `pcsd`-Dienst und Pacemaker. So können Knoten dem Cluster nach dem Neustart erneut beitreten. Führen Sie den folgenden Befehl auf beiden Knoten aus.

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

1. Installieren Sie den FCI-Ressourcenagent für SQL Server. Führen Sie die folgenden Befehle auf beiden Knoten aus. 

   ```bash
   sudo yum install mssql-server-ha
   ```

## <a name="configure-the-failover-cluster-instance"></a>Konfigurieren Sie die Failover-Clusterinstanz

Die FCI wird in einer Ressourcengruppe erstellt. Dies ist etwas einfacher, da die Ressourcengruppe für Einschränkungen nicht werden muss. Fügen Sie die Ressourcen jedoch in der Ressourcengruppe, in der Reihenfolge, in die sie gestartet werden soll. Ist die Reihenfolge, die sie gestartet werden soll: 

1. Storage-Ressource
2. Network-Ressource
3. Anwendungsressource

In diesem Beispiel wird eine FCI in der Gruppe NewLinFCIGrp erstellt. Der Name der Ressourcengruppe muss über eine Ressource in Pacemaker erstellt eindeutig sein.

1.  Erstellen Sie die Datenträgerressource. Sie erhalten keine Antwort zurück, wenn es kein Problem ist. Die Möglichkeit zum Erstellen der Ressource hängt von den Speichertyp ab. Folgendes ist ein Beispiel für jeden Speichertyp. Verwenden Sie das Beispiel, das für den Speichertyp für Ihren Cluster Speicher gilt.

    **iSCSI**

    ```bash
    sudo pcs resource create <iSCSIDiskResourceName> Filesystem device="/dev/<VolumeGroupName>/<LogicalVolumeName>" directory="<FolderToMountiSCSIDisk>" fstype="<FileSystemType>" --group RGName
    ```

    \<iSCSIDIskResourceName > ist der Name der Ressource verknüpft ist, mit dem iSCSI-Datenträger

    \<VolumeGroupName > ist der Name der Volumegruppe  

    \<LogicalVolumeName > ist der Name des logischen Volumes, die erstellt wurde  

    \<FolderToMountiSCSIDIsk > ist der Ordner zum Bereitstellen des Datenträgers (Systemdatenbanken und den Standardspeicherort, es wäre /var/opt/mssql/data)

    \<FileSystemType > wäre EXT4 oder das XFS je nachdem, wie Dinge formatiert wurden und welche die Verteilung unterstützt. 

    **NFS**

    ```bash
    sudo pcs resource create <NFSDiskResourceName> Filesystem device="<IPAddressOfNFSServer>:<FolderOnNFSServer>" directory="<FolderToMountNFSShare>" fstype=nfs4 options=" nfsvers=4.2,timeo=14,intr" --group RGName
    mount -t nfs4 IPAddressOfNFSServer:FolderOnNFSServer /var/opt/mssql/data -o 
    ```

    \<NFSDIskResourceName > der Name der Ressource, die NFS-Freigabe zugeordnet

    \<IPAddressOfNFSServer > ist die IP-Adresse der NFS-Server, die verwendet werden

    \<FolderOnNFSServer > ist der Name des der NFS-Freigabe

    \<FolderToMountNFSShare > ist der Ordner zum Bereitstellen des Datenträgers (Systemdatenbanken und den Standardspeicherort, es wäre /var/opt/mssql/data)

    Ein Beispiel sehen Sie hier:

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    **SMB**

    ```bash
    sudo pcs resource create SMBDiskResourceName Filesystem device="//<ServerName>/<ShareName>" directory="<FolderName>" fstype=cifs options="vers=3.0,username=<UserName>,password=<Password>,domain=<ADDomain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777" --group <RGName>
    ```

    \<ServerName > ist der Name des Servers mit der SMB-Freigabe

    \<ShareName > ist der Name der Freigabe

    \<Ordnername > ist der Name des Ordners im letzten Schritt erstellt haben
    
    \<Benutzername > ist der Name des Benutzers, der Zugriff auf die Dateifreigabe

    \<Kennwort > ist das Kennwort für den Benutzer

    \<ADDomain > wird von die AD DS-Domäne (falls zutreffend, wenn Sie eine Windows Server-basierten SMB-Freigabe zu verwenden)

    \<MssqlUID > ist die UID die Mssql-Benutzer

    \<MssqlGID > ist die GID von der Mssql-Benutzer

    \<RGName > ist der Name der Ressourcengruppe
 
2.  Erstellen Sie die IP-Adresse, die von der FCI verwendet werden. Sie erhalten keine Antwort zurück, wenn es kein Problem ist.

    ```bash
    sudo pcs resource create <IPResourceName> ocf:heartbeat:IPaddr2 ip=<IPAddress> nic=<NetworkCard> cidr_netmask=<NetMask> --group <RGName>
    ```

    \<IPResourceName > der Name der Ressource, die IP-Adresse zugeordnet ist

    \<IP-Adresse > ist die IP-Adresse für die FCI

    \<NetworkCard > ist die Netzwerkkarte, die dem Subnetz (d. h. "eth0") zugeordnet

    \<Netzmaske > ist die Netzmaske des Subnetzes (z.B. 24)

    \<RGName > ist der Name der Ressourcengruppe
 
3.  Die FCI-Ressource zu erstellen. Sie erhalten keine Antwort zurück, wenn es kein Problem ist.

    ```bash
    sudo pcs resource create FCIResourceName ocf:mssql:fci op defaults timeout=60s --group RGName
    ```

    \<FCIResourceName > ist nicht nur den Namen der Ressource, sondern auch der Anzeigename, der die FCI zugeordnet ist. Dies wird Benutzern und Anwendungen verwendet, um eine Verbindung herstellen. 

    \<RGName > ist der Name der Ressourcengruppe.
 
4.  Führen Sie den Befehl `sudo pcs resource`. Die FCI muss online sein.
 
5.  Verbinden Sie mit der FCI mit SSMS oder mithilfe des DNS-/ Resource-Namens der FCI Sqlcmd.

6.  Geben Sie die Anweisung `SELECT @@SERVERNAME`. Sie sollte den Namen der FCI zurückgeben.

7.  Geben Sie die Anweisung `SELECT SERVERPROPERTY('ComputerNamePhysicalNetBIOS')`. Der Name des Knotens sollte zurückgegeben, die die FCI ausgeführt wird.

8.  Manuelles Failover der anderen Knoten der FCI. Lesen Sie die Anweisungen unter [Operate-Failoverclusterinstanz – SQL Server unter Linux](sql-server-linux-shared-disk-cluster-operate.md).

9.  Abschließend die FCI wieder auf den ursprünglichen Knoten fehl, und entfernen Sie die Zusammenstellung-Einschränkung.

<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
-->
## <a name="summary"></a>Zusammenfassung

In diesem Tutorial haben Sie die folgenden Aufgaben aus.

> [!div class="checklist"]
> * Einrichten und Konfigurieren von Linux
> * Installieren und Konfigurieren von SQL Server
> * Konfigurieren Sie die Datei "Hosts"
> * Konfigurieren von freigegebenem Speicher, und verschieben Sie die Dateien
> * Installieren Sie und konfigurieren Sie auf jedem Clusterknoten die Pacemaker
> * Konfigurieren Sie die Failover-Clusterinstanz

## <a name="next-steps"></a>Nächste Schritte

- [Arbeiten Sie Failoverclusterinstanz – SQL Server unter Linux](sql-server-linux-shared-disk-cluster-operate.md)

<!--Image references-->
