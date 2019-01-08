---
title: Übersicht über logische Architektur (Analysis Services – mehrdimensionale Daten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], examples
- cubes [Analysis Services], about cubes
ms.assetid: 1a547bce-dacf-4d32-bc0f-3829f4b026e1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fd2aad1cf57852c2b78db1128a972c0490a52a85
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52416491"
---
# <a name="logical-architecture-overview-analysis-services---multidimensional-data"></a>Übersicht über logische Architektur (Analysis Services – Mehrdimensionale Daten)
  Analysis Services wird in einem Serverbereitstellungsmodus ausgeführt, durch den die von den unterschiedlichen Analysis Services-Modelltypen verwendete Arbeitsspeicherarchitektur und Laufzeitumgebung bestimmt wird. Der Servermodus wird während der Installation bestimmt. **Mehrdimensionaler und Data Mining-Modus** unterstützt herkömmliches OLAP und Datamining. **Im tabellarischen Modus** unterstützt tabellarische Modelle. **Integrierten SharePoint-Modus** bezieht sich auf einer Instanz von Analysis Services, die als PowerPivot für SharePoint – wird verwendet, die für das Laden und Abfragen von Excel- oder PowerPivot-Datenmodellen innerhalb einer Arbeitsmappe installiert wurde.  
  
 In diesem Thema wird die grundlegende Architektur von Analysis Services bei der Ausführung im mehrdimensionalen und Data Mining-Modus erläutert. Weitere Informationen zu anderen Modi finden Sie unter [Tabellenmodellierung &#40;SSAS – tabellarisch&#41; ](../../tabular-models/tabular-models-ssas.md) und [Vergleichen von tabellarischen und mehrdimensionalen Lösungen &#40;SSAS&#41;](../../../analysis-services/comparing-tabular-and-multidimensional-solutions-ssas.md).  
  
## <a name="basic-architecture"></a>Grundlegende Architektur  
 Eine [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]-Instanz kann mehrere Datenbanken enthalten, und eine Datenbank kann gleichzeitig OLAP-Objekte und Data Mining-Objekte enthalten. Anwendungen stellen eine Verbindung mit einer angegebenen Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] und einer angegebenen Datenbank her. Ein Servercomputer kann mehrere Instanzen von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] hosten. Instanzen von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ihre Namen lauten "\<ServerName >\\< InstanceName\>". Die folgende Abbildung zeigt alle genannten Beziehungen zwischen [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Objekte.  
  
 ![AMO ausgeführte objektbeziehungen](../../../analysis-services/dev-guide/media/amo-runningobjects.gif "AMO ausgeführte objektbeziehungen")  
  
 Basisklassen sind der minimale Satz von Objekten, der für die Erstellung eines Cubes erforderlich ist. Dieser minimale Satz von Objekten ist eine Dimension, eine Measuregruppe und eine Partition. Eine Aggregation ist optional.  
  
 Dimensionen werden aus Attributen und Hierarchien gebildet. Hierarchien bestehen aus einem sortierten Satz von Attributen, wobei jedes Attribut des Satzes einer Ebene der Hierarchie entspricht.  
  
 Cubes werden aus Dimensionen und Measuregruppen gebildet. Die Dimensionen in der Dimensionsauflistung eines Cubes gehören zur Dimensionsauflistung der Datenbank. Measuregruppen sind Auflistungen von Measures, die die gleiche Datenquellensicht und die gleiche Dimensionsteilmenge des Cubes besitzen. Eine Measuregruppe besitzt mindestens eine Partition, um die physischen Daten zu verwalten. Eine Measuregruppe kann einen Standardaggregationsentwurf besitzen. Der Standardaggregationsentwurf kann von allen Partitionen in der Measuregruppe verwendet werden. Außerdem kann jede Partition Ihren eigenen Aggregationsentwurf besitzen.  
  
 Serverobjekte  
 Jede Instanz von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] wird in AMO als einzelnes Serverobjekt betrachtet. Jede einzelne Instanz ist über eine andere Verbindung mit einem <xref:Microsoft.AnalysisServices.Server>-Objekt verbunden. Jedes Serverobjekt enthält mindestens eine Datenquelle und Datenquellensicht, mindestens ein Datenbankobjekt sowie Assemblys und Sicherheitsrollen.  
  
 Dimensionsobjekte  
 Jedes Datenbankobjekt enthält mehrere Dimensionsobjekte. Jedes Dimensionsobjekt enthält ein oder mehrere Attribute, die in Hierarchien organisiert werden.  
  
 Cubeobjekte  
 Jedes Datenbankobjekt enthält mindestens ein Cubeobjekt. Ein Cube wird durch seine Measures und Dimensionen definiert. Die Measures und Dimensionen in einem Cube werden aus Tabellen und Sichten der Datenquellensicht abgeleitet, auf der der Cube basiert bzw. die von den Measure- und Dimensionsdefinitionen generiert wird.  
  
## <a name="object-inheritance"></a>Objektvererbung  
 Das ASSL-Objektmodell enthält zahlreiche wiederkehrende Elementgruppen. Z. B. die Elementgruppe "`Dimensions` enthalten `Hierarchies`," die Dimensionshierarchie eines Elements definiert. Sowohl `Cubes` als auch `MeasureGroups` enthalten die Elementgruppe "`Dimensions` enthalten `Hierarchies`".  
  
 Wenn dies nicht ausdrücklich überschrieben wird, erbt ein Element die Details dieser wiederkehrenden Elementgruppe von der höheren Ebene. Beispielsweise sind die `Translations` für eine `CubeDimension` die gleichen wie die `Translations` für sein Vorgängerelement `Cube`.  
  
 Um die von einem Objekt einer höheren Ebene geerbten Eigenschaften explizit zu überschreiben, muss das Objekt nicht explizit die gesamte Struktur und die gesamten Eigenschaften des Objekts der höheren Ebene wiederholen. Die einzigen Eigenschaften, die von einem Objekt explizit angegeben werden müssen, sind die Eigenschaften, die von dem Objekt überschrieben werden sollen. Beispielsweise kann eine `CubeDimension` nur die `Hierarchies` auflisten, die im `Cube` deaktiviert werden sollen, deren Sichtbarkeit geändert werden soll oder für die einige `Level`-Details auf der `Dimension`-Ebene nicht bereitgestellt wurden.  
  
 Einige auf einem Objekt angegebene Eigenschaften stellen Standardwerte für die gleiche Eigenschaft auf einem untergeordneten oder nachfolgenden Objekt bereit. Beispielsweise stellt `Cube.StorageMode` den Standardwert für `Partition.StorageMode` bereit. ASSL wendet folgende Regeln auf geerbte Standardwerte an:  
  
-   Wenn die Eigenschaft für das untergeordnete Objekt in XML NULL ist, nimmt der Wert der Eigenschaft standardmäßig den geerbten Wert an. Wenn Sie den Wert jedoch vom Server abfragen, gibt der Server den NULL-Wert des XML-Elements zurück.  
  
-   Es ist nicht möglich, programmgesteuert festzustellen, ob die Eigenschaft eines untergeordneten Objekts direkt auf dem untergeordneten Objekt festgelegt oder geerbt wurde.  
  
## <a name="example"></a>Beispiel  
 Der Imports-Cube enthält die beiden Measures Packages und Last sowie die drei verwandten Dimensionen Route, Source und Time.  
  
 ![Beispielcube 1](../../../analysis-services/dev-guide/media/cubeintro1.gif "Beispielcube 1")  
  
 Die kleineren alphanumerischen Werte um den Cube herum stellen die Elemente der Dimension dar. Beispiele für Elemente sind ground (Element der Route-Dimension), Africa (Element der Source-Dimension) und 1st quarter (Element der Time-Dimension).  
  
### <a name="measures"></a>Measures  
 Die Werte innerhalb der Cubezellen stellen die beiden Measures Packages und Last dar. Das Packages-Measure gibt die Anzahl importierter Pakete an, und die `Sum`-Funktion wird zum Aggregieren der Measurefakten verwendet. Das Last-Measure gibt das Empfangsdatum an, und die `Max`-Funktion wird zum Aggregieren der Measurefakten verwendet.  
  
### <a name="dimensions"></a>Dimensionen  
 Die Route-Dimension stellt dar, auf welchem Weg die Importwaren ihr Ziel erreichen. Zu den Elementen dieser Dimension gehören ground, nonground, air, sea, road und rail. Die Source-Dimension gibt die Orte an, an denen die Importe produziert werden, z. B. Africa oder Asia. Die Time-Dimension stellt die Quartale und Halbjahre eines einzelnen Jahres dar.  
  
### <a name="aggregates"></a>Aggregate  
 Anwender des Produkts im geschäftlichen Bereich, die einen Cube verwenden, können beliebige Measurewerte für jedes Element in jeder Dimension bestimmen, unabhängig von der Ebene des Elements innerhalb der Dimension, da Werte von [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] auf höheren Ebenen als erforderlich aggregiert werden. Beispielsweise können die Measure-Werte in der vorherigen Abbildung gemäß einer Hierarchie aggregiert werden, mithilfe der Calendar Time-Hierarchie in der Time-Dimension, wie im folgenden Diagramm dargestellt.  
  
 ![Diagramm mit Measures auf der Zeitdimension organisiert](../../../analysis-services/dev-guide/media/cubeintro2.gif "Diagramm mit Measures organisiert Time-Dimension")  
  
 Ergänzend zur Aggregation von Measures mithilfe einer einzigen Dimension können Sie Measures mithilfe von Kombinationen von Elementen unterschiedlicher Dimensionen aggregieren. Auf diese Weise ist es Anwendern des Produkts im geschäftlichen Bereich möglich, in mehreren Dimensionen gleichzeitig Measures auszuwerten. Wenn ein Anwender des Produkts im geschäftlichen Bereich z. B. die Quartalsimporte analysieren möchte, die per Luftfracht aus der östlichen und der westlichen Hemisphäre eingetroffen sind, kann der Anwender eine Abfrage an den Cube eingeben, um das folgende Dataset abzurufen.  
  
||||Pakete|||Letzter|||  
|-|-|-|--------------|-|-|----------|-|-|  
||||All Sources|Eastern Hemisphere|Western Hemisphere|All Sources|Eastern Hemisphere|Western Hemisphere|  
|All Time|||25110|6547|18563|29.12.1999|22.12.1999|29.12.1999|  
||Erste Hälfte||11173|2977|8196|28.06.1999|20.06.1999|28.06.1999|  
|||Erstes Quartal|5108|1452|3656|30.03.1999|19.03.1999|30.03.1999|  
|||Zweites Quartal|6065|1525|4540|28.06.1999|20.06.1999|28.06.1999|  
||2nd half||13937|3570|10367|29.12.1999|22.12.1999|29.12.1999|  
|||3rd quarter|6119|1444|4675|30.09.1999|18.09.1999|30.09.1999|  
|||Viertes Quartal|7818|2126|5692|29.12.1999|22.12.1999|29.12.1999|  
  
 Wenn ein Cube definiert wurde, können Sie neue Aggregationen erstellen, oder Sie können vorhandene Aggregationen ändern, um Optionen festzulegen, die angeben, ob Aggregationen während der Verarbeitung im Voraus oder zum Zeitpunkt der Abfrage berechnet werden. **Verwandtes Thema:**[Aggregationen und Aggregationsentwürfe](../../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
### <a name="mapping-measures-attributes-and-hierarchies"></a>Zuordnen von Measures, Attributen und Hierarchien  
 Die Measures, Attribute und Hierarchien des Cubes in dem Beispiel werden aus den folgenden Spalten in den Fakten- und Dimensionstabellen des Cubes abgeleitet.  
  
|Measure oder Attribut (Ebene)|Member|Quelltabelle|Quellspalte|Beispielspaltenwert|  
|------------------------------------|-------------|------------------|-------------------|-------------------------|  
|Packages-Measure|Nicht verfügbar|ImportsFactTable|Pakete|12|  
|Last-Measure|Nicht verfügbar|ImportsFactTable|Letzter|May-03-99|  
|Route Category-Ebene in Route-Dimension|nonground, ground|RouteDimensionTable|Route_Category|Nonground|  
|Route-Attribut in Route-Dimension|air, sea, road, rail|RouteDimensionTable|Route|Sea|  
|Hemisphere-Attribut in Source-Dimension|Eastern Hemisphere, Western Hemisphere|SourceDimensionTable|Hemisphere|Eastern Hemisphere|  
|Continent-Attribut in Source-Dimension|Afrika, Asien, Australien, Europa, Nordamerika Südamerika|SourceDimensionTable|Continent|Europe|  
|Half-Attribut in Time-Dimension|1st half, 2nd half|TimeDimensionTable|Half|2nd half|  
|Quarter-Attribut in Time-Dimension|1st quarter, 2nd quarter, 3rd quarter, 4th quarter|TimeDimensionTable|Quarter|3rd quarter|  
  
 Daten in einer einzelnen Cubezelle werden normalerweise aus mehreren Zeilen in der Faktentabelle abgeleitet. Die Cubezelle am Schnittpunkt von Air-Element, Africa-Element und 1st Quarter-Element enthält beispielsweise einen Wert, der durch Aggregieren der folgenden Zeilen in abgeleitet ist die **ImportsFactTable** Faktentabelle.  
  
|||||||  
|-|-|-|-|-|-|  
|Import_ReceiptKey|RouteKey|SourceKey|TimeKey|Pakete|Letzter|  
|3516987|1|6|1|15|10.01.1999|  
|3554790|1|6|1|40|19.01.1999|  
|3572673|1|6|1|34|27.01.1999|  
|3600974|1|6|1|45|02.02.1999|  
|3645541|1|6|1|20|09.02.1999|  
|3674906|1|6|1|36|17.02.1999|  
  
 In der obigen Tabelle weist jede Zeile die gleichen Werte für die **RouteKey**, **SourceKey**, und **TimeKey** Spalten, die angibt, dass diese Zeilen zur selben Cubezelle beitragen.  
  
 In dem hier dargestellten Beispiel geht es um einen sehr einfachen Cube, der nur eine einzige Measuregruppe enthält und bei dem alle Dimensionstabellen in einem Sternschema mit der Faktentabelle verknüpft sind. In weiteres häufiges Schema ist das Schneeflockenschema, in dem mindestens eine Dimensionstabelle mit einer anderen Dimensionstabelle und nicht direkt mit der Faktentabelle verknüpft wird. **Verwandtes Thema:**[Dimensionen &#40;Analysis Services – mehrdimensionale Daten&#41;](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).  
  
 Das hier dargestellte Beispiel enthält nur eine einzige Faktentabelle. Wenn ein Cube mehrere Faktentabellen enthält, werden die Measures aus jeder Faktentabelle in Measuregruppen organisiert, und eine Measuregruppe wird mithilfe von definierten Dimensionsbeziehungen mit einer bestimmten Gruppe von Dimensionen verbunden. Diese Beziehungen werden durch Angeben der teilnehmenden Tabellen in der Datenquellensicht und der Granularität der Beziehung definiert. **Verwandtes Thema:**[Dimensionsbeziehungen](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Mehrdimensionale Modelldatenbanken &#40;SSAS&#41;](../multidimensional-model-databases-ssas.md)  
  
  
