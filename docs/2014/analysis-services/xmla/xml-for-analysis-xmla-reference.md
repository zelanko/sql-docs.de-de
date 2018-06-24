---
title: XML for Analysis (XMLA)-Referenz | Microsoft Docs
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
- XML for Analysis, reference
- XMLA, reference
ms.assetid: 88045e05-ce47-4e28-999b-7f9c74af9faf
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 32093211db376a156c456d4f769f78bcc1135ceb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36046969"
---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA)-Referenz
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] verwendet die XML for Analysis (XMLA)-Protokoll zum Verarbeiten aller Kommunikation zwischen Clientanwendungen und einer Analysis Services-Instanz an. Die Erstellung von Anforderungen und Decodierung von Antworten in anderen Clientbibliotheken, z. B. ADOMD.NET und AMO, erfolgt auf elementarster Ebene in XMLA und dient als Zwischenstufe für eine Analysis Services-Instanz, die ausschließlich XMLA verwendet.  
  
 Um die Ermittlung und Bearbeitung von Daten in multidimensionalen und tabellarischen Format zu unterstützen, die XMLA-Spezifikation definiert zwei allgemein verfügbare Methoden [Discover](xml-elements-methods-discover.md) und [Execute](xml-elements-methods-execute.md), und ein die Auflistung von XML-Elemente und Datentypen. Da XML eine lose verbundene Client- und Server-Architektur ermöglicht, wickeln beide Methoden eingehende und ausgehende Informationen im XML-Format ab. Analysis Services ist mit der XMLA 1.1-Spezifikation kompatibel, erweitert diese jedoch um Datendefinitions- und Bearbeitungsfunktionen, die als Anmerkungen in der `Discover`-Methode und `Execute`-Methode implementiert wurden. Die erweiterte XML-Syntax wird als Analysis Services Scripting Language (ASSL) bezeichnet. ASSL baut auf der XMLA-Spezifikation auf, ohne diese zu verletzen. Die XMLA-Interoperabilität ist unabhängig davon gewährleistet, ob lediglich XMLA verwendet oder ob XMLA und ASSL kombiniert werden.  
  
 Als Programmierer können Sie XMLA als befehlsorientierte Benutzerschnittstelle verwenden, wenn für eine Lösung Standardprotokolle, wie XML, SOAP und HTTP, erforderlich sein sollten. Programmierer und Administratoren können XMLA auch auf einer Ad-hoc-Basis verwenden, um Informationen vom Server abzurufen oder Befehle auszuführen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[XML-Elemente &#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)|Beschreibt Elemente in der XMLA-Spezifikation.|  
|[XML-Datentypen &#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)|Beschreibt Datentypen in der XMLA-Spezifikation.|  
|[XML for Analysis-Kompatibilität &#40;XMLA&#41;](xml-for-analysis-compliance-xmla.md)|Beschreibt den Grad der Kompatibilität mit der XMLA 1.1-Spezifikation.|  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Entwickeln mit Analysis Services Scripting Language &#40;ASSL&#41;](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
 [XML for Analysis – Schemarowsets](../schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
 [Entwickeln mit ADOMD.NET](../multidimensional-models/adomd-net/developing-with-adomd-net.md)  
  
 [Entwickeln mit Analysis Management Objects &#40;AMO&#41;](../multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zur Microsoft OLAP-Architektur](../multidimensional-models/olap-physical/understanding-microsoft-olap-architecture.md)  
  
  