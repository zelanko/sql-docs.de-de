---
title: Veraltete Funktionen in den Reporting Services von SQL Server 2019 | Microsoft-Dokumentation
description: In diesem Artikel werden Features beschrieben, die in der nächsten Version von SQL Server Reporting Services veraltet sein werden.
ms.date: 11/21/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services, backward compatibility
- deprecated features [Reporting Services]
- HTML OWC rendering extension [Reporting Services]
- Report Server Web service, endpoints
ms.assetid: 3876c01e-f81d-4cce-9104-5106a8c369e6
author: maggiesMSFT
ms.author: maggies
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: eaa7edebe99a7c444fe1bfa23971317517399ea2
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74320274"
---
# <a name="deprecated-features-in-sql-server-2019-reporting-services"></a>Als veraltet markierte Features in SQL Server 2019 Reporting Services

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2019-and-later](../includes/ssrs-appliesto-2019-and-later.md)] [!INCLUDE [ssrs-appliesto-pbirs](../includes/ssrs-appliesto-pbirs.md)]

Wenn ein Feature als veraltet gekennzeichnet ist, bedeutet dies Folgendes:

- Die Funktion ist ausschließlich im Wartungsmodus. Es werden keine weiteren Änderungen vorgenommen, auch solche nicht, die mit der Interoperabilität mit neuen Features zu tun haben.
- Wir bemühen uns, veraltete Features nicht aus zukünftigen Versionen zu entfernen, um Upgrades zu vereinfachen. In seltenen Fällen kann es jedoch vorkommen, dass ein veraltetes Feature dauerhaft aus den Reporting Services entfernt wird, weil es zukünftige Innovationen beschränkt.
- Bei neuen Entwicklungen sollten Sie diese veralteten Features nicht verwenden.

**In zukünftigen Versionen von SQL Server veraltete Features**

SQL Server Reporting Services unterstützt die folgenden Features in der nächsten Version von SQL Server, jedoch werden sie in einer späteren Version als veraltet eingestuft. Die spezifische Version von SQL Server wurde noch nicht festgelegt.

| **Kategorie** | **Veraltetes Feature** | **Ersatz** |
| --- | --- | --- |
| Berichtsserver | Berichtsteilkatalog | Keine |
| Berichtsserver | Mobile Berichte und der Publisher für mobile Berichte | Die Power BI-Berichte im Power BI-Berichtsserver bieten mobile Funktionen. |
| Berichtsserver | XLS- und DOC-Renderformate | Die Formate XLSX und DOCX stehen zur Verfügung und werden unterstützt. |
| Berichtsserver | Atom-Datenfeed | Die Unterstützung des oData-Feeds ist für freigegebene Datasets in SSRS und Power BI-Berichtsserver verfügbar. |

## <a name="see-also"></a>Weitere Informationen

[Nicht mehr unterstützte Funktion in SQL Server 2019 Reporting Services (SSRS)](discontinued-functionality-sql-server-reporting-services-2019.md)

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
