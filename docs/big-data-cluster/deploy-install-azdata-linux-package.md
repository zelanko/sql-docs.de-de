---
title: Installieren von azdata mit dem Installationsprogramm unter Linux
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das Tool azdata zum Installieren und Verwalten von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Vorschau) mit dem Installationsprogramm (Linux) installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2795178cb975ecb620528c4a5dc8715b70d447fd
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342013"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-linux"></a>Installieren Sie `azdata`, um [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] unter Linux zu verwalten.

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie `azdata` für SQL Server 2019-Release Candidate für Big Data-Cluster unter Linux installieren. Vor der Verfügbarkeit dieser Paket-Manager war die Installation von `azdata` `pip` erforderlich.

Die Paket-Manager sind für verschiedene Betriebssysteme und Distributionen konzipiert.

- Installieren Sie für Linux (Ubuntu) [`azdata` mit `apt`](#azdata-apt)

Zurzeit sind keine Paket-Manager zum Installieren von `azdata` für andere Betriebssysteme oder Distributionen vorhanden. Informationen zu diesen Plattformen finden Sie unter [Installieren von `azdata` ohne Paket-Manager](./deploy-install-azdata.md).

## <a id="linux"></a>Installieren von `azdata` für Linux

`azdata`-Installationspaket ist für Ubuntu mit `apt` verfügbar.

### <a id="azdata-apt"></a>Installieren von `azdata` mit apt (Ubuntu)

>[!NOTE]
>Das Paket "`azdata`" verwendet nicht das System python, sondern installiert seinen eigenen Python-Interpreter.

1. Get-Pakete, die für den Installationsvorgang benötigt werden:

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl apt-transport-https lsb-release -y
    ```

2. Herunterladen und Installieren des Signatur Schlüssels:

    ```bash
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

3. Fügen Sie die `azdata`-Repository-Informationen hinzu:

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"
    ```

4. Aktualisieren Sie die Repository-Informationen, und installieren Sie `azdata`:

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. Überprüfen der Installation:

    ```bash
    azdata --version
    ```

### <a name="update"></a>Update

Upgrade `azdata`:

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>Deinstallieren

1. Deinstallieren mit apt-get remove:

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. Entfernen Sie die `azdata`-Repository-Informationen:

    >[!NOTE]
    >Dieser Schritt ist nicht erforderlich, wenn Sie planen, `azdata` zukünftig zu installieren.

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

Weitere Informationen zu Big Data Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
