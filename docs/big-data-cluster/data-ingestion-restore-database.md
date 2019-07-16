---
title: Wiederherstellen einer Datenbank
titleSuffix: SQL Server big data clusters
description: In diesem Artikel zeigt, wie zum Wiederherstellen einer Datenbank in der Masterinstanz von einer SQL Server-2019 big Data-Cluster (Vorschau) wird.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1ad5ca749f3862f0d7df3411efd78104052dba91
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958624"
---
# <a name="restore-a-database-into-the-sql-server-big-data-cluster-master-instance"></a>Wiederherstellen einer Datenbank in SQL Server big Data-Cluster master-Instanz

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel beschreibt, wie Sie eine vorhandene Datenbank auf der Masterinstanz von einer SQL Server-2019 big Data-Cluster (Vorschau) wiederherstellen. Die empfohlene Methode ist, verwenden Sie eine sicherungs-, Kopier-und Ansatz wiederherstellen.

## <a name="backup-your-existing-database"></a>Sichern Sie Ihre vorhandene Datenbank

Sichern Sie zunächst Ihre vorhandenen SQL Server-Datenbank über entweder SQL Server auf Windows oder Linux. Verwenden Sie die Standardverfahren für die Sicherung mit Transact-SQL oder mit einem Tool wie SQL Server Management Studio (SSMS).

In diesem Artikel zeigt, wie Sie die AdventureWorks-Datenbank wiederherstellen, jedoch können Sie datenbanksicherung. 

> [!TIP]
> Sie können die AdventureWorks-Sicherung [hier](https://www.microsoft.com/download/details.aspx?id=49502).

## <a name="copy-the-backup-file"></a>Kopieren der Sicherungsdatei

Kopieren der Sicherungsdatei auf den SQL Server-Container in den Pod-Masterinstanz des Kubernetes-Clusters an.

```bash
kubectl cp <path to .bak file> mssql-master-pool-0:/tmp -c mssql-server -n <name of your big data cluster>
```

Beispiel:

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-master-pool-0:/tmp -c mssql-server -n clustertest
```

Anschließend stellen Sie sicher, dass die Sicherungsdatei in den Pod-Container kopiert wurde.

```bash
kubectl exec -it mssql-master-pool-0 -n <name of your big data cluster> -c mssql-server -- bin/bash
cd /var/
ls /tmp
exit
```

Beispiel:

```bash
kubectl exec -it mssql-master-pool-0 -n clustertest -c mssql-server -- bin/bash
ls /tmp
exit
```

## <a name="restore-the-backup-file"></a>Stellt die Sicherungsdatei

Anschließend stellen Sie die datenbanksicherung, um SQL Server-Masterinstanz.  Wenn Sie eine datenbanksicherung wiederherstellen, die für Windows erstellt wurde, müssen Sie die Namen der Dateien abzurufen.  Klicken Sie in Azure Data Studio eine Verbindung mit dem master her, und führen Sie dieses SQL-Skript:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

Beispiel:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![Liste der Sicherungsdatei](media/restore-database/database-restore-file-list.png)

Nun wird wiederherstellen Sie die Datenbank. Das folgende Skript ist ein Beispiel. Ersetzen Sie die Namen/Pfade je nach Ihren sicherungsanforderungen für die Datenbank nach Bedarf.

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

## <a name="configure-data-pool-and-hdfs-access"></a>Datenpool und HDFS-Zugriff konfigurieren

Führen Sie für die master SQL Server-Instanz, die Zugriff auf Datenpools und HDFS nun die Verfahren zum Daten-Pool und Pool gespeichert. Führen Sie die folgenden Transact-SQL-Skripts für Ihre neu wiederhergestellte Datenbank:

```sql
USE AdventureWorks2016CTP3
GO
-- Create the SqlDataPool data source:
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
  CREATE EXTERNAL DATA SOURCE SqlDataPool
  WITH (LOCATION = 'sqldatapool://controller-svc/default');

-- Create the SqlStoragePool data source:
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
   CREATE EXTERNAL DATA SOURCE SqlStoragePool
   WITH (LOCATION = 'sqlhdfs://controller-svc/default');
GO
```

> [!NOTE]
> Sie müssen zum Ausführen über diese Setupskripts nur für Datenbanken, die von älteren Versionen von SQL Server wiederhergestellt. Wenn Sie eine neue Datenbank in SQL Server-Masterinstanz erstellen, werden Daten Pool und Pool gespeicherte Prozeduren bereits für Sie konfiguriert.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter der Übersicht über die folgenden:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
