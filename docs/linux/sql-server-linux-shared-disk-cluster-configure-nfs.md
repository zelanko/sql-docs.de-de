---
title: Konfigurieren Sie die Instanz failoverclusterspeicher NFS - SQL Server unter Linux
description: ''
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: cbac33943de34c8757d5319e5a59b049973d50c4
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833173"
---
# <a name="configure-failover-cluster-instance---nfs---sql-server-on-linux"></a>Konfigurieren Sie Failoverclusterinstanz – NFS - SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird erläutert, wie Sie NFS-Speicher für eine Failoverclusterinstanz (FCI) unter Linux konfigurieren. 

NFS oder NFS, ist eine gängige Methode für die Datenträger in der Linux-Welt, aber nicht die Windows eine Freigabe. Ähnlich wie bei iSCSI werden können NFS auf einem Server oder eine Art von Gerät oder Speichereinheiten konfiguriert werden, solange es sich um die speicheranforderungen für SQL Server erfüllt.

## <a name="important-nfs-server-information"></a>Wichtige Informationen der NFS-server

Die Source-Hostingsite von NFS (einem Linux-Server oder etwas anderes) muss mithilfe von/kompatibel mit Version 4.2 oder höher sein. Frühere Versionen funktionieren nicht mit SQL Server unter Linux.

Wenn Sie die Ordner auf dem Server für NFS freigegeben werden konfigurieren zu können, stellen Sie sicher, dass sie diese Richtlinien allgemeine Optionen entsprechen:
- `rw` um sicherzustellen, dass den Ordner können werden gelesen und geschrieben
- `sync` um sicherzustellen, dass garantiert Schreibvorgänge auf den Ordner
- Verwenden Sie keine `no_root_squash` optional; gilt dies ein Sicherheitsrisiko
- Stellen Sie sicher, dass der Ordner Vollzugriff (777) angewendet hat.

Stellen Sie sicher, dass für den Zugriff auf Ihre Sicherheitsstandards erzwungen werden. Wenn Sie den Ordner konfigurieren zu können, stellen Sie sicher, dass nur die Server, die Teilnahme an der FCI für den NFS-Ordner finden Sie unter sollten. Ein Beispiel für eine geänderte/etc/Exports auf einer Linux-basierten NFS-Lösung wird unten, in dem der Ordner auf FCIN1 und FCIN2 beschränkt ist.

![05-nfsacl][1]

## <a name="instructions"></a>Instructions

1. Wählen Sie einen der Server, die einbezogen werden, in der FCI-Konfiguration. Es spielt keine Rolle die. 

2. Überprüfen, ob der Server auf dem NFS-Server die Mount(s) sehen.

    ```bash
    sudo showmount -e <IPAddressOfNFSServer>
    ```

    \<IPAddressOfNFSServer > ist die IP-Adresse der NFS-Server, die verwendet werden.

3. Für Systemdatenbanken oder etwas in der Standardspeicherort für die Daten gespeichert die folgenden Schritte aus. Andernfalls fahren Sie mit Schritt 4.
 
   * Stellen Sie sicher, dass SQL Server auf dem Server beendet wird, an dem Sie arbeiten.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```
   * Wechseln Sie vollständig zu den Superuser sein. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    sudo -i
    ```

   * Wechseln Sie zu der Mssql-Benutzer sein. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    su mssql
    ```

   * Erstellen Sie ein temporäres Verzeichnis zum Speichern von SQL Server-Daten und Protokolldateien an. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    mkdir <TempDir>
    ```

    \<"TempDir" > ist der Name des Ordners. Das folgende Beispiel erstellt einen Ordner namens /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   * Kopieren Sie die SQL Server-Daten und Protokolldateien-Dateien in das temporäre Verzeichnis. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.
    
    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<"TempDir" > ist der Name des Ordners aus dem vorherigen Schritt.

   * Stellen Sie sicher, dass die Dateien im Verzeichnis.

    ```bash
    ls TempDir
    ```

    \<"TempDir" > ist der Name des Ordners aus Schritt d fort.

   * Löschen Sie die Dateien aus dem vorhandenen Verzeichnis der SQL Server-Daten. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    rm - f /var/opt/mssql/data/*
    ```

   * Stellen Sie sicher, dass die Dateien gelöscht wurden. 

    ```bash
    ls /var/opt/mssql/data
    ```
    
   * Geben Sie beenden, wechseln zurück an den Root-Benutzer.

   * Binden Sie die NFS-Freigabe in der SQL Server-Datenordner. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > ist die IP-Adresse der NFS-Server, die verwendet werden 

    \<FolderOnNFSServer > ist der Name des der NFS-Freigabe. Die folgende Beispielsyntax entspricht die NFS-Informationen aus Schritt2.

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

   * Überprüfen, ob die Bereitstellung erfolgreich war, indem Sie die Bereitstellung ohne Schalter ausgeben.

    ```bash
    mount
    ```

    ![10-mountnoswitches][2]

   * Wechseln Sie zu der Mssql-Benutzer. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    su mssql
    ```

   * Kopieren Sie die Dateien aus dem temporären Verzeichnis /var/opt/mssql/data. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssqldata
    ```

   * Stellen Sie sicher, dass die Dateien vorhanden sind.

    ```bash
    ls /var/opt/mssql/data
    ```

   * Geben Sie beenden, um nicht mssql 
    
   * Geben Sie beenden, um das Root nicht verwendet werden

   * Start SQL Server. Wenn alles richtig kopiert wurde und angewendeten Sicherheitsfunktionen ordnungsgemäß SQL Server zeigen sollte, wie gestartet.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
    
   * Erstellen Sie eine Datenbank zum Testen, ob die Sicherheit ordnungsgemäß eingerichtet ist. Das folgende Beispiel zeigt, die über Transact-SQL ausgeführt wird; Er kann über SSMS ausgeführt werden.
 
    ![CreateTestdatabase][3]

   * Beenden Sie SQL Server, und stellen Sie sicher, dass es heruntergefahren ist.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   * Wenn Sie keine anderen NFS-Bereitstellungen erstellen, die Bereitstellung heben Sie die Freigabe auf. Wenn Sie sind, nicht aufheben der Bereitstellung.

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > ist die IP-Adresse der NFS-Server, die verwendet werden

    \<FolderOnNFSServer > ist der Name des der NFS-Freigabe

    \<FolderMountedIn > ist der Ordner, der im vorherigen Schritt erstellt haben. 

4. Für etwas anderes als ein Systemdatenbanken, z. B. Benutzerdatenbanken oder Backups die folgenden Schritte aus. Wenn Sie nur den Standardspeicherort zu verwenden, fahren Sie mit Schritt 5 fort.

   * Wechseln Sie zu der Superuser sein. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    sudo -i
    ```

   * Erstellen Sie einen Ordner, der von SQL Server verwendet wird. 

    ```bash
    mkdir <FolderName>
    ```

    \<Ordnername > ist der Name des Ordners. Vollständiger Pfad des Ordners muss angegeben werden, sofern Sie nicht den richtigen Speicherort. Das folgende Beispiel erstellt einen Ordner namens /var/opt/mssql/userdata.

    ```bash
    mkdir /var/opt/mssql/userdata
    ```

   * Binden Sie die NFS-Freigabe, in dem Ordner, der im vorherigen Schritt erstellt wurde. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    Mount -t nfs4 <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn> -o nfsvers=4.2,timeo=14,intr
    ```

    \<IPAddressOfNFSServer > ist die IP-Adresse der NFS-Server, die verwendet werden

    \<FolderOnNFSServer > ist der Name des der NFS-Freigabe

    \<FolderToMountIn > ist der Ordner, der im vorherigen Schritt erstellt haben. Im folgenden ist ein Beispiel. 

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci2 /var/opt/mssql/userdata -o nfsvers=4.2,timeo=14,intr
    ```

   * Überprüfen, ob die Bereitstellung erfolgreich war, indem Sie die Bereitstellung ohne Schalter ausgeben.
  
   * Geben Sie beenden, um die Benutzer mit Administratorrechten nicht mehr.

   * Um zu testen, erstellen Sie eine Datenbank in diesem Ordner. Im folgenden Beispiel wird Sqlcmd, erstellen Sie eine Datenbank, damit den Kontext wechseln, überprüfen die Dateien vorhanden sind, auf der Betriebssystemebene und löscht dann den temporären Speicherort. Sie können SSMS verwenden.

    ![15-createtestdatabase][4]
 
   * Aufheben der Freigabe 

    ```bash
    sudo umount <IPAddressOfNFSServer>:<FolderOnNFSServer> <FolderToMountIn>
    ```

    \<IPAddressOfNFSServer > ist die IP-Adresse der NFS-Server, die verwendet werden
    
    \<FolderOnNFSServer > ist der Name des der NFS-Freigabe

    \<FolderMountedIn > ist der Ordner, der im vorherigen Schritt erstellt haben. Im folgenden ist ein Beispiel. 
 
5. Wiederholen Sie die Schritte in den anderen Knoten aus.


## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren Sie Failoverclusterinstanz – SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/05-nfsacl.png
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/10-mountnoswitches.png
[3]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/20-createtestdatabase.png
[4]: ./media/sql-server-linux-shared-disk-cluster-configure-nfs/15-createtestdatabase.png
