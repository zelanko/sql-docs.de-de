---
title: XML-Geräteinformationseinstellungen | Microsoft-Dokumentation
description: In diesem Artikel erfahren Sie mehr über die verschiedenen Geräteinformationseinstellungen zum Rendern im XML-Format.
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- XML [Reporting Services], rendering
- device information settings [Reporting Services], PDF rendering
ms.assetid: a32e83fe-c10e-4ebd-8975-5be7dcc422e7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 72a645983dadaeff9c446ef3baf6fbcbfc94990b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87247407"
---
# <a name="xml-device-information-settings"></a>XML-Geräteinformationseinstellungen
  In der folgenden Tabelle werden die Geräteinformationseinstellungen zum Rendern in das XML-Format aufgeführt.  
  
|Einstellung|Werte|Details|  
|-------------|------------|-------------|  
|**XSLT**|Der Pfad zum Berichtsserver-Namespace von XSLT, der auf die XML-Datei, z.B. **/Transforms/myxslt**angewendet werden soll.|Die XSL-Datei muss eine veröffentlichte Ressource auf einem Berichtsserver sein, und Sie müssen über einen Berichtsserver-Elementpfad darauf zugreifen. Der Wert dieser Einstellung wird nach jedem XSLT übernommen, das im Bericht angegeben wird. Wird die **XSLT** -Einstellung angewendet, wird die **OmitSchema** -Einstellung nicht beachtet.|  
|**MIMEType**|MIME-Typ (Multipurpose Internet Mail Extensions) der XML-Datei||  
|**UseFormattedValues**|**true**<br /><br /> **false**|Gibt an, ob der formatierte Wert eines Textfelds beim Generieren der XML-Daten gerendert werden soll.<br /><br /> Ein false-Wert gibt an, dass der zugrundeliegende Wert des Textfelds verwendet wird.|  
|**Indented**|**true**<br /><br /> **false**|Gibt an, ob XML-Dateien mit Einzug generiert werden sollen. Der Standardwert **FALSE** generiert komprimierte XML-Dateien ohne Einzug.|  
|**OmitNamespace**|**true**<br /><br /> **false**|Gibt an, ob der Standardnamespace in der XML-Datei weggelassen werden soll.<br /><br /> Bei "true" wird kein Standardnamespace in der XML-Datei angegeben.<br /><br /> Bei FALSE gibt die XML-Datei einen Standardnamespace mit dem Wert der DataSchema-Eigenschaft des Berichts an. Die DataSchema-Eigenschaft verwendet standardmäßig den Berichtsnamen.<br /><br /> Der Standardwert ist**false**.|  
|**OmitSchema**|**true**<br /><br /> **false**|Gibt an, ob der Schemaspeicherort in der XML-Datei weggelassen werden soll. Der Speicherort ist das SchemaLocation-Attribut.<br /><br /> Der Standardwert von OmitSchema hängt vom OmitNamespace-Wert ab:<br /><br /> Wenn OmitNamespace = False, gilt standardmäßig OmitSchema = **False** . Der Benutzer kann den Standardwert überschreiben, indem OmitSchema = True festgelegt wird.<br /><br /> Wenn OmitNamespace = true, gilt für OmitSchema **TRUE** – unabhängig vom explizit für OmitSchema konfigurierten Wert.|  
|**Codieren**|Der Internet Assigned Numbers Authority (IANA)-Name einer Zeichencodierung, die von .NET Framework unterstützt wird.|Der Standardwert ist **UTF-8**. Beispiele für andere Werte: ASCII, UTF-7 und UTF-16.|  
|**FileExtension**|Die Dateierweiterung für die generierte Datei.||  
|**Schema**|Der Wert **true** gibt an, dass ein XML-Schema gerendert wird. Der Standardwert ist **false**.|Gibt an, ob die XML-Schemadefinition (XSD) gerendert wird oder ob die tatsächlichen XML-Daten gerendert werden.|  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
