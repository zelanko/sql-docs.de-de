---
title: Geräteinformationseinstellungen für Excel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
caps.latest.revision: 40
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 518033807ca52001a09a01136225f3a7594af7d2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36151755"
---
# <a name="excel-device-information-settings"></a>Geräteinformationseinstellungen für Excel
  In der folgenden Tabelle werden die Geräteinformationseinstellungen zum Rendern in das Format [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] aufgeführt.  
  
|Einstellung|value|  
|-------------|-----------|  
|**OmitDocumentMap**|Gibt an, ob die Dokumentstruktur für Berichte weggelassen werden soll, die sie unterstützen. Der Standardwert lautet `false`.|  
|**OmitFormulas**|Gibt an, ob Formeln aus dem gerenderten Bericht weggelassen werden sollen. Der Standardwert lautet `false`.|  
|`SimplePageHeade`RS|Gibt an, ob der Seitenkopf des Berichts in den Excel-Seitenkopf gerendert wird. Der Wert `false` gibt an, dass der Seitenkopf in die erste Zeile des Arbeitsblatts gerendert wird. Der Standardwert lautet `false`.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  