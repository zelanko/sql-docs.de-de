---
title: Upgrade auf ein neues Release
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie SQL Server 2019 Big Data Cluster (Vorschauversion) auf eine neue Version aktualisieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7bdb1eb59fd36d065df9dba0f6d6879c1a294914
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419385"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>Aktualisieren von SQL Server Big Data Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel enthält Anleitungen zum Upgrade eines SQL Server Big Data-Clusters auf eine neue Version. Die Schritte in diesem Artikel beziehen sich speziell auf das Upgrade zwischen Vorschau Versionen.

## <a name="backup-and-delete-the-old-cluster"></a>Sichern und Löschen des alten Clusters

Derzeit besteht die einzige Möglichkeit zum Aktualisieren eines Big Data Clusters auf eine neue Version darin, den Cluster manuell zu entfernen und neu zu erstellen. Jedes Release verfügt über eine eindeutige Version von **azdata** , die mit der vorherigen Version nicht kompatibel ist. Wenn ein älterer Cluster ein Abbild auf einem neuen Knoten herunterladen musste, ist das neueste Image möglicherweise nicht mit den älteren Images auf dem Cluster kompatibel. Führen Sie die folgenden Schritte aus, um ein Upgrade auf die neueste Version durchzuführen:

1. Sichern Sie vor dem Löschen des alten Clusters die Daten auf der SQL Server Master Instanz und auf HDFS. Für die SQL Server Master Instanz können Sie [SQL Server Sicherung und Wiederherstellung](data-ingestion-restore-database.md)verwenden. Für HDFS können Sie [die Daten mit **curl**kopieren](data-ingestion-curl.md).

1. Löschen Sie den alten Cluster mit `azdata delete cluster` dem Befehl.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Verwenden Sie die Version von **azdata** , die Ihrem Cluster entspricht. Löschen Sie keinen älteren Cluster mit der neueren Version von **azdata**.

1. Vor CTP 3,2 wurde " **azdata** " als " **mssqlctl**" bezeichnet. Wenn Sie vorherige Versionen von **mssqlctl** oder **azdata** installiert haben, ist es wichtig, zuerst zu deinstallieren, bevor Sie die neueste Version von **azdata**installieren.

   Führen Sie für CTP 2,3 oder höher den folgenden Befehl aus. Ersetzen `ctp3.1` Sie im Befehl durch die Version von **mssqlctl** , die Sie deinstallieren. Wenn die Version vor CTP 3,1 ist, fügen Sie einen Bindestrich vor der Versionsnummer (z `ctp-2.5`. b.) ein.

   ```powershell
   pip3 uninstall -r https://mcr.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Installieren Sie die neueste Version von **azdata**. Mit den folgenden Befehlen werden **azdata** für CTP 3,2 installiert:

   **Windows:**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > Für jede Version ändert sich der Pfad zu **azdata** . Auch wenn Sie zuvor **azdata** oder **mssqlctl**installiert haben, müssen Sie vor dem Erstellen des neuen Clusters aus dem aktuellen Pfad neu installieren.

## <a id="azdataversion"></a>Überprüfen der azdata-Version

Vergewissern Sie sich vor dem Bereitstellen eines neuen Big Data Clusters, dass Sie die neueste Version von **azdata** mit dem `--version` Parameter verwenden:

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Installieren Sie die neue Version.

Nachdem Sie den vorherigen Big Data Cluster entfernt und die neuesten **azdata**installiert haben, stellen Sie den neuen Big Data Cluster mithilfe der aktuellen Bereitstellungs Anweisungen bereit. Weitere Informationen finden Sie unter Bereitstellen [von SQL Server Big Data Clustern auf Kubernetes](deployment-guidance.md). Stellen Sie anschließend alle erforderlichen Datenbanken oder Dateien wieder her.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter [Was sind SQL Server Big Data Cluster](big-data-cluster-overview.md).
