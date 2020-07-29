---
title: Installieren von azdata mit dem Installationsprogramm unter Linux
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das azdata-Tool zum Installieren und Verwalten von Big Data-Clustern in SQL Server mit dem Installationsprogramm (unter Linux) installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 304515dcd288978c0d85ab992312eb2444430bfc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85773647"
---
# <a name="install-azdata-with-apt"></a>Installieren von `azdata` mit apt

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel wird beschrieben, wie Sie `azdata` für Big Data-Cluster in SQL Server 2019 unter Linux installieren. Bevor diese Paket-Manager verfügbar waren, was `pip` für die Installation von `azdata` erforderlich.

[!INCLUDE [azdata-package-installation-remove-pip-install](../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-azdata-for-linux"></a><a id="linux"></a>Installieren von `azdata` für Linux

Das `azdata`-Installationspaket ist mit `apt` für Ubuntu verfügbar.

### <a name="install-azdata-with-apt-ubuntu"></a><a id="azdata-apt"></a>Installieren von `azdata` mit apt (Ubuntu)

>[!NOTE]
>Das `azdata` Paket verwendet nicht die Systemversion von Python, stattdessen wird ein eigener Python-Interpreter installiert.

1. Rufen Sie die für die Installation erforderlichen Pakete ab:

    ```bash
    sudo apt-get update
    sudo apt-get install gnupg ca-certificates curl wget software-properties-common apt-transport-https lsb-release -y
    ```

2. Laden Sie den Signaturschlüssel herunter, und installieren Sie diesen:

    ```bash
    curl -sL https://packages.microsoft.com/keys/microsoft.asc |
    gpg --dearmor |
    sudo tee /etc/apt/trusted.gpg.d/microsoft.asc.gpg > /dev/null
    ```

3. Fügen Sie die Repositoryinformationen für `azdata` hinzu.

   Führen Sie für Ubuntu 16.04-Clients den folgenden Befehl aus:
    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2019.list)"
    ```

   Führen Sie für Ubuntu 18.04-Clients den folgenden Befehl aus:
    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/mssql-server-2019.list)"
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

### <a name="update"></a>Aktualisieren

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
