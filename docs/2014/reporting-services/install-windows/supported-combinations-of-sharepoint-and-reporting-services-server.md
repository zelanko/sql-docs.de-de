---
title: Unterstützte Kombinationen von SharePoint- und Reporting Services-Server und-Add-in (SQLServer 2014) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SharePoint mode
- add-in for sharepoint
ms.assetid: dc6a3372-db26-43f0-b7aa-f725acc635c2
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: b4e1a516f10c15b8e84d80ff91de1aa9d66d8e1b
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034101"
---
# <a name="supported-combinations-of-sharepoint-and-reporting-services-server-and-add-in-sql-server-2014"></a>Unterstützte Kombinationen von SharePoint und Reporting Services-Server und -Add-In (SQL Server 2014)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsserver können im SharePoint-Modus installiert und in eine SharePoint-Bereitstellung integriert werden. Nicht alle Funktionen werden in allen Kombinationen von Berichtsserver, Reporting Services-Add-In für SharePoint und SharePoint-Produkten unterstützt. In diesem Thema werden die unterstützten Kombinationen zusammengefasst. In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] resultiert die Integration aus der Kombination folgender Komponenten:  
  
-   Eine Version eines für den SharePoint-Modus konfigurierten [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Berichtsservers.  
  
-   Ein SharePoint-Produkt.  
  
-   Das [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]-Add-In für SharePoint-Produkte, die Sie auf den SharePoint-Servern installieren.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  SharePoint 2013 &#124; SharePoint 2010 &#124; SharePoint 2007|  
  
## <a name="supported-combinations-of-sharepoint-and-reporting-services-components"></a>Unterstützte Kombinationen von SharePoint- und Reporting Services-Komponenten  
 In der folgenden Tabelle werden die unterstützten Kombinationen von Berichtsserver, dem Reporting Services-Add-In für SharePoint-Produkte und SharePoint-Produkten zusammengefasst. Nicht in der folgenden Tabelle aufgeführte Kombinationen werden nicht unterstützt.  
  
### <a name="supported-combinations"></a>Unterstützte Kombinationen  
  
||Berichtsserver|Add-In|SharePoint-Version|Supported|  
|-|-------------------|-------------|------------------------|---------------|  
|1|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2013|Ja|  
|2|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Ja|  
|3|[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] und [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2013|Ja|  
|4|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Ja<br /><br /> Ausnahme: Power View-Integration wird nicht unterstützt.|  
|5|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|SharePoint 2010|Ja|  
|6|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|SharePoint 2010|Ja|  
|7|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] und [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]|SharePoint 2010|Ja|  
|8|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|SharePoint 2010|Ja|  
|9|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|Ja|  
|10|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] R2|SharePoint 2010|Ja|  
|11|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] SP2|SharePoint 2007|Ja|  
  
 Weitere Informationen zu [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Features und-berichtsservermodi finden Sie unter [Reporting Services-Berichtsserver](../reporting-services-report-server.md).  
  
 **Weitere Hinweise:**  
  
-   Die Unterstützung von SharePoint 2013, einschließlich der Power View-Integration, erfordert den [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Berichtsserver und die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In-Version von SQL Server 2012 SP1 oder höher.  
  
-   Power View wurde in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]eingeführt. Daher erfordert die Power View-Integration in SharePoint 2010 die [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] -Version des Add-Ins oder eine höhere Version.  
  
-   Das SQL Server 2008 R2-Add-In wird von Berichtsservern von SQL Server 2012 (oder höher) nicht unterstützt. Das SQL Server 2008 R2-Add-In wird vom SharePoint 2010-Installationsprogramm für erforderliche Komponenten automatisch installiert. Vor der Installation einer neueren Add-In-Version muss das Add-In deinstalliert werden. Direkte Upgrades des Add-Ins werden nicht unterstützt.  
  
-   **Upgrade:** SharePoint 2010 mit der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-In installiert ist, kann nicht aktualisiert werden direkt auf SharePoint 2013. SharePoint 2013 erfordert [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] oder eine höhere Version des [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Add-Ins und -Berichtsservers. Weitere Informationen zum Upgrade finden Sie unter [Upgrade and Migrate Reporting Services](upgrade-and-migrate-reporting-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Verfügbarkeit des Reporting Services-Add-Ins für SharePoint-Produkte](where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)   
 [Von den Editionen von SQLServer 2014 unterstützte Funktionen](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Aktualisieren und Migrieren von Reporting Services](upgrade-and-migrate-reporting-services.md)  
  
  
