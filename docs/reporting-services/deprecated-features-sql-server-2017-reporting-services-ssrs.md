---
title: Veraltete Funktionen in den Reporting Services von SQL Server 2017 | Microsoft-Dokumentation
description: In diesem Artikel werden Funktionen beschrieben, die in der nächsten Version von SQL Server Reporting Services veraltet sein werden.
ms.date: 11/20/2019
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
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: d8fe51ce9d86688669e84ad866ad9f5e6da075e8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74320314"
---
# <a name="deprecated-features-in-sql-server-2017-reporting-services"></a>Veraltete Funktionen in den Reporting Services von SQL Server 2017

[!INCLUDE [ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE [ssrs-appliesto-2017](../includes/ssrs-appliesto-2017.md)] [!INCLUDE [ssrs-appliesto-not-pbirs](../includes/ssrs-appliesto-not-pbirs.md)]

Wenn eine Funktion als veraltet gekennzeichnet ist, bedeutet dies Folgendes:

- Die Funktion ist ausschließlich im Wartungsmodus. Es werden keine weiteren Änderungen vorgenommen, auch solche nicht, die mit der Interoperabilität mit neuen Funktionen zu tun haben.
- Wir bemühen uns, veraltete Funktionen in zukünftigen Versionen zu belassen, um Upgrades zu vereinfachen. In seltenen Fällen kann es jedoch vorkommen, dass eine veraltete Funktion aus den Reporting Services entfernt wird, weil sie zukünftige Innovationen beschränkt.
- Bei neuen Entwicklungen sollten Sie diese veralteten Funktionen nicht verwenden.

## <a name="features-deprecated-in-the-next-version-of-sql-server"></a>Funktionen, die ab der nächsten Version von SQL Server veraltet sind

Die folgenden Funktionen in den Reporting Services von SQL Server 2017 werden in der nächsten Version von SQL Server veraltet sein. Verwenden Sie diese Funktionen nicht zum Entwickeln neuer Anwendungen, und ändern Sie so bald wie möglich die Anwendungen, die diese Funktionen zurzeit verwenden.

> [!NOTE]
> Diese Liste entspricht der Liste für die Reporting Services (13.x) von SQL Server 2016. Für die Reporting Services (14.x) von SQL Server 2017 gibt es keine neuen Funktionen, die als veraltet gelten oder nicht mehr unterstützt werden.


| **Kategorie** | **Veraltete Funktion** | **Ersatz** |
| --- | --- | --- |
| Berichtsserver | HTML 4.0 Renderer | HTML 5 Renderer |

## <a name="see-also"></a>Weitere Informationen

[Nicht mehr unterstützte Funktion in SQL Server Reporting Services (SSRS)](discontinued-functionality-to-sql-server-reporting-services-in-sql-server.md)

Haben Sie dazu Fragen? [Stellen Sie eine Frage im Reporting Services-Forum](https://go.microsoft.com/fwlink/?LinkId=620231)
