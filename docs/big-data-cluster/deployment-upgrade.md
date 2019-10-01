---
title: Upgrade auf ein neues Release
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Vorschau) auf eine neue Version aktualisieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bb1bf33c9ccb342e6afc4d22d67463791c0d67b6
ms.sourcegitcommit: 36c3ead6f2a3628f58040acf47f049f0b0957b8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2019
ms.locfileid: "71688277"
---
# <a name="how-to-upgrade-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Upgraden von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Dieser Artikel enthält Anleitungen zum Upgrade eines SQL Server-Big Data-Clusters auf ein neues Release. Die Schritte in diesem Artikel beziehen sich speziell auf das Upgrade zwischen Vorschauversionen.

## <a name="backup-and-delete-the-old-cluster"></a>Sichern und Löschen des alten Clusters

Derzeit besteht die einzige Möglichkeit zum Aktualisieren eines Big Data-Clusters auf ein neues Release darin, den Cluster manuell zu entfernen und neu zu erstellen. Jedes Release verfügt über eine eindeutige Version von `azdata`, die mit der vorherigen Version nicht kompatibel ist. Auch wenn ein älterer Cluster ein Image auf einen neuen Knoten herunterladen musste, ist das neueste Image möglicherweise nicht mit den älteren Images auf dem Cluster kompatibel. Führen Sie die folgenden Schritte aus, um ein Upgrade auf das neueste Release durchzuführen:

1. Sichern Sie vor dem Löschen des alten Clusters die Daten auf der SQL Server-Masterinstanz und auf HDFS. Für die SQL Server-Masterinstanz können Sie [SQL Server-Sicherung und -Wiederherstellung](data-ingestion-restore-database.md) verwenden. Für HDFS können Sie [die Daten mit `curl` Kopieren](data-ingestion-curl.md).

1. Löschen Sie den alten Cluster mit dem `azdata delete cluster`-Befehl.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Verwenden Sie die Version von `azdata`, die Ihrem Cluster entspricht. Löschen Sie keinen älteren Cluster mit der neueren Version von `azdata`.

   > [!Note]
   > Wenn Sie einen `azdata bdc delete`-Befehl ausgeben, werden alle Objekte, die innerhalb des Namespace erstellt wurden, mit dem zu löschenden Big Data Cluster Namen, jedoch nicht der Namespace selbst erstellt. Der Namespace kann für nachfolgende bereit Stellungen wieder verwendet werden, solange er leer ist und keine anderen Anwendungen in erstellt wurden.

1. Vor CTP 3,2 wurde "`azdata`" `mssqlctl` "aufgerufen. Wenn Sie frühere Versionen von `mssqlctl` oder `azdata` installiert haben, ist es wichtig, zuerst zu deinstallieren, bevor Sie die neueste Version von `azdata` installieren.

   Führen Sie für CTP 2.3 oder höher den folgenden Befehl aus. Ersetzen Sie `ctp3.1` im Befehl durch die Version von `mssqlctl`, die Sie deinstallieren. Fügen Sie bei einer früheren Version als CTP 3.1 einen Bindestrich vor der Versionsnummer ein (z.B. `ctp-2.5`).

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Installieren Sie die neueste Version von `azdata`. Mit den folgenden Befehlen wird `azdata` für die Release Candidate installiert:

   **Windows:**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux:**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > Für jede Version wird der Pfad zu `azdata` geändert. Auch wenn Sie zuvor `azdata` oder `mssqlctl` installiert haben, müssen Sie vor dem Erstellen des neuen Clusters aus dem aktuellen Pfad neu installieren.

## <a id="azdataversion"></a> Überprüfen der azdata-Version

Vergewissern Sie sich vor dem Bereitstellen eines neuen Big Data Clusters, dass Sie die neueste Version von `azdata` mit dem Parameter `--version` verwenden:

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Installieren des neuen Releases

Nachdem Sie den vorherigen Big Data Cluster entfernt und die neueste `azdata` installiert haben, stellen Sie den neuen Big Data Cluster mithilfe der aktuellen Bereitstellungs Anweisungen bereit. Weitere Informationen finden Sie unter Bereitstellen [von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] auf Kubernetes](deployment-guidance.md). Stellen Sie anschließend alle erforderlichen Datenbanken oder Dateien wieder her.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter [Was ist [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](big-data-cluster-overview.md).
