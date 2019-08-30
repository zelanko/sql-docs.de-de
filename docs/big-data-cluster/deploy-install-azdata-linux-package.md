---
title: Installieren von azdata mit dem Installationsprogramm unter Linux
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das Tool azdata zum Installieren und [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] Verwalten von (Vorschau) mit dem Installationsprogramm (Linux) installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e11e4851294ac8ffd8efa66e2156dcd47bce3aa0
ms.sourcegitcommit: 71fac5fee00e0eca57e555f44274dd7e08d47e1e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70160685"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-linux"></a>Zu `azdata` verwaltende [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Installation unter Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, `azdata` wie Sie für SQL Server 2019-Big Data-Cluster Release Candidate unter Linux installieren. Bevor diese Paket-Manager verfügbar waren, ist die `azdata` Installation `pip`von erforderlich.

Die Paket-Manager sind für verschiedene Betriebssysteme und Distributionen konzipiert.

- Installieren Sie für Linux (Ubuntu) [mit `apt` `azdata` ](#azdata-apt)

Zurzeit sind keine Paket-Manager für die Installation `azdata` auf anderen Betriebssystemen oder Distributionen vorhanden. Informationen zu diesen Plattformen finden Sie unter [installieren `azdata` ohne Paket-Manager](./deploy-install-azdata.md).

## <a id="linux"></a>Installieren `azdata` für Linux

`azdata`das Installationspaket ist für Ubuntu mit `apt`verfügbar.

### <a id="azdata-apt"></a>Installieren `azdata` mit apt (Ubuntu)

>[!NOTE]
>Das `azdata` Paket verwendet nicht das System python, sondern installiert seinen eigenen Python-Interpreter.

1. Get-Pakete, die für den Installationsvorgang benötigt werden:

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl apt-transport-https lsb-release -y
    ```

2. Herunterladen und Installieren des Signatur Schlüssels:

    ```bash
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add –
    ```

3. Fügen Sie `azdata` die Repository-Informationen hinzu:

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
    ```

4. Repository-Informationen aktualisieren und `azdata`installieren:

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. Überprüfen der Installation:

    ```bash
    azdata --version
    ```

### <a name="update"></a>Update

Nur `azdata` Upgrade:

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>Deinstallieren

1. Deinstallieren mit apt-get remove:

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. Entfernen Sie `azdata` die Repository-Informationen:

    >[!NOTE]
    >Dieser Schritt ist nicht erforderlich, wenn Sie planen, `azdata` in Zukunft zu installieren.

    ```bash
    sudo rm /etc/apt/sources.list.d/azdata-cli.list
    ```

3. Entfernen Sie den Signatur Schlüssel:

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
    ```

4. Entfernen Sie alle nicht benötigten Abhängigkeiten, die mit der azdata CLI installiert wurden:

    ```bash
    sudo apt autoremove
    ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter [was [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]ist?](big-data-cluster-overview.md).
