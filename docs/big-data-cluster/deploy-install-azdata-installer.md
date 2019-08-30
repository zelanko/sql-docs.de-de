---
title: Installieren von azdata mit Windows Installer
titleSuffix: SQL Server big data clusters
description: Erfahren Sie, wie Sie das Tool azdata zum Installieren und [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] Verwalten von (Vorschau) mit dem Installationsprogramm installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a8dd5d2c7d0210880a82d774185a3f2a915608ec
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158145"
---
# <a name="install-azdata-to-manage-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-with-windows-installer"></a>Zu `azdata` verwaltende [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Installation mit Windows Installer

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, `azdata` wie Sie für SQL Server 2019-Big Data-Cluster Release Candidate unter Windows installieren. Vor der Verfügbarkeit der Windows-Installation ist die `azdata` Installation `pip`von erforderlich.

>Informationen zu Linux (Ubuntu) finden Sie unter [ `azdata` install with Installer](./deploy-install-azdata-linux-package.md).

Zurzeit sind keine Paket-Manager für die Installation `azdata` auf anderen Betriebssystemen oder Distributionen vorhanden. Informationen zu diesen Plattformen finden Sie unter [installieren `azdata` ohne Paket-Manager](./deploy-install-azdata.md).

## <a name="install-azdata-with-the-microsoft-windows-installer"></a>Installieren `azdata` Sie mit dem Microsoft Windows Installer

So installieren `azdata` Sie mit dem Microsoft Windows Installer

1. Entfernen `azdata` Sie diese Option, wenn `pip`Sie mit installiert wurde. Wenn `azdata` Sie mit Windows Installer installiert wurde, fahren Sie mit dem nächsten Schritt fort.
1. Installieren `azdata` Sie mit dem Windows Installer.

### <a name="uninstall-if-previous-installation-done-with-pip"></a>Deinstallieren, wenn die vorherige Installation mit abgeschlossen wurde`pip`

Wenn Sie vorherige Versionen von **mssqlctl** installiert haben, entfernen Sie Sie. Der folgende Befehl entfernt die CTP 3,1-Version von **mssqlctl**.

   ```bash
   pip3 uninstall -r https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

Wenn Sie frühere Versionen von `azdata` installiert haben, ist es wichtig, diese zuerst zu deinstallieren, bevor Sie die neueste Version installieren.

   Führen Sie für CTP 3,2 den folgenden Befehl aus.

   ```bash
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-ctp3.2/requirements.txt
   ```

Nach dem Entfernen [installieren `azdata` Sie unter Windows](#install-azdata-windows).

>[!NOTE]
>Wenn die vorherige Installation mit der MSI-Datei erfolgt ist, müssen Sie vor der Verwendung des MSI-Installers keine aktuellen Versionen deinstallieren.

### <a id="install-azdata-windows"></a>Installieren mit Windows Installer

Verwenden Sie die Windows Installer, um unter `azdata` Windows zu installieren oder zu aktualisieren.

[Laden Sie `azdata` die Windows Installer herunter](http://aka.ms/azdata-msi).

Wenn das Installationsprogramm gefragt wird, ob es Änderungen an Ihrem Computer vornehmen `Yes`kann, klicken Sie auf.

### <a name="uninstall-azdata-with-windows-installer"></a>Deinstallieren `azdata` mit Windows Installer

Befolgen Sie `azdata` die Anweisungen für das entsprechende Betriebssystem, um mit Windows Installer zu deinstallieren.

| Platform      | Anweisungen                                           |
| ------------- |--------------------------------------------------------|
| Windows 10    | Starten > Einstellungen > apps                                |
| Windows 8     | Starten > Systemsteuerung > Programme > Deinstallieren eines Programms |

Das zu deinstallierende Programm **`Azdata CLI`** wird aufgerufen. Wählen Sie diese Anwendung aus, und `Uninstall` klicken Sie auf die Schaltfläche.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data Clustern finden Sie unter [was [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]ist?](big-data-cluster-overview.md).
