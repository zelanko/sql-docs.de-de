---
title: Entwickeln mit Analysis Services Scripting Language (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0b51658907fe792855cbcdd38c56dcf68b5f5b1c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218842"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Entwickeln mit Analysis Services Scripting Language (ASSL)
  Analysis Services Scripting Language (ASSL) ist eine Erweiterung, die XMLA durch eine Objektdefinitionssprache und Befehlssprache zum Erstellen und Verwalten von Analysis Services-Strukturen direkt auf dem Server ergänzt. Sie können ASSL in benutzerdefinierten Anwendung zur Kommunikation mit Analysis Services über das XMLA-Protokoll verwenden. ASSL umfasst zwei Teile:  
  
-   Ein Windows-Verwaltungsinstrumentation (Data Definition Language, Datendefinitionssprache) oder objektdefinitionssprache, die definiert, und beschreibt eine Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], sowie die Datenbanken und Datenbankobjekte, die die Instanz enthält.  
  
-   Eine Befehlssprache, die aktionsbefehle, wie z. B. sendet `Create`, `Alter`, oder `Process`, mit einer Instanz von Analysis Services. Diese Befehlssprache wird erläutert, der [XML for Analysis &#40;XMLA&#41; Verweis](../../xmla/xml-for-analysis-xmla-reference.md).  
  
 Zur Anzeige der ASSL, die in eine mehrdimensionale Lösung beschreibt [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], können Sie den Befehl Anzeigecode auf Projektebene. Kann auch erstellen oder Bearbeiten von ASSL-Skript in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] mithilfe des XMLA-Abfrage-Editors. Die erstellten Skripts können zum Verwalten von Objekten oder Ausführen von Befehlen auf dem Server verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [ASSL-Objekte und Objekteigenschaften](assl-objects-and-object-characteristics.md)   
 [ASSL XML-Konventionen](assl-xml-conventions.md)   
 [Datenquellen und-Bindungen &#40;SSAS – mehrdimensional&#41;](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  
