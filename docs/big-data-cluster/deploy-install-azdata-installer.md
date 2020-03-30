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
ms.openlocfilehash: 5b2e87cf96d6237521caeaae55802d2d72769603
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "73594338"
---
# <a name="install-azdata-to-manage-big-data-clusters-2019-with-windows-installer"></a>Installieren von `azdata` zur Verwaltung von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] mit dem Windows Installer

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie `azdata` für Big Data-Cluster in SQL Server 2019 unter Windows installieren. Bevor die Windows-Installation zur Verfügung stand, war `azdata` für die Installation von `pip` erforderlich.

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

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)