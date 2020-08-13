---
title: Atom-Geräteinformationseinstellungen | Microsoft-Dokumentation
description: Hier erfahren Sie mehr über die Geräteinformationseinstellungen für die Atom-Renderingerweiterung, die das Übergeben des Atom-Feednamens und der zu verwendenden Zeichencodierung unterstützt.
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 274815c98aa15aead103e33de761b8b496212242
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242500"
---
# <a name="atom-device-information-settings"></a>ATOM-Geräteinformationseinstellungen
  Die Geräteinformationseinstellungen für die Atom-Renderingerweiterung unterstützen die Übergabe des Namens eines Atom-Feeds und der zu verwendenden Zeichencodierung.  
  
 In der folgenden Tabelle sind die Geräteinformationseinstellungen für das Rendering in einem Datendienstdokument aufgeführt.  
  
|Einstellung|Wert|  
|-------------|-----------|  
|**DataFeed**|Wenn diese Einstellung angegeben ist, wird der Atom-Feed entsprechend dem Feednamen gerendert, der in ihr bereitgestellt wird. Andernfalls wird das Atom-Dienstdokument für den Bericht gerendert. Der eindeutige automatisch generierte Bezeichner des Datenfeeds. Dieser Wert wird intern verwendet, und Sie sollten ihn nicht ändern.|  
|**Codieren**|Der Internet Assigned Numbers Authority (IANA)-Name einer Zeichencodierung, die von .NET Framework unterstützt wird. Der Standardwert ist **UTF-8**. Beispiele für andere Werte: ASCII, UTF-7 und UTF-16.|  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
