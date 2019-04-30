---
title: Geräteinformationseinstellungen für MHTML | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], MHTML rendering
- MHTML [Reporting Services]
ms.assetid: 60b85dd8-b4fb-4ad9-be6a-e7c89ac076fe
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 196afebcabea54fda1b315b1c2f17c0029842f07
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63280385"
---
# <a name="mhtml-device-information-settings"></a>Geräteinformationseinstellungen für MHTML
  In der folgenden Tabelle werden die Einstellungen der Geräteinformationen zum Rendern von Berichten in das Webarchivformat (MHTML) aufgeführt.  
  
|Einstellung|Wert|  
|-------------|-----------|  
|**JavaScript**|Gibt an, ob JavaScript im gerenderten Bericht unterstützt wird.|  
|**OutlookCompat**|Gibt an, ob beim Rendern zusätzliche Metadaten verwendet werden sollen, um die Darstellung des Berichts in Outlook zu optimieren. Der Standardwert ist `true`.|  
|**MHTML-Fragment**|Gibt an, ob anstelle eines vollständigen MHTML-Dokuments ein MHTML-Fragment erstellt wird. Ein MHTML-Fragment enthält den Berichtsinhalt in einem TABLE-Element und lässt das HTML-Element und das BODY-Element aus. Der Standardwert ist `false`.|  
|**DataVisualizationFitSizing**|Gibt das Verhalten für die Datenvisualisierungsanpassung in einem Tablix an. Dies schließt Diagramm, Messgerät und Karte ein.<br /><br /> Mögliche Werte: **Ungefähr** und **Genau**.<br /><br /> Der Standardwert lautet **Ungefähr**. Wird die Einstellung aus der Datei **rsreportserver.config** entfernt, lautet der Wert für das Standardverhalten **Genau**.<br /><br /> Die Aktivierung von **Genau** hat möglicherweise Auswirkungen auf die Leistung, da die Verarbeitung zur Ermittlung der genauen Größe möglicherweise länger dauert.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei RSReportServer.config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
