---
title: Nicht mehr unterstützte Funktionen in SQL Server Reporting Services in SQLServer 2014 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- discontinued functionality [Reporting Services]
- Reporting Services, backward compatibility
- Rsactivate.exe
- unsupported features [Reporting Services]
ms.assetid: d529cc96-3483-480b-9bfc-bd28b1d0ef52
caps.latest.revision: 47
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 971662bbb0b1c8b08507574d569418d065f6204a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37201030"
---
# <a name="discontinued-functionality-to-sql-server-reporting-services-in-sql-server-2014"></a>Nicht mehr unterstützte Funktionen in SQL Server Reporting Services in SQL Server 2014
  In diesem Thema werden die Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] beschrieben, die in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]nicht mehr verfügbar sind. Das Thema enthält keine Hinweise zu Versionen von Betriebssystemen oder [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Services (IIS), die nicht mehr unterstützt werden. Weitere Informationen zu den Systemanforderungen finden Sie unter [Hardware- und Softwareanforderungen für die Installation von SQL Server 2014](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
 In diesem Thema:  
  
-   [Nicht mehr unterstützte Funktionen in SQL Server 2014 Reporting Services](#bkmk_sql14)  
  
-   [Nicht mehr unterstützte Funktionen in SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
-   [Nicht mehr unterstützte Funktionen in SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="bkmk_sql14"></a> [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Reporting Services nicht mehr unterstützte Funktionen  
 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden alle [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]-Funktionen weiterhin unterstützt.  
  
##  <a name="bkmk_rc0"></a> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Reporting Services nicht mehr unterstützte Funktionen  
 In diesem Abschnitt werden in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] nicht mehr unterstützte [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]-Funktionen beschrieben.  
  
 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden alle [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]-Funktionen weiterhin unterstützt.  
  
##  <a name="bkmk_kj"></a> Nicht mehr unterstützte Funktionen in SQL Server 2008 R2 Reporting Services  
 In diesem Abschnitt wird beschrieben, die nicht mehr [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  Da SQL Server 2008 R2 ein kleineres Versionsupgrade von SQL Server 2008 darstellt, wird empfohlen, auch den Inhalt im Abschnitt zu SQL Server 2008 zu lesen.  
  
### <a name="64-bit-platform-support"></a>64-Bit-Plattformunterstützung  
 Ab [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Komponente keine Unterstützung mehr für Itanium-basierte Server unter Windows Server 2003 oder Windows Server 2003 R2. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] weiterhin andere 64-Bit-Betriebssystemen, einschließlich Windows Server 2008 für Itanium-basierte Systeme und Windows Server 2008 R2 für Itanium-basierte Systeme unterstützt. Um von einer [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]-Installation mit [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] unter einer Itanium-basierten Systemedition von Windows Server 2003 oder Windows Server 2003 R2 auf [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] zu aktualisieren, müssen Sie zunächst das Betriebssystem aktualisieren.  
  
### <a name="data-source-credentials-in-url-access"></a>Datenquellenanmeldeinformationen beim URL-Zugriff  
 Die Parameterzeichenfolgen für den URL-Zugriff *dsu:datasourcename=value* und *dsp:datasourcename=value* wurden eingestellt. In vorherigen Versionen wurden diese Parameterzeichenfolgen im Textformat im Browsercache gespeichert, was nicht sicher ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Neues &#40;Reporting Services&#41;](what-s-new-reporting-services.md)   
 [Verhaltensänderungen in SQL Server Reporting Services in SQLServer 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)   
 [Als veraltet markierte Features in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)  
  
  
