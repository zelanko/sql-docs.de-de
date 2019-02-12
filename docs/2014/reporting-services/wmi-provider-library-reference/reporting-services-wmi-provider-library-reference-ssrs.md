---
title: WMI-Anbieterbibliotheksreferenz für Reporting Services (SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- Reporting Services WMI Provider Library
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], library
ms.assetid: 17ba711d-7eff-4423-9168-63dc425a3428
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 302e7f1b58fdb2a63af9f2a1b4e9dad3127c6d57
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56034511"
---
# <a name="reporting-services-wmi-provider-library-reference-ssrs"></a>Reporting Services-WMI-Anbieterbibliotheksreferenz (SSRS)
  Der Anbieter der [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Windows-Verwaltungsinstrumentation (Windows Management Instrumentation, WMI) unterstützt WMI-Vorgänge, die es Ihnen ermöglichen, Skripts und Code zum Ändern der Einstellungen des Berichtsservers und des Berichts-Managers zu erstellen.  
  
 Wenn Sie zum Beispiel ändern möchten, ob die integrierte Sicherheit verwendet wird, wenn der Berichtsserver eine Verbindung zur Berichtsserver-Datenbank herstellt, erstellen Sie eine Instanz der MSReportServer_ConfigurationSetting-Klasse, und verwenden Sie die DatabaseIntegratedSecurity-Eigenschaft der Berichtsserverinstanz. Die in der folgenden Tabelle angezeigten Klassen stellen [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Komponenten dar. Die Klassen werden entweder im [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)] -Namespace oder im [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)] -Namespace definiert. Jede der Klassen unterstützt Lese- und Schreibvorgänge. Erstellvorgänge werden nicht unterstützt.  
  
## <a name="classes"></a>Klassen  
 [MSReportServer_Instance-Klasse](msreportserver-instance-class.md)  
 Stellt grundlegende Informationen bereit, die ein Client benötigt, um eine Verbindung mit einem installierten Berichtsserver herzustellen.  
  
 [MSReportServer_ConfigurationSetting Class (MSReportServer_ConfigurationSetting-Klasse)](msreportserver-configurationsetting-class.md)  
 Stellt die Installationsparameter und die Laufzeitparameter einer Berichtsserverinstanz dar. Diese Parameter werden in der Konfigurationsdatei für den Berichtsserver gespeichert.  
  
 Weitere Informationen zu WMI-Vorgängen finden Sie in der WMI SDK-Dokumentation, die mit dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK geliefert wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf den Reporting Services-WMI-Anbieter](../tools/access-the-reporting-services-wmi-provider.md)   
 [Technische Referenz &#40;SSRS&#41;](../technical-reference-ssrs.md)  
  
  
