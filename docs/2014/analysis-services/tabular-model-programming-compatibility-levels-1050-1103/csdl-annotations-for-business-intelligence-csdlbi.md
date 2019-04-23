---
title: CSDL-Anmerkungen für Business Intelligence (CSDLBI) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: bf6f372a-bc67-45ea-a771-b2dc5b0527e5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 760e90c34c84bd4b44af90cbbb78aec7e025689a
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158168"
---
# <a name="csdl-annotations-for-business-intelligence-csdlbi"></a>CSDL-Anmerkungen für Business Intelligence (CSDLBI)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützt die Darstellung der Definition eines tabellarischen Modells im XML-Format Conceptual Schema Definition Language mit Business Intelligence-Anmerkungen (CSDLBI).  
  
 Dieses Thema bietet eine Übersicht über CSDLBI und seine Verwendung in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Datenmodellen.  
  
## <a name="understanding-the-role-of-csdl"></a>Grundlegendes zur Rolle von CSDL  
 Die Conceptual Schema Data Language (CSDL) ist eine XML-basierte Sprache, die Entitäten, Beziehungen und Funktionen beschreibt. CSDL ist als Teil des Entity Data Framework definiert. Die BI-Anmerkungen sind eine Erweiterung, die entwickelt wurde, um die Datenmodellierung mithilfe von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]zu unterstützen.  
  
 Obwohl CSDL mit Entity Data Framework kompatibel ist, müssen Sie das Entitätsbeziehungsmodell nicht verstehen, und Sie benötigen keine besonderen Tools zum Erstellen eines Tabellenmodells oder eines Berichts auf Grundlage eines Modells. Modelle werden mithilfe von Clienttools wie [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] oder einer API wie AMO erstellt, und anschließend wird das Modell auf einem Server bereitgestellt. Clients stellt mithilfe einer Modelldefinitionsdatei eine Verbindung zum Modell her, die überlichweise in einer SharePoint-Bibliothek veröffentlich wird, wo sie von Berichts-Designern und Berichtskonsumenten verwendet werden kann. Weitere Informationen finden Sie in den folgenden Links:  
  
-   [Tabellenmodelllösungen &#40;SSAS – tabellarisch&#41;](../tabular-model-solutions-ssas-tabular.md)  
  
-   [Bereitstellung von Tabellenmodelllösungen &#40;SSAS – tabellarisch&#41;](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md)  
  
-   [PowerPivot BI-Semantikmodellverbindung &#40;bism-Datei&#41;](../power-pivot-sharepoint/power-pivot-bi-semantic-model-connection-bism.md)  
  
 Das CSDLBI-Schema wird vom Analysis Services-Server als Reaktion auf eine Anforderung für eine Modelldefinition von einem Client wie [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] generiert. Die Clientanwendung sendet eine XML-Abfrage an den Analysis Services-Server, der die Modelldaten hostet. Im Gegenzug sendet der Server mithilfe der CSDLBI-Anmerkungen eine XML-Meldung, die eine Definition der Entitäten im Modell enthält. Der Berichtsclient verwendet dann die Informationen zur Darstellung der im Modell verfügbaren Felder, Aggregationen und Measures. Die CSDLBI-Anmerkungen enthalten auch Informationen zum Gruppieren, Sortieren und Formatieren der Daten.  
  
 Allgemeine Informationen über die CSDLBI finden Sie unter [CSDLBI-Konzepte](https://docs.microsoft.com/bi-reference/csdl/csdlbi-concepts).  
  
### <a name="working-with-csdl"></a>Arbeiten mit CSDL  
 Der Satz von CSDLBI-Anmerkungen, der ein bestimmtes tabellarische Modell darstellt, ist ein XML-Dokument, das eine Auflistung einfacher und komplexer Entitäten enthält. Die Entitäten definieren Tabellen (oder Dimensionen), Spalten (Attribute), Zuordnungen (Beziehungen) und Formeln in berechneten Spalten, Measures oder KPIs.  
  
 Sie können diese Objekte nicht direkt ändern, sondern müssen auf für die Arbeit mit Tabellenmodellen bereitgestellte Clienttools und Anwendungsprogrammierschnittstellen (APIs) zurückgreifen.  
  
 Sie können die CSDL für ein Modell abrufen, indem Sie eine DISCOVER-Anforderung an den Server senden, der das Modell hostet. Die Anforderung muss qualifiziert werden, indem der Server und das Modell und optional eine Sicht oder Perspektive angegeben werden. Die zurückgegebene Meldung ist eine XML-Zeichenfolge. Bestimmte Elemente sind sprachabhängig und geben je nach Sprache der aktuellen Verbindung unter Umständen andere Werte zurück. Weitere Informationen finden Sie unter [DISCOVER_CSDL_METADATA-Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-csdl-metadata-rowset).  
  
### <a name="csdlbi-versions"></a>CSDLBI-Versionen  
 Die ursprüngliche CSDL-Spezifikation (aus dem Entity Data Framework) stellt die meisten Entitäten und Eigenschaften bereit, die zur Unterstützung der Modellierung erforderlich sind. Die BI-Anmerkungen unterstützen besondere Anforderungen von tabellarischen Modellen, Berichtseigenschaften, die für Clients wie [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]erforderlich sind, sowie zusätzliche Metadaten, die für mehrdimensionale Modelle erforderlich sind. In diesem Abschnitt werden die Updates der einzelnen Versionen beschrieben.  
  
 **CSDLBI 1.0**  
  
 Der Anfangssatz von Ergänzungen zum CSDL-Schema für die Unterstützung tabellarischer [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]-Modelle enthielt Anmerkungen für die Datenmodellierung sowie für benutzerdefinierte Berechnungen und verbesserte Präsentationen:  
  
-   Neue Elemente und Eigenschaften zur Unterstützung tabellarischer Modelle. Beispielsweise wurde eine Eigenschaft hinzugefügt, um den Typ der Datenbankabfrage zum Füllen des Modells anzugeben.  
  
-   Neue Eigenschaften und Erweiterungen für vorhandene Entitäten.  So wurde das Zuordnungselement erweitert, um Beziehungen zu unterstützen.  
  
-   Visualisierungs- und Navigationseigenschaften. Beispielsweise wurden Eigenschaften hinzugefügt, um u. a. benutzerdefinierte Sortierfelder und Standardbilder zu unterstützen.  
  
 **CSDLBI 1.1**  
  
 Diese Version des CSDLBI-Schemas enthält Erweiterungen zur Unterstützung mehrdimensionaler Datenbanken (wie OLAP-Cubes). Die neuen Elemente und Eigenschaften sind nachstehend aufgeführt:  
  
-   Unterstützung für Dimensionen als Entitäten.  
  
-   Unterstützung für Hierarchien.  
  
-   Macht ROLAP-Partitionen verfügbar.  
  
-   Unterstützung für Übersetzungen.  
  
-   Unterstützung für Perspektiven.  
  
 Ausführliche Informationen zu einzelnen Elemente in CSDLBI-Anmerkungen finden Sie unter [technische Referenz für BI-Anmerkungen zu CSDL](https://docs.microsoft.com/bi-reference/csdl/technical-reference-for-bi-annotations-to-csdl). Informationen zu CSDL-hauptspezifikation finden Sie unter den [CSDL v3-Spezifikation](https://docs.microsoft.com/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).  
  
  
## <a name="see-also"></a>Siehe auch  
 [Grundlegendes zum tabellarischen Objektmodell](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)   
 [CSDLBI-Konzepte](https://docs.microsoft.com/bi-reference/csdl/csdlbi-concepts)   
 [Grundlegendes zum tabellarischen Objektmodell](representation/understanding-tabular-object-model-at-levels-1050-through-1103.md)  
  
  
