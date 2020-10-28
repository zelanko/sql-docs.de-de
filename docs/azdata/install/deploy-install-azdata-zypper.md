---
title: Installieren der Azure Data CLI (azdata) mit zypper
titleSuffix: ''
description: Erfahren Sie, wie Sie das Tool Azure Data CLI (azdata) mit zypper installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d43a1f9c65aa17fae3d262a51f45105b5f583cdd
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257511"
---
# <a name="install-azure-data-cli-azdata-with-zypper"></a>[!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] mit zypper installieren

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

Für Linux-Distributionen mit `zypper` gibt es ein Paket für die `azdata-cli`. Das CLI-Paket wurde mit den folgenden Linux-Versionen getestet, die `zypper` verwenden:

- openSUSE 42.2 (Leap) und höher
- SLES 12 SP 2 und höher

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-zypper"></a>Installieren mit zypper

>[!IMPORTANT]
>Das RPM-Paket von `azdata-cli` ist vom Python 3-Paket abhängig. Auf Ihrem System handelt es sich dabei möglicherweise um eine ältere Python-Version als die erforderliche *Version 3.6.x* . Sollte dies ein Problem für Sie darstellen, ersetzen Sie das Python 3-Paket, oder führen Sie die Anweisungen zur manuellen Installation mit [`pip`](../install/deploy-install-azdata-pip.md) aus.

1. Installieren Sie die für die Installation von `azdata-cli` erforderlichen Abhängigkeiten.

   ```bash
   sudo zypper install -y curl
   ```

1. Importieren Sie den Microsoft-Repositoryschlüssel.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. Erstellen Sie lokale Repositoryinformationen.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/prod.repo
   ```

1. Installieren von `azdata-cli`.

   ```bash
   sudo zypper install --from packages-microsoft-com-mssql-server-2019 -y azdata-cli
   ```

## <a name="verify-install"></a>Überprüfen der Installation

```bash
azdata
azdata --version
```

## <a name="update"></a>Aktualisieren

Aktualisieren Sie die `azdata-cli` mit dem Befehl `zypper update`.

```bash
sudo zypper refresh
sudo zypper update azdata-cli
```

## <a name="uninstall"></a>Deinstallieren

Entfernen Sie das Paket aus Ihrem System.

```bash
sudo zypper removerepo azdata-cli
```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Verwenden von azdata mit [Azure Arc-fähigen Datendiensten](/azure/azure-arc/data/)