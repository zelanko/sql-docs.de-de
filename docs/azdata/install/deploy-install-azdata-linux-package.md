---
title: Installieren der Azure Data CLI (azdata) mit apt
description: Erfahren Sie, wie Sie das Tool Azure Data CLI (azdata) mit apt installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2f248978e09be4670d702805873a5ae6f4f7c9de
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257463"
---
# <a name="install-azure-data-cli-azdata-with-apt"></a>Installieren von [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] mit apt

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

Für Linux-Distributionen mit `apt` gibt es ein Paket für die `azdata-cli`. Das CLI-Paket wurde mit den folgenden Linux-Versionen getestet, die `apt` verwenden:

- Ubuntu 16.04, Ubuntu 18.04

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-apt"></a>Installieren mit apt

>[!IMPORTANT]
> Das RPM-Paket von `azdata-cli` ist vom Python 3-Paket abhängig. Auf Ihrem System handelt es sich dabei möglicherweise um eine ältere Python-Version als die erforderliche *Version 3.6.x* . Sollte dies ein Problem für Sie darstellen, ersetzen Sie das Python 3-Paket, oder führen Sie die Anweisungen zur manuellen Installation mit [`pip`](../install/deploy-install-azdata-pip.md) aus.

1. Installieren Sie die für die Installation von `azdata-cli` erforderlichen Abhängigkeiten.

   ```bash
   sudo apt-get update
   sudo apt-get install gnupg ca-certificates curl wget software-properties-common apt-transport-https lsb-release -y
   ```

2. Importieren Sie den Microsoft-Repositoryschlüssel.

   ```bash
   curl -sL https://packages.microsoft.com/keys/microsoft.asc |
   gpg --dearmor |
   sudo tee /etc/apt/trusted.gpg.d/microsoft.asc.gpg > /dev/null
   ```

3. Erstellen Sie lokale Repositoryinformationen.

   Führen Sie für Ubuntu 16.04-Clients den folgenden Befehl aus:

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/16.04/prod.list)"
    ```

   Führen Sie für Ubuntu 18.04-Clients den folgenden Befehl aus:

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/18.04/prod.list)"
    ```

   Führen Sie für Ubuntu 20.04-Clients den folgenden Befehl aus:

    ```bash
    sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/prod.list)
    ```

4. Installieren von `azdata-cli`.

   ```bash
   sudo apt-get update
   sudo apt-get install -y azdata-cli
   ```

## <a name="verify-install"></a>Überprüfen der Installation

```bash
azdata
azdata --version
```

## <a name="update"></a>Aktualisieren

Aktualisieren Sie die `azdata-cli` mit den Befehlen `apt-get update` und `apt-get install`.

```bash
sudo apt-get update && sudo apt-get install --only-upgrade -y azdata-cli
```

## <a name="uninstall"></a>Deinstallieren

1. Entfernen Sie das Paket aus Ihrem System.

   ```bash
   sudo apt-get remove -y azdata-cli
   ```

2. Entfernen Sie die Repositoryinformationen, wenn Sie nicht planen, `azdata-cli` neu zu installieren.

   ```bash
   sudo rm /etc/apt/sources.list.d/azdata-cli.list
   ```

3. Entfernen Sie den Repositoryschlüssel.

   ```bash
   sudo rm /etc/apt/trusted.gpg.d/dpgswdist.v1.asc.gpg
   ```

4. Entfernen Sie Abhängigkeiten, die nicht mehr benötigt werden.

   ```bash
   sudo apt autoremove
   ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Verwenden von azdata mit [Azure Arc-fähigen Datendiensten](/azure/azure-arc/data/)