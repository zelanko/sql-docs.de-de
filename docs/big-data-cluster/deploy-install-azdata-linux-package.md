---
title: Installieren von azdata mit dem Installationsprogramm unter Linux
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das azdata-Tool zum Installieren und Verwalten von Big Data-Clustern in SQL Server mit dem Installationsprogramm (unter Linux) installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9d8d4a34e89de7c136e1e80b43929531a2d10eba
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532072"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-on-linux"></a>Installieren von `azdata` zum Verwalten von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] unter Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie `azdata` für Big Data-Cluster in SQL Server 2019 unter Linux installieren. Bevor diese Paket-Manager verfügbar waren, was `pip` für die Installation von `azdata` erforderlich.

Die Paket-Manager sind für verschiedene Betriebssysteme und Verteilungen konzipiert.

- Unter Windows und Linux (Ubuntu-Distribution) ist es einfacher, wenn Sie einen [Paket-Manager](./deploy-install-azdata-installer.md) für die Installation verwenden.
- [Installieren Sie `azdata` unter Linux (Ubuntu) mit `apt`](#azdata-apt).

Zurzeit gibt es keine Paket-Manager zur Installation von `azdata` unter anderen Betriebssystemen oder Verteilungen. Informationen zur Installation auf diesen Plattformen finden Sie unter [Installieren von `azdata` ohne Paket-Manager](./deploy-install-azdata.md).

## <a id="linux"></a>Installieren von `azdata` für Linux

Das `azdata`-Installationspaket ist mit `apt` für Ubuntu verfügbar.

### <a id="azdata-apt"></a>Installieren von `azdata` mit apt (Ubuntu)

>[!NOTE]
>Das `azdata` Paket verwendet nicht die Systemversion von Python, stattdessen wird ein eigener Python-Interpreter installiert.

1. Rufen Sie die für die Installation erforderlichen Pakete ab:

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl apt-transport-https lsb-release -y
    ```

2. Laden Sie den Signaturschlüssel herunter, und installieren Sie diesen:

    ```bash
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

3. Fügen Sie die Repositoryinformationen für `azdata` hinzu:

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
    ```

4. Aktualisieren Sie die Repositoryinformationen, und installieren Sie `azdata`:

    ```bash
    sudo apt-get update
    sudo apt-get install -y azdata-cli
    ```

5. Überprüfen Sie die Installation:

    ```bash
    azdata --version
    ```

### <a name="update"></a>Update

Führen Sie ein Upgrade nur für `azdata` durch:

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

### <a name="uninstall"></a>Deinstallieren

1. Führen Sie die Deinstallation mit „apt-get remove“ durch:

    ```bash
    sudo apt-get remove -y azdata-cli
    ```

2. Entfernen Sie die Repositoryinformationen für `azdata`:

    >[!NOTE]
    >Dieser Schritt ist nicht erforderlich, wenn Sie planen, `azdata` in der Zukunft zu installieren.

    ```bash
    sudo rm /etc/apt/sources.list.d/azdata-cli.list
    ```

3. Entfernen Sie den Signaturschlüssel:

    ```bash
    sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
    ```

4. Entfernen Sie alle nicht benötigten Abhängigkeiten, die mit der Azdata-CLI installiert wurden:

    ```bash
    sudo apt autoremove
    ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
