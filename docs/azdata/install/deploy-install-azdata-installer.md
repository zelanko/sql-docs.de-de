---
title: Installieren der Azure Data CLI (azdata) mit Windows Installer
titleSuffix: ''
description: Erfahren Sie, wie Sie das Tool Azure Data CLI (azdata) mit dem Installer installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 09/30/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9dd953a78a992a9a5fed7135ae0aee02f88e4de9
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257493"
---
# <a name="install-azure-data-cli-azdata-with-windows-installer"></a>Installieren von [!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)] mit dem Windows Installer

[!INCLUDE [azdata](../../includes/applies-to-version/azdata.md)]

In diesem Artikel wird beschrieben, wie Sie `azdata` unter Windows mit einem Installationsprogramm installieren. Verwenden Sie `azdata`, um SQL Server Big Data-Cluster oder Azure Arc-fähige Datendienste zu verwalten.

## <a name="steps-to-install-azdata-with-the-microsoft-windows-installer"></a>Schritte zum Installieren von `azdata` mit dem Microsoft Windows Installer

So installieren Sie `azdata` mit dem Microsoft Windows Installer:

1. Entfernen Sie `azdata`, falls installiert, mithilfe von `pip`. Wenn `azdata` mit dem Windows Installer installiert wurde, fahren Sie mit dem nächsten Schritt fort.
1. Installieren Sie `azdata` mit dem [Windows Installer](https://aka.ms/azdata-msi).

### <a name="uninstall-azdata-with-windows-installer"></a>Deinstallieren von `azdata` mit dem Windows Installer

Wenn Sie `azdata` mit dem Windows Installer deinstallieren möchten, befolgen Sie die Anweisungen für das jeweilige Betriebssystem.

| Plattform      | Instructions                                           |
| ------------- |--------------------------------------------------------|
| Windows 10| Start > Einstellungen > Apps                                |
| Windows 8     | Start > Systemsteuerung > Programme > Programm deinstallieren |

Das zu deinstallierende Programm wird als `Azdata CLI` bezeichnet. Wählen Sie diese Anwendung aus, und klicken Sie dann auf die Schaltfläche `Uninstall`.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md)

Verwenden von `azdata` mit [Azure Arc-fähigen Datendiensten](/azure/azure-arc/data/)
