---
title: Geräteinformationseinstellungen für MHTML | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.suite: pro-bi
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3e5bf5f929be3af2d5fa911c4aed93458713ceba
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43282405"
---
# <a name="mhtml-device-information-settings"></a>Geräteinformationseinstellungen für MHTML
  In der folgenden Tabelle werden die Einstellungen der Geräteinformationen zum Rendern von Berichten in das Webarchivformat (MHTML) aufgeführt.  
  
|Einstellung|value|  
|-------------|-----------|  
|**JavaScript**|Gibt an, ob JavaScript im gerenderten Bericht unterstützt wird.|  
|**OutlookCompat**|Gibt an, ob beim Rendern zusätzliche Metadaten verwendet werden sollen, um die Darstellung des Berichts in Outlook zu optimieren. Der Standardwert ist **true**.|  
|**MHTML-Fragment**|Gibt an, ob anstelle eines vollständigen MHTML-Dokuments ein MHTML-Fragment erstellt wird. Ein MHTML-Fragment enthält den Berichtsinhalt in einem TABLE-Element und lässt das HTML-Element und das BODY-Element aus. Der Standardwert ist **false**.|  
|**DataVisualizationFitSizing**|Gibt das Verhalten für die Datenvisualisierungsanpassung in einem Tablix an. Dies schließt Diagramm, Messgerät und Karte ein.<br /><br /> Mögliche Werte: **Ungefähr** und **Genau**.<br /><br /> Der Standardwert lautet **Ungefähr**. Wird die Einstellung aus der Datei **rsreportserver.config** entfernt, lautet der Wert für das Standardverhalten **Genau**.<br /><br /> Die Aktivierung von **Genau** hat möglicherweise Auswirkungen auf die Leistung, da die Verarbeitung zur Ermittlung der genauen Größe möglicherweise länger dauert.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
