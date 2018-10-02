---
title: Atom-Geräteinformationseinstellungen | Microsoft-Dokumentation
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 34ffe695a79ed0f7c7f71d82238c945723218373
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629779"
---
# <a name="atom-device-information-settings"></a>ATOM-Geräteinformationseinstellungen
  Die Geräteinformationseinstellungen für die Atom-Renderingerweiterung unterstützen die Übergabe des Namens eines Atom-Feeds und der zu verwendenden Zeichencodierung.  
  
 In der folgenden Tabelle sind die Geräteinformationseinstellungen für das Rendering in einem Datendienstdokument aufgeführt.  
  
|Einstellung|value|  
|-------------|-----------|  
|**DataFeed**|Wenn diese Einstellung angegeben ist, wird der Atom-Feed entsprechend dem Feednamen gerendert, der in ihr bereitgestellt wird. Andernfalls wird das Atom-Dienstdokument für den Bericht gerendert. Der eindeutige automatisch generierte Bezeichner des Datenfeeds. Dieser Wert wird intern verwendet, und Sie sollten ihn nicht ändern.|  
|**Codierung**|Der Internet Assigned Numbers Authority (IANA)-Name einer Zeichencodierung, die von .NET Framework unterstützt wird. Der Standardwert ist **UTF-8**. Beispiele für andere Werte: ASCII, UTF-7 und UTF-16.|  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
