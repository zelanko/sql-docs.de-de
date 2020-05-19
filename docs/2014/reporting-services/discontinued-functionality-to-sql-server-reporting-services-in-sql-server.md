---
title: Unterstützte Funktionen
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: conceptual
ms.custom: seodec18
ms.date: 12/14/2018
ms.openlocfilehash: 8cdec8ed3fbdd539b0c630af2a298ebf9807d6a7
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82755755"
---
# <a name="discontinued-functionality-in-sql-server-reporting-services-ssrs"></a>Nicht mehr unterstützte Funktion in SQL Server Reporting Services (SSRS)

  In diesem Thema werden die Funktionen von [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] beschrieben, die in [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]nicht mehr verfügbar sind. Das Thema enthält keine Hinweise zu Versionen von Betriebssystemen oder [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Services (IIS), die nicht mehr unterstützt werden. Weitere Informationen zu den Systemvoraussetzungen finden Sie unter [Hardware-und Software Anforderungen für die Installation von SQL Server 2014](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
 Inhalte dieses Themas:  
  
- [SQL Server 2014 Reporting Services nicht mehr unterstützte Funktionalität](#bkmk_sql14)  
  
- [Nicht mehr unterstützte Funktionen in SQL Server 2012 Reporting Services](#bkmk_rc0)  
  
- [Nicht mehr unterstützte Funktionen in SQL Server 2008 R2 Reporting Services](#bkmk_kj)  
  
##  <a name="sssql14-reporting-services-discontinued-functionality"></a><a name="bkmk_sql14"></a>Nicht mehr unterstützte [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] Funktionen Reporting Services

 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden alle [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]-Funktionen weiterhin unterstützt.  
  
##  <a name="sssql11-reporting-services-discontinued-functionality"></a><a name="bkmk_rc0"></a>Nicht mehr unterstützte [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Funktionen Reporting Services

 In diesem Abschnitt werden in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] nicht mehr unterstützte [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]-Funktionen beschrieben.  
  
 In [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] werden alle [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]-Funktionen weiterhin unterstützt.  
  
##  <a name="sql-server-2008-r2-reporting-services-discontinued-functionality"></a><a name="bkmk_kj"></a>SQL Server 2008 R2 Reporting Services nicht mehr unterstützte Funktionalität

 In diesem Abschnitt wird in nicht mehr unterstützt [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] .  
  
> [!NOTE]  
> Da SQL Server 2008 R2 ein kleineres Versionsupgrade von SQL Server 2008 darstellt, wird empfohlen, auch den Inhalt im Abschnitt zu SQL Server 2008 zu lesen.
  
### <a name="64-bit-platform-support"></a>64-Bit-Plattformunterstützung

 Ab [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]bietet die [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Komponente keine Unterstützung mehr für Itanium-basierte Server unter Windows Server 2003 oder Windows Server 2003 R2. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]unterstützt weiterhin andere 64-Bit-Betriebssysteme, einschließlich Windows Server 2008 für Itanium-basierte Systeme und Windows Server 2008 R2 für Itanium-basierte Systeme. Um von einer [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] -Installation mit [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] unter einer Itanium-basierten Systemedition von Windows Server 2003 oder Windows Server 2003 R2 auf [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] zu aktualisieren, müssen Sie zunächst das Betriebssystem aktualisieren.  
  
### <a name="data-source-credentials-in-url-access"></a>Datenquellenanmeldeinformationen beim URL-Zugriff

 Die Parameterzeichenfolgen für den URL-Zugriff *dsu:datasourcename=value* und *dsp:datasourcename=value* wurden eingestellt. In vorherigen Versionen wurden diese Parameterzeichenfolgen im Textformat im Browsercache gespeichert, was nicht sicher ist.  
  
## <a name="next-steps"></a>Nächste Schritte

 - [Neues &#40;Reporting Services&#41;](what-s-new-reporting-services.md)
 - [Verhaltensänderungen in SQL Server Reporting Services in SQL Server 2014](behavior-changes-to-sql-server-reporting-services-in-sql-server-2016.md)
 - [Als veraltet markierte Funktionen in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md)