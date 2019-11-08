---
title: Upgrade auf ein neues Release
titleSuffix: SQL Server big data clusters
description: Hier erfahren Sie, wie Sie [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Vorschauversion) auf ein neues Release upgraden können.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 90bfaaa1a8cb6fd42081d8afa5feff13f9aec37c
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531963"
---
# <a name="how-to-upgrade-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Upgraden von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel enthält Anleitungen zum Upgrade eines SQL Server-Big Data-Clusters auf ein neues Release. Die Schritte in diesem Artikel gelten insbesondere für Upgrades von einem Vorschaurelease auf ein Dienstupdaterelease von SQL Server 2019.

## <a name="backup-and-delete-the-old-cluster"></a>Sichern und Löschen des alten Clusters

Derzeit besteht die einzige Möglichkeit zum Aktualisieren eines Big Data-Clusters auf ein neues Release darin, den Cluster manuell zu entfernen und neu zu erstellen. Jedes Release verfügt über eine eindeutige Version von `azdata`, die mit der vorherigen Version nicht kompatibel ist. Auch wenn ein älterer Cluster ein Containerimage auf einen neuen Knoten herunterladen musste, ist das neueste Image möglicherweise nicht mit den älteren Images auf dem Cluster kompatibel. Beachten Sie, dass das neuere Image nur abgerufen wird, wenn Sie das Imagetag `latest` in der Bereitstellungskonfigurationsdatei für die Containereinstellungen verwenden. Standardmäßig verfügt jedes Release über ein bestimmtes Imagetag, das der Releaseversion von SQL Server entspricht. Führen Sie die folgenden Schritte aus, um ein Upgrade auf das neueste Release durchzuführen:

1. Sichern Sie vor dem Löschen des alten Clusters die Daten auf der SQL Server-Masterinstanz und auf HDFS. Für die SQL Server-Masterinstanz können Sie [SQL Server-Sicherung und -Wiederherstellung](data-ingestion-restore-database.md) verwenden. Für HDFS [können Sie die Daten mit `curl` herauskopieren](data-ingestion-curl.md).

1. Löschen Sie den alten Cluster mit dem `azdata delete cluster`-Befehl.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Verwenden Sie die Version von `azdata`, die Ihrem Cluster entspricht. Löschen Sie keinen älteren Cluster mit der neueren Version von `azdata`.

   > [!Note]
   > Wenn Sie einen `azdata bdc delete`-Befehl ausführen, werden alle innerhalb des Namespace erstellten Objekte mit dem Namen des Big Data-Clusters gelöscht, der Namespace jedoch nicht. Der Namespace kann für nachfolgende Bereitstellungen wiederverwendet werden, solange er leer ist und keine anderen Anwendungen in ihm erstellt wurden.

1. Deinstallieren Sie die alte Version von `azdata`.

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Installieren Sie die neueste Version von `azdata`. Mit den folgenden Befehlen wird `azdata` aus dem neuesten Release installiert:

   **Windows:**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux:**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > Für jedes Release ändert sich der Pfad zur `n-1`-Version von `azdata`. Auch wenn Sie zuvor `azdata` installiert haben, müssen Sie vor dem Erstellen des neuen Clusters vom aktuellen Pfad aus neu installieren.

## <a id="azdataversion"></a> Überprüfen der azdata-Version

Vergewissern Sie sich vor dem Bereitstellen eines neuen Big Data-Clusters, dass Sie die neueste Version von `azdata` mit dem `--version`-Parameter verwenden:

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Installieren des neuen Releases

Nachdem Sie den vorherigen Big Data-Cluster entfernt und die neueste `azdata`-Version installiert haben, stellen Sie den neuen Big Data-Cluster mithilfe der aktuellen Bereitstellungsanweisungen bereit. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] auf Kubernetes](deployment-guidance.md). Stellen Sie anschließend alle erforderlichen Datenbanken oder Dateien wieder her.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]?](big-data-cluster-overview.md).
