---
title: Upgrade auf ein neues Release
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie Big Data-Cluster für SQL Server 2019 (Vorschauversion) auf ein neues Release aktualisieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7bdb1eb59fd36d065df9dba0f6d6879c1a294914
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419385"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>Vorgehensweise: Aktualisieren von SQL Server-Big Data-Clustern

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel enthält Anleitungen zum Upgrade eines SQL Server-Big Data-Clusters auf ein neues Release. Die Schritte in diesem Artikel beziehen sich speziell auf das Upgrade zwischen Vorschauversionen.

## <a name="backup-and-delete-the-old-cluster"></a>Sichern und Löschen des alten Clusters

Derzeit besteht die einzige Möglichkeit zum Aktualisieren eines Big Data-Clusters auf ein neues Release darin, den Cluster manuell zu entfernen und neu zu erstellen. Jedes Release verfügt über eine eindeutige Version von **azdata**, die mit der vorherigen Version nicht kompatibel ist. Auch wenn ein älterer Cluster ein Image auf einen neuen Knoten herunterladen musste, ist das neueste Image möglicherweise nicht mit den älteren Images auf dem Cluster kompatibel. Führen Sie die folgenden Schritte aus, um ein Upgrade auf das neueste Release durchzuführen:

1. Sichern Sie vor dem Löschen des alten Clusters die Daten auf der SQL Server-Masterinstanz und auf HDFS. Für die SQL Server-Masterinstanz können Sie [SQL Server-Sicherung und -Wiederherstellung](data-ingestion-restore-database.md) verwenden. Für HDFS [können Sie die Daten mit **curl** herauskopieren](data-ingestion-curl.md).

1. Löschen Sie den alten Cluster mit dem `azdata delete cluster`-Befehl.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Verwenden Sie die Version von **azdata**, die Ihrem Cluster entspricht. Löschen Sie keinen älteren Cluster mit der neueren Version von **azdata**.

1. Vor CTP 3.2 wurde **azdata** als **mssqlctl** bezeichnet. Wenn Sie vorherige Releases von **mssqlctl** oder **azdata** installiert haben, müssen Sie zuerst deinstallieren, bevor Sie die neueste Version von **azdata** installieren.

   Führen Sie für CTP 2.3 oder höher den folgenden Befehl aus. Ersetzen Sie `ctp3.1` im Befehl durch die Version von **mssqlctl**, die Sie deinstallieren. Fügen Sie bei einer früheren Version als CTP 3.1 einen Bindestrich vor der Versionsnummer ein (z.B. `ctp-2.5`).

   ```powershell
   pip3 uninstall -r https://mcr.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Installieren Sie die neueste Version von **azdata**. Mit den folgenden Befehlen wird **azdata** für CTP 3.2 installiert:

   **Windows:**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux:**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > Für jedes Release ändert sich der Pfad zu **azdata**. Auch wenn Sie zuvor **azdata** oder **mssqlctl** installiert haben, müssen Sie vor dem Erstellen des neuen Clusters vom aktuellen Pfad aus neu installieren.

## <a id="azdataversion"></a> Überprüfen der azdata-Version

Vergewissern Sie sich vor dem Bereitstellen eines neuen Big Data-Clusters, dass Sie die neueste Version von **azdata** mit dem `--version`-Parameter verwenden:

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Installieren des neuen Releases

Nachdem Sie den vorherigen Big Data-Cluster entfernt und die neueste **azdata**-Version installiert haben, stellen Sie den neuen Big Data-Cluster mithilfe der aktuellen Bereitstellungsanweisungen bereit. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen von Big Data-Clustern für SQL Server in Kubernetes](deployment-guidance.md). Stellen Sie anschließend alle erforderlichen Datenbanken oder Dateien wieder her.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind SQL Server-Big Data-Cluster?](big-data-cluster-overview.md).
