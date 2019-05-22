---
title: Upgrade auf ein neues Release
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie SQL Server-2019 big Data-Cluster (Vorschau) auf eine neue Version zu aktualisieren.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 1f8291eeb292226b3dfcb2bd1a89816926c53d88
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993978"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>Das upgrade von SQL Server-big Data-Cluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel enthält Anleitungen zum Aktualisieren einer SQL Server-big Data-Cluster auf eine neue Version. Die Schritte in diesem Artikel gelten speziell für zwischen Preview-Versionen aktualisieren verwendet werden.

## <a name="backup-and-delete-the-old-cluster"></a>Sichern Sie und löschen Sie den alten cluster

Derzeit ist die einzige Möglichkeit, einen big Data-Cluster auf eine neue Version ein upgrade manuell entfernen und erstellen Sie den Cluster neu. Jede Version weist eine eindeutige Version **Mssqlctl** , die nicht mit der vorherigen Version kompatibel ist. Darüber hinaus, wenn ein ältere Cluster ein Image auf einem neuen Knoten herunterzuladen musste, kann das neueste Image mit den älteren Images auf dem Cluster nicht kompatibel. Um auf die neueste Version aktualisieren, verwenden Sie die folgenden Schritte aus:

1. Sichern Sie vor dem Löschen der alten Clusters, die Daten auf dem SQL Server-Masterinstanz und HDFS aus. Für die master SQL Server-Instanz, können Sie [SQL Server-Sicherung und Wiederherstellung](data-ingestion-restore-database.md). Für HDFS Sie [können kopieren Sie die Daten mit **curl**](data-ingestion-curl.md).

1. Löschen Sie den alten Cluster mit der `mssqlctl delete cluster` Befehl.

   ```bash
    mssqlctl cluster delete --name <old-cluster-name>
   ```

   > [!Important]
   > Verwenden Sie die Version der **Mssqlctl** Ihres Clusters entspricht. Löschen Sie einen ältere Cluster mit der neueren Version von nicht **Mssqlctl**.

1. Wenn Sie alle früheren Versionen von haben **Mssqlctl** installiert, es ist wichtig, deinstallieren Sie **Mssqlctl** vor der Installation der neuesten Version.

   Wenn Sie Deinstallieren **Mssqlctl** für CTP-Version 2.2 oder niedriger ausführen:

   ```powershell
   pip3 uninstall mssqlctl
   ```

   Führen Sie für CTP 2.3 oder höher verwenden, den folgenden Befehl aus. Ersetzen Sie dies `ctp-2.4` im Befehl mit der Version der **Mssqlctl** , die Sie deinstallieren:

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp-2.4/mssqlctl/requirements.txt
   ```

1. Installieren Sie die neueste Version des **Mssqlctl**. Die folgenden Befehle installieren **Mssqlctl** für CTP 3.0:

   **Windows:**

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.5/mssqlctl/requirements.txt
   ```

   **Linux:**

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp-2.5/mssqlctl/requirements.txt --user
   ```

   > [!IMPORTANT]
   > Für jede Version, die den Pfad zur **Mssqlctl** Änderungen. Wenn Sie zuvor installiert **Mssqlctl**, installieren Sie erneut aus dem aktuellen Pfad vor dem Erstellen des neuen Clusters.

## <a id="mssqlctlversion"></a> Überprüfen Sie die Mssqlctl-version

Vor der Bereitstellung eines neue big Data-Clusters, stellen Sie sicher, dass Sie die neueste Version des verwenden **Mssqlctl** mit der `--version` Parameter:

```bash
mssqlctl --version
```

## <a name="install-the-new-release"></a>Installieren Sie die neue Version

Nach dem Entfernen der vorherigen big Data-Cluster, und installieren die neueste Version **Mssqlctl**, die neue big Data-Cluster mithilfe der aktuellen bereitstellungsanweisungen bereitstellen. Weitere Informationen finden Sie unter [große SQL Server-Daten bereitstellen in Kubernetes-Clustern](deployment-guidance.md). Anschließend wiederherstellen Sie aller erforderlichen Datenbanken oder Dateien.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen über big Data-Cluster finden Sie unter [wie SQL Server-big Data-Cluster sind](big-data-cluster-overview.md).
