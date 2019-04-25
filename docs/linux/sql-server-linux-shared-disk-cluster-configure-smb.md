---
title: Konfigurieren Sie die Instanz failoverclusterspeicher SMB – SQL Server unter Linux | Microsoft-Dokumentation
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: e93f85302417674b31de0129650dbb85092f8962
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62634158"
---
# <a name="configure-failover-cluster-instance---smb---sql-server-on-linux"></a>Konfigurieren der Failoverclusterinstanz – SMB – SQL Server unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

In diesem Artikel wird erläutert, wie zum Konfigurieren des Linux SMB-Speicher für eine Failoverclusterinstanz (FCI) werden. 
 
In der nicht-Windows-Welt ist SMB häufig zum Freigeben von als ein Common Internet File System (CIFS) bezeichnet und über Samba implementiert. In der Windows-Welt auf eine SMB-Dateifreigabe zugreifen auf diese Weise erfolgt: \\SERVERNAME\FREIGABENAME. Für Linux-basierten SQL Server-Installationen muss die SMB-Freigabe als Ordner bereitgestellt werden.

## <a name="important-source-and-server-information"></a>Wichtige Informationen zu Quelle und server

Hier sind einige Tipps und Hinweise für die erfolgreiche Verwendung von SMB:
- Die SMB-Freigabe kann auf Windows, Linux oder sogar von einer Appliance wie lange ist es mithilfe von SMB 3.0 oder höher sein. Weitere Informationen zu Samba als auch SMB 3.0, finden Sie unter [SMB 3.0](https://wiki.samba.org/index.php/Samba3/SMB2#SMB_3.0) um festzustellen, ob Ihre Samba-Implementierung mit SMB 3.0 kompatibel ist.
- Die SMB-Freigabe sollte hoch verfügbar sein.
- Sicherheit muss festgelegt werden, ordnungsgemäß auf die SMB-Freigabe. Unten ist ein Beispiel von /etc/samba/smb.conf, wobei SQLData1 den Namen der Freigabe.

![05-smbsource][1]

## <a name="instructions"></a>Instructions

1.  Wählen Sie einen der Server, die einbezogen werden, in der FCI-Konfiguration. Es spielt keine Rolle die.

2.  Abrufen von Informationen zu den Mssql-Benutzer.

    ```bash
    sudo id mssql
    ```
    
    Beachten Sie die Benutzer-ID, Gid und Gruppen. 

3. Führen Sie `sudo smbclient -L //NameOrIP/ShareName -U User`.

    \<NameOrIP > ist der DNS-Namen oder die IP-Adresse des Servers mit der SMB-Freigabe.

    \<ShareName > ist der Name der SMB-Freigabe. 

4. System o. Datenbanken gespeichert, die am Standardspeicherort für die Daten gehen Sie folgendermaßen vor. Andernfalls fahren Sie mit Schritt 5 fort. 

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

    <TempDir> ist der Name des Ordners. Das folgende Beispiel erstellt einen Ordner namens /var/opt/mssql/tmp.

    ```bash
    mkdir /var/opt/mssql/tmp
    ```

   *    Kopieren Sie die SQL Server-Daten und Protokolldateien-Dateien in das temporäre Verzeichnis. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    cp /var/opt/mssql/data/* <TempDir>
    ```

    \<"TempDir" > ist der Name des Ordners aus dem vorherigen Schritt.
    
   *    Stellen Sie sicher, dass die Dateien im Verzeichnis.

    ```bash
    ls <TempDir>
    ```

    \<"TempDir" > ist der Name des Ordners aus Schritt d fort.
    
   *    Löschen Sie die Dateien aus dem vorhandenen Verzeichnis der SQL Server-Daten. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.
 
    ```bash
    rm - f /var/opt/mssql/data/*
    ```

   *    Stellen Sie sicher, dass die Dateien gelöscht wurden. 

    ```bash
    ls /var/opt/mssql/data
    ```
 
   *    Geben Sie beenden, wechseln zurück an den Root-Benutzer.

   *    Stellen Sie die SMB-Freigabe in der SQL Server-Datenordner. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung. Dieses Beispiel zeigt die Syntax für die Verbindung mit einer Windows Server-basierten SMB 3.0-Freigabe.

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> /var/opt/mssql/data -o vers=3.0,username=<UserName>,password=<Password>,domain=<domain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<ServerName > ist der Name des Servers mit der SMB-Freigabe
    
    \<ShareName > ist der Name der Freigabe

    \<Benutzername > ist der Name des Benutzers, der Zugriff auf die Dateifreigabe

    \<Kennwort > ist das Kennwort für den Benutzer

    \<Domäne > ist der Name des Active Directory

    \<MssqlUID > ist die UID die Mssql-Benutzer 
 
    \<MssqlGID > ist die GID von der Mssql-Benutzer
 
   *    Überprüfen, ob die Bereitstellung erfolgreich war, indem Sie die Bereitstellung ohne Schalter ausgeben.

    ```bash
    mount
    ```
 
   *    Wechseln Sie zu der Mssql-Benutzer. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    su mssql
    ```

   *    Kopieren Sie die Dateien aus dem temporären Verzeichnis /var/opt/mssql/data. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung.

    ```bash
    cp /var/opt/mssql/tmp/* /var/opt/mssql/data
    ```

   *    Stellen Sie sicher, dass die Dateien vorhanden sind.

    ```bash
    ls /var/opt/mssql/data
    ```

   *    Geben Sie beenden, um nicht mssql 

   *    Geben Sie beenden, um das Root nicht verwendet werden

   *    Start SQL Server. Wenn alles richtig kopiert wurde und angewendeten Sicherheitsfunktionen ordnungsgemäß SQL Server zeigen sollte, wie gestartet.

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    ```
 
   *    Um weitere zu testen, erstellen Sie eine Datenbank, um sicherzustellen, dass die Berechtigungen in Ordnung sind. Im folgenden Beispiel wird die Transact-SQL; Sie können SSMS verwenden.

    ![10_testcreatedb][2] 
  
   *    Beenden Sie SQL Server, und stellen Sie sicher, dass es heruntergefahren ist. Wenn Sie zum Hinzufügen oder anderen Datenträgern testen möchten, nicht ausgeschaltet werden SQL Server, bis die hinzugefügt und getestet werden.

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl status mssql-server
    ```

   *    Nur, wenn Sie fertig sind, heben Sie die Freigabe. Wenn dies nicht der Fall ist, heben Sie nach Abschluss der Tests/zusätzliche Datenträger hinzufügen.

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName /<FolderMountedIn>
    ```

    \<IPAddressOrServerName > ist die IP-Adresse oder den Namen des SMB-Hosts

    \<ShareName > ist der Name der Freigabe
    
    \<FolderMountedIn > ist der Name des Ordners, in denen SMB eingebunden ist,

5.  Für etwas anderes als ein Systemdatenbanken, z. B. Benutzerdatenbanken oder Backups die folgenden Schritte aus. Wenn Sie nur den Standardspeicherort zu verwenden, fahren Sie mit Schritt 14 fort.
    
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

   *    Stellen Sie die SMB-Freigabe in der SQL Server-Datenordner. Sie erhalten Bestätigung nicht bei erfolgreicher Ausführung. Dieses Beispiel zeigt die Syntax für die Verbindung mit einer Samba-basierte SMB 3.0-Freigabe.

    ```bash
    Mount -t cifs //<ServerName>/<ShareName> <FolderName> -o vers=3.0,username=<UserName>,password=<Password>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777
    ```

    \<ServerName > ist der Name des Servers mit der SMB-Freigabe

    \<ShareName > ist der Name der Freigabe

    \<Ordnername > ist der Name des Ordners im letzten Schritt erstellt haben  

    \<Benutzername > ist der Name des Benutzers, der Zugriff auf die Dateifreigabe

    \<Kennwort > ist das Kennwort für den Benutzer

    \<MssqlUID > ist die UID die Mssql-Benutzer

    \<MssqlGID > ist die GID von der Mssql-Benutzer.
 
   * Überprüfen, ob die Bereitstellung erfolgreich war, indem Sie die Bereitstellung ohne Schalter ausgeben.
 
   * Geben Sie beenden, um die Benutzer mit Administratorrechten nicht mehr.

   * Um zu testen, erstellen Sie eine Datenbank in diesem Ordner. Im folgenden Beispiel wird Sqlcmd, erstellen Sie eine Datenbank, damit den Kontext wechseln, überprüfen die Dateien vorhanden sind, auf der Betriebssystemebene und löscht dann den temporären Speicherort. Sie können SSMS verwenden.
 
   * Aufheben der Freigabe 

    ```bash
    sudo umount //<IPAddressorServerName>/<ShareName> /<FolderMountedIn>
    ```
    
    \<IPAddressOrServerName > ist die IP-Adresse oder den Namen des SMB-Hosts
 
    \<ShareName > ist der Name der Freigabe
 
    \<FolderMountedIn > ist der Name des Ordners, in denen SMB bereitgestellt wird.
 
6.  Wiederholen Sie die Schritte in den anderen Knoten aus.

Sie können nun zum Konfigurieren der FCI.

## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren Sie Failoverclusterinstanz – SQL Server unter Linux](sql-server-linux-shared-disk-cluster-configure.md)

<!--Image references-->
[1]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/05-smbsource.png 
[2]: ./media/sql-server-linux-shared-disk-cluster-configure-smb/10-testcreatedb.png 
