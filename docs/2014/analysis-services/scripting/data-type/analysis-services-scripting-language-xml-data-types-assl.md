---
title: Analysis Services Scripting Language-XML-Datentypen (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Analysis Services Scripting Language XML Data Types
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- ASSL, data types
- Analysis Services Scripting Language, data types
- data types [Analysis Services Scripting Language]
ms.assetid: 8e527916-932e-48ec-9010-f22cd4b721e2
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bc773c4eda7b9f26b8ddafab5f6c80b068d32ec9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37276636"
---
# <a name="analysis-services-scripting-language-xml-data-types-assl"></a>Analysis Services Scripting Language-XML-Datentypen (ASSL)
  In diesem Referenzabschnitt finden Sie Syntax- und Nutzungsinformationen für jedes Element, das im ASSL-Schema (Analysis Services Scripting Language) als Typ agiert.  
  
 Obwohl das ASSL-Schema nur XML-Elemente enthält, entsprechen die Elemente, die in diesem Abschnitt beschrieben werden, aus der Sicht eines Entwicklers Typen (z. B. `Binding` und `Permission`), die zum Definieren der untergeordneten Elemente und Eigenschaften anderer Objekte verwendet werden.  
  
 Typelemente wie Objektelemente sind niemals Blattebenenelemente im ASSL-Schema, sondern besitzen untergeordnete Elemente und Elemente, die Objekteigenschaften entsprechen.  
  
 Jedoch ein Type-Element nicht als ein Element in einem Skript wird angezeigt, die definiert oder beschreibt [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] Objekte. Stattdessen sind sie der Typ anderer Objektelemente; dies wird normalerweise über das `type`-Attribut des XML Schema Instance-Schemas mithilfe von `xsi:type` oder `xs:type` bestimmt. Beispiel: `<Assembly xsi:type="ClrAssembly">...</Assembly>`.  
  
 In einigen Fällen wird ein Typ von einem anderen Typ abgeleitet. Zum Beispiel leitet sich der `CubeBinding`-Typ vom übergeordneten `Binding`-Typ ab.  
  
|Element|Description|  
|-------------|-----------------|  
|[Action-Datentyp &#40;ASSL&#41;](action-data-type-assl.md)|Definiert einen abstrakten Grunddatentyp, der eine Aktion in einer [Cube](../objects/cube-element-assl.md) Element oder ein [Perspektive](../objects/perspective-element-assl.md) Element.|  
|[AggregationAttribute-Datentyp &#40;ASSL&#41;](aggregationattribute-data-type-assl.md)|Definiert einen Grunddatentyp, der die Zuordnung zwischen einem [Aggregation](../objects/aggregation-element-assl.md) Element und ein Attribut.|  
|[AggregationDesignAttribute-Datentyp &#40;ASSL&#41;](aggregationdesignattribute-data-type-assl.md)|Definiert einen Grunddatentyp, der die Zuordnung zwischen einem Attribut darstellt und ein [AggregationDesignDimension](dimension-data-type-assl.md) Element.|  
|[AggregationDesignDimension-Datentyp &#40;ASSL&#41;](dimension-data-type-assl.md)|Definiert einen Grunddatentyp, der die Beziehung zwischen einer Cubedimension darstellt und ein [AggregationDesign](../objects/aggregationdesign-element-assl.md) Element.|  
|[AggregationDimension-Datentyp &#40;ASSL&#41;](aggregationdimension-data-type-assl.md)|Definiert einen Grunddatentyp, der die Beziehung zwischen einer Dimension darstellt und ein [Aggregation](../objects/aggregation-element-assl.md) Element.|  
|[AggregationInstanceAttribute-Datentyp &#40;ASSL&#41;](aggregationinstanceattribute-data-type-assl.md)|Definiert einen Grunddatentyp, der Informationen über ein Attribut, das von einer Aggregationsinstanz verwendet wird, darstellt.|  
|[AggregationInstanceCubeDimension-Datentyp &#40;ASSL&#41;](cubedimension-data-type-assl.md)|Definiert einen Grunddatentyp, der Informationen über eine Cubedimension, die von einer Aggregationsinstanz verwendet wird, darstellt.|  
|[AggregationInstanceMeasure-Datentyp &#40;ASSL&#41;](aggregationinstancemeasure-data-type-assl.md)|Definiert einen Grunddatentyp, der Informationen über ein Measure, das von einer Aggregationsinstanz verwendet wird, darstellt.|  
|[Assembly-Datentyp &#40;ASSL&#41;](assembly-data-type-assl.md)|Definiert einen abstrakten Grunddatentyp, der darstellt eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Assembly oder eine COM-dynamic Link Library (DLL) zugeordneten eine [Server](../objects/server-element-assl.md) oder [Datenbank](../objects/database-element-assl.md) Element.|  
|[AttributeBinding-Datentyp &#40;ASSL&#41;](binding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Bindung für ein [Attribut](../objects/attribute-element-assl.md) Element.|  
|[AttributeTranslation-Datentyp &#40;ASSL&#41;](translation-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine zugeordnete Übersetzung darstellt, der eine [Attribut](../objects/attribute-element-assl.md) Element|  
|[Binding-Datentyp &#40;ASSL&#41;](binding-data-type-assl.md)|Definiert einen abstrakten Grunddatentyp, der eine abhängige Beziehung zwischen zwei Objekten darstellt, in der die Daten oder Metadaten des einen Objekts von den Daten oder Metadaten eines gebundenen Objekts abhängen.|  
|[ClrAssembly-Datentyp &#40;ASSL&#41;](clrassembly-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der darstellt, der eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zugeordnete Assembly einen [Datenbank](../objects/database-element-assl.md) oder [Server](../objects/server-element-assl.md) Element|  
|[ClrAssemblyFile-Datentyp &#40;ASSL&#41;](clrassemblyfile-data-type-assl.md)|Definiert einen Grunddatentyp, der eine der Dateien darstellt, aus denen ein [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Assembly ([ClrAssembly](clrassembly-data-type-assl.md) Element).|  
|[ColumnBinding-Datentyp &#40;ASSL&#41;](columnbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die Bindung einer Spalte in einer Datenquellensicht zu darstellt, der eine [DataItem](dataitem-data-type-assl.md) Element.|  
|[ComAssembly-Datentyp &#40;ASSL&#41;](comassembly-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine COM-Bibliothek im Zusammenhang mit darstellt, der eine [Server](../objects/server-element-assl.md) oder [Datenbank](../objects/database-element-assl.md) Element.|  
|[CubeAttribute-Datentyp &#40;ASSL&#41;](cubeattribute-data-type-assl.md)|Definiert einen Grunddatentyp, der ein Attribut mit verknüpften darstellt eine [Cube](../objects/cube-element-assl.md) Element.|  
|[CubeAttributeBinding-Datentyp &#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|Definiert einen abgeleiteten Datentyp, der die Bindung eines Attributs in einer Cubedimension zu entweder einer Aktions- oder einer Miningstrukturspalte darstellt.|  
|[CubeBinding-Datentyp &#40;Out-of-Line-&#41; &#40;ASSL&#41;](cubebinding-data-type-out-of-line-assl.md)|Definiert einen Grunddatentyp, der die Beziehung zwischen einer [Cube](../objects/cube-element-assl.md) Element und ein [DataSource](../objects/datasource-element-assl.md) Element.|  
|[CubeDimension-Datentyp &#40;ASSL&#41;](cubedimension-data-type-assl.md)|Definiert einen Grunddatentyp, der die Beziehung zwischen einer Dimension und einem Cube darstellt.|  
|[CubeDimensionBinding-Datentyp &#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die Bindung darstellt, der eine [Dimension](../objects/dimension-element-assl.md), [Measure](../objects/measure-element-assl.md), oder [MiningModel](../objects/miningmodel-element-assl.md) Element auf eine Cubedimension.|  
|[CubeDimensionPermission-Datentyp &#40;ASSL&#41;](permission-data-type-assl.md)|Definiert einen Grunddatentyp, der die Berechtigungen einer einzelnen Rolle in einer bestimmten Dimension in einem Cube darstellt.|  
|[CubeHierarchy-Datentyp &#40;ASSL&#41;](hierarchy-data-type-assl.md)|Definiert einen Grunddatentyp ab, die Informationen über eine [Hierarchie](../objects/hierarchy-element-assl.md) Element in einer [Cube](../objects/cube-element-assl.md) Element.|  
|[DataBlock-Datentyp &#40;ASSL&#41;](datablock-data-type-assl.md)|Definiert einen Grunddatentyp, der eine von Datenblöcken verwendet Auflistung, um die binären Inhalte speichern eine [ClrAssemblyFile](clrassemblyfile-data-type-assl.md) Element.|  
|[DataItem-Datentyp &#40;ASSL&#41;](dataitem-data-type-assl.md)|Definiert einen Grunddatentyp, der die datenbezogenen Merkmale eines Datenelements darstellt, z. B. eine Spalte oder ein Attribut.|  
|[DataMiningMeasureGroupDimension-Datentyp &#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die Beziehung zwischen einer Measuregruppe und einer Data Mining-Dimension darstellt.|  
|[DataSource-Datentyp &#40;ASSL&#41;](datasource-data-type-assl.md)|Definiert einen abstrakten Grunddatentyp, der eine Datenquelle in einem [Datenbank](../objects/database-element-assl.md) Element.|  
|[DataSourceViewBinding-Datentyp &#40;ASSL&#41;](datasourceviewbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Bindung zwischen einer Datenquellensicht und dem übergeordneten Element darstellt.|  
|[DegenerateMeasureGroupDimension-Datentyp &#40;ASSL&#41;](degeneratemeasuregroupdimension-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die Beziehung zwischen einer degenerierten Dimension (d. h. einer Faktdimension) und einer Measuregruppe darstellt.|  
|[Dimension-Datentyp &#40;ASSL&#41;](dimension-data-type-assl.md)|Definiert einen Grunddatentyp, der eine Datenbankdimension darstellt.|  
|[DimensionAttribute-Datentyp &#40;ASSL&#41;](dimensionattribute-data-type-assl.md)|Definiert einen primitiven Datentyp, der ein Attribut in einer Dimension darstellt.|  
|[DimensionBinding-Datentyp &#40;ASSL&#41;](dimensionbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die Bindung zwischen einer Datenquelle darstellt und einen [Dimension](../objects/dimension-element-assl.md) Element.|  
|[DimensionPermission-Datentyp &#40;ASSL&#41;](permission-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die einer Datenbankdimension zugewiesenen Berechtigungen darstellt.|  
|[DrillThroughAction-Datentyp &#40;ASSL&#41;](drillthroughaction-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Drillthrough-Aktion darstellt.|  
|[DSVTableBinding-Datentyp &#40;ASSL&#41;](tablebinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die Bindung zwischen einer Tabelle darstellt und einen [DataSourceView](../objects/datasourceview-element-assl.md) Element.|  
|[EventColumn-Datentyp &#40;ASSL&#41;](eventcolumn-data-type-assl.md)|Definiert einen Grunddatentyp, der eine Spalte mit Informationen für die aufzuzeichnende darstellt ein [Ereignis](../objects/event-element-assl.md) -Element als Teil einer [Ablaufverfolgung](../objects/trace-element-assl.md) Element.|  
|[Hierarchy-Datentyp &#40;ASSL&#41;](hierarchy-data-type-assl.md)|Definiert einen Grunddatentyp, der eine Hierarchie in einer Dimension darstellt.|  
|[ImpersonationInfo-Datentyp &#40;ASSL&#41;](impersonationinfo-data-type-assl.md)|Definiert einen Grunddatentyp, der die Informationen darstellt, die zur Identitätsbestimmung eines Benutzers verwendet werden.|  
|[IncrementalProcessingNotification-Datentyp &#40;ASSL&#41;](incrementalprocessingnotification-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, womit Informationen zu den [ProactiveCaching](../objects/proactivecaching-element-assl.md) Element über eine Abfrage zum Ermitteln des Fortschritts der inkrementellen Verarbeitung ausgeführt.|  
|[InheritedBinding-Datentyp &#40;ASSL&#41;](inheritedbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der angibt, die eine [MeasureGroupAttribute](measuregroupattribute-data-type-assl.md) -Element seine Bindungen vom Attribut erbt.|  
|[ManyToManyMeasureGroupDimension-Datentyp &#40;ASSL&#41;](manytomanymeasuregroupdimension-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die Beziehung zwischen einer m:n-Dimension und einer Measuregruppe darstellt.|  
|[MeasureBinding-Datentyp &#40;ASSL&#41;](measurebinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die Bindung einer Measure zum übergeordneten Element darstellt.|  
|[MeasureGroupAttribute-Datentyp &#40;ASSL&#41;](measuregroupattribute-data-type-assl.md)|Definiert einen Grunddatentyp, der die Beziehung zwischen einem Attribut und einer Measuregruppe darstellt.|  
|[MeasureGroupBinding-Datentyp &#40;ASSL&#41;](measuregroupbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Bindung an eine [MeasureGroup](../objects/group-element-assl.md) Element.|  
|[MeasureGroupBinding-Datentyp &#40;Out-of-Line-&#41; &#40;ASSL&#41;](measuregroupbinding-data-type-out-of-line-assl.md)|Definiert einen Grunddatentyp, der eine Bindung mit einer Measuregruppe darstellt.|  
|[MeasureGroupDimension-Datentyp &#40;ASSL&#41;](measuregroupdimension-data-type-assl.md)|Definiert einen abstrakten Grunddatentyp, der die Beziehung zwischen einer Dimension und einer Measuregruppe darstellt.|  
|[MeasureGroupDimensionBinding-Datentyp &#40;ASSL&#41;](measuregroupdimensionbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Bindung zwischen einer Dimension und einer Measuregruppe darstellt.|  
|[MeasureGroupHierarchy-Datentyp &#40;ASSL&#41;](measuregrouphierarchy-data-type-assl.md)|Definiert einen Grunddatentyp, der Informationen über eine Hierarchie in einer Measuregruppe darstellt.|  
|[MiningModelColumn-Datentyp &#40;ASSL&#41;](miningmodelcolumn-data-type-assl.md)|Definiert einen Grunddatentyp, der die Informationen über eine Spalte in einer [MiningModel](../objects/miningmodel-element-assl.md) Element.|  
|[MiningModelingFlag-Datentyp &#40;ASSL&#41;](miningmodelingflag-data-type-assl.md)|Definiert einen Grunddatentyp, der die verfügbaren Modellierungsflags für eine [ModelingFlag](../objects/modelingflag-element-assl.md) Element.|  
|[MiningStructureColumn-Datentyp &#40;ASSL&#41;](miningstructurecolumn-data-type-assl.md)|Definiert einen abstrakten Grunddatentyp ab, die Informationen über eine Spalte in einer [MiningStructure](../objects/miningstructure-element-assl.md) Element.|  
|[OlapDataSource-Datentyp &#40;ASSL&#41;](olapdatasource-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der ein mehrdimensionales darstellt [DataSource](../objects/datasource-element-assl.md) Element.|  
|[PartitionBinding-Datentyp &#40;ASSL&#41;](partitionbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Bindung an eine [Partition](../objects/partition-element-assl.md) Element.|  
|[Permission-Datentyp &#40;ASSL&#41;](permission-data-type-assl.md)|Definiert einen abstrakten, Grunddatentyp, der Informationen über eine individuelle Berechtigung darstellt.|  
|[PerspectiveAction-Datentyp &#40;ASSL&#41;](perspectiveaction-data-type-assl.md)|Definiert einen Grunddatentyp, der die Informationen über eine Aktion in einem [Perspektive](../objects/perspective-element-assl.md) Element.|  
|[PerspectiveAttribute-Datentyp &#40;ASSL&#41;](perspectiveattribute-data-type-assl.md)|Definiert einen Grunddatentyp, der die Informationen über ein Attribut in einem [PerspectiveDimension](perspectivedimension-data-type-assl.md) Element.|  
|[PerspectiveCalculation-Datentyp &#40;ASSL&#41;](perspectivecalculation-data-type-assl.md)|Definiert einen Grunddatentyp, der die Beziehung zwischen einer Berechnung darstellt und einen [Perspektive](../objects/perspective-element-assl.md) Element.|  
|[PerspectiveDimension-Datentyp &#40;ASSL&#41;](perspectivedimension-data-type-assl.md)|Definiert einen Grunddatentyp, der Informationen über eine Dimension in einer Perspektive darstellt.|  
|[PerspectiveHierarchy-Datentyp &#40;ASSL&#41;](perspectivehierarchy-data-type-assl.md)|Definiert einen Grunddatentyp, der die Informationen über eine Hierarchie in eine [PerspectiveDimension](perspectivedimension-data-type-assl.md) Element.|  
|[PerspectiveKpi-Datentyp &#40;ASSL&#41;](perspectivekpi-data-type-assl.md)|Definiert einen Grunddatentyp, der Informationen zu einem Key Performance Indicator (KPI) darstellt, in einem [Perspektive](../objects/perspective-element-assl.md) Element.|  
|[PerspectiveMeasure-Datentyp &#40;ASSL&#41;](perspectivemeasure-data-type-assl.md)|Definiert einen Grunddatentyp, der die Informationen über eine Measure in einem [PerspectiveMeasureGroup](perspectivemeasuregroup-data-type-assl.md) Element.|  
|[PerspectiveMeasureGroup-Datentyp &#40;ASSL&#41;](perspectivemeasuregroup-data-type-assl.md)|Definiert einen Grunddatentyp, der die Informationen über eine Measuregruppe in einem [Perspektive](../objects/perspective-element-assl.md) Element.|  
|[ProactiveCachingBinding-Datentyp &#40;ASSL&#41;](proactivecachingbinding-data-type-assl.md)|Definiert einen abstrakten abgeleiteten Datentyp, die Informationen darstellt, das die [ProactiveCaching](../objects/proactivecaching-element-assl.md) Element über datenquellenänderungen, die Neuerstellung des Caches erfordern, sowie über den Status des Neuerstellungsprozesses.|  
|[ProactiveCachingIncrementalProcessingBinding-Datentyp &#40;ASSL&#41;](proactivecachingincrementalprocessingbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Bindung an darstellt, der die [ProactiveCaching](../objects/proactivecaching-element-assl.md) Element über den Status des Neuerstellungsprozesses des Caches.|  
|[ProactiveCachingInheritedBinding-Datentyp &#40;ASSL&#41;](proactivecachinginheritedbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, die Informationen darstellt, das die [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Element über datenquellenänderungen in Tabellen und Sichten, die über vorhandene datenbindungen, die Neuerstellung des Caches erfordern, identifiziert.|  
|[ProactiveCachingObjectNotificationBinding-Datentyp &#40;ASSL&#41;](proactivecachingobjectnotificationbinding-data-type-assl.md)|Definiert einen abstrakten abgeleiteten Datentyp, die Informationen darstellt, das die [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Element über datenquellenänderungen in angegebenen Tabellen und Sichten oder in Tabellen und Sichten, die über vorhandene datenbindungen, identifiziert die Neuerstellen des Caches erfordern.|  
|[ProactiveCachingQueryBinding-Datentyp &#40;ASSL&#41;](querybinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, die Informationen darstellt, das die [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Element über datenquellenänderungen in Tabellen und Sichten, die über die Ausführung von angegebenen Abfragen, die Neuerstellen des Caches erfordern, identifiziert.|  
|[ProactiveCachingTablesBinding-Datentyp &#40;ASSL&#41;](proactivecachingtablesbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, die Informationen darstellt, das die [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Element über datenquellenänderungen in angegebenen Tabellen und Sichten, die Neuerstellung des Caches erfordern.|  
|[PushedDataSource-Datentyp &#40;ASSL&#41;](pusheddatasource-data-type-assl.md)|Definiert einen Grunddatentyp, der eine Datenquelle darstellt (z. B. eine [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] Paket) zum "drücken" von Daten in einem [Cube](../objects/cube-element-assl.md) Element.|  
|[QueryBinding-Datentyp &#40;ASSL&#41;](querybinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der die Zuordnung der darstellt, der eine [DataSource](../objects/datasource-element-assl.md) -Element mit einer [QueryDefinition](../properties/querydefinition-element-assl.md) Element.|  
|[ReferenceMeasureGroupDimension-Datentyp &#40;ASSL&#41;](referencemeasuregroupdimension-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Dimension darstellt, die indirekt über eine Zwischendimension mit der Faktentabelle verbunden ist. (Eine Sales-Measuregruppe kann beispielsweise auf eine Geography-Dimension verweisen, die über die Customer-Dimension verbunden ist.)|  
|[RegularMeasureGroupDimension-Datentyp &#40;ASSL&#41;](regularmeasuregroupdimension-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine reguläre Beziehung zwischen einer Dimension und einer Measuregruppe darstellt.|  
|[RelationalDataSource-Datentyp &#40;ASSL&#41;](relationaldatasource-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der darstellt, der eine [DataSource](../objects/datasource-element-assl.md) -Elements auf Grundlage einer relationalen Datenquelle.|  
|[ReportAction-Datentyp &#40;ASSL&#41;](reportaction-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Aktion darstellt, die einen [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Bericht generiert.|  
|[RowBinding-Datentyp &#40;ASSL&#41;](rowbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Bindung, auf die Zeilen einer Tabelle in darstellt eine [DataSourceView](../objects/datasourceview-element-assl.md) Element.|  
|[ScalarMiningStructureColumn-Datentyp &#40;ASSL&#41;](scalarminingstructurecolumn-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der darstellt, der eine [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) Element, das Skalare Werte als auch im Gegensatz zu den geschachtelten Tabellen zugeordneten enthält die [TableMiningStructureColumn](tableminingstructurecolumn-data-type-assl.md) Element geschachtelte Tabellen enthält.|  
|[StandardAction-Datentyp &#40;ASSL&#41;](standardaction-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine stellt [Aktion](../objects/action-element-assl.md) Element außer einer [DrillThroughAction](drillthroughaction-data-type-assl.md) Element oder ein [ReportAction](reportaction-data-type-assl.md) Element.|  
|[TableBinding-Datentyp &#40;ASSL&#41;](tablebinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Bindung mit einer Tabelle darstellt.|  
|[TableMiningStructureColumn-Datentyp &#40;ASSL&#41;](tableminingstructurecolumn-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der darstellt, der eine [MiningStructureColumn](miningstructurecolumn-data-type-assl.md) -Element, das im Gegensatz zu den skalaren Werten, die zugeordneten geschachtelte Tabellen enthalten die [ScalarMiningStructureColumn](scalarminingstructurecolumn-data-type-assl.md) Element die Skalare Werte enthält.|  
|[TabularBinding-Datentyp &#40;ASSL&#41;](tabularbinding-data-type-assl.md)|Definiert einen abstrakten abgeleiteten Datentyp, der eine Bindung mit einem Tabellenelement wie einer Tabelle oder einer Cubedimension darstellt.|  
|[TimeAttributeBinding-Datentyp &#40;ASSL&#41;](timebinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der für generierte Elemente in einer Serverzeitdimension (z. B. die Schlüsselspalten eines Attributs) eine "Platzhalter"-Bindung darstellt.|  
|[TimeBinding-Datentyp &#40;ASSL&#41;](timebinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine Bindung an Zeiträume darstellt.|  
|[Translation-Datentyp &#40;ASSL&#41;](translation-data-type-assl.md)|Definiert einen Grunddatentyp, der eine lokalisierte Übersetzung darstellt.|  
|[UserDefinedGroupBinding-Datentyp &#40;ASSL&#41;](userdefinedgroupbinding-data-type-assl.md)|Definiert einen abgeleiteten Datentyp, der eine benutzerdefinierte Gruppierung für ein Attribut darstellt.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Element-Hierarchie &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
