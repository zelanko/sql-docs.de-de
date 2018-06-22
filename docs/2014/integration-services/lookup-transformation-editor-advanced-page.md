---
title: Transformations-Editor (Seite erweitert) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4982bd1a964e72d6a7e36d88a6f500d2a3ba5d89
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150203"
---
# <a name="lookup-transformation-editor-advanced-page"></a>Transformations-Editor für Suche (Seite 'Erweitert')
  Auf der Seite **Erweitert** des Dialogfelds **Transformations-Editor für Suche** können Sie die teilweise Zwischenspeicherung konfigurieren und die SQL-Anweisung für die Suchtransformation ändern.  
  
 Weitere Informationen zur Transformation für Suche finden Sie unter [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Cachegröße (32-Bit)**  
 Passen Sie die Cachegröße (in Megabytes) für 32-Bit-Computer an. Der Standardwert ist 5 Megabytes.  
  
 **Cachegröße (64-Bit)**  
 Passen Sie die Cachegröße (in Megabytes) für 64-Bit-Computer an. Der Standardwert ist 5 Megabytes.  
  
 **Cache für Zeilen ohne übereinstimmende Einträge aktivieren**  
 Zeilen ohne übereinstimmende Einträge im Verweisdataset werden zwischengespeichert.  
  
 **Zuordnung von Cache**  
 Geben Sie den Prozentsatz des Caches an, der für Zeilen ohne übereinstimmende Einträge im Verweisdataset zugeordnet werden soll.  
  
 **SQL-Anweisung ändern**  
 Hiermit ändern Sie die zum Generieren des Verweisdatasets verwendete SQL-Anweisung.  
  
> [!NOTE]  
>  Durch die auf dieser Seite angegebene optionale SQL-Anweisung wird der auf der Seite **Verbindung** im **Transformations-Editor für Suche**angegebene Tabellenname überschrieben und ersetzt. Weitere Informationen finden Sie unter [Transformations-Editor für Suche &#40;Seite „Verbindung“&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md).  
  
 **Abfrageparameter festlegen**  
 Ordnen Sie mithilfe des Dialogfelds **Abfrageparameter festlegen** die Eingabespalten den Parametern zu.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 Blogeintrag [Lookup cache modes](http://go.microsoft.com/fwlink/?LinkId=219518) (Suchcachemodi) auf blogs.msdn.com  
  
## <a name="see-also"></a>Siehe auch  
 [Transformations-Editor &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Transformations-Editor &#40;Seite "Verbindung"&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Spalten“&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Transformations-Editor &#40;Seite "Fehlerausgabe"&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Erstellen und Meldungsreferenz von Integration Services-Fehler](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformation für Fuzzysuche](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  