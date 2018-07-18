---
title: Migrieren eine SQL Server-Datenbank von Windows bis Linux | Microsoft-Dokumentation
description: In diesem Tutorial wird die Sicherung von SQL Server-Datenbank auf Windows und einfach auf einem Linux-Computer mit SQL Server 2017 veranschaulicht.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/16/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 9ac64d1a-9fe5-446e-93c3-d17b8f55a28f
ms.openlocfilehash: 559ae24a819cfff1172d1829ef3ca5e679a40122
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38020188"
---
# <a name="migrate-a-sql-server-database-from-windows-to-linux-using-backup-and-restore"></a>Migrieren einer SQL Server-Datenbank von Windows bis Linux, die mit Sicherung und Wiederherstellung

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server mit dem sicherungs- und Wiederherstellungsfunktion ist die empfohlene Methode zum Migrieren einer Datenbank von SQL Server unter Windows, SQL Server 2017 unter Linux. In diesem Tutorial führt Sie durch die erforderlichen Schritte zum Verschieben einer Datenbank in Linux mit Backup und Wiederherstellungsverfahren.

> [!div class="checklist"]
> * Erstellen einer Sicherungsdatei in Windows mit SSMS
> * Installieren Sie eine Bash-Shell auf Windows
> * Verschieben Sie die Sicherungsdatei mit Linux in der Bash-shell
> * Stellt die Sicherungsdatei für Linux mit Transact-SQL
> * Ausführen einer Abfrage zum Überprüfen der migration

Sie können auch eine SQL Server AlwaysOn-Verfügbarkeitsgruppe zum Migrieren von SQL Server-Datenbank von Windows bis Linux erstellen. Finden Sie unter [sql-server-linux-availability-group-cross-platform](sql-server-linux-availability-group-cross-platform.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

Die folgenden Voraussetzungen sind erforderlich, um dieses Lernprogramm abzuschließen:

* Windows-Computer mit den folgenden:
  * [SQL Server](https://www.microsoft.com/sql-server/sql-server-2016-editions) installiert.
  * [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) installiert.
  * Die Zieldatenbank zu migrieren.

* Linux-Computer Folgendes installiert:
  * SQL Server 2017 ([RHEL](quickstart-install-connect-red-hat.md), [SLES](quickstart-install-connect-suse.md), oder [Ubuntu](quickstart-install-connect-ubuntu.md)) mit Befehlszeilentools.

## <a name="create-a-backup-on-windows"></a>Erstellen Sie eine Sicherung für Windows

Es gibt mehrere Möglichkeiten, eine Datenbank eine Sicherungsdatei in Windows zu erstellen. Verwenden Sie die folgenden Schritte aus SQL Server Management Studio (SSMS) aus.

1. Starten Sie **SQL Server Management Studio** auf Ihrem Windows-Computer.

1. Geben Sie im Verbindungsdialogfeld **"localhost"**.

1. Erweitern Sie im Objekt-Explorer **Datenbanken**.

1. Mit der rechten Maustaste in der Zieldatenbank, wählen Sie **Aufgaben**, und klicken Sie dann auf **sichern...** .

   ![Verwenden Sie SSMS, um eine Sicherungsdatei erstellen](./media/sql-server-linux-migrate-restore-database/ssms-create-backup.png)

1. In der **Sicherung Datenbank** Dialogfeld, überprüfen Sie, ob **Sicherungstyp** ist **vollständige** und **Sichern auf** ist **Datenträger**. Notieren Sie den Namen und Speicherort der Datei. Z. B. eine Datenbank, die mit dem Namen **YourDB** auf SQL Server 2016 wurde eine Standardsicherungspfad von `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak`.

1. Klicken Sie auf **OK** , um Ihre Datenbank zu sichern.

> [!NOTE]
> Eine weitere Möglichkeit ist die Ausführung eine Transact-SQL-Abfrage, um die Sicherungsdatei zu erstellen. Die folgende Transact-SQL-Befehl führt die gleichen Aktionen wie die vorherigen Schritte für eine Datenbank namens **YourDB**:
>
> ```sql
> BACKUP DATABASE [YourDB] TO  DISK =
> N'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\YourDB.bak'
> WITH NOFORMAT, NOINIT, NAME = N'YourDB-Full Database Backup',
> SKIP, NOREWIND, NOUNLOAD, STATS = 10
> GO
> ```

## <a name="install-a-bash-shell-on-windows"></a>Installieren Sie eine Bash-Shell auf Windows

Um die Datenbank wiederherzustellen, müssen Sie zuerst die Sicherungsdatei auf dem Windows-Computer auf den Linux-Zielcomputer übertragen. In diesem Tutorial verschieben wir die Datei mit Linux über eine Bash-Shell (terminal-Fenster) auf Windows ausgeführt wird.

1. Installieren Sie eine Bash-Shell auf Ihrem Windows-Computer, die unterstützt die **scp** (secure Copy) und **ssh** -Befehle (remote-Anmeldung). Zwei Beispiele:

   * Die [Windows-Subsystem für Linux](https://msdn.microsoft.com/commandline/wsl/about) (Windows 10)
   * Die Git Bash-Shell ([https://git-scm.com/downloads](https://git-scm.com/downloads))

1. Öffnen Sie eine Bash-Sitzung, auf Windows.

## <a id="scp"></a> Kopieren der Sicherungsdatei auf Linux

1. Navigieren Sie zu dem Verzeichnis, das die Sicherungsdatei enthält, in der Bash-Sitzung. Zum Beispiel:

   ```bash
   cd 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Backup\'
   ```

1. Verwenden der **scp** Befehl aus, um die Datei auf dem Ziel-Linux-Computer übertragen. Das folgende Beispiel-Übertragungen **YourDB.bak** in das Stammverzeichnis des *"user1"* auf dem Linux-Server mit IP-Adresse *192.0.2.9*:

   ```bash
   scp YourDB.bak user1@192.0.2.9:./
   ```
   ![SCP-Befehl](./media/sql-server-linux-migrate-restore-database/scp-command.png)

> [!TIP]
> Es gibt Alternativen zur Verwendung von scp für die Übertragung von Dateien. Eine ist die Verwendung [Samba](https://help.ubuntu.com/community/Samba) so konfigurieren Sie eine SMB-Netzwerkfreigabe zwischen Windows und Linux. Eine exemplarische Vorgehensweise unter Ubuntu finden Sie unter [Vorgehensweise: Erstellen einer Netzwerk-Dateifreigabe über Samba](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!). Sobald eingerichtet, können Sie darauf zugreifen, als Netzwerkdatei Freigeben von Windows, z. B.  **\\ \\Machinenameorip\\freigeben**.

## <a name="move-the-backup-file-before-restoring"></a>Verschieben Sie vor dem Wiederherstellen der Sicherungsdatei

An diesem Punkt wird die Sicherungsdatei auf dem Linux-Server im Basisverzeichnis des Benutzers ein. Sie müssen die Sicherung vor dem Wiederherstellen der Datenbank zu SQL Server platzieren, in einem Unterverzeichnis des **/var/opt/mssql**.

1. In der gleichen Windows Bash-Sitzung Herstellen einer Remoteverbindung mit Ihrem Linux-Zielcomputer mit **ssh**. Im folgenden Beispiel wird eine Verbindung mit dem Linux-Computer her. **192.0.2.9** als Benutzer **"user1"**.

   ```bash
   ssh user1@192.0.2.9
   ```

   Sie sind jetzt Befehle auf dem Linux-Remoteserver ausführen.

1. Geben Sie die Administrator-Modus.

   ```bash
   sudo su
   ```

1. Erstellen Sie ein neues Verzeichnis für die Sicherung. Der Parameter "-p" führt keine Aktion aus, wenn das Verzeichnis bereits vorhanden ist.

   ```bash
   mkdir -p /var/opt/mssql/backup
   ```

1. Verschieben Sie die Sicherungsdatei auf das Verzeichnis an. Im folgenden Beispiel wird die Sicherungsdatei im home-Verzeichnis befindet *"user1"*. Ändern Sie den Befehl mit dem Speicherort und Namen der backup-Datei übereinstimmen.

   ```bash
   mv /home/user1/YourDB.bak /var/opt/mssql/backup/
   ```

1. Administrator-Modus beenden.

   ```bash
   exit
   ```

## <a name="restore-your-database-on-linux"></a>Wiederherstellen der Datenbank unter Linux

Um die datenbanksicherung wiederherzustellen, können Sie die **RESTORE DATABASE** Transact-SQL (TQL)-Befehl.

> [!NOTE]
> Die folgenden Schritte verwenden den **Sqlcmd** Tool. Wenn Sie noch nicht installiert SQL Server-Tools finden Sie unter [Installieren von SQL Server-Befehlszeilentools für Linux](sql-server-linux-setup-tools.md).

1. Starten Sie in der gleichen Terminal **Sqlcmd**. Im folgenden Beispiel wird eine Verbindung herstellt, mit der lokalen SQL Server-Instanz mit der **SA** Benutzer. Geben Sie das Kennwort, wenn Sie aufgefordert werden, oder geben Sie das Kennwort durch das Hinzufügen der **-P** Parameter.

   ```bash
   sqlcmd -S localhost -U SA
   ```

1. Auf der `>1` dazu aufgefordert werden, geben Sie den folgenden **RESTORE DATABASE** Befehl ein, Drücken der EINGABETASTE nach jeder Zeile (Sie können keine kopieren und Einfügen den gesamten mehrzeiligen Befehl gleichzeitig). Ersetzen Sie alle Vorkommen von `YourDB` mit dem Namen Ihrer Datenbank.

   ```sql
   RESTORE DATABASE YourDB
   FROM DISK = '/var/opt/mssql/backup/YourDB.bak'
   WITH MOVE 'YourDB' TO '/var/opt/mssql/data/YourDB.mdf',
   MOVE 'YourDB_Log' TO '/var/opt/mssql/data/YourDB_Log.ldf'
   GO
   ```

   Sie sollten eine Meldung erhalten, die die Datenbank erfolgreich wiederhergestellt wird.

1. Überprüfen Sie die Wiederherstellung, indem Sie alle Datenbanken auf dem Server auflisten. Die wiederhergestellte Datenbank sollte aufgeführt sein.

   ```sql
   SELECT Name FROM sys.Databases
   GO
   ```

1. Andere Abfragen der migrierten Datenbank ausführen. Der folgende Befehl einen Kontextwechsel auf die **YourDB** Datenbank und wählt die Zeilen aus einer Tabelle.

   ```sql
   USE YourDB
   SELECT * FROM YourTable
   GO
   ```

1. Wenn Sie fertig sind mit **Sqlcmd**, Typ `exit`.

1. Wenn Sie fertig sind arbeiten in der Remotetabelle **ssh** "Sitzung", Typ `exit` erneut aus.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie zum Sichern einer Datenbank auf Windows und verschieben Sie es auf einem Linux-Server, SQL Server 2017 ausgeführt wird. Sie haben gelernt, wie auf:
> [!div class="checklist"]
> * Verwenden von SSMS und Transact-SQL zum Erstellen einer Sicherungsdatei in Windows
> * Installieren Sie eine Bash-Shell auf Windows
> * Verwendung **scp** Sicherungsdateien von Windows bis Linux zu verschieben.
> * Verwendung **ssh** eine Remoteverbindung mit Ihrem Linux-Computer herstellen
> * Verschieben Sie die backup-Datei zur Vorbereitung der Wiederherstellung
> * Verwendung **Sqlcmd** zum Ausführen von Transact-SQL-Befehlen
> * Wiederherstellen der datenbanksicherung durch die **RESTORE DATABASE** Befehl 
> * Führen Sie die Abfrage zum Überprüfen der migration

Als Nächstes untersuchen Sie andere Migrationsszenarien für SQL Server unter Linux. 

> [!div class="nextstepaction"]
>[Migrieren von Datenbanken zu SQL Server unter Linux](sql-server-linux-migrate-overview.md)
