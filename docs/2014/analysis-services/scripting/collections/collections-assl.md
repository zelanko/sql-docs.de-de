---
title: Auflistungen (ASSL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- collections [Analysis Services Scripting Language]
- Analysis Services Scripting Language, collections
- ASSL, collections
ms.assetid: 072b8c6b-1550-4cab-ae64-ba0e3e60b059
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9f549a8d84f356b9315cdf3ec03ee41234e4dd0d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199710"
---
# <a name="collections-assl"></a>Auflistungen (ASSL)
  In diesem Referenzabschnitt finden Sie Syntax- und Nutzungsinformationen für jedes Element, das im ASSL-Schema (Analysis Services Scripting Language) als Sammlung agiert.  
  
 Obwohl das ASSL-Schema nur XML-Elemente enthält, entsprechen die Elemente, die in diesem Abschnitt beschrieben werden, aus der Sicht eines Entwicklers Auflistungen von Objekten wie `Dimensions`- und `Cubes`-Auflistungen.  
  
 Auflistungen sind meistens Auflistungen von Objektelementen, bei denen ein Substantiv im Plural die Auflistung benennt (z. B. `Cubes`) und bei denen die Auflistung Elemente enthält, die von dem gleichen Substantiv im Singular benannt werden (z. B. `Cube`).  
  
 In einigen Fällen weicht das Schema von dieser allgemeinen Regel ab. Beispielsweise enthält die `ClassifiedColumns`-Auflistung `ClassifiedColumnID`-Elemente.  
  
 In anderen Fällen enthält eine Auflistung Elemente, die nicht Objekten, sondern Objekteigenschaften entsprechen. Zum Beispiel enthält die `Aliases`-Auflistung `Alias`-Eigenschaften, von denen jede ein einfacher Zeichenfolgewert ist.  
  
|Element|Description|  
|-------------|-----------------|  
|[Konten Element &#40;ASSL&#41;](accounts-element-assl.md)|Enthält die Auflistung der Kontotypen, die in definierten eine [Datenbank](../objects/database-element-assl.md) Element.|  
|[Actions-Element &#40;ASSL&#41;](actions-element-assl.md)|Enthält die Auflistung der Aktionen für eine [Cube](../objects/cube-element-assl.md) oder [Perspektive](../objects/perspective-element-assl.md) Element.|  
|[AggregationDesigns-Element &#40;ASSL&#41;](aggregationdesigns-element-assl.md)|Enthält die Auflistung der Aggregationsentwürfe, die für mehrere Partitionen in einer Datenbank freigegeben sein können.|  
|[AggregationInstances-Element &#40;ASSL&#41;](aggregationinstances-element-assl.md)|Enthält die Auflistung der aggregationsinstanzen, die definiert sind eine [Partition](../objects/partition-element-assl.md) Element.|  
|[Aggregations-Element &#40;ASSL&#41;](aggregations-element-assl.md)|Enthält die Auflistung von Aggregationen für definierte ein [AggregationDesign](../objects/aggregationdesign-element-assl.md) Element.|  
|[AlgorithmParameters-Element &#40;ASSL&#41;](algorithmparameters-element-assl.md)|Enthält die Auflistung der Parameter für den Algorithmus ein, die eine [MiningModel](../objects/miningmodel-element-assl.md) Element.|  
|[Aliases-Element &#40;ASSL&#41;](aliases-element-assl.md)|Enthält die Auflistung der [Alias](../properties/alias-element-assl.md) Elemente, die zu einem [Konto](../objects/account-element-assl.md) Element|  
|[AllMemberTranslations-Element &#40;ASSL&#41;](translations-element-assl.md)|Enthält die Auflistung der [Übersetzung](../objects/translation-element-assl.md) Elemente für die Beschriftung des alle-Elements ein [Hierarchie](../objects/hierarchy-element-assl.md) Element.|  
|[Annotations-Element &#40;ASSL&#41;](annotations-element-assl.md)|Enthält die Auflistung der [Anmerkung](../objects/annotation-element-assl.md) Elemente, mit dem übergeordneten Element verknüpft sind.|  
|[Assemblies-Element &#40;ASSL&#41;](assemblies-element-assl.md)|Enthält die Auflistung der [Assembly](../objects/assembly-element-assl.md) Elemente, die zu einem [Server](../objects/server-element-assl.md) Element oder ein [Datenbank](../objects/database-element-assl.md) Element.|  
|[AttributeAllMemberTranslations-Element &#40;ASSL&#41;](attributeallmembertranslations-element-assl.md)|Enthält die Auflistung von Übersetzungen für die Beschriftung des "Alle"-Elements der Dimension.|  
|[AttributePermissions-Element &#40;ASSL&#41;](attributepermissions-element-assl.md)|Enthält die Auflistung der Attributberechtigungen für ein einzelnes [Rolle](../objects/role-element-assl.md) Element auf einer spezifischen Dimension eine [Cube](../objects/cube-element-assl.md) Element.|  
|[AttributeRelationships-Element &#40;ASSL&#41;](relationships-element-assl.md)|Enthält die Auflistung der [AttributeRelationship](../objects/attributerelationship-element-assl.md) Elemente für das Attribut.|  
|[Attributes-Element &#40;ASSL&#41;](attributes-element-assl.md)|Enthält die Auflistung der Attribute für die verknüpfte Dimension.|  
|[Element blockiert &#40;ASSL&#41;](blocks-element-assl.md)|Enthält die Auflistung der Blöcke mit binären Daten, die den binären Inhalt darstellen einer [ClrAssemblyFile](../data-type/clrassemblyfile-data-type-assl.md) Element.|  
|[CalculationProperties-Element &#40;ASSL&#41;](calculationproperties-element-assl.md)|Enthält die Auflistung der [CalculationProperty](../objects/calculationproperty-element-assl.md) Elemente, die zu einem [MdxScript](../objects/mdxscript-element-assl.md) Element.|  
|[Calculations-Element &#40;ASSL&#41;](calculations-element-assl.md)|Enthält die Auflistung der [PerspectiveCalculation](../data-type/perspectivecalculation-data-type-assl.md) Elemente, die zu einem [Perspektive](../objects/perspective-element-assl.md) Element.|  
|[CellPermissions-Element &#40;ASSL&#41;](cellpermissions-element-assl.md)|Enthält die Auflistung der Berechtigungen für Zellen im zugehörigen [Cube](../objects/cube-element-assl.md) Element.|  
|[ClassifiedColumns-Element &#40;ASSL&#41;](columns-element-assl.md)|Enthält die Auflistung der verknüpften Spalten, die von klassifiziert werden die [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md) Element.|  
|[Columns-Element &#40;ASSL&#41;](columns-element-assl.md)|Enthält die Auflistung der Spalten, die mit dem übergeordneten Element verknüpft sind.|  
|[Befehle Element &#40;ASSL&#41;](commands-element-assl.md)|Enthält die Auflistung der [Command](../objects/command-element-assl.md) -Elemente, die mit einem [MdxScript](../objects/mdxscript-element-assl.md) -Element verknüpft sind.|  
|[CubePermissions-Element &#40;ASSL&#41;](cubepermissions-element-assl.md)|Enthält die Auflistung der Berechtigungen für eine [Cube](../objects/cube-element-assl.md) Element.|  
|[Cubes-Element &#40;ASSL&#41;](cubes-element-assl.md)|Enthält die Auflistung der [Cube](../objects/cube-element-assl.md) Elemente, die zu einem [Datenbank](../objects/database-element-assl.md) Element.|  
|[DatabasePermissions-Element &#40;ASSL&#41;](databasepermissions-element-assl.md)|Enthält die Auflistung der [DatabasePermission](../objects/databasepermission-element-assl.md) Elemente, die zu einem [Datenbank](../objects/database-element-assl.md) Element.|  
|[Databases-Element &#40;ASSL&#41;](databases-element-assl.md)|Enthält die Auflistung der [Datenbank](../objects/database-element-assl.md) Elemente, die zu einem [Server](../objects/server-element-assl.md) Element.|  
|[DataSources-Element &#40;ASSL&#41;](datasources-element-assl.md)|Enthält die Auflistung der [DataSourcePermission](../objects/datasourcepermission-element-assl.md) Elemente, die zu einem [DataSource](../data-type/datasource-data-type-assl.md) -Datentyp.|  
|[DataSourcePermissions-Element &#40;ASSL&#41;](datasourcepermissions-element-assl.md)|Enthält die Auflistung der [DataSource](../objects/datasource-element-assl.md) Elemente, die zu einem [Datenbank](../objects/database-element-assl.md) Element.|  
|[DataSourceViews-Element &#40;ASSL&#41;](datasourceviews-element-assl.md)|Enthält die Auflistung der [DataSourceView](../objects/datasourceview-element-assl.md) Elemente, die zu einem [Datenbank](../objects/database-element-assl.md) Element.|  
|[DimensionPermissions-Element &#40;ASSL&#41;](dimensionpermissions-element-assl.md)|Enthält die Auflistung der Berechtigungen für eine [Dimension](../objects/dimension-element-assl.md) Element oder ein [CubePermission](../objects/cubepermission-element-assl.md) Element.|  
|[Dimensions-Element &#40;ASSL&#41;](dimensions-element-assl.md)|Enthält die Auflistung der Dimensionen, die mit dem übergeordneten Element verknüpft sind.|  
|[Events-Element &#40;ASSL&#41;](events-element-assl.md)|Definiert die Auflistung von Ereignis-Elementen, die erfasst werden eine [Ablaufverfolgung](../objects/trace-element-assl.md).|  
|[Dateien Element &#40;ASSL&#41;](files-element-assl.md)|Enthält die Auflistung der [Datei](../objects/file-element-assl.md) Elemente, aus denen ein [ClrAssembly](../data-type/assembly-data-type-assl.md) Element.|  
|[ForeignKeyColumns-Element &#40;ASSL&#41;](keycolumns-element-assl.md)|Enthält die Sammlung der Spalten, die den Join mit der übergeordneten Tabelle für eine relationale Datenquelle identifizieren.|  
|[Element für Gruppen &#40;ASSL&#41;](groups-element-assl.md)|Enthält die Auflistung der Gruppen von Elementen, die an ein Attribut gebunden sind.|  
|[Hierarchies-Element &#40;ASSL&#41;](hierarchies-element-assl.md)|Enthält die Auflistung der [Hierarchie](../objects/hierarchy-element-assl.md) Elemente, mit dem übergeordneten Element verknüpft sind.|  
|[IncrementalProcessingNotifications-Element &#40;ASSL&#41;](incrementalprocessingnotifications-element-assl.md)|Enthält die Auflistung der [IncrementalProcessingNotification](../objects/incrementalprocessingnotification-element-assl.md) Elemente, die Informationen zum Bereitstellen der [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Element zu Abfragen ausgeführt werden, um den Fortschritt zu bestimmen. inkrementelle Verarbeitung.|  
|[KeyColumns-Element &#40;ASSL&#41;](keycolumns-element-assl.md)|Enthält die Auflistung der [KeyColumn](../objects/column-element-assl.md) -Elementdefinitionen für ein übergeordnetes Objekt.|  
|[KPIs-Element &#40;ASSL&#41;](kpis-element-assl.md)|Enthält die Auflistung der [Kpi](../objects/kpi-element-assl.md) Elemente, mit dem übergeordneten Element verknüpft sind.|  
|[Ebenen Element &#40;ASSL&#41;](levels-element-assl.md)|Enthält die Auflistung der [Ebene](../objects/level-element-assl.md) Elemente in einem [Hierarchie](../objects/hierarchy-element-assl.md) Element.|  
|[MdxScripts-Element &#40;ASSL&#41;](mdxscripts-element-assl.md)|Enthält die Auflistung der [MdxScript](../objects/mdxscript-element-assl.md) Elemente, die zu einem [Cube](../objects/cube-element-assl.md) Element.|  
|[MeasureGroups-Element &#40;ASSL&#41;](measuregroups-element-assl.md)|Enthält die Auflistung der [MeasureGroup](../objects/group-element-assl.md) Elemente, mit dem übergeordneten Element verknüpft sind.|  
|[Measures-Element &#40;ASSL&#41;](measures-element-assl.md)|Enthält die Auflistung der [Measure](../objects/measure-element-assl.md) Elemente, mit dem übergeordneten Element verknüpft sind.|  
|[Members-Element &#40;ASSL&#41;](members-element-assl.md)|Enthält die Auflistung der [Member](../objects/member-element-assl.md) -Elemente des übergeordneten Elements.|  
|[MiningModelPermissions-Element &#40;ASSL&#41;](miningmodelpermissions-element-assl.md)|Enthält die Auflistung der Berechtigungen für eine [MiningModel](../objects/miningmodel-element-assl.md) Element.|  
|[MiningModels-Element &#40;ASSL&#41;](miningmodels-element-assl.md)|Enthält die Auflistung der [MiningModel](../objects/miningmodel-element-assl.md) Elemente, die zu einem [MiningStructure](../objects/miningstructure-element-assl.md).|  
|[MiningStructurePermissions-Element &#40;ASSL&#41;](miningstructurepermissions-element-assl.md)|Enthält die Auflistung der Berechtigungen für eine [MiningStructure](../objects/miningstructure-element-assl.md) Element.|  
|[MiningStructures-Element &#40;ASSL&#41;](miningstructures-element-assl.md)|Enthält die Auflistung der [MiningStructure](../objects/miningstructure-element-assl.md) Elemente in einem [Datenbank](../objects/database-element-assl.md) Element.|  
|[ModelingFlags-Element &#40;ASSL&#41;](modelingflags-element-assl.md)|Enthält die Auflistung der [ModelingFlag](../objects/modelingflag-element-assl.md) Elemente für eine Spalte in einer [MiningStructure](../objects/miningstructure-element-assl.md) oder [MiningModel](../objects/miningmodel-element-assl.md).|  
|[Namingtemplatetranslation-Element &#40;ASSL&#41;](namingtemplatetranslations-element-assl.md)|Stellt eine Auflistung lokalisierter Übersetzungen für die [NamingTemplate](../properties/namingtemplate-element-assl.md) -Element des übergeordneten [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md).|  
|[Partitionen Element &#40;ASSL&#41;](partitions-element-assl.md)|Enthält die Auflistung der [Partition](../objects/partition-element-assl.md) Elemente ein, die eine [MeasureGroup](../objects/group-element-assl.md) Element oder die Auflistung der partitionsbindungen, eine Out-of-line [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-out-of-line-assl.md)Element.|  
|[Perspectives-Element &#40;ASSL&#41;](perspectives-element-assl.md)|Enthält die Auflistung der [Perspektive](../objects/perspective-element-assl.md) Elemente, die zu einem [Cube](../objects/cube-element-assl.md) Element.|  
|[QueryNotifications-Element &#40;ASSL&#41;](querynotifications-element-assl.md)|Enthält die Auflistung der [QueryNotification](../objects/querynotification-element-assl.md) Elemente, die Informationen zum Bereitstellen der [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Element zu Abfragen ausgeführt werden, um zu bestimmen, ob eine Datenquelle geändert wurde.|  
|[ReportFormatParameters-Element &#40;ASSL&#41;](reportformatparameters-element-assl.md)|Enthält die Auflistung der [ReportFormatParameter](../objects/reportformatparameter-element-asl.md) -Elemente für ein [ReportAction](../data-type/action-data-type-assl.md) -Element.|  
|[ReportParameters-Element &#40;ASSL&#41;](reportparameters-element-assl.md)|Enthält die Auflistung der [ReportParameter](../objects/reportparameter-element-assl.md) Elemente für eine [ReportAction](../data-type/action-data-type-assl.md) Element.|  
|[Roles-Element &#40;ASSL&#41;](roles-element-assl.md)|Enthält die Auflistung der [Role](../objects/role-element-assl.md) -Elemente, die unter dem übergeordneten Element definiert sind.|  
|[ServerProperties-Element &#40;ASSL&#41;](serverproperties-element-assl.md)|Enthält die Auflistung der [ServerProperty](../objects/serverproperty-element-assl.md) Elemente, die zu einem [Server](../objects/server-element-assl.md) Element.|  
|[TableNotifications-Element &#40;ASSL&#41;](tablenotifications-element-assl.md)|Enthält die Auflistung der [TableNotification](../objects/tablenotification-element-assl.md) Elemente, die Informationen für die [ProactiveCaching](../objects/proactivecaching-element-assl.md) -Element Informationen über Tabellen oder Sichten in einer Datenquelle, die geändert wurden.|  
|[Führt eine Ablaufverfolgung für Element &#40;ASSL&#41;](traces-element-assl.md)|Enthält die Auflistung der [Trace](../objects/trace-element-assl.md) -Elemente, die zu einem [Server](../objects/server-element-assl.md) -Element gehören.|  
|[Translations-Element &#40;ASSL&#41;](translations-element-assl.md)|Enthält die Auflistung der [Übersetzung](../objects/translation-element-assl.md) Elemente, mit dem übergeordneten Element verknüpft sind.|  
|[UnknownMemberTranslations-Element &#40;ASSL&#41;](unknownmembertranslations-element-assl.md)|Enthält die Auflistung der Übersetzungen für die Beschriftung des der [UnknownMember](../properties/unknownmember-element-assl.md) -Elements einer Dimension.|  
  
## <a name="see-also"></a>Siehe auch  
 [Analysis Services Scripting Language-XML-Element-Hierarchie &#40;ASSL&#41;](../analysis-services-scripting-language-xml-element-hierarchy-assl.md)  
  
  
