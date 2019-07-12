---
title: Konfigurieren von Failover Cluster-Instanz Speicher iSCSI - SQL Server unter Linux
description: ''
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 89a72a7390b3b782781c4849d69f81065544e991
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833190"
---
# <a name="configure-failover-cluster-instance---iscsi---sql-server-on-linux"></a>Konfigurieren von Failover-Clusterinstanz - iSCSI - SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel erläutert das Konfigurieren von iSCSI-Speicher für eine Failoverclusterinstanz (FCI) unter Linux. 

## <a name="configure-iscsi"></a>ISCSI-konfigurieren 
iSCSI verwendet Netzwerkfunktionen, um Datenträger von einem Server, die als Ziel bezeichnet wird, auf Servern vorzulegen. Die verbindungsherstellung mit dem iSCSI-Ziel-Server erfordern, dass ein iSCSI-Initiator konfiguriert ist. Die Datenträger auf dem Ziel explizite Berechtigungen erhalten, damit nur die Initiatoren, die für den Zugriff darauf können dies durchführen können. Das Ziel selbst sollte es sich um hoch verfügbar und zuverlässig sein.

### <a name="important-iscsi-target-information"></a>Wichtige iSCSI-Ziel-Informationen
Obwohl in diesem Abschnitt kein iSCSI-Ziel zu konfigurieren behandelt wird, da es für den Typ der Quelle spezifisch ist, die Sie verwenden möchten, stellen Sie sicher, dass die Sicherheit für die Datenträger, die von den Clusterknoten verwendet werden, konfiguriert ist.  

Das Ziel sollte nie auf einem der FCI-Knoten konfiguriert werden, wenn Sie ein Linux-basierten iSCSI-Ziel zu verwenden. Für Leistung und Verfügbarkeit sollte unabhängig von den regulären Netzwerkdatenverkehr für die Quell- und die Clientserver ein, die iSCSI-Netzwerke. Für iSCSI verwendete Netzwerke sollte schnell ausgeführt werden. Beachten Sie, dass das Netzwerk führt einige Prozessorbandbreite verbraucht, daher entsprechend planen, wenn einen normalen Server verwenden.
Um sicherzustellen, dass das wichtigste ist abgeschlossen auf dem Ziel, dass die Datenträger, die erstellt werden die entsprechenden Berechtigungen zugewiesen werden, damit nur die Teilnahme an der FCI Server darauf zugreifen können. Ein Beispiel ist unten dargestellt aus dem Microsoft iSCSI-Ziel, in denen linuxnodes1 ist der Name der erstellt, und die IP-Adressen der Knoten werden in diesem Fall zugewiesen, sodass NewFCIDisk1.vhdx Ihnen angezeigt wird.

![Initiator][1]

### <a name="instructions"></a>Instructions

In diesem Abschnitt wird beschrieben, wie einen iSCSI-Initiator auf den Servern zu konfigurieren, die als Knoten, für die FCI dienen. Die Anweisungen sollten funktionieren, auf dem RHEL und Ubuntu ausgeführt wird.

Weitere Informationen zu iSCSI-Initiator für die unterstützten Distributionen finden Sie in den folgenden Links:
- [Red Hat](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/iscsi-api.html)
- [SUSE](https://www.suse.com/documentation/sles11/stor_admin/data/sec_inst_system_iscsi_initiator.html) 
- [Ubuntu](https://help.ubuntu.com/lts/serverguide/iscsi-initiator.html)

1.  Wählen Sie einen der Server, die einbezogen werden, in der FCI-Konfiguration. Es spielt keine Rolle die. iSCSI muss in einem dedizierten Netzwerk also zur Konfiguration von iSCSI, um zu erkennen und diesem Netzwerk verwenden. Führen Sie `sudo iscsiadm -m iface -I <iSCSIIfaceName> -o new` , in denen `<iSCSIIfaceName>` ist der eindeutige oder benutzerfreundliche Name für das Netzwerk. Im folgenden Beispiel wird `iSCSINIC`:
   
    ```bash
    sudo iscsiadm -m iface -I iSCSINIC -o new
    ```
    ![7-setiscsinetwork][6]
 
2.  Bearbeiten Sie `/var/lib/iscsi/ifaces/iSCSIIfaceName`. Stellen Sie sicher, dass die folgenden Werte, die vollständig ausgefüllt wurden:

    - iface.net_ifacename ist der Name der Netzwerkkarte aus, wie in das Betriebssystem.
    - iface.hwaddress ist die MAC-Adresse, der den eindeutigen Namen, der für diese Schnittstelle, die unten erstellt wird.
    - iface.ipaddress
    - iface.subnet_Mask 

    Sehen Sie sich folgendes Beispiel an:

    ![iSCSITargetSettings][2]

3.  Das iSCSI-Ziel zu finden.

    ```bash
    sudo iscsiadm -m discovery -t sendtargets -I <iSCSINetName> -p <TargetIPAddress>:<TargetPort>
    ```

     \<iSCSINetName > ist die eindeutige/Anzeigenamen für das Netzwerk \<TargetIPAddress > die IP-Adresse des iSCSI-Ziels und \<TargetPort > ist der Port des iSCSI-Ziel. 

    ![iSCSITargetResults][3]

 
4.  Melden Sie sich bei dem Ziel

    ```bash
    sudo iscsiadm -m node -I <iSCSIIfaceName> -p TargetIPAddress -l
    ```

    \<iSCSIIfaceName > ist der eindeutige/Anzeigenamen für das Netzwerk und \<TargetIPAddress > die IP-Adresse des iSCSI-Ziels.

    ![iSCSITargetLogin][4]

5.  Überprüfen, ob eine Verbindung mit dem iSCSI-Ziel vorhanden ist.

    ```bash
    sudo iscsiadm -m session
    ```

    ![iSCSIVerify][5]

 
6.  Überprüfen der angefügte iSCSI-Datenträger

    ```bash
    sudo grep "Attached SCSI" /var/log/messages
    ```
    ![30-iSCSIattachedDisks][7]

7.  Erstellen von einem physischen Volume auf dem iSCSI-Datenträger.

    ```bash
    sudo pvcreate /dev/<devicename>
    ```

    \<DeviceName > ist der Name des Geräts aus dem vorherigen Schritt. 

 
8.  Erstellen Sie eine Volumegruppe, auf dem iSCSI-Datenträger. Einer einzelnen Volumegruppe zugewiesenen Datenträger aufgegriffen werden, wie eines Pools oder einer Auflistung. 

    ```bash
    sudo vgcreate <VolumeGroupName> /dev/devicename
    ```

    \<VolumeGroupName > ist der Name der Volumegruppe und \<Devicename > ist der Name des Geräts aus Schritt 6. 
 
9.  Erstellen Sie und überprüfen Sie die logischen Volumes für den Datenträger.

    ```bash
    sudo lvcreate -Lsize -n <LogicalVolumeName> <VolumeGroupName>
    ```
    
    \<Größe > ist die Größe des Volumes zu erstellen, und kann angegeben werden, mit G (GB), T (Terabyte) usw.,\<LogicalVolumeName > ist der Name des logischen Volumes, und \<VolumeGroupName > ist der Name der Volumegruppe aus der vorherigen Schritt. 

    Das folgende Beispiel erstellt ein Volume 25GB an.
 
    ![Create25GBVol][10]

10. Führen Sie `sudo lvs` die LVM angezeigt, die erstellt wurde.
 
11. Die logischen Volumes mit einem unterstützten Dateisystem zu formatieren. Verwenden Sie für EXT4 das folgende Beispiel aus:

    ```bash
    sudo mkfs.ext4 /dev/<VolumeGroupName>/<LogicalVolumeName>
    ```

    \<VolumeGroupName > ist der Name der Volumegruppe aus dem vorherigen Schritt. \<LogicalVolumeName > ist der Name des logischen Datenträgers aus dem vorherigen Schritt.  

12. Für Systemdatenbanken oder etwas in der Standardspeicherort für die Daten gespeichert die folgenden Schritte aus. Andernfalls fahren Sie mit Schritt 13.

   *    Stellen Sie sicher, dass SQL Server auf dem Server beendet wird, an dem Sie arbeiten.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Wechseln Sie vollständig zu den Superuser sein. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    sudo -i
    ```

   *    Wechseln Sie zu der Mssql-Benutzer sein. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    su mssql
    ```

   *    Erstellen Sie ein temporäres Verzeichnis zum Speichern von SQL Server-Daten und Protokolldateien an. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    mkdir <TempDir>
    ```

    \<"TempDir" > ist der Name des Ordners. Das folgende Beispiel erstellt einen Ordner namens /var/opt/mssql/TempDir.

    ```bash
    mkdir /var/opt/mssql/TempDir
    ```
    
   *    Kopieren Sie die SQL Server-Daten und Protokolldateien-Dateien in das temporäre Verzeichnis. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<"TempDir" > ist der Name des Ordners aus dem vorherigen Schritt.
    
   *    Stellen Sie sicher, dass die Dateien im Verzeichnis.

    ```bash
    ls \<TempDir>
    ```
    \<"TempDir" > ist der Name des Ordners aus Schritt d fort.

   *    Löschen Sie die Dateien aus dem vorhandenen Verzeichnis der SQL Server-Daten. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    rm - f /var/opt/mssql/data/*
    ```

   *    Stellen Sie sicher, dass die Dateien gelöscht wurden. Die folgende Abbildung zeigt ein Beispiel für die gesamte Sequenz von c bis h.

    ```bash
    ls /var/opt/mssql/data
    ```

    ![45-CopyMove][8]
 
   *    Typ `exit` So wechseln Sie zurück an den Root-Benutzer.

   *    Binden Sie das logische iSCSI-Volume in der SQL Server-Datenordner. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> /var/opt/mssql/data
    ``` 

    \<VolumeGroupName > ist der Name der Volumegruppe und \<LogicalVolumeName > ist der Name des logischen Volumes, die erstellt wurde. Die folgende Beispielsyntax entspricht der Volumegruppe und logische Volumes aus dem vorherigen Befehl.

    ```bash
    mount /dev/FCIDataVG1/FCIDataLV1 /var/opt/mssql/data
    ``` 

   *    Ändern Sie den Besitzer aus der Bereitstellung, um Mssql. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    chown mssql /var/opt/mssql/data
    ```

   *    Ändern Sie den Besitz der Gruppe aus der Bereitstellung in Mssql an. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    chgrp mssql /var/opt/mssql/data
    ``` 

   *    Wechseln Sie zu der Mssql-Benutzer. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    su mssql
    ``` 

   *    Kopieren Sie die Dateien aus dem temporären Verzeichnis /var/opt/mssql/data. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    cp /var/opt/mssql/TempDir/* /var/opt/mssql/data
    ``` 

   *    Stellen Sie sicher, dass die Dateien vorhanden sind.

    ```bash
    ls /var/opt/mssql/data
    ``` 
 
   *    Geben Sie `exit` Mssql nicht sind.
    
   *    Geben Sie `exit` kein Stammverzeichnis sein.

   *    Start SQL Server. Wenn alles richtig kopiert wurde und angewendeten Sicherheitsfunktionen ordnungsgemäß SQL Server zeigen sollte, wie gestartet.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ``` 
 
   *    Beenden Sie SQL Server, und stellen Sie sicher, dass es heruntergefahren ist.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ``` 

13. Für etwas anderes als ein Systemdatenbanken, z. B. Benutzerdatenbanken oder Backups die folgenden Schritte aus. Wenn Sie nur den Standardspeicherort zu verwenden, fahren Sie mit Schritt 14 fort.

   *    Wechseln Sie zu der Superuser sein. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    sudo -i
    ```

   *    Erstellen Sie einen Ordner, der von SQL Server verwendet wird. 

    ```bash
    mkdir <FolderName>
    ```

    \<Ordnername > ist der Name des Ordners. Vollständiger Pfad des Ordners muss angegeben werden, sofern Sie nicht den richtigen Speicherort. Das folgende Beispiel erstellt einen Ordner namens /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   *    Binden Sie das logische iSCSI-Volume, in dem Ordner, der im vorherigen Schritt erstellt wurde. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.
    
    ```bash
    mount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > ist der Name der Volumegruppe, \<LogicalVolumeName > ist der Name des logischen Volumes, die erstellt wurde, und \<Ordnername > ist der Name des Ordners. Beispiele für die Syntax ist unten dargestellt.

    ```bash
    mount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

   *    Ändern des Besitzes des Ordners erstellt, um Mssql. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    chown mssql <FolderName>
    ```

    \<Ordnername > ist der Name des Ordners, der erstellt wurde. Das folgende Beispiel soll dies erläutern:

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```
  
   *    Ändern Sie die Gruppe des Ordners erstellt, um Mssql. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    chown mssql <FolderName>
    ```

    \<Ordnername > ist der Name des Ordners, der erstellt wurde. Das folgende Beispiel soll dies erläutern:

    ```bash
    chown mssql /var/opt/mssql/userdata
    ```

   *    Typ `exit` nicht mehr die Superuser sein.

   *    Um zu testen, erstellen Sie eine Datenbank in diesem Ordner. Im nachstehenden Beispiel verwendet Sqlcmd, erstellen Sie eine Datenbank, damit den Kontext wechseln, überprüfen die Dateien vorhanden sind, auf der Betriebssystemebene und löscht dann den temporären Speicherort. Sie können SSMS verwenden.
  
    ![50-ExampleCreateSSMS][9]

   *    Aufheben der Freigabe 

    ```bash
    sudo umount /dev/<VolumeGroupName>/<LogicalVolumeName> <FolderName>
    ```

    \<VolumeGroupName > ist der Name der Volumegruppe, \<LogicalVolumeName > ist der Name des logischen Volumes, die erstellt wurde, und \<Ordnername > ist der Name des Ordners. Beispiele für die Syntax ist unten dargestellt.

    ```bash
    sudo umount /dev/FCIDataVG2/FCIDataLV2 /var/opt/mssql/userdata 
    ```

14. Konfigurieren Sie den Server aus, damit diese nur Pacemaker die Volumegruppe aktiviert werden kann.

    ```bash
    sudo lvmconf --enable-halvm --services -startstopservices
    ```
 
15. Generiert eine Liste der Volumegruppen auf dem Server. Elemente aufgeführt, die nicht den iSCSI-Datenträger wird vom System, z. B. für den Betriebssystem-Datenträger verwendet.

    ```bash
    sudo vgs
    ```

16. Ändern Sie den Abschnitt Aktivierung Configuration der Datei /etc/lvm/lvm.conf. Konfigurieren Sie die folgende Zeile:

    ```bash
    volume_list = [ <ListOfVGsNotUsedByPacemaker> ]
    ```

    \<ListOfVGsNotUsedByPacemaker > ist die Liste der Volumegruppen aus der Ausgabe von Schritt 20, die nicht von der FCI verwendet werden. Fügen Sie jeweils in Anführungszeichen eingeschlossen und getrennt durch ein Komma. Das folgende Beispiel soll dies erläutern:

    ![55-ListOfVGs][11]
 
 
17. Wenn Linux gestartet wird, wird er im Dateisystem bereitstellen. Um sicherzustellen, dass nur Pacemaker der iSCSI-Datenträger einbinden zu kann, erstellen Sie die Stamm-Dateisystem-Image neu. 

    Führen Sie den folgenden Befehl ein paar Minuten in Anspruch nehmen kann. Sie erhalten keine Meldung bei erfolgreicher Ausführung zurück.

    ```bash
    sudo dracut -H -f /boot/initramfs-$(uname -r).img $(uname -r)
    ```

18. Starten Sie den Server.

19. Führen Sie auf einem anderen Server, die in der FCI einbezogen werden, die Schritte 1 – 6. Dies wird das iSCSI-Ziel mit dem SQL Server darstellen. 
 
20. Generiert eine Liste der Volumegruppen auf dem Server. Es sollte die Volumegruppe, die zuvor erstellte angezeigt. 

    ```bash
    sudo vgs
    ``` 
23. Starten Sie SQL Server, und stellen Sie sicher, dass es auf diesem Server gestartet werden kann.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```

24. Beenden Sie SQL Server, und stellen Sie sicher, dass er heruntergefahren wird.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
25. Wiederholen Sie die Schritte 1 bis 6 auf andere Server, die in der FCI einbezogen werden.

Sie können nun zum Konfigurieren der FCI.

|Distribution |Thema 
|----- |-----
|**Red Hat Enterprise Linux mit HA-Add-On** |[Konfigurieren](sql-server-linux-shared-disk-cluster-configure.md)<br/>[Operate (Ausführen)](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server mit HA-Add-On** |[Konfigurieren](sql-server-linux-shared-disk-cluster-sles-configure.md)

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren Sie Failoverclusterinstanz – SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/05-initiator.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/10-iscsiTargetSettings.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/15-iSCSITargetResults.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/20-iSCSITargetLogin.png
[5]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/25-iSCSIVerify.png
[6]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/7-setiscsinetwork.png
[7]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/30-iSCSIattachedDisks.png
[8]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/45-CopyMove.png
[9]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/50-ExampleCreateSSMS.png
[10]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/40-Create25GBVol.png
[11]: ./media/sql-server-linux-shared-disk-cluster-configure-iscsi/55-ListOfVGs.png
