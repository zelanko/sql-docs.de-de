---
title: Installieren von azdata
titleSuffix: SQL Server big data clusters
description: In diesem Artikel erfahren Sie, wie Sie das azdata-Tool zum Installieren und Verwalten von Big Data-Clustern installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 408dec76480a36ff2280926147b948859fa7088d
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733899"
---
# <a name="install-azdata"></a>Installieren von `azdata`

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

`azdata` ist ein in Python geschriebenes Befehlszeilen-Hilfsprogramm für das Starten und Verwalten eines Big Data-Clusters über REST-APIs. 

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

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).
