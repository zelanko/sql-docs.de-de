---
title: WMI-Anbieterbibliotheksreferenz für Reporting Services (SSRS) | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: wmi-provider-library-reference
ms.topic: conceptual
apiname:
- Reporting Services WMI Provider Library
apilocation:
- reportingservices.mof
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: af3b51f934b9b0221747116772af7a747813e70f
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65571058"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a>Reporting Services-WMI-Anbieterbibliotheksreferenz (SSRS)
  Der Anbieter der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) unterstützt WMI-Vorgänge, die es Ihnen ermöglichen, Skripts und Code zum Ändern der Einstellungen des Berichtsservers und des Berichts-Managers zu erstellen.  
  
 Wenn Sie zum Beispiel ändern möchten, ob die integrierte Sicherheit verwendet wird, wenn der Berichtsserver eine Verbindung zur Berichtsserver-Datenbank herstellt, erstellen Sie eine Instanz der MSReportServer_ConfigurationSetting-Klasse, und verwenden Sie die DatabaseIntegratedSecurity-Eigenschaft der Berichtsserverinstanz. Die in der folgenden Tabelle angezeigten Klassen stellen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten dar. Die Klassen werden entweder im [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] -Namespace oder im [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] -Namespace definiert. Jede der Klassen unterstützt Lese- und Schreibvorgänge. Erstellvorgänge werden nicht unterstützt.  
  
## <a name="classes"></a>Klassen  
 [MSReportServer_Instance-Klasse](../../reporting-services/wmi-provider-library-reference/msreportserver-instance-class.md)  
 Stellt grundlegende Informationen bereit, die ein Client benötigt, um eine Verbindung mit einem installierten Berichtsserver herzustellen.  
  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-class.md)  
 Stellt die Installationsparameter und die Laufzeitparameter einer Berichtsserverinstanz dar. Diese Parameter werden in der Konfigurationsdatei für den Berichtsserver gespeichert.  
  
 Weitere Informationen zu WMI-Vorgängen finden Sie in der WMI SDK-Dokumentation, die mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK geliefert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Zugreifen auf den Reporting Services-WMI-Anbieter](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md)   
 [Technische Referenz &#40;SSRS&#41;](../../reporting-services/technical-reference-ssrs.md)  
  
  
