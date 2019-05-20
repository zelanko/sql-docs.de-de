---
title: Geräteinformationseinstellungen für Word | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 776a825c480568be2640d1309c7c3a48970e2c54
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65571139"
---
# <a name="word-device-information-settings"></a>Geräteinformationseinstellungen für Word
  In der folgenden Tabelle werden die Geräteinformationseinstellungen zum Rendern in das Format [!INCLUDE[ofprword](../includes/ofprword-md.md)] aufgeführt.  
  
|Einstellung|value|  
|-------------|-----------|  
|**AutoFit**|**False**. AutoAnpassen wird in jeder Word-Tabelle auf **false** eingestellt.<br /><br /> **True**. AutoAnpassen wird in jeder Word-Tabelle auf **true** eingestellt.<br /><br /> **Never**. Die Werte für AutoAnpassen sind in keiner Word-Tabelle festgelegt, und der Word-Standardwert wird wiederhergestellt.<br /><br /> **Default**. AutoAnpassen wird in den Tabellen eingestellt, die enger als der physische Zeichenbereich (physische Seitenbreite ohne Ränder) pro logischer Seite sind.|  
|**ExpandToggles**|Gibt an, ob alle Elemente, die aus- und eingeschaltet werden können, in ihrem voll erweiterten Status gerendert werden sollten. Der Standardwert ist **false**.|  
|**FixedPageWidth**|Gibt an, ob die in die DOC-Datei geschriebene Seitenbreite erhöht wird, damit die Breite der größten Seite im Hauptteil des Berichts hineinpasst. Der Standardwert ist **false**.|  
|**OmitHyperlinks**|Gibt an, ob die Linkaktion auf allen Elementen weggelassen werden soll, wo sie festgelegt ist. Der Standardwert ist **false**|  
|**OmitDrillthroughs**|Gibt an, ob die Drillthrough-Aktion auf allen Elementen weggelassen werden soll, wo sie festgelegt ist. Der Standardwert ist **false**|  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei RSReportServer.config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz &#40;SSRS&#41;](../reporting-services/technical-reference-ssrs.md)  
  
  
