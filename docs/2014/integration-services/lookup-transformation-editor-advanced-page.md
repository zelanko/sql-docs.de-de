---
title: Transformations-Editor für Suche (Seite "Erweitert") | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f78c568d467601b2f23ae8952036764ea2b464d8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057879"
---
# <a name="lookup-transformation-editor-advanced-page"></a>Transformations-Editor für Suche (Seite 'Erweitert')
  Auf der Seite **Erweitert** des Dialogfelds **Transformations-Editor für Suche** können Sie die teilweise Zwischenspeicherung konfigurieren und die SQL-Anweisung für die Suchtransformation ändern.  
  
 Weitere Informationen zur Transformation für Suche finden Sie unter [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Tastatur  
 **Cache Größe (32 Bit)**  
 Passen Sie die Cachegröße (in Megabytes) für 32-Bit-Computer an. Der Standardwert ist 5 Megabytes.  
  
 **Cache Größe (64 Bit)**  
 Passen Sie die Cachegröße (in Megabytes) für 64-Bit-Computer an. Der Standardwert ist 5 Megabytes.  
  
 **Cache für Zeilen ohne übereinstimmende Einträge aktivieren**  
 Zeilen ohne übereinstimmende Einträge im Verweisdataset werden zwischengespeichert.  
  
 **Zuordnung aus dem Cache**  
 Geben Sie den Prozentsatz des Caches an, der für Zeilen ohne übereinstimmende Einträge im Verweisdataset zugeordnet werden soll.  
  
 **Ändern der SQL-Anweisung**  
 Hiermit ändern Sie die zum Generieren des Verweisdatasets verwendete SQL-Anweisung.  
  
> [!NOTE]  
>  Durch die auf dieser Seite angegebene optionale SQL-Anweisung wird der auf der Seite **Verbindung** im **Transformations-Editor für Suche**angegebene Tabellenname überschrieben und ersetzt. Weitere Informationen finden Sie unter [Transformations-Editor für Suche &#40;Seite „Verbindung“&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md).  
  
 **Parameter festlegen**  
 Ordnen Sie mithilfe des Dialogfelds **Abfrageparameter festlegen** die Eingabespalten den Parametern zu.  
  
## <a name="external-resources"></a>Externe Ressourcen  
 Blogeintrag [Lookup cache modes](https://go.microsoft.com/fwlink/?LinkId=219518) (Suchcachemodi) auf blogs.msdn.com  
  
## <a name="see-also"></a>Weitere Informationen  
 [Transformations-Editor für Suche &#40;Seite "Allgemein"&#41;](general-page-of-integration-services-designers-options.md)   
 [Transformations-Editor für Suche &#40;Verbindungs Seite&#41;](../../2014/integration-services/lookup-transformation-editor-connection-page.md)   
 [Transformations-Editor für Suche &#40;Seite „Spalten“&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Transformations-Editor für Suche &#40;Seite "Fehlerausgabe"&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [Fehler- und Meldungsreferenz von Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformation für Fuzzysuche](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
