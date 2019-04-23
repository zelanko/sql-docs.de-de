---
title: PDF-Geräteinformationseinstellungen - Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], PDF rendering
- PDF [Reporting Services]
ms.assetid: 9a4aabe5-dbdc-4884-b999-1200983fee47
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 29274efcc4bc88c13537d240efcbc9ce4b25ea58
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59962738"
---
# <a name="pdf-device-information-settings"></a>PDF-Geräteinformationseinstellungen
  In der folgenden Tabelle werden die Einstellungen der Geräteinformationen zum Rendern von Berichten in das PDF-Format aufgeführt.  
  
|Einstellung|Wert|  
|-------------|-----------|  
|**Spalten**|Die für den Bericht gewünschte Anzahl der Spalten. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**ColumnSpacing**|Der für den Bericht gewünschte Spaltenabstand. Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**DpiX**|Die Auflösung des Ausgabegeräts in x-Richtung.|  
|**DpiY**|Die Auflösung des Ausgabegeräts in y-Richtung.|  
|**EndPage**|Die letzte Seite des zu rendernden Berichts. Der Standardwert ist der Wert für `StartPage`.|  
|`HumanReadablePDF`|Gibt an, ob die PDF komprimiert werden soll, was die Quelle lesbarer macht. Der Standardwert ist `false.`|  
|**MarginBottom**|Der für den Bericht gewünschte Wert für den unteren Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „1in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginLeft**|Der für den Bericht gewünschte Wert für den linken Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „1in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginRight**|Der für den Bericht gewünschte Wert für den rechten Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „1in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**MarginTop**|Der für den Bericht gewünschte Wert für den oberen Rand in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „1in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PageHeight**|Die für den Bericht gewünschte Seitenhöhe in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert gefolgt von „in“ angeben (z. B. „11in“). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|**PageWidth**|Die für den Bericht gewünschte Seitenbreite in Zoll. Sie müssen eine ganze Zahl oder einen Dezimalwert angeben, gefolgt von „in“ (z. B. 8,5in). Dieser Wert überschreibt die ursprünglichen Einstellungen des Berichts.|  
|`StartPage`|Die erste Seite des zu rendernden Berichts. Der Wert `0` gibt an, dass alle Seiten des Berichts gerendert werden. Der Standardwert ist `1`.|  
  
## <a name="see-also"></a>Siehe auch  
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei RSReportServer.config](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz &#40;SSRS&#41;](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
