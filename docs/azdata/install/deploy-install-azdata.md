---
title: Installieren der Azure Data CLI (azdata)
titleSuffix: ''
description: Erfahren Sie, wie Sie das Tool Azure Data CLI (azdata) installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 82aa3a2795328804a10a76e9ecd8af80f3bf7152
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257405"
---
# <a name="install-azure-data-cli-azdata"></a>Installieren von [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

[!INCLUDE[azdata](../../includes/applies-to-version/azdata.md)]

[!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm für Bootstraps und Verwaltung der Datendienste über REST-APIs. 

## <a name="find-latest-version"></a>Abrufen der aktuellen Version

Unter [https://aka.ms/azdata](https://aka.ms/azdata) finden Sie immer eine Liste der Dateien für die jeweils aktuelle Version.

Führen Sie `azdata --version` aus, um Ihre installierte Version zu ermitteln und festzustellen, ob Sie die CLI aktualisieren müssen.

## <a name="os-specific-instructions"></a>Betriebssystemspezifische Anweisungen

* [Installieren unter Windows](../install/deploy-install-azdata-installer.md)
* [Installieren unter macOS](../install/deploy-install-azdata-macos.md)
* Installieren unter Linux oder [Windows-Subsystem für Linux (WSL)](/windows/wsl/about/)
   * [Installieren mit apt unter Debian oder Ubuntu](../install/deploy-install-azdata-linux-package.md)
   * [Installieren von azdata mit YUM](../install/deploy-install-azdata-yum.md)
   * [Installieren von azdata mit Zypper](../install/deploy-install-azdata-zypper.md)
   * [Installieren per Skript](../install/deploy-install-azdata-pip.md)

[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Verwendung von azdata mit Big Data-Cluster finden Sie unter [Was ist [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md)

Verwenden von azdata mit [Azure Arc-fähigen Datendiensten](/azure/azure-arc/data/)
