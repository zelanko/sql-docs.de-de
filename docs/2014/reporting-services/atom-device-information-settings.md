---
title: Atom-Geräteinformationseinstellungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe4a56a4-5552-423c-85c1-895e2e212fee
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: f2742b7507eecaadc26604f4217b1c6b2f1def1d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059090"
---
# <a name="atom-device-information-settings"></a>ATOM-Geräteinformationseinstellungen
  Die Geräteinformationseinstellungen für die Atom-Renderingerweiterung unterstützen die Übergabe des Namens eines Atom-Feeds und der zu verwendenden Zeichencodierung.  
  
 In der folgenden Tabelle sind die Geräteinformationseinstellungen für das Rendering in einem Datendienstdokument aufgeführt.  
  
|Einstellung|value|  
|-------------|-----------|  
|`DataFeed`|Wenn diese Einstellung angegeben ist, wird der Atom-Feed entsprechend dem Feednamen gerendert, der in ihr bereitgestellt wird. Andernfalls wird das Atom-Dienstdokument für den Bericht gerendert. Der eindeutige automatisch generierte Bezeichner des Datenfeeds. Dieser Wert wird intern verwendet, und Sie sollten ihn nicht ändern.|  
|**Codierung**|Der Internet Assigned Numbers Authority (IANA)-Name einer Zeichencodierung, die von .NET Framework unterstützt wird. Der Standardwert lautet `UTF-8`. Beispiele für andere Werte: ASCII, UTF-7 und UTF-16.|  
  
## <a name="see-also"></a>Siehe auch  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  