---
title: XML for Analysis (XMLA)-Referenz | Microsoft Docs
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e8c3645175d8d1f3251fd621825f5a542669cbb
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2018
ms.locfileid: "34576762"
---
# <a name="xml-for-analysis--xmla-reference"></a>XML for Analysis (XMLA)-Referenz
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]   

Azure Analysis Services und SQL Server Analysis Services verwenden das XML for Analysis (XMLA)-Protokoll für die Kommunikation zwischen Clientanwendungen und einer Analysis Services-Instanz. Die Erstellung von Anforderungen und Decodierung von Antworten in anderen Clientbibliotheken, z. B. ADOMD.NET und AMO, erfolgt auf elementarster Ebene in XMLA und dient als Zwischenstufe für eine Analysis Services-Instanz, die ausschließlich XMLA verwendet.  
  
 Um die Ermittlung und Bearbeitung von Daten in tabellarische und mehrdimensionale Modi zu unterstützen, die XMLA-Spezifikation definiert zwei allgemein verfügbare Methoden, [Discover](../../analysis-services/xmla/xml-elements-methods-discover.md) und [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md), und ein die Auflistung von XML-Elemente und Datentypen. Da XML eine lose verbundene Client- und Server-Architektur ermöglicht, wickeln beide Methoden eingehende und ausgehende Informationen im XML-Format ab. 

Analysis Services ist mit der XMLA 1.1-Spezifikation -Spezifikation, erweitert diese Datendefinitions- und Bearbeitungsfunktionen zusätzliche Verarbeitungskapazität, implementiert als Anmerkungen auf Einbeziehung jedoch die **Discover** und **Execute** Methoden. Die erweiterte XML-Syntax sind Tabular Model Scripting Language (TMSL) und Analysis Services Scripting Language (ASSL). 

TMSL ist der Befehl und Objekt Modell-Definition-Syntax für Tabellenmodell-Datenbanken mit Kompatibilitätsgrad 1200 oder höher. TMSL kommuniziert mit Analysis Services über das XMLA-Protokoll, in dem die `XMLA.Execute` Methode akzeptiert beide JSON-basierte Anweisung Skripts in TMSL sowie die herkömmlichen XML-basierte Skripts in Analysis Services Scripting Language (ASSL XMLA). Weitere Informationen finden Sie unter [Tabular Model Scripting Language (TMSL) Verweis](../tabular-model-scripting-language-tmsl-reference.md).

ASSL ist der Befehl und Objekt Model-Definition-Syntax für mehrdimensionale modelldatenbanken und tabellarischen Modus Datenbanken mit Kompatibilitätsgrad 1103 oder niedriger. Diese Definition baut auf der XMLA-Spezifikation, ohne diese zu verletzen. Die XMLA-Interoperabilität ist unabhängig davon gewährleistet, ob lediglich XMLA verwendet oder ob XMLA und ASSL kombiniert werden. Weitere Informationen finden Sie unter [Analysis Services Scripting Language (ASSL XMLA)](../scripting/analysis-services-scripting-language-assl-for-xmla.md).
  
 Als Entwickler können Sie XMLA als Schnittstelle verwenden, wenn Anforderungen der Lösung Standardprotokolle, wie XML, SOAP und HTTP angeben. Entwickler und Administratoren können auch XMLA auf Ad-hoc-Basis Informationen vom Server abzurufen oder Befehle ausführen. 
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[XML-Datentypen (XMLA)](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)|Beschreibt Datentypen in der XMLA-Spezifikation.|  
|[XML-Elemente - Befehle (XMLA)](../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)|Elemente, die während der Aufruf einer Methode in der Command-Element verwendet werden können.|  
|[XML-Elemente - Befehle (XMLA)](../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)|Elemente, die während der Aufruf einer Methode in der Command-Element verwendet werden können.|  
|[XML-Elemente - Header (XMLA)](../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)| Header-Elemente, die von Microsoft Analysis Services implementiert.|  
|[XML-Elemente - Eigenschaften (XMLA)](../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)| Elemente, die Darstellung von Eigenschaftsinformationen und Werten für XMLA-Header, Methoden, Objekte, Befehle und Datentypen.|  
|[XML-Elemente - Methoden - Ermittlung (XMLA)](../../analysis-services/xmla/xml-elements-methods-discover.md)| Ruft die Informationen, z. B. die Liste der verfügbaren Datenbanken oder Details zu einem bestimmten Objekt von einer Instanz von Analysis Services ab.|  
|[XML-Elemente - Methoden - ausführen (XMLA)](../../analysis-services/xmla/xml-elements-methods-execute.md)| Sendet XML für Analysis (XMLA) Befehle mit einer Instanz von Analysis Services.|  
|[XML-Elemente - Objekte - DiscoverResponse (XMLA)](../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)| Enthält die Informationen, die von einer Instanz von Analysis Services als Antwort auf den Aufruf einer Discover-Methode zurückgegeben.|  
|[XML-Elemente - Objekte - ExecuteResponse (XMLA)](../../analysis-services/xmla/xml-elements-objects-executeresponse.md)| Enthält die Informationen, die von einer Instanz von Analysis Services als Antwort auf einen Aufruf der Execute-Methode zurückgegeben.|  
|[XML-Elemente - Objekten (XMLA)](../../analysis-services/xmla/xml-elements-objects.md)| Objekte, die von Analysis Services implementiert werden.|  
|[XML for Analysis Compliance (XMLA) (XML for Analysis-Kompatibilität (XMLA))](../../analysis-services/xmla/xml-for-analysis-compliance-xmla.md)|Beschreibt den Grad der Kompatibilität mit der XMLA 1.1-Spezifikation.|  
  
## <a name="see-also"></a>Siehe auch
 [XML for Analysis – Schemarowsets](../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
 [Entwickeln mit ADOMD.NET](../../analysis-services/multidimensional-models/adomd-net/developing-with-adomd-net.md)  
 [Entwickeln mit Analysis Management Objects &#40;AMO&#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)  
