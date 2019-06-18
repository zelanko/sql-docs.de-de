---
title: Finden Sie den Product Key für SQL Server 2017 Reporting Services (SSRS) | Microsoft-Dokumentation
ms.date: 12/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 36460943b233f02e4d029b7865c7d7fa3844b488
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65502923"
---
# <a name="how-to-find-the-product-key-for-sql-server-2017-reporting-services"></a>Finden Sie den Product Key für SQL Server 2017 Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

Erfahren Sie, wo Sie den Product Key für SQL Server 2017 Reporting Services (SSRS) finden, um Ihren Server in einer Produktionsumgebung installieren zu können.

Laden Sie zunächst das Setup für SQL Server 2017 herunter, und führen Sie dieses aus.

1. SQL Server 2017 können Sie von einer der folgenden Quellen herunterladen:

    - Volume Licensing Service Center
    - MSDN-Abonnement
    - Im Handel (als Download in Microsoft Store)

1. Führen Sie das SQL Server 2017-Setup aus, und kopieren Sie den vorausgefüllten Schlüssel:

    ![Kopieren Sie den Product Key von SQL Server 2017](media/find-reporting-services-product-key-ssrs/ssrs-ss2017-copy-product-key.png)

1. [Führen Sie das Reporting Services-Setup aus](install-reporting-services.md), und fügen Sie den Schlüssel ein:

     ![Geben Sie den Product Key ein](media/find-reporting-services-product-key-ssrs/ssrs-ssrs2017-paste-product-key.png)

Diesen Schritt müssen Sie nur bei der ersten Installation von SSRS 2017 durchführen. Wenn Sie Wartungsupdates durchführen, sollten Sie ihn nicht eingeben müssen.

## <a name="related-information"></a>Verwandte Informationen

- Informationen zur Installation von SQL Server 2016 Reporting Services im einheitlichen Modus finden Sie unter [Installieren des Reporting Services-Berichtsservers im nativen Modus](install-reporting-services-native-mode-report-server.md). 

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

- Informationen zur Installation von SQL Server 2016 Reporting Services (und früheren Versionen) im SharePoint-Integrationsmodus finden Sie unter [Installieren des ersten Berichtsservers im SharePoint-Modus](install-the-first-report-server-in-sharepoint-mode.md).

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

- [Installation von SQL Server 2017 Reporting Services](install-reporting-services.md)
- Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
