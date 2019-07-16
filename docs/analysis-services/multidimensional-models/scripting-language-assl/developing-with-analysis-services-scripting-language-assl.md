---
title: Entwickeln mit Analysis Services Scripting Language (ASSL) | Microsoft-Dokumentation
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c113e07099ed96abdb0eb5f62c8517ee422d3cc7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "68208483"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Entwickeln mit Analysis Services Scripting Language (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Analysis Services Scripting Language (ASSL) ist eine Erweiterung, die XMLA durch eine Objektdefinitionssprache und Befehlssprache zum Erstellen und Verwalten von Analysis Services-Strukturen direkt auf dem Server ergänzt. Sie können ASSL in benutzerdefinierten Anwendung zur Kommunikation mit Analysis Services über das XMLA-Protokoll verwenden. ASSL umfasst zwei Teile:  
  
-   eine Datendefinitionssprache (Data Definition Language, DDL) oder Objektdefinitionssprache, mit der eine Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]definiert und beschrieben wird, sowie die in der Instanz enthaltenen Datenbanken und Datenbankobjekte.  
  
-   Eine Befehlssprache, mit der Aktionsbefehle wie **Create**, **Alter**oder **Process**an eine Instanz von Analysis Services gesendet werden. Diese Befehlssprache wird erläutert, der [XML for Analysis &#40;XMLA&#41; Verweis](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).  
  
 Zur Anzeige der ASSL, durch die eine mehrdimensionale Lösung in [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]beschrieben wird, können Sie den Befehl Code anzeigen auf Projektebene verwenden. Sie können ein ASSL-Skript in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] auch mit dem XMLA-Abfrage-Editor erstellen oder bearbeiten. Die erstellten Skripts können zum Verwalten von Objekten oder Ausführen von Befehlen auf dem Server verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [ASSL-Objekte und Objekteigenschaften](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)   
 [ASSL XML-Konventionen](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-xml-conventions.md)   
 [Datenquellen und Bindungen &#40;SSAS – mehrdimensional&#41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)  
  
  
