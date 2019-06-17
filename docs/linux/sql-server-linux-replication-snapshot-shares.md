---
title: Konfigurieren von SQL Server-Replikation momentaufnahmefreigaben Ordner unter Linux | Microsoft-Dokumentation
description: Dieser Artikel beschreibt, wie SQLServer-Replikation von Momentaufnahmen Ordner Freigaben unter Linux konfigurieren.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 09/24/2018
ms.topic: article
ms.prod: sql
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 7569eaf92484038e998595405df42dd1f2d31b3d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718155"
---
# <a name="configure-replication-snapshot-folder-with-shares"></a>Konfigurieren Sie die Ordner des Replikations-Momentaufnahme mit Dateifreigaben

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Der momentaufnahmeordner ist ein Verzeichnis, das Sie als Freigabe festgelegt haben. Agents, die Lese- und Schreibzugriff auf diesen Ordner müssen ausreichende Berechtigungen für den Zugriff haben.

![Diagramm der Replikation][1]

### <a name="replication-snapshot-folder-share-explained"></a>Replikation Ordner Momentaufnahmefreigabe erläutert

Bevor Sie die Beispiele betrachten wie Samba-Freigaben von SQL Server bei der Replikation verwendet. Es folgt ein einfaches Beispiel, wie dies funktioniert.

1. Samba-Freigaben werden konfiguriert, die Dateien geschrieben, um `/local/path1` die Replikation-Agents auf dem Verleger angezeigt werden können, vom Abonnenten
2. SQL Server für die Verwendung konfiguriert freigabepfade beim Einrichten des Verlegers auf den Verteilungsserver so, dass alle Instanzen ansehen würden die `//share/path`
3. SQL Server findet den lokalen Pfad aus dem `//share/path` wissen, wo nach Dateien gesucht werden soll
4. SQL Server-Lese-und Schreibvorgänge auf lokale Pfade, die gesichert werden, indem Sie einen Samba-Freigabe


## <a name="configure-a-samba-share-for-the-snapshot-folder"></a>Konfigurieren Sie eine Samba-Freigabe für den momentaufnahmeordner 

Replikations-Agents benötigen ein freigegebenes Verzeichnis zwischen Hosts der Replikation auf Snapshot-Ordner auf andere Computer zugreifen. Beispielsweise befindet sich im transaktionalen Pull-Replikation der Verteilungs-Agent auf dem Abonnenten, der Zugriff auf dem Verteiler für die erste Artikel erfordert. In diesem Abschnitt werden wir ein Beispiel so konfigurieren Sie eine Samba-Freigabe auf zwei Hosts der Replikation durchlaufen.


## <a name="steps"></a>Schritte

Als Beispiel konfigurieren wir einen Standardordner für momentaufnahmeordner auf dem Host 1 (dem Verteiler), Host 2 (Abonnent), Samba Verwendung freigegeben werden. 

### <a name="install-and-start-samba-on-both-machines"></a>Installieren Sie und starten Sie auf beiden Computern Samba 

On Ubuntu:

```bash
sudo apt-get -y install samba
sudo service smbd restart
```

Unter RHEL:

```bash
sudo yum install samba
sudo service smb start
sudo service smb status
```

### <a name="on-host-1-distributor-set-up-the-samba-share"></a>Auf Host 1 (Verteiler) richten die Samba-Freigabe 

1. Setup-Benutzer und das Kennwort für Samba:

  ```bash
  sudo smbpasswd -a mssql 
  ```

1. Bearbeiten der `/etc/samba/smb.conf` auf den folgenden Eintrag enthalten, und geben Sie die *Freigabename* und *Pfad* Felder
 ```bash
  <[share_name]>
  path = </local/path/on/host/1>
  writable = yes
  create mask = 770
  directory mask 
  valid users = mssql 
  ```

  **Beispiel**

  ```bash
  [mssql_data]    <- Name of the shared directory
  path = /var/opt/mssql/repldata <- location of directory we wish to share
  writable = yes  <- determines if the share is writable from other hosts
  create mask = 770  <- Linux permissions for files created 
  directory mask = 770 <- Linux permissions for directories created
  valid users = mssql   <- list of users who can login to this share
  ```

### <a name="on-host-2-subscriber--mount-the-samba-share"></a>Stellen Sie die Samba-Freigabe, auf dem Host 2 (Abonnent)

Bearbeiten Sie den Befehl durch die richtigen Pfade aus, und führen Sie den folgenden Befehl in "machine2":

  ```bash
  sudo mount //<name_of_host_1>/<share_name> </local/path/on/host/2> -o user=mssql,uid=mssql,gid=mssql
  ```

  **Beispiel**

  ```bash
  mount //host1/mssql_data /var/opt/mssql/repldata_shared -o user=mssql,uid=mssql,gid=mssql

  user=mssql <- sets the login name for samba
  uid=mssql   <- makes the mssql user as the owner of the mounted directory
  gid=mssql   <- sets the mssql group as the owner of the mounted directory
  ```

### <a name="on-both-hosts--configure-sql-server-on-linux-instances-to-use-snapshot-share"></a>Auf beiden Hosts konfigurieren von SQL Server für Linux-Instanzen, verwenden Sie die Momentaufnahmefreigabe

Fügen Sie folgenden Abschnitt auf `mssql.conf` auf beiden Computern. Verwenden Sie immer das Samba-Freigabe für den / / / Freigabepfad. In diesem Beispiel wäre dies `//host1/mssql_data`

  ```bash
  [uncmapping]
  //share/path = /local/path/on/hosts/
  ```

  **Beispiel**

  Klicken Sie auf "host1":

  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/1
  ```

  Auf host2:
  
  ```bash
  [uncmapping]
  //host1/mssql_data = /local/path/on/hosts/2
  ```

### <a name="configuring-publisher-with-shared-paths"></a>Konfigurieren des Verlegers mit Shared-Pfaden

* Beim Einrichten der Replikation verwenden Sie den Freigaben-Pfad (z. B. `//host1/mssql_data`
* Zuordnung `//host1/mssql_data` auf einem lokalen Verzeichnis und die Zuordnung hinzugefügt `mssql.conf`.

## <a name="next-steps"></a>Nächste Schritte

[Konzepte: SQL Server-Replikation unter Linux](sql-server-linux-replication.md)

[Gespeicherte Replikationsprozeduren](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md).

[1]: ./media/sql-server-linux-replication-snapshot-shares/image1.png
