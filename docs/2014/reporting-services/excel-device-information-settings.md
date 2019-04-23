---
title: Geräteinformationseinstellungen für Excel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], Excel rendering
- Excel [Reporting Services], rendering
ms.assetid: bb5f3566-f033-4470-be87-1f52fb7a4ab6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5d1ec9b650592be41c8ae2f7043649c91ea78442
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59948326"
---
# <a name="excel-device-information-settings"></a>Geräteinformationseinstellungen für Excel
  In der folgenden Tabelle werden die Geräteinformationseinstellungen zum Rendern in das Format [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] aufgeführt.  
  
|Einstellung|Wert|  
|-------------|-----------|  
|**OmitDocumentMap**|Gibt an, ob die Dokumentstruktur für Berichte weggelassen werden soll, die sie unterstützen. Der Standardwert ist `false`.|  
|**OmitFormulas**|Gibt an, ob Formeln aus dem gerenderten Bericht weggelassen werden sollen. Der Standardwert ist `false`.|  
|`SimplePageHeade`rs|Gibt an, ob der Seitenkopf des Berichts in den Excel-Seitenkopf gerendert wird. Der Wert `false` gibt an, dass der Seitenkopf in die erste Zeile des Arbeitsblatts gerendert wird. Der Standardwert ist `false`.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei RSReportServer.config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
