---
title: Geräteinformationseinstellungen für Excel | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die verschiedenen Geräteinformationseinstellungen zum Rendern im Microsoft Excel-Format.
ms.date: 01/23/2020
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c4d84c98923a3cee94f64fed863e621821bd7a39
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245129"
---
# <a name="excel-device-information-settings"></a>Geräteinformationseinstellungen für Excel
  In der folgenden Tabelle werden die Geräteinformationseinstellungen zum Rendern in das Format [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] aufgeführt.  
  
|Einstellung|Wert|  
|-------------|-----------|  
|**OmitDocumentMap**|Gibt an, ob die Dokumentstruktur für Berichte weggelassen werden soll, die sie unterstützen. Der Standardwert ist **false**.|  
|**OmitFormulas**|Gibt an, ob Formeln aus dem gerenderten Bericht weggelassen werden sollen. Der Standardwert ist **false**.|  
|**SimplePageHeaders**|Gibt an, ob der Seitenkopf des Berichts in den Excel-Seitenkopf gerendert wird. Der Wert **false** gibt an, dass der Seitenkopf in die erste Zeile des Arbeitsblatts gerendert wird. Der Standardwert ist **false**.|  
|**DynamicImageDpi**|Diese Einstellung bezieht sich auf die Auflösung dynamischer Bilder wie Diagramme, Messgeräte und Karten. Der Standardwert ist **96** (im Power BI-Berichtsserver der Version von Januar 2020 und in neueren Versionen verfügbar).|  

  
## <a name="see-also"></a>Weitere Informationen  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
