---
title: Sichern und Wiederherstellen von SQL Server-Datenbanken unter Linux | Microsoft-Dokumentation
description: Informationen Sie zum Sichern und Wiederherstellen von SQL Server-Datenbanken unter Linux.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/14/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: d30090fb-889f-466e-b793-5f284fccc4e6
ms.openlocfilehash: 6e4699fb2ffadc3aaad73c4032073ff8567c856c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38006092"
---
# <a name="backup-and-restore-sql-server-databases-on-linux"></a>Sichern und Wiederherstellen der SQL Server-Datenbanken unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Sie können Sicherungen der Datenbanken von SQL Server 2017 unter Linux mit den gleichen Tools wie andere Plattformen nutzen. Sie können auf einem Linux-Server verwenden **Sqlcmd** zum Verbinden mit SQL Server, und erstellen Sie Sicherungen. Von Windows können Sie eine Verbindung mit SQL Server unter Linux herstellen und erstellen Sie Sicherungen mit der Benutzeroberfläche. Die Sicherungsfunktion ist für Plattformen gleich. Beispielsweise können Sie Datenbanken sichern, lokal, remote-Laufwerke oder zu [Microsoft Azure-Blob-Speicherdienst](../relational-databases/backup-restore/sql-server-backup-to-url.md).

## <a name="backup-a-database"></a>Sichern einer Datenbank

Im folgenden Beispiel **Sqlcmd** eine Verbindung mit lokalen SQL Server-Instanz her und nimmt eine vollständige Sicherung einer Benutzerdatenbank wird aufgerufen, `demodb`.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP DATABASE [demodb] TO DISK = N'/var/opt/mssql/data/demodb.bak' WITH NOFORMAT, NOINIT, NAME = 'demodb-full', SKIP, NOREWIND, NOUNLOAD, STATS = 10"
```

Wenn Sie den Befehl ausführen, wird SQL Server ein Kennwort einzugeben. Nachdem Sie das Kennwort eingegeben haben, werden die Shell den Sicherungsstatus zurückgegeben. Zum Beispiel:

```
Password:
10 percent processed.
21 percent processed.
32 percent processed.
40 percent processed.
51 percent processed.
61 percent processed.
72 percent processed.
80 percent processed.
91 percent processed.
Processed 296 pages for database 'demodb', file 'demodb' on file 1.
100 percent processed.
Processed 2 pages for database 'demodb', file 'demodb_log' on file 1.
BACKUP DATABASE successfully processed 298 pages in 0.064 seconds (36.376 MB/sec).
```

### <a name="backup-the-transaction-log"></a>Sichern des Transaktionsprotokolls

Wenn Ihre Datenbank in das vollständige Wiederherstellungsmodell verwendet wird, können Sie auch Sicherungen des Transaktionsprotokolls für eine feiner abgestimmte Wiederherstellungsoptionen vornehmen. Im folgenden Beispiel **Sqlcmd** eine Verbindung mit lokalen SQL Server-Instanz her und nimmt ein Transaktionsprotokoll sichern.

```bash
sqlcmd -S localhost -U SA -Q "BACKUP LOG [demodb] TO DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak' WITH NOFORMAT, NOINIT, NAME = N'demodb_LogBackup', NOSKIP, NOREWIND, NOUNLOAD, STATS = 5"
```

## <a name="restore-a-database"></a>Wiederherstellen einer Datenbank

Im folgenden Beispiel **Sqlcmd** eine Verbindung mit der lokalen Instanz von SQL Server her, und die Demodb-Datenbank wieder her. Beachten Sie, dass die `NORECOVERY` Option wird verwendet, um weitere Wiederherstellungen von protokollsicherungen für die Datei zu ermöglichen. Wenn Sie nicht beabsichtigen, um zusätzliche Protokolldateien bei wiederherzustellen, entfernen Sie die `NORECOVERY` Option.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE DATABASE [demodb] FROM DISK = N'/var/opt/mssql/data/demodb.bak' WITH FILE = 1, NOUNLOAD, REPLACE, NORECOVERY, STATS = 5"
```

> [!TIP]
> Wenn Sie versehentlich WITH NORECOVERY, aber keine zusätzliche protokollsicherungen-Datei, führen Sie den Befehl `RESTORE DATABASE demodb` ohne zusätzliche Parameter. Dies schließt die Wiederherstellung ab und belässt die Datenbank betriebsbereit.

### <a name="restore-the-transaction-log"></a>Wiederherstellen des Transaktionsprotokolls

Die folgenden Befehl wird die vorherige Sicherung des Transaktionsprotokolls wiederhergestellt.

```bash
sqlcmd -S localhost -U SA -Q "RESTORE LOG demodb FROM DISK = N'/var/opt/mssql/data/demodb_LogBackup.bak'"
```

## <a name="backup-and-restore-with-sql-server-management-studio-ssms"></a>Sichern und Wiederherstellen mit SQL Server Management Studio (SSMS)

Sie können SSMS auf einem Windows-Computer verwenden, um eine Verbindung mit einer Linux-Datenbank, und erstellen Sie eine Sicherung über die Benutzeroberfläche.

>[!NOTE] 
> Verwenden Sie die neueste Version von SSMS eine Verbindung mit SQL Server herstellen. Zum Herunterladen und installieren die neueste Version, finden Sie unter [Herunterladen von SSMS](../ssms/download-sql-server-management-studio-ssms.md). Weitere Informationen zur Verwendung von SSMS finden Sie unter [SSMS verwenden, um die Verwaltung von SQL Server unter Linux](sql-server-linux-manage-ssms.md).

Die folgenden Schritte werden über eine Sicherung mit SSMS führen. 

1. Starten Sie SSMS, und Verbinden mit dem Server in SQL Server 2017 unter Linux.

1. Objekt-Explorer mit der Maustaste auf Ihre Datenbank, klicken Sie auf **Aufgaben**, und klicken Sie dann auf **sichern...** .

1. In der **Sicherung Datenbank** Dialogfeld, überprüfen Sie, den Parametern und Optionen, und klicken Sie auf **OK**.
 
SQL Server wird die Sicherung abgeschlossen.

### <a name="restore-with-sql-server-management-studio-ssms"></a>Wiederherstellen Sie mit SQL Server Management Studio (SSMS) 

Die folgenden Schritte führen Sie durch das Wiederherstellen einer Datenbank mit SSMS.

1. In SSMS mit der Maustaste **Datenbanken** , und klicken Sie auf **Wiederherstellen von Datenbanken...** . 

1. Klicken Sie unter **Quelle** klicken Sie auf **Gerät:** , und klicken Sie dann auf die Auslassungspunkte (...).

1. Suchen Sie die Sicherungsdatei der Datenbank, und klicken Sie auf **OK**. 

1. Klicken Sie unter **Wiederherstellungsplan**, überprüfen Sie die Sicherungsdatei und die Einstellungen. Klicken Sie auf **OK**. 

1. SQL Server stellt die Datenbank wieder her. 

## <a name="see-also"></a>Siehe auch

* [Erstellen einer vollständigen Datenbanksicherung (SQLServer)](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)
* [Sichern eines Transaktionsprotokolls (SQL Server)](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)
* [BACKUP (Transact-SQL)](../t-sql/statements/backup-transact-sql.md)
* [SQL Server-Sicherung über URLs](../relational-databases/backup-restore/sql-server-backup-to-url.md)
