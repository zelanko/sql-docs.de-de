---
title: Bildgerät-Informationseinstellungen | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- images [Reporting Services], rendering
- device information settings [Reporting Services], IMAGE rendering
ms.assetid: edad9498-69f7-4726-8699-fa615f704dff
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b59fcf947a283ef60f5dd34f60e2cf365092cfa7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47738728"
---
# <a name="image-device-information-settings"></a>Geräteinformationseinstellungen für Bilder
  In der folgenden Tabelle sind die Geräteinformationseinstellungen zum Rendern in das Bildformat aufgeführt.  
  
|Einstellung|value|  
|-------------|-----------|  
|**Spalten**|Die für den Bericht gewünschte Anzahl der Spalten. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**ColumnSpacing**|Der für den Bericht gewünschte Spaltenabstand. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**DpiX**|Die horizontale Auflösung des Ausgabebilds. Der Standardwert ist **96** Gilt für die Ausgabeformate **BMP**, **GIF**, **PNG**und **TIFF** .|  
|**DpiY**|Die vertikale Auflösung des Ausgabebilds. Der Standardwert ist **96** Gilt für die Ausgabeformate **BMP**, **GIF**, **PNG**und **TIFF** .|  
|**EndPage**|Die letzte Seite des zu rendernden Berichts. Der Standardwert ist der Wert für **StartPage**.|  
|**MarginBottom**|Der für den Bericht gewünschte Wert für den unteren Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **1in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginLeft**|Der für den Bericht gewünschte Wert für den linken Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **1in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginRight**|Der für den Bericht gewünschte Wert für den rechten Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **1in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginTop**|Der für den Bericht gewünschte Wert für den oberen Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **1in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**Ausgabeformat**|Eines der [!INCLUDE[ndptecgdiexpanded](../includes/ndptecgdiexpanded-md.md)] ([!INCLUDE[ndptecgdi](../includes/ndptecgdi-md.md)]) unterstützten Ausgabeformate: **BMP**, **EMF**, **GIF**, **JPEG**, **PNG**oder **TIFF**.|  
|**PageHeight**|Die für den Bericht gewünschte Seitenhöhe in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z.B. **11in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PageWidth**|Die für den Bericht gewünschte Seitenbreite in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert angeben, gefolgt von „in“ (z.B. **8,5in**). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PrintDpiX**|Die horizontale Auflösung des Ausgabebilds. Der Standardwert lautet **300**. Gilt für das**EMF**-Ausgabeformat (Enhanced MetaFile).|  
|**PrintDpiY**|Die vertikale Auflösung des Ausgabebilds. Der Standardwert lautet **300**. Gilt für das**EMF**-Ausgabeformat (Enhanced MetaFile).|  
|**StartPage**|Die erste Seite des zu rendernden Berichts. Der Wert **0** gibt an, dass alle Seiten des Berichts gerendert werden. Der Standardwert ist **1**.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
