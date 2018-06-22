---
title: Geräteinformationseinstellungen für Word | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Word [Reporting Services]
- device information settings [Reporting Services], Word
ms.assetid: 28146498-fae7-4b13-b47f-6ec05aa8e057
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 5b31b3c3ea0cf5b70967ca099e0b979f0c929334
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36147817"
---
# <a name="word-device-information-settings"></a>Geräteinformationseinstellungen für Word
  In der folgenden Tabelle werden die Geräteinformationseinstellungen zum Rendern in das Format [!INCLUDE[ofprword](../includes/ofprword-md.md)] aufgeführt.  
  
|Einstellung|value|  
|-------------|-----------|  
|`AutoFit`|`False`installiert haben. AutoAnpassen wird festgelegt, um `false` in keiner Wordtabelle festgelegt.<br /><br /> `True`installiert haben. AutoAnpassen wird festgelegt, um `true` in jeder Word-Tabelle.<br /><br /> `Never`installiert haben. Die Werte für AutoAnpassen sind in keiner Word-Tabelle festgelegt, und der Word-Standardwert wird wiederhergestellt.<br /><br /> `Default`installiert haben. AutoAnpassen wird in den Tabellen eingestellt, die enger als der physische Zeichenbereich (physische Seitenbreite ohne Ränder) pro logischer Seite sind.|  
|`ExpandToggles`|Gibt an, ob alle Elemente, die aus- und eingeschaltet werden können, in ihrem voll erweiterten Status gerendert werden sollten. Der Standardwert lautet `false`.|  
|`FixedPageWidth`|Gibt an, ob die in die DOC-Datei geschriebene Seitenbreite erhöht wird, damit die Breite der größten Seite im Hauptteil des Berichts hineinpasst. Der Standardwert lautet `false`.|  
|**OmitHyperlinks**|Gibt an, ob die Linkaktion auf allen Elementen weggelassen werden soll, wo sie festgelegt ist. Der Standardwert ist `false`|  
|`OmitDrillthroughs`|Gibt an, ob die Drillthrough-Aktion auf allen Elementen weggelassen werden soll, wo sie festgelegt ist. Der Standardwert ist `false`|  
  
## <a name="see-also"></a>Siehe auch  
 [Übergeben von Geräteinformationseinstellungen an Renderingerweiterungen](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Anpassen der Parameter für Renderingerweiterungen in der Datei „RSReportServer.config“](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Technische Referenz (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  