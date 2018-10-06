---
title: Wiederherstellen einer Datenbank in SQL Server-big Data-Cluster | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 04514fb0184fa28e0ba959f3dd33cb2e1ec945cb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796447"
---
# <a name="restore-a-database-into-the-sql-server-big-data-cluster-master-instance"></a>Wiederherstellen einer Datenbank in SQL Server big Data-Cluster master-Instanz

Um einer vorhandenen SQL Server-Datenbank die master-Instanz zu erreichen, wird empfohlen, mithilfe einer Sicherung, kopieren und Wiederherstellen von Ansatz.  In diesem Beispiel erfahren Sie, wie die AdventureWorks-Datenbank wiederherstellen, aber Sie können datenbanksicherung, die Sie verwenden.  Sie können die AdventureWorks-Sicherung [hier](https://www.microsoft.com/en-us/download/details.aspx?id=49502).

Sichern Sie zunächst Ihre vorhandenen SQL Server-Datenbank auf beiden SQL-Server unter Windows oder Linux, die mit einer der üblichen Methoden zum Erstellen einer datenbanksicherung.

Kopieren der Sicherungsdatei auf den SQL Server-Container in den Pod-Masterinstanz des Kubernetes-Clusters an.

```bash
kubectl cp <path to .bak file> mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n <name of your cluster>
```

Beispiel:

```bash
kubectl cp ~/Downloads/AdventureWorks2016CTP3.bak mssql-data-pool-master-0:/tmp/ -c mssql-data-pool-data -n clustertest
```

Anschließend stellen Sie sicher, dass die Sicherungsdatei in den Pod-Container kopiert wurde.

```bash
kubectl exec -it mssql-data-pool-master-0 -n <name of your cluster> -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
root@mssql-data-pool-master-0:/# exit
```

Beispiel:

```bash
kubectl exec -it mssql-data-pool-master-0 -n clustertest -c mssql-data-pool-data -- bin/bash
root@mssql-data-pool-master-0:/# ls /tmp
```

Anschließend stellen Sie die datenbanksicherung, um SQL Server-Masterinstanz.  Wenn Sie eine datenbanksicherung wiederherstellen, die für Windows erstellt wurde, müssen Sie die Namen der Dateien abzurufen.  Führen Sie folgende SQL-Skript, in Ops-Studio, die mit der master-Instanz verbunden:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/<db file name>.bak'
```

Beispiel:

```sql
RESTORE FILELISTONLY FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
```

![Liste der Sicherungsdatei](media/restore-database/database-restore-file-list.png)

Jetzt Wiederherstellen der Datenbank mit einem Skript wie folgt, und Ersetzen Sie dabei die Namen/Pfade je nach Ihren sicherungsanforderungen für die Datenbank nach Bedarf.

```sql
RESTORE DATABASE AdventureWorks2016CTP3
FROM DISK='/tmp/AdventureWorks2016CTP3.bak'
WITH MOVE 'AdventureWorks2016CTP3_Data' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Data.mdf',
        MOVE 'AdventureWorks2016CTP3_Log' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_Log.ldf',
        MOVE 'AdventureWorks2016CTP3_mod' TO '/var/opt/mssql/data/AdventureWorks2016CTP3_mod'
```

Nun, wenn Sie möchten werden Ihre hochwertigen-Datenbank Datenpools für die zugreifen, die Sie mit der Einrichtung die Datenpool Prozeduren benötigen, gespeicherte indem Sie öffnen und die Ausführung dieser Skripts aus dem GitHub-Repository.

Führen Sie die **High-Wert-Db-Configuration\data_pool_ddl_install. SQL** Skript.

- Setup-Unterstützung, die gespeicherten Prozeduren

Führen Sie die **High-Wert-Db-Configuration\supportability. SQL** Skript.
