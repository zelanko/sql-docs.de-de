---
title: Entwickeln mit Analysis Services Scripting Language (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
caps.latest.revision: 11
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7b68282f6327ac52cdf47bb761c764609292d7c3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37185177"
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
  
  
