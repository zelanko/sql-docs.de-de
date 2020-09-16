---
title: Installieren von azdata mit dem Windows Installer
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das azdata-Tool zum Installieren und Verwalten von Big Data-Clustern in SQL Server mit dem Installationsprogramm installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 60d3b60f98a93cb6b724cd569fb2871adec3f1ce
ms.sourcegitcommit: 883435b4c7366f06ac03579752093737b098feab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "89733876"
---
# <a name="install-azdata-to-manage-big-data-clusters-2019-with-windows-installer"></a>Installieren von `azdata` zur Verwaltung von [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] mit dem Windows Installer

[!INCLUDE[SQL Server 2019](../../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel wird beschrieben, wie Sie `azdata` für Big Data-Cluster in SQL Server 2019 unter Windows installieren. Bevor die Windows-Installation zur Verfügung stand, war `pip` für die Installation von `azdata` erforderlich.

>Weitere Informationen zu Linux (Ubuntu) finden Sie unter [Installieren von `azdata` mit dem Installationsprogramm](./deploy-install-azdata-linux-package.md).

Zurzeit gibt es keine Paket-Manager zur Installation von `azdata` unter anderen Betriebssystemen oder Verteilungen. Für diese Plattformen lesen Sie den Artikel zum [Installieren von `azdata` ohne Paket-Manager](./deploy-install-azdata.md).

## <a name="install-azdata-with-the-microsoft-windows-installer"></a>Installieren von `azdata` mit dem Microsoft Windows Installer

So installieren Sie `azdata` mit dem Microsoft Windows Installer:

1. Entfernen Sie `azdata`, falls installiert, mithilfe von `pip`. Wenn `azdata` mit dem Windows Installer installiert wurde, fahren Sie mit dem nächsten Schritt fort.
1. Installieren Sie `azdata` mithilfe des Windows Installer.

### <a name="uninstall-if-previous-installation-done-with-pip"></a>Deinstallieren bei vorheriger Installation mit `pip`

Wenn Sie vorherige Releases von `azdata` installiert haben, müssen Sie diese zuerst deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie den folgenden Befehl aus, um die Release Candidate-Version von `azdata` zu entfernen.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

Nach dem Entfernen [installieren Sie `azdata` unter Windows](#install-azdata-windows).

>[!NOTE]
>Wenn Ihre vorherige Installation mit der MSI-Datei durchgeführt wurde, müssen Sie keine aktuellen Versionen deinstallieren, bevor Sie das MSI-Installationsprogramm verwenden können.

### <a name="install-with-windows-installer"></a><a id="install-azdata-windows"></a>Installieren mit dem Windows Installer

Verwenden Sie den Windows Installer, um `azdata` unter Windows zu installieren oder zu aktualisieren.

[Laden den Windows Installer für `azdata` herunter](https://aka.ms/azdata-msi).

Wenn das Installationsprogramm fragt, ob es Änderungen an Ihrem Computer vornehmen darf, klicken Sie auf `Yes`.

### <a name="uninstall-azdata-with-windows-installer"></a>Deinstallieren von `azdata` mit dem Windows Installer

Wenn Sie `azdata` mit dem Windows Installer deinstallieren möchten, befolgen Sie die Anweisungen für das jeweilige Betriebssystem.

| Plattform      | Instructions                                           |
| ------------- |--------------------------------------------------------|
| Windows 10| Start > Einstellungen > Apps                                |
| Windows 8     | Start > Systemsteuerung > Programme > Programm deinstallieren |

Das zu deinstallierende Programm wird als `Azdata CLI` bezeichnet. Wählen Sie diese Anwendung aus, und klicken Sie dann auf die Schaltfläche `Uninstall`.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md)